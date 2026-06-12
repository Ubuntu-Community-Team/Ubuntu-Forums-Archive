---
title: "sound from 9.10 karmic to 9.04"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by marginean.m on 2009-09-23
Hi all. I am fairly new to linux so please be gentile... :)

I'm runing ubuntu 9.04 now on a Toshiba Satellite (A200 1M4) laptop. Everything runs as it should except the sound. It seems that ubuntu can't tell if I have the headphones inserted or not and the sound is outputed on both the speakers and the headphones. 
Of course, I've made some googleing about this issue and found some possible solutions. Bottom line is...none worked. 
Anyhow, after the first alpha from 9.10 karmic was out I decided to give it a try. As expected, it seemed a little unstable (this is why I didn't keep it) **but** the initial sound issue was no more. So now I'm thinking to port the sound driver from 9.10 to 9.04 (if this is even possible) but as I'm new to this I would need some guidance. 
I would be very grateful to anyone who can help me.
Thanks!



this is my ***aplay -l*** output:

 ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and my ***lspci -v*** :

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff02
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

