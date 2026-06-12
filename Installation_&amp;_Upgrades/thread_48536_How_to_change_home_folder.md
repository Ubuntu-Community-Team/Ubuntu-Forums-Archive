---
title: "How to change home folder"
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by Adrenal on 2005-07-12
Recently, I formatted and reinstalled Ubuntu. I had my /home folder on a different partition, and, while i can still easily access it, I would like to set this partition as my /home folder, as it was before.
I am guessing I would need to edit my fstab, so if anyone could give me some steps, that would be great.
Thankyou in advance

---

### Post by jaranguren on 2005-07-12
You can try this:
1)  Before you update your /etc/fstab, first make a copy of it.  (Just to be sure  :) )
```
sudo cp /etc/fstab /etc/fstab.bak
```
2)  Update your /etc/fstab by
```
sudo vi /etc/fstab
```
3)  Look for the line that says /home as mount point
Here's what I have in my /etc/fstab
```
/dev/hda6       /home           ext3    defaults        0       2
```
4)  Change /dev/hda6 to what ever partition you want it to be.
5)  save and exit.
6)  you can reboot or just try mounting it
```
sudo mount -a
```

---

### Post by Adrenal on 2005-07-12
[QUOTE=jaranguren]You can try this:
1)  Before you update your /etc/fstab, first make a copy of it.  (Just to be sure  :) )
```
sudo cp /etc/fstab /etc/fstab.bak
```
2)  Update your /etc/fstab by
```
sudo vi /etc/fstab
```
3)  Look for the line that says /home as mount point
Here's what I have in my /etc/fstab
```
/dev/hda6       /home           ext3    defaults        0       2
```
4)  Change /dev/hda6 to what ever partition you want it to be.
5)  save and exit.
6)  you can reboot or just try mounting it
```
sudo mount -a
```[/QUOTE]
 I don't have /home mount point, all I have is this
[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
~[/PHP]

---

### Post by Adrenal on 2005-07-12
[QUOTE=jaranguren]You can try this:
1)  Before you update your /etc/fstab, first make a copy of it.  (Just to be sure  :) )
```
sudo cp /etc/fstab /etc/fstab.bak
```
2)  Update your /etc/fstab by
```
sudo vi /etc/fstab
```
3)  Look for the line that says /home as mount point
Here's what I have in my /etc/fstab
```
/dev/hda6       /home           ext3    defaults        0       2
```
4)  Change /dev/hda6 to what ever partition you want it to be.
5)  save and exit.
6)  you can reboot or just try mounting it
```
sudo mount -a
```[/QUOTE]
 I don't have /home mount point, all I have is this
[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
~[/PHP]

---

### Post by Xian on 2005-07-12
[QUOTE=Adrenal]Recently, I formatted and reinstalled Ubuntu. I had my /home folder on a different partition, and, while i can still easily access it, I would like to set this partition as my /home folder, as it was before.[/QUOTE]
What is the partition number for your former /home?
Let's assume it is /dev/sda5.

Open your fstab. Edit it to look like the one listed below.
Rename your current /home folder.
Make a new /home path.

Now mount the new /home and verify the contents.
Logout/Login.

Look okay?


```
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1 
/dev/sda2       none            swap    sw              0       0 
/dev/sda5      /home       ext3    defaults           1       2
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0 
~
```

---

### Post by Adrenal on 2005-07-12
A thousand thankyous good sir

---

### Post by MEGAMANULTIMATE on 2007-12-15
I'm in the same situation, more or less. I want to change my home folder to /dev/sda1, but when I bring up the fstab folder, it's not listed at all. All I get is this:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=a7c9dd05-0d86-4b2e-8998-72b1f0eac898 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda6
UUID=b445dff8-13ce-49b6-a2e2-30ccf80dbbff none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

Any thoughts?

---

