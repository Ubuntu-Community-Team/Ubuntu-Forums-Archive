---
title: "No sound in 2.6.31"
date: 2009-07-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by durand on 2009-07-05
As of upgrading the kernel to the latest, my sound has completely stopped working. PA and alsa don't complain about a lack of sound drivers or anything like that and I don't actually get any errors but nothing comes out of my speakers. This has got to be a kernel problem because it works fine if I use 2.6.30 instead.

```
durand@Deuterium ~> lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

dmesg doesn't show any errors.

This is on a Dell Vostro laptop.

Would anyone be able to help?
Thanks!

---

### Post by Joe_Bishop on 2009-07-05
**sudo adduser $USER audio** should help

---

### Post by lithorus on 2009-07-05
What does 'lspci -v -s 00:1b.0' output?
What does 'cat /proc/asound/cards' output?
If you do 'alsamixer -D hw' which controls do you have and are some of them muted?

---

### Post by plun on 2009-07-05
With my Laptop, Intel based, PCM was muted and also volume to zero.

---

### Post by durand on 2009-07-05
> durand@Deuterium ~> sudo lspci -v -s 00:1b.0
[sudo] password for durand: 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Device 0275
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f8300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

> durand@Deuterium ~> cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8300000 irq 22


[IMG]http://files.getdropbox.com/u/336801/Screenshot-durand%40Deuterium%3A%20alsamixer%20-D%20hw.png[/IMG]

---

### Post by durand on 2009-07-05
> **plun said:**
> With my Laptop, Intel based, PCM was muted and also volume to zero.

That was the case when I first booted back to 2.6.30 after the update but not anymore.

---

### Post by budluva04 on 2009-07-05
ok, quit screwing with alsa mixer....

$ sudo apt-get install pavucontrol

^^ pulse audio volume control

try playing with the sliders in pavucontrol...then report back if your problem still persists

---

### Post by durand on 2009-07-05
I pretty much only use pavucontrol for volume control. I'm 99% sure that the problem lies with the kernel and not pulseaudio.

PA is exactly the same as in 2.6.30, and streams cause the mixer levels to rise and fall as normal, as if sound is working perfectly fine.

---

### Post by budluva04 on 2009-07-05
usually playing with the volume sliders going from 0 to 100 gets sound working, also i had a problem with no audio coming out, but the stream showed it was outputting audio, a reboot fixed it, have you rebooted lately?

---

### Post by durand on 2009-07-05
Many times :( I'm waiting for a new kernel package. I think the last one missed off my sound drivers.

---

### Post by durand on 2009-07-05
I already came across that in another thread and it didn't change anything.
> durand@Deuterium ~> sudo adduser $USER audio
[sudo] password for durand: 
The user `durand' is already a member of `audio'.

Am I the only one experiencing this problem?

---

### Post by lithorus on 2009-07-06
Have you tried 2.6.31-rc2 from here ?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc2/)

It seems that it's been fixed in rc2 :
> ALSA: hda - Add missing initializations for ALC268 and ALC269
Hopefully rc2 should come to karmic soon.

---

### Post by durand on 2009-07-06
Thanks for the heads up! I hope that clears it up. BTW, how did Joe Bishop's post become #2?

---

### Post by durand on 2009-07-07
My sound lives again with the latest kernel. Thanks everyone!

---

