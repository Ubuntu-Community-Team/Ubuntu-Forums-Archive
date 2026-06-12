---
title: "No file root system - Installation error"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by D_N_A on 2010-10-01
Hello forum helpers,
I have a PC with one physical hard drive divided to two not-physical drives:
C:/ in which I currently have XP installed, without any important files
D:/ in which I put all my important files I don't want deleted.
While installing XP, I get to choose on which of them to install the OS, and I chose C:/ and formated it. After installing, XP didn't recognize the network card (it could connect to the internet before, that connection works with other computers)
With Ubuntu liveCD, I managed to connect to the internet.
When I tried to install it, it saw my hard drive as one unit, and divided it into two sections as shown below:
[IMG]http://img97.imageshack.us/img97/3333/001jvs.jpg[/IMG]
 
I only want to formate the C:/ drive with XP (/dev/sda1) and to leave D:/ (/dev/sda5) intact. So the first option isn't good for me. When I chose the second option, I got to the next stage:
[IMG]http://img822.imageshack.us/img822/8715/002eki.jpg[/IMG]
 
Now here I didn't realy know what to do, so I tried double clicking /dev/sda1, and got to the following dialog: [IMG]http://img704.imageshack.us/img704/6906/004euv.jpg[/IMG]
I chose the following settings, _leaving "mount point" empty_, because I didn't know what to put there: [IMG]http://img441.imageshack.us/img441/3637/005czg.jpg[/IMG]
 
Then, all excited, I got the clear and explaining following message: 
[IMG]http://img338.imageshack.us/img338/2879/009ql.jpg[/IMG]
 
I would like to say again - I am interested in leaving D:/ intact and installing the OS only on C:/ . Can someone help me please?
Thank you very much!

---

### Post by CandidMan on 2010-10-01
Do you want to replace C drive completely? Or just dual-boot?

Also, you might want to consider choosing a filesystem other than NTFS to get one of the benefits of a linux system i.e. virtually no defragging

---

### Post by psusi on 2010-10-01
You can not install on an NTFS filesystem so you need to choose another type, preferably ext4.  You then need to set the mount point to "/".

---

### Post by zepita on 2010-10-01
I see you have two partitions on SDA:

SDA1 (C: in windows)
SDA5 (D in windows)

Linux partitions are way too different than on windows,

The settings I personally use and recommend are the following:

SDA
   SDA1 mount point / (15 GB)
   SDA2 mount point SWAP (1 GB)
   SDA3 mount point /home (remaining disk space)

if you come from a windows installation and never going to install windows ever ever again :P you may want to follow this procedure:


SDA
SDA1 (50gb)
SDA5 (120gb)

-Delete SDA1
-Create a new partition on SDA1 (primary, start of disk) EXT4 size 15GB and mount point to /
-Create a new partition for SWAP (800mb will be fine)
-Create a new partition for /home EXT4 (remaining partition space)
-Edit sda5 and set filesystem to ntfs and mount point to /dos (do not check format partition!!)

you will have:

SDA
__sda1 for / ext4 filesystem 15gb (programs and system folders)
__sda? for swap space 800mb (virtual ram, rarely used in linux...)
__sda? for /home ext4 filesystem (your personal files and configuration)
__sda5 for /dos ntfs filesystem (do not format or resize!!)

If asked for grub, just install it in the MBR (Master boot record)

In the future, you could make a backup of your ntfs files and format the partition to EXT4 and merge it into /home partition to have things clean and secure ;)

I hope this helps,

---

### Post by psusi on 2010-10-01
There is no good reason to have a separate /home partition, unless you are booting multiple Linux installs.

---

### Post by CandidMan on 2010-10-01
Well, that's made me redundant :)

Good luck

---

