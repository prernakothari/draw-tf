# Network Architecture

The basic structure of a DRAW network is similar to that of other variational auto-encoders: an encoder network determines
a distribution over latent codes that capture salient information about the input data; a decoder network receives
samples from the code distribuion and uses them to condition its own distribution over images.
However, there are three key differences,

1.  Firstly, both the encoder and decoder are recurrent networks in DRAW, so that a sequence
     of code samples is exchanged between them; moreover the encoder is privy to the decoder’s previous outputs, allowing
     it to tailor the codes it sends according to the decoder’s behaviour so far.

2. Secondly, the decoder’s outputs are successively added to the distribution that will ultimately generate
    the data, as opposed to emitting this distribution in a single step.

3. Dynamically updated attention mechanism is used to restrict both the input region observed by the encoder,
    and the output region modified by the decoder.

In simple terms, the network decides at each time-step “where to read” and “where to write” as well as “what to write”.
