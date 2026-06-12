---
title: "Syslinux fails on Aspire one"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by Francois2175 on 2012-12-01
Yes, it's another problem with syslinux.
I have an Acer Aspire One with an Atom N270 and Intel GMA950 video card.
I had strange problems with Ubuntu 12.10 which forced me to wipe the drive (If I still get these issue, I'll talk about them some other time).
So I downloaded the Desktop 32 bit ISO (i386), put it on a key using Universal USB Installer and tried to boot from it. I get the syslinux header (the Peter Anvin line) and then nothing. I tried reinstalling it on the key using unetbootin and LiLi but both gave me the same result.

Now, I do know ubuntu works on this machine as I have been successfully upgrading the OS since version 10.something. I also know it's not a booting failure since I have been able to boot UBCD4Win and Puppy Linux without fault.

I tried downgrading to LTS 10.4 but still get the same problem. I tried booting from a different USB Stick, same problem.

So, the big question is: what now?

---

### Post by oldfred on 2012-12-03
Welcome to the forums.

Some of the older versions of syslinux has bugs. Often then another flash drive creators have worked. Some just have issues with certain flash drives.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Some get it to work just by pressing enter, others rename files or other workarounds.

 syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
[http://ubuntuforums.org/showthread.php?t=2078599](http://ubuntuforums.org/showthread.php?t=2078599)
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

---

### Post by Francois2175 on 2012-12-03
So far, I've tried all the suggestions you made and nothing seems to work.
I tried running recent distros from other versions of linux and for some reason they all stopped working. I never had this problem before and I did try a ton of different distros on this machine before settling on Ubuntu.

Only an old version of Puppy Linux I had installed permanently to a flash key works.

Now, I did notice they all have one thing in common: they all use the same version of Syslinux.

I went to the syslinux site and they say to press shift or alt at boot time to go into a console. But mine freezes-up so fast it won't even go there!

Since the machine doesn't have a CD drive, I'm pretty much stuck making USB sticks.

Any suggestions?

---

### Post by oldfred on 2012-12-03
Both unetbootin & pendrive are totally different flash drive creators. Try one of them.

---

### Post by Francois2175 on 2012-12-03
I already tried them... that's what bums me out.
They boot fine on my very old Athlon64 machine but freeze up solid on the more recent netbook...

I found in my stuff the old Netbook Remix 10.04 and tried to copy the installer files over. But I guess syslinux gets put inside the boot sector so that was a whole bunch of nothing.

Right now, I pretty much exhausted all my linux knowledge (which I must admit is somewhat limited)...

---

### Post by oldfred on 2012-12-03
Intel only has one driver, so this may also apply even though for a different model?

       If booting from USB it just may be easier to edit syslinux with whatever boot parameters you need like this:
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
[http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/)
simply edit “syslinux.cfg”
Welcome to the new support thread for the GMA500 (Poulsbo) graphics card.
[http://ubuntuforums.org/showthread.php?t=1984236](http://ubuntuforums.org/showthread.php?t=1984236)

---

### Post by Francois2175 on 2012-12-03
I was just reading the syslinux page. I'm thinking of re-writing the syslinux on the boot sector so it can boot in "stupid mode". Maybe that will work :confused::confused::confused:
I noticed that universal USB installer writes the mbr in "force" mode. (-maf option)

---

### Post by Francois2175 on 2012-12-04
OK!
I have just found the problem and the solution to it! :P
The problem is a bug in Syslinux 4.06.
I think the bug extends all the way to 4.04 as I've had some issues with LiLi which uses that version. So, here's an easy fix which worked on mine. (easy to apply, not to discover)

1-get the Universal USB Installer.
2-get the Ubuntu ISO of your choice.
3-install Ubuntu to the USB stick.
4-go to [http://www.syslinux.org](http://www.syslinux.org) and download version 4.03 of syslinux.
5-extract the proper version to the USB stick
6-run **syslinux -mafs h: **where h: is the drive letter of the USB stick.
7-edit syslinux.cfg and remove the **ui** option
8-take the key to the offending machine and install.

What I'm doing is telling a previous version of syslinux to install to the MBR, mark the partition as active, ignore precautions (force mode) and run in compatibility mode (stupid mode).

As of now, Ubuntu is officially back on my netbook and running!:cool:

Now, the big question that remains is what was changed in syslinux that prevents it from working properly?

---

