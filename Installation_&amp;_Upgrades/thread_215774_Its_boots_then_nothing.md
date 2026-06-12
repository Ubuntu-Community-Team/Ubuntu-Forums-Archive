---
title: "Its boots then nothing"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by Mazehero55 on 2006-07-14
Okey I have a major problem When trying to boot unbuntu, For some strange reason after it tries to boot, and it finishes the loading screen it goes to a blank screen and theres the blinking thing for typing up in the upper left corner, but it's not blinking it's like an underscore ex:" _ ". I've tried other distributions too, like LinSpire and it's the same thing. But when I try DSL or Puppy linux it works. But I don't want DSL I want Ubuntu, or xubuntu or something. It does it with the live cd too, it does the load screen then it's just blank. Thats it, nothing more. The weird thing though is I tried it on my brother's computer too, It's the exact same computer model from dell. The only difference is that mine has more memory, and a better graphics card. And it works on his computer. 
I would really appreciate it if someone new how to fix this, this is the only thing keeping me from going to Linux forever. And another weird thing is I think it used to work on mine too, but now it dosn't. PLease help me.](*,)

---

### Post by Mazehero55 on 2006-07-14
hello can someone please help me, I really need help with this. Is there any ideas at all. I posted this today and already it's been bumped off the first page with "0" replies. I thought for sure the people at the main site would be able to help. All I need is one answer. Ubuntu used to work on this computer but doesn't anymore. Even after a reformatting or the hardrive.

Anything?

---

### Post by Lord Illidan on 2006-07-14
What is the make of your graphics card?

---

### Post by Mazehero55 on 2006-07-14
Her's everything system info says about it. 

Name	RAGE XL  PCI
PNP Device ID	PCI\VEN_1002&DEV_4752&SUBSYS_80081002&REV_27\4&24AB0D93&0&48F0
Adapter Description	RAGE XL  PCI
Adapter RAM	8.00 MB 
Resolution	1024 x 768 x 60 hertz
Bits/Pixel	32

My computer's other specs are:

System Manufacturer	Dell Computer Corporation
System Model	L700C
System Type	X86-based PC
Processor	x86 Family 6 Model 8 Stepping 6 GenuineIntel ~697 Mhz
BIOS Version/Date	Intel Corp. A11, 3/7/2001
SMBIOS Version	2.3
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "5.1.2600.1106 (xpsp1.020828-1920)"
Total Physical Memory	384.00 MB

Does this help at all?
Thank you so much

---

### Post by Lord Illidan on 2006-07-14
Try booting failsafe option.

And see if you can run

```
nano /etc/X11/xorg.conf
``` at the terminal.

Try changing the driver of Section Device to "vesa".

---

### Post by Mazehero55 on 2006-07-14
sorry I updated the specs dang system information got the video card specs all wrong, I fixed it. Does that change anything? 

if not then what is that supposed to do?

thanks.

---

### Post by Mazehero55 on 2006-07-15
okey I tried what you said but it just comes up with an error message saying it can't find certain things, like screens or something? any ideas?

I tried puppy linux again and it said it was vesa so maybe your right, but there's probably other things to do to make it vesa. 

oh yeah I also noticed that it didn't recognized my better graphics card, it just lists the built in one in my motherboard, a crappy 4 mg one.

---

