---
title: "Installed on 2nd Partition of External Hard Drive; Black Screen on Boot"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by biolizard89 on 2012-09-12
I want to install Ubuntu 12.04 onto a partition of an external (USB3) hard drive, while using the other partition of that drive as an NTFS backup of my internal (Windows 7) hard drive.

I booted from the Ubuntu disc, and when it asked me whether I wanted to install alongside Windows 7, install over Windows 7, or something else, I said something else.  My external drive has 3 partitions: 2 of which each make up almost half of the 1.5TB drive, and a 3rd free space partition which is 10GB.  (I setup those partitions in the Windows Computer Management tool; the drive originally had 1 NTFS partition.)  I instructed the installer to use the first partition as / (ext4), leaving the second partition untouched as the preexisting NTFS.  I also chose to use the remaining 10GB as swap.

The install procedure appeared to go smoothly with no obvious problems.  However, when I reboot my computer and instruct the BIOS to boot from USB, I get a black screen.  If I hold Shift while booting from USB (a Google suggested that I try that), the word "Grub." appears at the top of the screen, and stays there; nothing else happens.

I was unable to find anything with Google, but maybe I'm searching for the wrong thing.  "black screen" gives a lot of results, but they all seem to be about the video card drivers being bad, which I'm fairly confident is not relevant to my problem, because (a) the live CD works fine for me, (b) the error message obtained via Shift is different in those results than it is for me, and (c) the suggested solutions (e.g. mashing F6 during boot) don't seem to do anything for me.

I'm on an Alienware M17X R3 laptop.  Hopefully I'm not asking a stupid question.  Any suggestions would be greatly appreciated.  Thanks.

---

### Post by oldfred on 2012-09-12
Not sure what sytem you have. Some have had issues booting from USB3 ports. But if you are getting a grub, it sounds like it is trying to boot.

Is your system UEFI or BIOS? And which way did you install Ubuntu?

Different model.
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)

Post link from BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by biolizard89 on 2012-09-13
> **oldfred said:**
> Not sure what sytem you have. Some have had issues booting from USB3 ports. But if you are getting a grub, it sounds like it is trying to boot.

Is your system UEFI or BIOS? And which way did you install Ubuntu?

Different model.
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)

Post link from BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
While it is a USB3 hard drive, I've attempted using both USB3 ports and USB2 ports; no difference.  So I gather that USB3 is not the issue.

I've never actually heard of UEFI, so I assume I have a standard BIOS.  Not sure though; how would I check this?

The Alienware link you gave was solved by using x64 Ubuntu; I'm already using the x64 ISO to install, so my guess is that the problem is not the same.

Here is the BootInfo report:
[http://paste.ubuntu.com/1201911/](http://paste.ubuntu.com/1201911/)

Any ideas?

Thanks.

---

### Post by YannBuntu on 2012-09-13
Hello

> **biolizard89 said:**
> Here is the BootInfo report:
[http://paste.ubuntu.com/1201911/](http://paste.ubuntu.com/1201911/)

Any ideas?

You have a Legacy (non-EFI) BIOS. This makes things easier.
Your Ubuntu root partition ends far from the start of your disk. This may be the cause of your problem. 

Please:
1) use [Gparted]("https://help.ubuntu.com/community/GParted") to reduce your sda1 partition from 734GB to 100GB. (reduce it from the right-side so that it still start at the beginning of the disk). Create a data partition in the free 634GB.
2) Reboot the PC, making your BIOS boot on the Ubuntu disk
3) if still not good, run Boot-Repair's "Recommended repair" and tell us the new URL that will appear

---

