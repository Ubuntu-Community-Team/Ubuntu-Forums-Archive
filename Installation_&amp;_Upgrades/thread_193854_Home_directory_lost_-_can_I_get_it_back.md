---
title: "Home directory lost - can I get it back?"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by tjacobs on 2006-06-10
I wanted to back up my home directory to an external usb drive. Using disks manager, I formatted the external drive but mounted it on /home. Now my real home directory is lost. I'm using the Dapper live disk for now. Is there any way to get my /home back?

---

### Post by goodmaj on 2006-06-10
Just unmount the drive.  When you mount a drive in a directory you can't see what was in the directory, but it is still all there.

Create a new empty directory such as mnt to use as a mounting point.

---

### Post by tjacobs on 2006-06-10
[QUOTE=goodmaj]Just unmount the drive.  When you mount a drive in a directory you can't see what was in the directory, but it is still all there.[/QUOTE]

How do I do this? I can't log in anymore since my home directory doesn't exist. What am I missing?

Thanks.

---

### Post by goodmaj on 2006-06-10
Have you rebooted with the drive disconnected.  If you still can not log in, try logging in as root.  If that fails try booting with a Live CD and re-creating the home directory.  It will be in /home/ and will be named by your username.

If all else fails you might have to reinstall.  However, if the home directory has been really deleted, then you did more than just mounting a drive over it.

---

### Post by tjacobs on 2006-06-10
Well, I thought I did try to log in with the drive disconnected but apparently, in my frantic state, I didn't. I disconnected it, rebooted and am now logged into my home directory. Thanks much.

---

