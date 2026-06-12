---
title: "Fat32 Partition for sharing"
date: 2005-01-03
forum: Installation &amp; Upgrades
---

### Post by Niomi on 2005-01-03
Follow-up to this thread: [http://ubuntuforums.org/showthread.php?t=9918](http://ubuntuforums.org/showthread.php?t=9918)

My system is an AMD Athalon 2.7 2800+, 1GB of RAM, and two hard drives. Master drive is 80GB and slave is 120GB. Linux is on the slave, XP is on the master.

I installed Ubuntu on the slave according to the defaults and install worked fine. I re-installed, planning to have a 79.5BG root partition, 5MB swap, and 40GB FAT32.

Every time I try this, install seems to work fine until the base config. It'll ask me for a full name, username, and password. After I've entered the password, it will ask me for a full name again and loop like this indefinatly. When going to the menu and proceeding on with config, my username and pass doesn't open the system up.

I think I am mounting the system wrong in the partitioning, I'm not sure if I should have it mount into / or /home or /usr or what... I'm pretty sure it's not supposed to be bootable. (that's the non-swap drive that it boots from, right?) I'm 100% inexpirienced, can anyone help me out?

---

### Post by Niomi on 2005-01-05
Well... thanks for the help.  :confused: 

After much trial and error I learned that it works if I set the drive as logical instead of primary as I had been doing. Now my FAT32 drive is refusing to be read and written to because of permissions, I have read pages and pages of SUDO commands and nothing I seem to be doing is working. Root terminal is giving me errors and refusing to open, Windows isn't detecting the FAT32 partition.

Windows is looking nicer and nicer. I don't regret installing Linux, but there's very little for complete Linux newbies out there, and not much of it seems to apply to this distro.

I don't understand why I didn't get any replies to this thread. The FAT32 partition is something that many people have done, but I couldn't find any detailed information on it. Nowhere could I find if it should be logical or primary, where should I mount it, should the boot flag be on or off?

Did I do or say something wrong? Did I post this in the wrong forum section? I really need some help learning about this completely alien operating system. If someone had just told me to set the partition from primary to logical, I could have saved a lot of time and fustration.

---

### Post by Rancoras on 2005-01-05
Even with 1 GB RAM, a 5 mb swap seems a little low to me.  During partitioning you don't set the FAT32 to mount anywhere, you do that after the system is running and then I would mount it at /media/share.  Making the FAT32 a primary partition shouldn't cause any problems.

---

### Post by fng on 2005-01-06
Niomi, If you got patience, i'll write a guide for mounting removable fat32 media when i got home.  That will be around 20 CET. Working for the moment (Im browsing the forums @ worsk shhhhhhht)

---

### Post by Niomi on 2005-01-06
Thanks, FNG. When I can efficiently transfer my important files between systems, I can start moving into ubuntu and making it my own. :)

Rancoras: I made a typo, that would be 500MB - not 5. That would put my virtual memory to 1.5 gigs.
Making the FAT32 primary seemed to cause problems when choosing a username and password in the config, the Fullname, Username, and Password feilds would keep looping and didn't appear to be saving my changes to disk.

---

### Post by fng on 2005-01-06
I iinserted my USB Stick for starting this tutorial, but i had some other things lying around.  After 5-10 minutes, ubuntu auto-mounted it. I even got a icon on the desktop.  Anyway read on :)

Make a symbolic link in /media
```
fng@butters:~ $ sudo mkdir /media/usb
fng@butters:~ $ sudo chmod 777 /media/usb
fng@butters:~ $
```
Look if the usb drive is found
```
fng@butters:~ $ ls /dev/sd*
/dev/sda  /dev/sda1
fng@butters:~ $
```
If there aren't any sda devices, you're usb drive isnt recognized.

edit /etc/fstab with your favorite editor 
```
fng@butters:~ $ sudo vi /etc/fstab
```
Look for the cdrom lines
Add a line below that looks like this :
```
/dev/sda1       /media/usb      udf,vfat rw,user,noauto  0       0/CODE]
Change sda1 by the partitions listed by the ls above.

[CODE]fng@butters:~ $ mount /media/usb/
mount: /dev/sda1 already mounted or /media/usb busy
mount: according to mtab, /dev/sda1 is already mounted on /media/sda1
fng@butters:~ $ sudo umount /dev/sda1
fng@butters:~ $ sudo mount /media/usb
```

You're usb drive is now mounted!!!

Test :
```
fng@butters:~ $ cp .bashrc /media/usb
`.bashrc' -> `/media/usb/.bashrc'
fng@butters:~ $ ls -al /media/usb
total 2758
drwxr--r--    2 fng      fng         16384 2005-01-06 22:54 .
drwxr-xr-x    7 root     root         4096 2005-01-06 22:25 ..
-rwxr--r--    1 fng      fng          1776 2005-01-06 22:54 .bashrc
fng@butters:~ $
``` 
Works if you ask me :)

Before you remove the usb-drive dont forget to unmount it!!!! : sudo umount /media/usb

---

### Post by fng on 2005-01-06
Maybe editing the fstab isnt such a good idea although it works.
Look here : [http://ubuntuforums.org/showthread.php?t=7571](http://ubuntuforums.org/showthread.php?t=7571)

---

