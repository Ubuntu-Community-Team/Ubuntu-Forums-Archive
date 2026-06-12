---
title: "Change Permissions for a Folder: /media/download"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by SEEDster on 2007-12-25
Hello there!

I am fairly new to the Linux world.  However, I love it so much that I hardly use XP anymore.

Today, I reformated my HDD.  As my friend suggested, I created a partition for /media/download.  Unfortunately, I could not find a way to change the permission.  As a user, I could not write anything to the folder.  I researched it online but still didn't work it out.  

So far, I have tried the command such:

sudo chmod -R /media/download
sudo chmod -R 644 /media/download
sudo chmod 644 /media/download

I also tried to quote my directory: "/media/download"

I wonder if anyone is kind enough to tell me what I must do.  Thanks a lot for your help!  Mary Christmas :-)

-tim

---

### Post by Pumalite on 2007-12-25
What format is the hard drive? and From where did you do it?

---

### Post by MunkyJunky on 2007-12-25
I had a similar problem with not being able to write to some folders (specifically /var/www). I found it quite easy to fix, and simple to understand (I'm fairly new to full-time Linux).

Press Alt + F2 (run command) then run 'gksudo nautilus'. Stick in your system admin password and it should open a file browser as root. Navigate into /media/downloads, right click and alter the permissions so users can read/write to it.

Worked for me, so I hope it helps you!

---

### Post by odiseo77 on 2007-12-25
You probably must change the permissions on /etc/fstab. Could you copy and paste here the contents of your /etc/fstab file?

---

### Post by SEEDster on 2007-12-25
Yes!  This is my fstab setting:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8852b772-52d6-44b3-a6c6-7368b8775204 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=10eeb103-2120-4aa5-a5be-babd98c88bd0 /boot           ext3    defaults        0       2
# /dev/sda5
UUID=52b4b433-9c47-4647-96a1-f294baadd3e7 /home           ext3    defaults        0       2
# /dev/sda6
UUID=38687097-8c60-4861-892a-817fd13fcd39 /media/download ext3    defaults        0       2
# /dev/sda1
UUID=38083D8F083D4D5E /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=9E0C-840A  /shared         vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=0d3a74d8-d2d7-4b9d-a3c2-d2b4e740053e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by SEEDster on 2007-12-25
I just posted my /etc/fstab info.  I believe it's formated under ext3

thanks

---

### Post by taurus on 2007-12-25
```
sudo chmod -R 755 /media/download
sudo chown -R **username**:**username** /media/download
ls -la /media/download
```
where **username** is your actual login name.

---

### Post by johngonewbie on 2007-12-27
> **MunkyJunky said:**
> I had a similar problem with not being able to write to some folders (specifically /var/www). I found it quite easy to fix, and simple to understand (I'm fairly new to full-time Linux).

Press Alt + F2 (run command) then run 'gksudo nautilus'. Stick in your system admin password and it should open a file browser as root. Navigate into /media/downloads, right click and alter the permissions so users can read/write to it.

Worked for me, so I hope it helps you!

I am having issues writing permissions to a folder. I found an answer to getting wireless working by changing the interface file in /etc/network/ folder. however I cannot save it. I tried the 'gksudo nautilis' and nothing happens. Where do I login for the system admin?

---

### Post by taurus on 2007-12-27
> **johngonewbie said:**
> I am having issues writing permissions to a folder. I found an answer to getting wireless working by changing the interface file in /etc/network/ folder. however I cannot save it. I tried the 'gksudo nautilis' and nothing happens. Where do I login for the system admin?

You mean you edit something and would like to save it to /etc/network?  What did you edit and how did you edit it? 

Try something like

```
gksudo gedit /etc/network/**filename**
```

---

### Post by SEEDster on 2008-01-12
Thanks a lot :-)  It worked!!!

---

