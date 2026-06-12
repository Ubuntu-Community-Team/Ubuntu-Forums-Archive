---
title: "formatting and fstab file, help needed"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by Uta on 2005-06-17
I need advice on how to get my new 2nd hard drive mounted. I see in my laptop's BIOS that the 2nd HD in the modular bay is seen. Once Kubuntu booted, if I run gparted how shall I partition this 40GIG; this 2nd HD  will be used only for storage and sharing.
options:Primary Partition or Extented? Filesystem: ext2, ext3...FAT32 etc...? I will be sharing this drive with Mac OS. Please advise and THANKS in advance! PS/ does this automatically list the drive in the fstab file or do I do that manually and if so please advise. Thanks!

---

### Post by intangible on 2005-06-17
I'm pretty sure you will have to add it to fstab yourself.

One large primary partition should be okay.
Are you going to be removing the drive itself and plugging it in the Mac?  If so, you'll have to go with a partition type both Linux and Mac can see, Fat32 will work up to 8TB, Windows can only format one up to 32GB, but it can read anything larger, and Mac can read it as well.
If you're going to be sharing it over a network, any file-system will work, try to use Ext3 or Reiserfs.

If you are going to be moving it from computer to computer, try to get an external usb drive case for it (around $20) then it will just be plug and play and show up as an icon on your desktop, which I think is what you want.

---

### Post by Uta on 2005-06-17
Thanks for the info...It is a HD in the modular bay of my laptop and it's not going anywhere-- Please give me the specifics what to enter in the fstab file... the drive is located /dev/hdc1
Thanks!

---

### Post by intangible on 2005-06-17
First, create a directory somewhere where you want to mount it, then
I'll assume you formatted it ext3, add this line to /etc/fstab:
```
/dev/hdc1       /newdrive           ext3        defaults        0       1
``` 
replace /newdrive with the new location.

To mount it, type **sudo mount /newdrive**

Then you can use chmod and chown/chgrp to manage the permissions on it.  (There's plenty of tutorials out there for that)

---

### Post by Uta on 2005-06-17
Thank you! I got the drive mounted!

---

