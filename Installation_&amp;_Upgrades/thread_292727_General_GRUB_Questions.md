---
title: "General GRUB Questions"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by Computer Guru on 2006-11-04
Hello All,

I'm working on a program that ties into the GRUB bootloader (EasyBCD if you've heard of it) from Windows, and the latest version (1.5 + 1.51 path) works OK for some people, and not for others, leading me to asking around on some topics.. Any help would be appreciated.

**1) Does the actual bootloader section of the MBR/Partition-Bootsector differ from PC-to-PC/Config-to-Config?**

I mean, LILO, NTLDR, BCD they all store the same exact information to the MBR/Bootsector and read the configuration data off a file on the HD's filesystem (such as boot.ini).

I know that GRUB uses menu.lst, but it seems that when you install GRUB to the bootsector it also stores some configuration-specific information to the bootsector as well? As in, exporting the bootsector from one GRUB-enabled PC and installing it on another will *not* work, even if the required menu.lst file exists on both computers so long as the configuration is different?

**2) I can't seem to chainload from a copy of the MBR, it has to be a copy of the bootsector.**

What this means when issuing a 'dd' command to copy the MBR + bootsector to a file ```
dd if=hda of=grub bs=512 count=1
``` I can't use the created 'grub' file to chainload into GRUB from Lilo or NTLDR.. even if GRUB was installed to the MBR.

However, if GRUB was installed to the bootsector of a partition, hda1 for example, issuing this command ```
dd if=hda1 of=grub bs=512 count=1
``` then using the created 'grub' file to chainload into GRUB works.

Doesn't make sense to me: isn't it the same exact bootloader data in both cases, the only difference being that one is activated on selecting the disk from the BIOS, and the second is only activated when the *partition* is selected - yet it shouldn't matter since this behaviour comes from the *location* of the bootloader, and not its content.

----------

If you can help me understand either of these two points I'd be very grateful, I'm against a wall here. If there is a way to export a "standard" GRUB chainloading file (with regards to question #1) that will work on all PCs, then question #2 is no longer that important - but I'd still love to know just for the sake of knowledge.

I know it's a lengthy post, really sorry, just have no idea what to do now - I've literally tried everything.

And, yes, I know this isn't a GNU GRUB forum, but nevertheless it *is* home to the most popular Linux distro on the planet, I figure if I can't get an answer here I never will. 

Many Thanks!

---

### Post by Kateikyoushi on 2006-11-04
In my opinion the bootloader in mbr has to point to the boot partition, this might be different among computers, because of the partitioning.

You can find more about it here, [installing grub natively.]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html")

---

### Post by Computer Guru on 2006-11-04
Just to clarify:

Neither the grub.mbr created in the first nor the second code boxes above works on all PCs.

So it doesn't matter whether I grab hda1 or hda, it's simply not universal - but thanks for the quick reply.

---

### Post by confused57 on 2006-11-04
Herman and adrian15(developer of Super Grub Disk) might be able to help you.

Here's Herman's website:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Computer Guru on 2006-11-04
Thanks for the link, they certainly do seem to know their stuff!

But I can't see any contact info on the site at all ... :?

I've read the GRUB documentation there, some really interesting stuff, but it doesn't answer my question: how come the GRB boosector can't be copied from one PC to the other in a hexadecimal/binary dump format and instead it must be installed with the grub-install package?

---

### Post by Kateikyoushi on 2006-11-04
Herman is active on this forum, you could PM him.

---

### Post by Computer Guru on 2006-11-04
Thanks a lot for your help/advice Kateikyoushi,

Just did that, hopefully I can get this problem fixed :D

So many people flooding the support forums because it's not working for them... and I have no idea what the real problem is!

---

### Post by Computer Guru on 2006-11-05
From my PM-discussion with **Herman** it seems that the GRUB bootloader code itself differs from PC to PC... 
 
Looking into other means now ;(

---

