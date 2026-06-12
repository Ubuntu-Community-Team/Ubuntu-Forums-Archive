---
title: "Restore broken grub from running install?"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by D. Michael McIntyre on 2007-11-23
I have a pure Linux system with an ordinary bog standard hard drive setup.  No SATA, RAID,  USB, etc., and I installed GRUB in the most simplistic default way.

I just upgraded Feisty to Gutsy, and had an issue I decided to try to cure by booting the new kernel.

BIOS found something on the hard drive, because it didn't do the usual "please install boot disk" dance, but something was broken.  I arrived at a black screen with the cursor about three lines down from the top, sitting there blinking.  No disk activity, so I wasn't booting blind due to some graphics problem.  It just seemed GRUB had gotten busted somehow.

So I grabbed the nearest CD I had handy, which happened to be Dapper.  Booted that from my external DVD drive, and choose "Boot from hard disk" or whatever the actual text of the option was.

I then got the expected list of kernels from the menu.lst off the hard drive, chose the new kernel, and was back in business.

I can boot this way, so I'm not really troubled, but it seems like there ought to be some way to fix this sitting right here, instead of reinstalling GRUB from a rescue disc or something.

Reinstall the grub packages?  Run some grub command?  Everything I found in my first search was about emergency measures after XP trashed the MBR and so forth, but my situation is not so complicated as that, with only one distro installed, and no alien operating systems.

I could use a hint, and I'd like to avoid wading through all that unrelated crap to ferret out the key piece of information I really need.

---

### Post by zvacet on 2007-11-23
```
sudo update-grub
```

---

### Post by meierfra on 2007-11-23
> Everything I found in my first search was about emergency measures after XP trashed the MBR 

But it looks like Gutsy trashed your MBR. So i recommend reinstalling grub to the MBR:
[URL="http://ubuntuforums.org/showthread.php?t=224351"]
http://ubuntuforums.org/showthread.php?t=224351[/URL]

---

