---
title: "Boot problems with Windows 8"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by riccardo2 on 2013-08-12
Hello everybody, I have got few problems booting Ubuntu after i installed it on a Windows 8 laptop. At the start-up it doesn't allow me to chose between windows 8 and Ubuntu. It simply starts with windows 8... I can select Ubuntu only from the BIOS and I have already tried to run "boot-repair" but I didn't solve the problem. I attach the code from "boot-repair" that may help someone to help me and other people with the same problems: [http://paste.ubuntu.com/5978561/](http://paste.ubuntu.com/5978561/)
Thanks to everybody.
RiccardoB

---

### Post by Boab1993 on 2013-08-12
Hi riccardo2,

A very common problem on here, a problem with UEFI, try here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2013-08-13
Does your system boot Windows with secure boot off?
Is the issue with Ubuntu a black screen or video issue. Then what video chip do you have. 

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)


 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

