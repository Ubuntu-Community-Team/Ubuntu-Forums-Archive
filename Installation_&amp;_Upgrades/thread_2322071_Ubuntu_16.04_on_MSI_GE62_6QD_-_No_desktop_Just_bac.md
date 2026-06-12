---
title: "Ubuntu 16.04 on MSI GE62 6QD - No desktop Just background post login"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by lawrence-john-wyatt on 2016-04-26
Has anyone got Ubuntu 16.04 running on this laptop or similar in the series (i7 6700HQ, Nvidia gtx 960m).  I can install Ubuntu mate using the nomodeset argument on the linux line in the grub menu and turning off secureboot, speedstep and fastboot.  It works fine without any grub args post the nvidia and intel driver install but with Unity I can get past the login screen but just get a blank background and the odd notification window post login nothing more.

Thanks

---

### Post by rodrigo.garcia.val on 2016-04-26
Similar situation here. I attach some info in case it can be of use:

"I have installed Ubuntu 16.04 on a MSI PE60 6QE (Nvidia GTX960M, I7 Skylake). However, it is not working well.

I have tried all these steps with the "Prime select intel", nvidia drivers 361 and 364 options; and also trying with the 4.4-021 and the recent 4.6 kernels.

-I can make it work with "ACPI=off", not with "ACPI=ht". It works well, but it is not a secure mode, I think, as I have to use a lot of CPU power. Funny thing, the touchpad is not detected with this option, and the same happens with the Fn+Key combinations. External mouse is detected and works well.

-I can make it work with the "nomodeset idle=nomwait" option. It enters however in the login screen loop. With this option enabled, the touchpad is detected. If I use the nvidia driver 364, the refresh of the screen is very low, it "blinks" a lot. I also get the "wifi: unsupported splx structure" error at the beginning of the loading screen and continuous "pcieport... : receiver error".  does not help, also.

-If I use the "nomodeset idle=nomwait ACPI=off" I can go to the desktop menu... although it does not load, I just can see some icons while they blink among different positions in the screen."


Can someone help us? :/

---

### Post by gentra-a on 2016-04-26
I can install the OS almost fully-stable by using these:
- SecureBoot off
- kernel options "acpi=off" on installation and booting

However I can't install the NVIDIA Driver. If I install the nvidia driver the computer won't boot up after grub only showing blank screen.

My computer: MSI GE62 6QC, UbuntuGNOME 16.04

---

### Post by oldfred on 2016-04-26
Different users have posted different solutions, not sure what may be correct.

 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

### Post by erkanea on 2016-04-27
I am using GL62 6QC (&#305;7 6700HQ - 940MX). I can install and run Ubuntu 16.04 fine although there are some problems with GPU drivers and suspend-resume. I am trying to find solution in [this]("http://ubuntuforums.org/showthread.php?t=2322244") thread.

---

### Post by lawrence-john-wyatt on 2016-04-27
Thanks for the replies, I will have another go at it, see if any of those links help.

---

### Post by jag-f on 2016-05-28
> **gentra-a said:**
> I can install the OS almost fully-stable by using these:
- SecureBoot off
- kernel options "acpi=off" on installation and booting

However I can't install the NVIDIA Driver. If I install the nvidia driver the computer won't boot up after grub only showing blank screen.

My computer: MSI GE62 6QC, UbuntuGNOME 16.04


----

I had a similar option.  Go here to address, the advice stepheny did the trick:
[http://ubuntuforums.org/showthread.php?t=2322942&p=13481566](http://ubuntuforums.org/showthread.php?t=2322942&p=13481566)

---

