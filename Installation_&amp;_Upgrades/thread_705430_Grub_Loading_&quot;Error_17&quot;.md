---
title: "Grub Loading &quot;Error 17&quot;"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by SoshimoJunai on 2008-02-23
Newbie to linux needs help!!!

A few days ago while experimenting with Ubuntu 7.1, I attempted to change the resolution to 1680x1050 so I could use Ubuntu without having a stretched desktop, but that resulted in the screen going completely bonkers, so I reformatted the hard drive to reinstall Ubuntu (for some reason my motherboard will not listen when I tell it to boot from CD as priority, it will always boot from hard drive) using the Vista partition manager. I reformatted it to NTFS which is the format it was in before I reformatted it, and put it back into the system.

I put in the Ubuntu disc, and computer says "No Operating System found", but after a reboot it came up with "GRUB Loading...Error 17"

Any ideas? Ubuntu ran fine in this pc before, even natively supported my belkin wifi card which surprised me.

Please help, I want to get this ubuntu machine running so that I can escape from windows vista sometimes, as running Ubuntu under Virtual PC generally results nowadays in black windows follwed by glitched graphics:(

---

### Post by Pumalite on 2008-02-23
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by uidb4056 on 2008-02-23
I think your problem is that the GRUB is still installed in your MBR of hard disk and is pointing the partition you have reformatted.

Anyway you need to be able to boot from CD to fix it because is the only way to reinstall Ubuntu even with fixed MBR (you can rebuild your MBR to get rid of your current GRUB configuration pointing to a formatted partition but you will need to boot from CD to reinstall Ubuntu)

Wich Ubuntu CD do you have? Live CD or Alternate CD?

how many hard disks do you have ?

---

### Post by SoshimoJunai on 2008-02-28
I think it's the Live CD...not exactly sure, as I downloaded the first ISO that came up. However, I only have the one hard disk installed in the computer. Maybe remove the hard drive and put it in an external enclosure and plug it in after ubuntu has loaded?

---

### Post by dstew on 2008-02-28
> that resulted in the screen going completely bonkers, so I reformatted the hard drive to reinstall UbuntuThis was where you went wrong. You should have reconfigured the xserver to get your video display back. The grub error means that you have the grub boot loader on the drive, along with grub stage1.5 in track 0. When grub stage1.5 was originally installed, the location of the grub root partition was embedded into it. Now that partition is gone, or moved, so grub cannot continue.

Did you install Ubuntu into that drive after you reformatted it? If so, you may only need to re-install grub, which is easy to do from a Live CD boot. You should be able to change the BIOS settings to boot the Live CD. When you get in the BIOS, look carefully at the menu items and make sure you choose "Save changes and exit" 

If you really cannot boot the Live CD in that system, you can make a [grub boot floppy]("http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html") that will also be able to re-install grub.

---

