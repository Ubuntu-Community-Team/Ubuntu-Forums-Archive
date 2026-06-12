---
title: "ubuntu + windows"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by cached on 2006-07-12
I want to reinstall windows on my other hard drive. I am wondering if this will mess up the master boot record and, if so, how I can restore it.

Thanks in advance!

---

### Post by angkor on 2006-07-12
Yes it will.

To restore grub, search the forums with the words 'reinstall grub' and a number of useful threads will turn up.

Or read [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

:)

Edit: I need to read posts more carefully. I just read that you said *other* hard drive in stead of other partition. I don't know if that page explains how to do that.

---

### Post by ikkejw on 2006-07-12
The Windows setup will install its own bootloader in the MBR. If you want it back you will need to install GRUB on a floppy, and make it boot Ubuntu from the harddrive. From there you can reinstall GRUB.
I have never done it before so I can't go into detail, but in theory this should work.

---

### Post by cotcot on 2006-07-12
Install windows. You will loose grub in the MBR. Reinstall this with the liveCD

in terminal :
```
sudo su
```
to become super user

```
grub
```
You will get the grub prompt :  grub>

```
root (hd0,2)  
```

(hd0,2) is the same as hda3. Change this to the partition where you have your /root on.

```
setup (hd0,0) 
```

---

