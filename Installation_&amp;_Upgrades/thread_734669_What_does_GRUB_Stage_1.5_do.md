---
title: "What does GRUB Stage 1.5 do?"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by MPH on 2008-03-24
I suspected that the HighPoint HPT366 ATA-66 disk controller chip on my Soyo SY-6BA+IV mobo was corrupting GRUB whenever I used the HPT366’s BIOS to change boot drives.  According to a post I just found at [http://forums.gentoo.org/viewtopic-p-3217132.html](http://forums.gentoo.org/viewtopic-p-3217132.html)...

> The problem with Highpoint + GRUB is that the Highpoint BIOS stores its metadata in sector 9 of each harddrive. Normally this area is unused, so GRUB puts its stage1.5 file in that area too. 

Since GRUB's stage1.5 is optional, the workaround is simple : don't use it :)
**Code:**
[COLOR="Green"]# cd /boot/grub
# rm *stage1_5
# grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit[/COLOR] 

This post refers to a newer Highpoint chip ([http://www.highpoint-tech.com/PDF/RR1522a/RR152x_User_Manual.pdf](http://www.highpoint-tech.com/PDF/RR1522a/RR152x_User_Manual.pdf)) but it showed that Highpoint has made a practice of writing BIOS metadata on the first track of the disk drives it controls.

Assuming that my HPT366 was also writing nearby the MBR, I decided to try the above recommendation.  But rather than risk deleting the stage 1.5 files, I created a subfolder and moved the stage 1.5 files to the subfolder.  Then I ran GRUB’s Root and Setup commands to reflect that change.

It worked!  Now I can change the boot drive without corrupting GRUB… but now Grub is minus stage 1.5 on my Ubuntu hard drive.  That raises two questions about GRUB:

[LIST=1]
[*]What functionality am I missing by not having stage 1.5 available?
[*]Is stage 1.5 ever recreated without reinstalling Ubuntu?  In other words, do activities like Ubuntu version upgrades or system updates recreate the GRUB stages?
[/LIST]

---

### Post by whazooo on 2008-03-25
From the GNU-grub wiki
[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

When a computer is turned on, the computer's BIOS finds the primary bootable device (usually the computer's hard disk) and transfers control to the master boot record (MBR), the first 512 bytes of the hard disk.

The MBR contains GRUB stage 1. Given the small size of the MBR, Stage 1 does little more than load the next stage of GRUB (which may reside physically elsewhere on the disk). Stage 1 can either load Stage 2 directly, or it can load stage 1.5: GRUB Stage 1.5 is located in the first 30 kilobytes of hard disk immediately following the MBR. Stage 1.5 loads Stage 2.

When GRUB Stage 2 receives control, it presents an interface to the user in order to select which operating system to boot. This normally takes the form of a graphical menu, although if this is not available or the user wishes further control, GRUB has its own command prompt, where the user can manually specify the boot parameters. GRUB can also be set to automatically load a particular kernel after a timeout period.

Once boot options have been selected, GRUB loads the selected kernel into memory and passes control on to the kernel. At this stage GRUB can pass control of the boot process to another loader using chain loading if required by the operating system.

---

