---
title: "Reboot Loop"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by wja777 on 2008-03-26
I am trying to install 7.10 64 desktop on a new virgin machine (no other operating system).  When booting from the install CD and choosing install from the menu that appears the system will reboot after the "kernal alive..." message at the bottom of the screen.  This then repeats...

I was beginning to wonder if my hardware was too new??

What is funny is that i found an old install disk of 7.04 and was able to load the 64 bit desktop version on this same machine.  Once done, I performed the upgrade to 7.10 and after the update was complete and a reboot was required, I ran into the same exact problem..

I am trying to use this new system as a test bed for running Vmware server on a linux 64 bit install with more than 4 gigs of memory, problem is I can not install Vmware if I can't get the operating system to load....

Any suggestions would be helpful....

The system details are as follows:
Gigabyte GA-G33M-52L motherboard using Intel GMA 3100 on board videon (9m shared memory)
          Chipset Intel G33 & Intel ICH9
Intel Core 2 Duo E6550
Corsair DDR2 800 (2 x 2GB)
160 gb seagate SATA HDD
DVD-CDR PATA drive

Nothing else other than what is built into the MB is installed...

Thanks in advance...

---

### Post by Pumalite on 2008-03-26
Use the Alternate CD.(64 bit)

---

### Post by wja777 on 2008-04-04
OK, back from vacation and finally got a chance to try the Alternate CD.(64 bit).

choose install in text mode, and again after choosing this when the "kernal alive..." message shows up at the bottom (My guess is that it is trying to load the kernal?), the system will reboot...

I have also tried the 6.06 LTS version and have had similar issues....

I am still wondering if it is an issue with the hardware being either too new or not supported?  Maybe the chip set?  I am not over clocking and have all of the bios settings at normal settings...

I still find it odd that I was able to load 7.04 successfully, but the system would not run after updating...

Anyone had any experience with this combo of processor / video / mobo or chip set??

---

### Post by Pumalite on 2008-04-04
You say the system reboots at the end of the install.
Have you tried configuring your xserver?
sudo dpkg-reconfigure xserver-xorg

---

### Post by wja777 on 2008-04-05
The system reboots even before the install starts.  Here is a more detailed step by step of what happens, this is all pertaining to v7.10 (64 bit Desktop)

1.  After turning on the machine with the install disk in the CD, I get the "Start or Install Ubuntu" with the normal CD; "Install in text mode" with the alternative CD.

2.  After selecting "start or install" or "install in text mode", I see a "Loading Kernel" progress bar.

3.  Once the progress bar reaches 100% at the very bottom of my screen the following text appears:  

Kernel alive
Kernel direct mapping tables up to 130000000 @ 8000-e0000

about 5-10 seconds after displaying the above message, the system reboots and the process starts all over again.

I have successfully installed v7.04 previous to v7.10 on this same hardware in its same configuration (64 bit desktop).  I did this thinking that I had a bad v7.10 install disk (because of the reboot loop).  Once this install was complete it stopped booting after I performed all the updates/upgrades and once this was complete, the system fell into this same reboot trap as above minus the install part.  It seems that for some reason the kernel used in v7.10 does not like something in my hardware setup...??

I am in the process of re-installing 7.04 now and will report back...

---

### Post by Pumalite on 2008-04-05
You might want to try some boot parameters before giving up. Here are various guides and a collection of parameters to be tried alone or in different combinations:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
Try the most common first:
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791
It wouldn't hurt burning a new CD after doing md5sum on your iso, at 4x or less on CD-R, check CD integrity after burn and before install.

---

### Post by EE&amp;E on 2008-04-13
wja777, have you worked out what it was yet ?

I have a very similar problem...

I am just trying to install the 64 bit Desktop  Ubuntu v7.10 on a new computer.

But the install isn't working.

I get to select the to option to load or install and then the "Loading Linux Kernel" bit comes up, and goes to 100%, but then all I see is:

Kernel alive
Kernel direct mapping tables up to 100000000 @ 8000-d0000

this stays for a short time and then the computer reboots, and goes back round in this loop.

I saw the post saying to try the Alternate CD.(64 bit) but also saw that wja777 had the same problem even with that.

My system is:
Gigabyte GA-G33M-S2L motherboard  (same board as wja777) ??
Intel Core 2 Duo E4500
2Gb DDR2 667mhz ram
512Mb Gigabyte 8600GT Video card
160 gb seagate SATA HDD
LG 20x DVD Writer

I do have an operating system on the computer, but intend wiping it off, as it is an old windows 2000 that I had lying around, and I loaded it on yesterday as something to try.  I did intend having XP Pro, but that CD is corrupt, so I decided to give Linux a try "Fingers Crossed"

I did the checksum and I burnt the CD at 4x just in case.

Any ideas from anyone ?

---

### Post by rickyrockrat on 2008-04-24
Go get Hardy Heron. I know for a fact the 7.10 is buggy in many ways, and IMHO it was NOT a stable release.

---

