---
title: "[SOLVED] I can't install ubuntu on va&#305;o SVE1513Y1ESI"
date: 2013-08-11
forum: Installation &amp; Upgrades
---

### Post by entreri2 on 2013-08-11
[B]Hi,

I have va&#305;o SVE1513Y1ESI laptop it has win8 but i don't install ubuntu. i try a lot of time.

I am trying ubuntu 12.04 and i take operating system not found error i see only this article with black screen.

And try ubuntu 13. Firstly i see black screen and install options when i select install option and then the screen is purple and  damaged i cant see anythink. After that I install with nomodeset code but it isn't work this time screen isn't damaged but i see only ubuntu logo under the logo points  change its color i am waiting,  waiting finaly  install is stop. install  don't contuine,  please help me.[/B]

---

### Post by oldfred on 2013-08-11
Did this system come with Windows 8 installed by vendor?

Are the video issue you get from the installer, or after you have installed it onto your system?

What video card/chip does this system have? Usually nomodeset will get you into system so you can install correct driver, but sometime additional boot parameters are required.

Some other Sony, may have similar settings even if different model.

 Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)
Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
 Sony SVE15125CXS Notebook  Only could Install in BIOS mode, Boot-Repair to UEFI dual boot works
[http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570](http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570)
Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help UEFI screens shown
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)

---

### Post by entreri2 on 2013-08-11
Yes, win8 installed by vendor. 

video issue  i get from installer

&#305;t have  AMD Radeon&#8482; HD 7650M  video card

---

### Post by oldfred on 2013-08-11
I do not know AMD, and i think you have one of the newest versions. Is it also dual video with Intel?

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by entreri2 on 2013-08-12
i solved this problem thanks for your all help



i do only turn off ufei mod i do this already and install screen is kile this: [http://j1308.hizliresim.com/1d/c/rcnd0.png](http://j1308.hizliresim.com/1d/c/rcnd0.png)  but there is onethink i must do i do not raise the first row  internal optical diks driver on Boot Priority menu you can do with F5 

[http://t1308.hizliresim.com/1d/d/rd5wq.jpg](http://t1308.hizliresim.com/1d/d/rd5wq.jpg)  can you see this picture

---

### Post by oldfred on 2013-08-12
The first is tiny, but looks like a grub menu. If booting in UEFI mode you get the grub menu on the installer and after installing you get grub menu.
If you have grub menu you may need to add nomodeset. Shown in examples for boot after install. But use e on grub menu, scroll down to linux line, and replace quiet spash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

