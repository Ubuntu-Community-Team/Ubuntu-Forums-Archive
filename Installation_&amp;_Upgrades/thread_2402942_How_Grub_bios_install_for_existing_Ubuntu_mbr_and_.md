---
title: "How?? Grub bios install for existing Ubuntu mbr and Windows mbr on seperate disks"
date: 2018-10-05
forum: Installation &amp; Upgrades
---

### Post by broccoflowers on 2018-10-05
Hi, can you help?

I have win server 2016 on one hard drive and it uses legacy bios mbr.  For some reason I couldn't get windows to install with UEFI a couple years back and never thought about it again---til now.

I added a brand new SSD for ubuntu.  When I tried to install Ubuntu using the install gui, it did not detect any other OS.  So, I stopped, verified that safeboot and such were disabled in the bios, but still no other OS was detected during ubuntu install.  I then pulled out my windows hard drive and set it on the desk (was getting nervous about messing it up (and yes I have a seperate bootable clone of my windows boot drive)).  I installed ubuntu using the "something else" option. I made a 300 MB partition and labeled it for grub bios.  I made the rest of the disk a primary partition for ubuntu.  Installed it, and all is well.  However, when I put back in my windows boot drive, to no suprise grub does not find it when I boot with shift held down.  But I can use the bios to select the windows disk and it will boot.  However, that requires me physically at the computer--and I work on this computer remotely 90% fo the time, and I need to switch sides roughly daily.

I would like grub to recognize my windows boot drive.  Then I would have the option to tell grub to reboot into windows from the command line.  This way I could do this all remotely--which is how I usually use this workstation.  

Since ubuntu didn't find my windows OS during the original install, how can I hope that reinstalling grub would find it the second time around?  Is it worth trying, is there a trick?  As you can probably tell, I'm not great with linux/grub/etc, so please don't assume I've done the most obvious thing--I haven't.  Thanks for your time, experience and advice.

GB

---

### Post by westie457 on 2018-10-05
Welcome to the Fora.
Here is one guide to help with your issue. [https://www.tenforums.com/tutorials/4189-turn-off-fast-startup-windows-10-a.html](https://www.tenforums.com/tutorials/4189-turn-off-fast-startup-windows-10-a.html)

If that does not help it might be better to see details using Boot Repair.
Boot your Ubuntu go to here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and select the 2nd option.
DO NOT attempt any repairs just select the 'Create a Boot Info Report' option. Post the generated link back here.

---

### Post by ubfan1 on 2018-10-05
Sounds like Ubuntu is installed in UEFI mode.  How the installer boots determines what type of install you get.  For a gpt partitioned disk, you only need a 2M bios-grub flagged partition, not a 300M one (which is a normal EFI partition size).  Check your BIOS/UEFI settings at power on and see what options you have for booting.  Some machines let you set the mode, legacy/UEFI, but some only let you set a preference of which to boot first -- Set legacy first in that case.  You could just try running upgate-grub, to see if Windows is picked up first before trying anything else.

---

