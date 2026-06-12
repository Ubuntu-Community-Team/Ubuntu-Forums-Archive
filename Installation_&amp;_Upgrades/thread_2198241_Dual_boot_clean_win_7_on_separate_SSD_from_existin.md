---
title: "Dual boot clean win 7 on separate SSD from existing Ubuntu 12.04 HD"
date: 2014-01-07
forum: Installation &amp; Upgrades
---

### Post by moswell on 2014-01-07
Okay, I've tried to do some reading on this, but I want to be sure I don't screw anything up before I do it!  I've been running Ubuntu for several years now, but I'm in a position where I regularly need Windows 7 to do some work.  For various reasons, I don't just want to use a virtualbox.  

I have an existing HD with Ubuntu 12.04 running.  I just purchased a new SSD and a copy of Windows 7.  I'd like to set up a dual boot so I can still use Ubuntu for my recreational computer use.  I had initially assumed that all I needed to do was go into my BIOS and switch out the boot drive when I want to go back and forth.  There are all sorts of tutorials for dual boot, but they all seem to deal with two clean installs.  I don't really want to clean install Ubuntu too, at least not yet, because I don't have a third drive for backing up the entirety of that drive.  

So, 

1. Am I likely to run into issues with simply installing Win7 on a separate HD and going into the BIOS to switch boot drives when I want?
2. Is there a better way to do this Win7 install with an existing Ubuntu installation that wouldn't require my entering the BIOS every time I want to switch OS?

Thanks!

---

### Post by cincibluer6 on 2014-01-07
Of course there's a better way, haha.

If you're just gonna install Win7 on a separate drive, do that and then just add a boot entry into GRUB to look to that hard drive (so I assume that it would go /dev/sda is Ubuntu and therefore /dev/sdb would be Windows 7.)
That way you just boot all the time from the first drive and then pick from GRUB which OS you want.

I might try to find something but otherwise just search for "add grub entry" to find the instructions to modify grub.conf (or whatever it is now) to look for Windows. Do this, of course, after installing Win7 on the second drive.

Edit- [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by moswell on 2014-01-07
:) - There's always an easier way I guess!  I suppose I was just looking for reassurance that installing WIndows on the second drive wasn't going to screw anything up majorly.  And I'll read up on the GRUB entry thing once windows is installed!

---

### Post by oldfred on 2014-01-08
I might unplug Ubuntu drive.

But you must change boot drive in BIOS to Windows drive or it will install the normally hidden 100MB boot partition to the Ubuntu drive. And since it does not see Linux correctly it just overwrites the first 100MB.
I would plug SSD into first SATA port on motherboard and leave it there. Windows likes to be first, but will work from other drives.
Ubuntu then will end up at sdb and a sudo update-grub should update everything.

New SSDs are large enough now for Windows and a 20GB / (root) partition for Ubuntu. Then you can have a shared NTFS data partition and /home or Linux data partition on rotating drive. Then both systems will be fast. I would keep current install on rotating drive as I prefer a system on every drive.

---

