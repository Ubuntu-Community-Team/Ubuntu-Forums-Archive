---
title: "cannot boot"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by vishnuprabhu on 2007-09-25
Hello

I did a dist-upgrade from edgy to feisty and now I am not able to boot.

The problem seems to be with the file - /dev/mapper/Ubuntu-root 
the system cannot mount the file and drops me into a debian busybox shell.

When I do an fsck on that file, it reports that the superblock cannot be found. I am using LVM if that helps.

But if I use a rescue disk, I'm able to mount / from /dev/Ubuntu/root - then I have complete access to all my files. I'm backing up all the files now.

I tried editing the grub boot menu to use /dev/Ubuntu/root instead of /dev/mapper/Ubuntu-root (that was what was set) - no luck.

I'm sorry I'm not able to give the verbatim error reports - I'm backing up all my files and hence cannot access the computer.

Thanks for any help
Vishnu

---

### Post by Pumalite on 2007-09-25
I would recommend saving /home (including 'Hidden Files') and data; if you have separate partition for /home; better, you can save it for clean install; just don't format. Do clean install of 7.04

---

### Post by vishnuprabhu on 2007-09-25
Thanks for the reply.

It is not so easy to just reinstall - there are cronjobs, several custom programs, lots of data (> 25gb), etc.

Since the harddisk seems to be ok, I was hoping there was no need for a reinstall.

---

### Post by Pumalite on 2007-09-25
Maye somebody will chime in with a better idea.

---

### Post by vishnuprabhu on 2007-09-25
Just to follow up:

I booted the computer via a live cd, installed lvm and mounted sda1.

I then did a fsck on /dev/mapper/Ubuntu-root and it is fine. 

So, the harddisk is fine - the upgrade messed up lvm I think.

---

### Post by Pumalite on 2007-09-25
That's why I recommended a re-install. Upgrades are messy.

---

