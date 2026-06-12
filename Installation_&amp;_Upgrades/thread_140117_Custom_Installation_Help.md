---
title: "Custom Installation Help"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by DotNaBox on 2006-03-05
I am in a bit of a pickle. First of all, I have never used nor seen linux Ubuntu so I am immediately at a disatvantage. Well, to make things more difficult I want to do a custom install and need some help to see if it is possible.

What I want to do is install Ubuntu onto a partition (easy part) but I want to run the install file (an .iso image file) from my hard drive.

Why? No CD-ROM drive on my computer currently and all mine are too outdated for me to want to use.

So does anyone have any helpful links or suggestions on how to go about this?

Thanks in advance.

---

### Post by Nachtengel on 2006-03-05
With you never having used Ubuntu before, I would perhaps suggest loading the .iso for the live CD on something like Daemon Tools (iso mounter) & try it out from there?  As far as I can tell, installing the OS requires access to the boot loader & you won't get that booting off the HD and looking for the .iso.  Just a suggestion as to something you can do to try it out.  It might just work.

---

### Post by DotNaBox on 2006-03-05
Now by loading it as a virtual drive, will I be able to boot from that drive when my system is booting up (before I'm into Windows) so that I can install it or can I start the install from inside Windows?

---

### Post by Nachtengel on 2006-03-05
You won't be able to get it to run before windows boots up, but you might be able to activate the Live CD from within windows... I'm just guessing at that actually, but why not give it a try?

---

### Post by DotNaBox on 2006-03-05
So I tried to mount it into Daemon Tools and it didn't work. All it did was let me access the files in the .iso file. I guess I'll have to dig out a CD-ROM drive and get this image file burned.

Also, for partitioning, should I juse use Partition Magic 8 or what?

---

### Post by lettas on 2006-03-06
There are few options if you can't find a bootable cdrom-drive. Easiest one is to use this guide:

[http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)

Find those two files initrd.gz and linux.bin in that breezy cd-rom you mounted in daemon tools, they should work.

---

