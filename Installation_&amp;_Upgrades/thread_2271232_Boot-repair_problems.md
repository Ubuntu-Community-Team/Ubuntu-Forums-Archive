---
title: "Boot-repair problems"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by lenniepaul on 2015-03-28
I was runnung windows 7 and Ubuntu 12? on my Dell XPS laptop and decided to update Ubuntu. After updating Ubuntu Windows would no longer load so I ran Boot-Repair. Unfortunately after running boot repair at start up I receive the message No Operating system found. I ran boot repair again which identified a problem and told me to run some commands from the terminal but shortly after this the operation just hung . I will do this again and make a note of the specific commands.

[http://paste.ubuntu.com/10696866/](http://paste.ubuntu.com/10696866/)

This is the command line that then hangs :

sudo chroot "/mnt/boot-sav/mapper/isw_bbbcgfgggb_6WS2G5ZC6" dpkg --configure -a

---

### Post by lenniepaul on 2015-03-28
[http://paste.ubuntu.com/10696866/](http://paste.ubuntu.com/10696866/)

---

### Post by yancek on 2015-03-28
You have syslinux installed to the master boot record of your primary drive (sda).  Not sure why you did that as it has overwritten Grub.  Are you running boot repair from inside Ubuntu?  Did you fully shut down windows before running the boot repair?  Your boot repair output does not show any grub.cfg file?  Also, you have LVM and I've never used that so I'm not sure what you would need to do.

---

