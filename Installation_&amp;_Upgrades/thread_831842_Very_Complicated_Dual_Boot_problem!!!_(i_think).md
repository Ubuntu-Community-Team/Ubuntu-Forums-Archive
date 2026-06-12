---
title: "Very Complicated Dual Boot problem!!! (i think)"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by magitronic2 on 2008-06-17
i'm VERY new to linux, I CANNOT GET WINDOWS TO BOOT!!! and i have been at this problem for DAYS!!!!! so any help would be greatly appreciated. 

i am running MEPIS antiX 7.2, and i am getting a variety of errors

first i installed windows xp, made the partitions from there, and then installed linux in the 2gb partition. i also installed the grub bootloader that the installer prompted me to install.

i have 2 drives, 
(hd1) 20 gb just for storage
(hd0) 30 gb, 
             (hd0,0)2gb partition for linux, 
             (hd0,4)28gb for windows xp
i got these numbers from Gparted

my menu.lst file:

title XP
rootnoverify (hd0,4)
makeactive
chainloader +1

when i boot it up, the XP option appears in the MEPIS boot menu, but when i select it i get the error:

root (hd0,4)
Filesystem type unknown, partition type 0x7
makeactive
Error 12: Invalid device requested

then when i go to the grub boot menu and try

grub> root (hd +Tab
grub> root (hd0 +Tab
grub> root (hd0,4)
grub> setup (hd0)

i get the error:
Error 17: Cannot mount selected partition


I just need Windows Xp to be able to boot. Thanks.

---

### Post by torgrot on 2008-06-17
I believe that windows is in an extended partition.  I don't think windows will boot from an extended partition.  You need to make the Windows partition a primary partition.

torgrot

---

### Post by magitronic2 on 2008-06-17
how do i make it the windows partition a primary partition?

can i do this
map (hd0,0) (hd0,4)
map (hd0,4) (hd0,0)
root (hd0,0)

or does that only work for different hard drives, and not partitions? thanks

---

### Post by meierfra. on 2008-06-17
(Edit: Read my next post first)

It is possible to boot XP from a logical partition. But sometimes it is a little bit  tricky. Please open a terminal in Mepis and post the output of

```
sudo fdisk -l
```
and 

```
gksudo gedit /boot/grub/menu.lst
```

( both l  are  lowercase L)

(I just realized that you are using Mepis, and not Ubuntu. You might have to adjust "sudo" and "gksudo  gedit")


Did you delete any partitions while installing Mepis
Did you move any partitions?

---

### Post by meierfra. on 2008-06-17
Reading through your first post again, you don't seem to have deleted any partitions or moved XP. Then I would guess that  the boot information for Windows is on the storage drive.

So  try

title XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

and 

title XP
rootnoverify (hd0,0)
makeactive
chainloader +1

---

### Post by magitronic2 on 2008-06-17
thanks for helping:)

when I put:

```

title XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

```

i get the error:

NTLDR is missing.
Press Ctrl+Alt+Del to restart.

and when i put:

```

title XP
rootnoverify (hd0,0)
makeactive
chainloader +1

```

i get the error:

Error 13: Invalid or unsupported executable format.
Press any key to continue...

---

### Post by magitronic2 on 2008-06-17
Also, here is my fdisk

Disk /dev/sda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ffe3ffd

Device    Boot  Start   End     Blocks  Id  System
/dev/sda1   *      1    261    2096451  83  Linux
/dev/sda2        262   3735   27904905   f  W95 Ext'd (LBA)
/dev/sda5        262   3735   27904873+  7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
128 heads, 63 sectors/track, 4849 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Disk identifier: 0x0000657f

Device    Boot  Start   End    Blocks   Id  System 
/dev/sdb1   *      1   4848  19547104+   7  HPFS/NTFS



And here is my menu.lst after the last attempt

```

timeout 15
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

title MEPIS at sda1, newest kernel
root (hd0,0)
kernel /boot/vmlinuz root=/dev/sda1 nomce quiet splash vga=791 
boot

title MEPIS at sda1, previous kernel (if any)
root (hd0,0)
kernel /boot/vmlinuz.old root=/dev/sda1 nomce quiet splash vga=791 
boot

title MEPIS at sda1, kernel 2.6.22-1-mepis-smp
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-1-mepis-smp root=/dev/sda1 nomce quiet splash vga=791 
boot

title MEMTEST
kernel /boot/memtest86+.bin

title XP
rootnoverify (hd0,0)
makeactive
chainloader +1

```

---

### Post by meierfra. on 2008-06-17
This should allow you to boot into Windows:

Step 1)  Mount your windows partition in Linux

```

sudo  -s   or su (this depends on the OS)
mkdir /Win
mount /dev/sda5 /Win 
ls /Win
```

The last command list all the files in the System  directory of your Windows Partition. Look for the files "boot.ini", "NTLDR" and "NTDETECT.COM". If you already have these files, skip Step 2.


Step 2) Get the boot files and copy them to your Windows partition


Download this file:[ http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573]("http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573")
and save it to your  home folder

```
cd /Win
tar -xvzf /home/your_mepis_username/Archive.tar.gz
```

```
ls /Win

```
Make sure you now have the files "boot.ini", "NTLDR" and "NTDETECT.COM"


Step 3 Edit boot.ini

```
nano /Win/boot.ini         (you may use a different editor than nano)
```


Change all  "partition(?)" to "partition(2)"      (there are two of them)   Do not change anything else.

Save the the file.


Step 4 Edit menu.lst:

Use 

title XP
rootnoverify (hd0,4)
chainloader +1

So do NOT use "makeactive"

Save the file. reboot and hope for the best. Sometimes this does not work right away and you have to do  a fifth  step. Just come back here and report any error messages,


( You can deleted  "Archive.tar.gz" at any time, but I would wait until you successfully booted into XP)

---

### Post by meierfra. on 2008-06-17
Here is a similar case which was solved with this method just a couple of days ago.

[http://ubuntuforums.org/showthread.php?t=829464]("http://ubuntuforums.org/showthread.php?t=829464")

---

### Post by magitronic2 on 2008-06-17
sorry about this but im having a problem with step 1

mkdir Win
sudo mount /dev/sda5 Win 
ls Win

when i enter mkdir Win it creates the directory

but then i enter 
sudo mount /dev/sda5 Win
  nothing happens

nothing also happens when i enter ls Win

before I do anything, I type su in the terminal and put in the password.

---

### Post by meierfra. on 2008-06-17
Sorry, all my instruction were geared toward Ubuntu. I rewrote my post, hopefully all the commands will now work on Mepis.

The only thing I'm not  sure about is  whether Mepis can mount ntfs partition with read and write access, and how to do it. So you might have to modify the line

```
mount /dev/sda5 /Win
```

But I suggest to just try it like that and see what happens.

---

### Post by magitronic2 on 2008-06-18
when i enter this 

mount /dev/sda5 /Win

i think it mounts because when i go into my media folder i cant see any sda5. i wonder if this is a problem?

but the ls /Win command doesn't work, i tried googling how to mount on mepis but i could really find syntax. Any other ways i could write it?
cant believe im stuck on step1 :(

---

### Post by meierfra. on 2008-06-18
Sorry, I just don't know enough about Mepis to help you. As a work around, you could get a Ubuntu 8.04 LiveCD and carry out Step 1-Step 3 from the  LiveCD.

---

### Post by magitronic2 on 2008-06-19
thanks for all ur help, im downloading ubuntu 8.04, so when i try it i'll let you know how it goes. thanks again. can u edit ur code back into ubuntu?

---

### Post by meierfra. on 2008-06-19
Actually just use "sudo -s" in place of "su" and everything will work in Ubuntu.

---

