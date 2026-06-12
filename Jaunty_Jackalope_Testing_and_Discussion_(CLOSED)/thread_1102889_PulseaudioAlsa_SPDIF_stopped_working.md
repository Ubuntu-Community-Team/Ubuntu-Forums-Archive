---
title: "Pulseaudio/Alsa SPDIF stopped working"
date: 2009-03-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by grigio on 2009-03-22
As in the title.
The flag IEC958 is ON and the volume is at the maximun level


The Audio works on stereo

lspci -vv

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 82fe
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at fe8f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by rperkins on 2009-03-22
here is my previous post.  looks like you have a similar mobo

[http://ubuntuforums.org/showthread.php?t=1100747](http://ubuntuforums.org/showthread.php?t=1100747)

with the latest kernel update uname -r 2.6.28-11-generic
i didnt try the custom model in modprobe.d.
i just installed a fresher compiled as mentioned in the above linked post.

you never mentioned if it was working on the previous kernel or if you just came to jaunty.  I also am assuming your are using the spdif at the rear of the mobo, not the header on the midpoint ( if your model has that one like mine does )

---

### Post by grigio on 2009-03-22
I compiled 'n' installed it but the situation it's the same

---

### Post by grigio on 2009-03-24
up

---

### Post by rperkins on 2009-03-24
hi
did you try to force the model number as i mentioned in the post that i linked to.

did you recompile the kernel, or newer alsa kernel modules ?

---

### Post by grigio on 2009-03-24
I compiled Alsa and now I forced the driver as in your thread.

Thanks, now it works again!

---

