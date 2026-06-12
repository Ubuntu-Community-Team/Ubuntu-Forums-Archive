---
title: "Dissapointment with grub and MD on upgrades"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by ykanello on 2006-12-28
I have faced the same issue multiple times.
Everytime i do an upgrade and is necessary to recreate a new initrd, the debconf recreates the grub menu.lst. 
All would be peachy if the autoconf would work in ALL systems, or it was easy to disable it.
I use ubuntu on a AMD server with 9 disks. 
I have 2 pairs of mirrored sata disks, and 5 scsi disks in raid5 with a hotspare.
Everytime i did an upgrade the menu.lst would be changed with result I could not restart the server. 
this is so stupid. Is there ANY way to hard write somewhere the disk configuration?
is there ANY way to stop debconf to alter my menu.lst?
Because this almost goes to the category microsoft bug...
I love ubuntu and I have been using it in plenty of systems for more than a year now, but really, this is so annoying that stopped the updates on the whole.
(plus the updates makes you reboot every 3 days!)

---

### Post by bernied on 2006-12-28
I think that this is managed through the AutoMagic malarky in /boot/grub/menu.lst - ie everything inside of:
```
### BEGIN AUTOMAGIC KERNELS LIST
.
.
.
### END DEBIAN AUTOMAGIC KERNELS LIST
```In this section, anything starting with a '#' is a comment to grub, but not to the debian script that does the updating. Comments to the script begin with '##', anything beginning with a '#' in this section is an instruction to the script to tell it how to create menu entries. I don't know sata or raid, but it is possible that tweaking those options (like '# kopt_2_6=root=/dev/hdb1 ro' or '# groot=(hd1,0)') will see you right.

Alternatively, put your default boot entry before or after that section, so that it is unaffected by upgrades. You could then have the option of testing upgrades before committing them to be the default.

---

### Post by ykanello on 2007-01-02
Thanx for the reply and the insight :)
I will give it a try.

---

### Post by ykanello on 2007-01-04
I want to apologize because I was not careful. 
Indeed the end of automatic kernels was bellow my default grub line. 
Next time I will rtfm before i flame. 
Sorry again.
y.

---

