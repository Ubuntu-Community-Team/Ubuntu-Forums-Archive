---
title: "Reinstall Ubunutu without affecting second hdd"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by lllll on 2010-07-06
I'm having a major problem with my system and have decided that to reformat the hard drive.  I am currently running Ubuntu 10.04 and have two hard drives installed, HDD-A which has the OS installed and HDD-B with all my files. On HDD-B I have some important files which are very large, so I can't really transfer them to a USB key and they won't fit on dual layer DVDs, plus I can't really go out and purchase an external hard drive. I wanted to know if I do a fresh install on HDD-A, will HDD-B be affected. Also will I have to do some configuration? I remember when I originally installed the second hard drive I had a hard configuring Ubuntu for it to detect it and to mount it on startup?

---

### Post by Yarui on 2010-07-06
I'm not sure how long ago it was that you had a hard time getting the drive configured, but with current versions of Ubuntu I have never had any trouble with that, Ubuntu always just autodetects the drives right away.

You shouldn't have to do any configuration.  If you install on hda it shouldn't have any effect on hdb.  Just be sure that you install on the right drive, you wouldn't want to choose to format and install Ubuntu on your data drive.  You should be able to tell which is which in the partition menu, but just to be safe you could unplug your second drive during installation and then plug it back in when you are done.

---

### Post by lyall on 2010-07-06
you can disconnect your second hard drive before you re-install Ubuntu on the first hard drive.
Then after the first hard drive has your OS on it and set up for you, then turn off the PC and connect the second hard drive back up

that is the way I did mine PC
works for me

you might want to copy some files from the first hard drive to the second hard drive.  like your bookmarks, favorites, etc for your browser.
also check your home directory for the hidden directories, you might find something that you might need

good luck and have fun learning

---

