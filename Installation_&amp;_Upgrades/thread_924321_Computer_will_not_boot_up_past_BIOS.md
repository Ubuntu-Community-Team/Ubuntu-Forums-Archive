---
title: "Computer will not boot up past BIOS"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by Sethos222 on 2008-09-19
Hi,

I finally decided to install Ubuntu on my XP Pro SP3 computer.  I made sure to defrag my computer before doing so.  I followed the instructions located in "The Linux Starter Pack" of the magazine Linux Format.  Although the process itself was very simple.  I went through all the steps without a problem, and partitioned 30GB (20%) of my hard drive for Ubuntu.

It prompted me to restart my computer, then to remove the CD.  Now the problem starts.  The computer will show the Dell BIOS load screen, then go to the Mirror screen, but then it repeats back to the Dell BIOS load screen.   HELP!

I never expected a problem with this install, so I am up a creek without a paddle in a bad way.  I will try to list all the relevant information:

Dell XPS 700
150GB drives x2 Mirrored
XP Pro SP3
Printer
7900 GTX x2 SLI
Pentium D dual-Core
Wired internet
keyboard 
mouse
1 monitor

Ubuntu 8.04.1
downloaded from the Ubuntu website
copied to a CD, then used to install the OS

Could there be a problem with the fact that the hard drive is mirrored?  I think I can break the mirror RAID since I can get to the Mirror screen, but I do not know how to specifically do that.

Please, anyone, help a lost soul.

Thanks,
Sethos

---

### Post by chavafloresv on 2008-09-19
hi !

Hey I have about the same problem... well i guess

I followed up a tutorial from "http://tuxpepino.wordpress.com/2008/04/29/instalar-ubuntu-alternate-cd/#comment-22782"

and the installation was running ok  bue at the final steps, they asked me if I wanted to install the GRUB in the "main boot list"  so that i can choose between Linux and my other OS (windows vista starter) and so I clicked  SI(YES) and then the installation was succesful and complete. 
Then it asked me to take out the CD because the reboot was comming. 
Then after the BIOS screen was gone (my laptop is an acer aspire 5315) the system shows:

”
…
All rights reserved.
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Broadcom PXE ROM.
No bootable device — insert boot disk and press any key
_

”

After trying several times i finally boot from the CD (alternate CD, not the Live CD) and selected one of the options, the one that says "start from the first hard disk"  and that's the only way I can make Ubuntu run. It runs perfectly.

What can I do to fix this ??, because i can't start my computer (neither windows, linux) without booting from the linux alternate CD !!

help help please :(

Salvador Flores, México

---

