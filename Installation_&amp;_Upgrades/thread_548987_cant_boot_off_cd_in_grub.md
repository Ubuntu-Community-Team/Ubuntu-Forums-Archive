---
title: "cant boot off cd in grub"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by tim202 on 2007-09-12
Hey guys.

I have a laptop with Feisty and Windows XP running dual boot.  I want to nuke the hard drive and give all the space to Feisty, but when I try to boot up off either my Ubuntu CD (the same one I used to install it in the first place, which isn't scratched or smudged)  or my (totally legal) bootable tool CD, I hit F12 to bring up boot device options, pick the CD-ROM, and then grub jumps in and boots ubuntu off my hard drive just like normal.  It totally ignores boot order.

I've tried my original Ubuntu disc, re-downloaded it, burned a new one, tried it, and tried the bootable tool disc, all of which yield the same result.  Is there like a grub command or something that i should be using?  I really don't know what to do with it... i realy need to reinstall because i'm running out of space and my wireless suddenly stopped working after 3 months of working beautifully-- but that's another post.  Any help is GREATLY appreciated.

Anyway, thanks in advance, as usual!
TIM

---

### Post by K.Mandla on 2007-09-12
If I understand you correctly, you're using a one-time boot option to jump to CD. Can you rearrange the boot order in the BIOS, or is that inaccessible to you?

---

### Post by logos34 on 2007-09-12
Try resetting the BIOS to the defaults.  Or clear it by taking out the CMOS battery.

Check to see if the cdrom laser lens needs cleaning. (Q-tip and Isopropyl alcohol)

If that doesn't work, there's [this workaround using memdisk and sbm]("http://ubuntuforums.org/showthread.php?t=168693&highlight=sbm+syslinux+boot+cd") which allows you to boot cdrom drive from the Grub menu.  Maybe that will force it to boot cd/dvd. 

If none of the above yields results, it might be time to check whether the drive is still under warranty or start shopping for a new one.

---

### Post by tim202 on 2007-09-12
I've rearranged the boot order in BIOS, and just brought up the 1-time boot device menu, neither work.  That "Add a menu entry to grub" tutorial looks promising, though, I'll give that a shot.

Thanks for the help, everyone

---

### Post by tim202 on 2007-09-25
Hey.

So i tried the tutorial logos34 posted, although without installing the syslinux package since my wifi card wasn't working (in part why i wanted to reinstall in the first place).  I just made the changes to the grub menu.lst file, and voila!  booted off cd just fine.  

Thanks again!

---

