---
title: "Backing up Windows"
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by WebDrake on 2005-11-30
Hello all,

Further to previous posts in this topic, I'm aiming to install Ubuntu on my laptop so it can dual-boot with WinXP.  Only one problem---the hard disk is currently a big 80GB NTFS partition.

Currently there are about 25-30GB of files on this system.

The question is, how do I back all of this up effectively?  What I want is not merely to back up data files but to back up Windows in its entirety so that, in the event of things going horribly wrong when I resize the NTFS partition, I can restore Windows *without* having to reinstall all my programs.

Windows has its own backup utility (under System Tools) which seems to do that.  Is anyone familiar with using this?

The question is, how much disk space do I need in order to effect this backup?  The full 80GB or just the ~25GB that is actually used right now?

The backup utility requests a floppy disk for system restore but I presume I can use a USB key, right? ;-)

Many thanks,

      -- Joe

---

### Post by megamania on 2005-11-30
This is what I would do:

-buy/borrow/find a second hard disk (removable is more convenient)
-copy your files (not the system data)
-delete your files from the win partition
-backup the operating system by creating a disk image (there are many many programs to choose from).

This way:
- you have a "light" copy of your operating sytem
- you are sure that if the disk image is messed up, your personal files are safe (i.e. if the hard disk breaks it is easier to recover single files rather than a big 25gb file).

To make a mirror you usually need the space actually used (although I remember that some programs -Nero?- make an exact sector copy thus needing 80gb for an 80gb hard disk, even if it is empty).

Hope that helps.

---

