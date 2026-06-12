---
title: "Help with NVIDIA drivers - not working after update"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by Mercedes300 on 2008-07-02
Hello, I am having trouble getting NVIDIA drivers installed on ubuntu Hardy after a distro update last week.

After the update, it rebooted in low graphics mode, and said that my card and screen could not be detected properly. I've read to load the "Proprietary Drivers" from System - Administration - Proprietary Drivers Manager, but that utility doesn't appear to be there (is there some code I can type to launch it?).

I've tried to install the NVIDIA driver from [here]("http://www.nvidia.com/object/linux_display_ia32_173.14.09.html") but it says that libc is not installed.

I guess I'm just wondering if there is an easy way to do this.

All help is much appreciated!

Ed

--Crappy Computer Specs--
Motherboard = Abit ATI-Max 2
CPU = Intel Celeron 2.0 GHz
GPU = Asus N6600
Monitor = Samsung 713n
HDD = Western Digital WD200
Ubuntu Hardy Heron 8.04

---

### Post by johniv on 2008-07-02
Hey! This happened to me too so i can relate.
I ended up starting over by reinstalling the OS, but i hope you don't need to do that!

Later i found out that it was probably caused by a conflict between the drivers. SO, you installed the nvidia driver and you made another one angry?

Why are you going after the nvidia driver? If it's for visual effects you don't need it.

Good luck!
John

---

### Post by Mercedes300 on 2008-07-02
So far I havn't installed anything other than the "propriatary driver" segjested by the install (which was running fine for about a month - untill the update a mensioned) now I can go in to System - Administration - Hardware Drivers, and it doesn't say anything is installed. So I guess it threw out the driver it had?

---

### Post by oldsoundguy on 2008-07-02
try installing using Envy (third party program)

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Worked for me on three Gutsy machines.  (and have had to re-install using the program following a kernel update .. still worked AGAIN)

Did have to go back into xorg and re comment for the screen rotation. but that was no big deal.

---

### Post by dave373 on 2008-07-03
I have just managed to get my nvidia 6200 working after many hours of trying everything... including apt-removing everything related to nvidia, installing and uninstalling envyng, I was pulling my hair out..

every time I restarted, I was getting the same "low graphics mode" X error, and it didn't matter what settings I made, it would not work.

The end result.. remove every mention of xorg.conf in /etc/X11/
that's right... everything!!! ie. rm -f xorg.conf*

At this stage, I figured I had nothing to lose.. on the next GDM restart, it was all working...

Please post if this works for you too...

---

### Post by Mercedes300 on 2008-07-03
Thanks oldsoundguy! That worked like a charm!

Also, when I was going threw the install how to for envy, I noticed that the repository for restricted proprietary drivers was disabled. Enabling them didn't appear to do anything, but it might be something to look into if you have this problem and Envy doesn't work.

Cheers

P.S. Thanks everyone else!

---

