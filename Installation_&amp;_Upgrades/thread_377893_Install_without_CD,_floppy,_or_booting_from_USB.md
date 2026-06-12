---
title: "Install without CD, floppy, or booting from USB?"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by rcoconnell on 2007-03-06
I'd like to install xubuntu onto a Ramline 510 I just picked up off of ebay.  It's a pretty old system, P3-500 with only 128MB of RAM.  Also, it has no CD-ROM, no floppy drive, and can't boot from USB.  No ethernet either, but I should be able to move files onto it over a wireless connection (whew).  Oh, and it's running Win98 right now.

If it weren't for Win98 I'd just install Wubi, but that requires XP.

I *do* have a laptop hard drive enclosure, so I can also connect the drive to another machine.  I'm a bit worried about this since I think the Ramline has some funny hardware, which would need to be detected.  But maybe this would work?

Any advice?

-ross

---

### Post by Dr. Nick on 2007-03-07
seen this yet?
[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

---

### Post by rcoconnell on 2007-03-07
Thank you, that's very helpful!

My question is now reduced to "how can I install grub without a floppy drive?"  And, since I'm averse to tinkering with my MBR, is there any analogue to putting grldr into boot.ini, as one might do with XP?  Or should I use loadlin, or something like that?

-ross

---

### Post by rcoconnell on 2007-03-07
One other thought -- I've decided that I'll need to attach the hard drive, via a USB adapter, to my Mac in order to take care of things like repartitioning the drive and putting the various images on the disk.  Is there a clever way to install grub from the Mac as well?

-ross

---

### Post by Dr. Nick on 2007-03-07
Never really messed with a mac in that regard. Their is another page that may help here

[http://marc.herbert.free.fr/linux/win2linstall.html#loadlin-or-grub-for-nt](http://marc.herbert.free.fr/linux/win2linstall.html#loadlin-or-grub-for-nt)

but that would require a Ethernet connection, That page uses loadlin for systems with win 98

---

### Post by rcoconnell on 2007-03-11
I ultimately got this to work by using the thread referenced above and grub4dos.  The latter lets you reboot into grub without writing to the MBR, which is nice if you don't have a floppy drive or anything like that to boot from.  Just run "grub.exe menu.lst".  From there I entered command mode, typed in the instructions from the thread (the ones that were supposed to go into a menu.lst file), and entered "boot" as my last command.  Voila!  As for partitioning, all I had to do was shrink my existing partition so that there was some extra space -- I was able to leave vmlinuz, initrd.gz, and the iso on the windows partition.

For reasons that are not clear to me, I ended up without the xubuntu desktop.  Since the iso was on the windows partition, I first edited fstab so that the windows partition would mount ( [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=last](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=last) ), then mounted the iso ( [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning) ) in /cdrom, so that it would be where apt-get expected to find it.  after that 'sudo apt-get install xubuntu-desktop' worked fine!

---

### Post by Dr. Nick on 2007-03-11
Cool, Glad it worked out.

---

