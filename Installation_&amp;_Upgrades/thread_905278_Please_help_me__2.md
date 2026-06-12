---
title: "Please help me _2"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-08-30
When I write sudo I get the following error
sudo: /etc/sudoers is mode 0777, should be 0440
I am trying but can not change it to 0440

---

### Post by forger on 2008-08-30
1) try it using a live cd, mount your root partition and change its permissions
2) try this:
```
getfacl /etc/sudoers
sudo chmod -v 440 /etc/sudoers
```

and reply with the full output

---

### Post by hoboy on 2008-08-30
> **forger said:**
> 1) try it using a live cd, mount your root partition and change its permissions
2) try this:
```
getfacl /etc/sudoers
sudo chmod -v 440 /etc/sudoers
```

and reply with the full output

I have tried 2) I don't know how to do the 1. I am using dual booting with vista.

---

### Post by forger on 2008-08-30
I requested full output with your reply :)

Please post the output of:
```

whoami
lsattr /etc/sudoers
ls -l /etc/sudoers
cat /etc/sudoers

```

If any of the commands don't work, use sudo in front and post that output

---

### Post by cosborn72 on 2008-08-30
hoboy, 

I don't have a copy of the live Cd, so I'm  not 100% sure, but I think that your root drive (the main one that stores all of your linux files, will mount automatically when you launch the CD.  If not, open the program Gparted and check to see which partition your root filesystem is on. It is probably the largest partition with an ext3 or ext2 filesystem (the one that says NTFS is your windows partition).

If your root partition is not mounted, I think you can mount it in gparted.  If not, note the drive number (probably sda*, where * is a number between 0-6).

open the terminal and type: mount -t ext3 /dev/sda* (where the * is the drive number).

Once you have mounted the drive, you should be able to navigate to it by typing cd /dev/sda* (again, the * is the drive number).

I hope this works.

---

