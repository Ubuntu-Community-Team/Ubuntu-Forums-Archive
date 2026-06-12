---
title: "Transcriber"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by kozhi on 2011-10-28
I had Transcriber installed under Ubuntu 11.04. On upgrading to 11.10, this is gone, and the Ubuntu Software Center doesn't list transcriber so that I might install it again. Under synaptic, it is listed, but on checking for installation, it shows an error that dependencies are not met. Is downloading from sourceforge the only option? Any advise on how to reinstall Transcriber in 11.10? I use it a lot for my research work and am at a loss really. Thanks.

---

### Post by hectorbernal on 2012-04-22
I can see you asked for long time ago but I answer anyway for those who would look for an answer to this. It took me a while to find help to install transcriber in 11.10.
Check the link:
[http://packages.ubuntu.com/lucid/amd64/transcriber/download](http://packages.ubuntu.com/lucid/amd64/transcriber/download)

---

### Post by herteljt on 2012-04-26
> **hectorbernal said:**
> I can see you asked for long time ago but I answer anyway for those who would look for an answer to this. It took me a while to find help to install transcriber in 11.10.
Check the link:
[http://packages.ubuntu.com/lucid/amd64/transcriber/download](http://packages.ubuntu.com/lucid/amd64/transcriber/download)

Thanks Hector!

Note that in order to get the audio playback to work properly I have had to use PulseAudio OSS Wrapper. 

```
padsp transcriber
```

---

