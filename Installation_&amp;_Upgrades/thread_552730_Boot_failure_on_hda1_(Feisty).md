---
title: "Boot failure on hda1 (Feisty)"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by ashenrose on 2007-09-16
Hi there, I initially posted this in General help, and as it progressed I realised that it was the wrong forum for it, so my apologies. My Original post is here - [http://ubuntuforums.org/showthread.php?t=552223](http://ubuntuforums.org/showthread.php?t=552223)

I have had Feisty installed since Thursday. It was running fine until Saturday night. Firefox crashed and the whole system froze, so I rebooted and the boot failed. I've been using the Live CD to search for help since. I cannot re-install off the live CD as when I get to the partition selection it only lets manual be selected and then when pressed forward it doesn't pick anything up so I cannot go any further.

I'm really stuck on this one. I cannot reach my HD from the live CD at all so I'm pretty flummoxed. 

I tried to [COLOR="Blue"]sudo fsck /dev/hda1[/COLOR] and got the following error message.

[COLOR="Blue"]ubuntu@ubuntu:~$ sudo fsck /dev/hda1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: No such file or directory while trying to open /dev/hda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
[/COLOR]

I'm at my knowledge limit now and I'm very confused. :lolflag:

---

### Post by Pumalite on 2007-09-16
Post(from Live CD):
sudo fdisk -lu
Mount your partition and post:
cat /boot/grub/menu.lst
blkid
cat /etc/fstab
df -h

---

### Post by ashenrose on 2007-09-16
sudo fdisk -lu
[COLOR="Blue"]ubuntu@ubuntu:~$ sudo fdisk -lu
ubuntu@ubuntu:~$ [/COLOR] (Nothing actually happens)

Mount your partition and post:
(I don't have any partitions, just ubuntu on the whole drive)[COLOR="Blue"]ubuntu@ubuntu:~$ mount /dev/hda1
mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab
[/COLOR]

cat /boot/grub/menu.lst
[COLOR="Blue"]ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
[/COLOR]

blkid
[COLOR="Blue"]ubuntu@ubuntu:~$ blkid
ubuntu@ubuntu:~$ 
[/COLOR] (Nothing)

cat /etc/fstab
[COLOR="Blue"]ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
[/COLOR]

Doesn't look very helpful really. :O

---

### Post by Pumalite on 2007-09-16
Get Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
And post a screenshot or a digital shot here.
Also get rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download), and investigate your system

---

### Post by ashenrose on 2007-09-16
The LiveCD has GParted, I tried that earlier. Let me get the SS for you.

---

### Post by Pumalite on 2007-09-16
I want you to get the stand alone, burn to CD, boot from, program. Newer,  more flexible, more features.

---

### Post by ashenrose on 2007-09-16
Ok Its eating the screenshots I take. When I Load GParted it searches and stays faded out with @No Devices found@ at the bottom. When I refresh the list (about my only option aside from help) It still doesn't find anything.

---

### Post by ashenrose on 2007-09-16
I have a slight problem with that. I don't have a CD Burner.

---

### Post by Pumalite on 2007-09-16
Go to a friend or get one. You are going to need it to solve this.

---

### Post by ashenrose on 2007-09-16
My Housemate has one, but seeing as its almost half 2am I will wait till he gets home from work tomorrow. Thanks for your help.I'll post more when I've followed these instructions. :-)

---

### Post by Pumalite on 2007-09-16
Ok.

---

### Post by ashenrose on 2007-09-17
I haven't managed to get GParted on disk yet, but I have had a look at my BIOS settings and according to my computer I don't have a hdd ><

IDE Primary Master [NONE] (This is where my hdd should be ><)
IDE Primary Slave [DVD DRIVE] (I can't remember the exact dvd drive wording)
IDE Secondary Master [NONE]
IDE Secondary Slave [NONE]

So I'm guessing its either dead or something else? I checked all the connections to it last night and they are all plugged in as they should be etc. I have 2 hdd's in another box so if this one is indeed b0rked beyond help, I can remove the secondary hdd from the other box and plug it into this one. (I know how to switch the jumpers accross to make it Primary Master).

---

### Post by Pumalite on 2007-09-17
Flash your BIOS and if that doesn't work stick another drive there.
You could check it first with rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
I would wait until trying to boot from Gparted and rescuecd

---

### Post by ashenrose on 2007-09-17
Thank you :-) I shall Follow the steps closely and update on prgress. :-)

---

### Post by ashenrose on 2007-09-19
I have both the GParted and Sysresccd Iso's burnt to seperate disks. I'm not too sure What I'm supposed to do with them. startx doesn't work on GParted but does on sysresc. I can't seem to find what I need though. 

Are there any commands I should be running? Or should I go straight to flashing my BIOS?

---

### Post by Pumalite on 2007-09-19
Flashing your BIOS is a good idea anyway, but remember there is always a risk involved.
For instructions on Gparted:
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

For rescuecd:

[http://www.sysresccd.org/Online-Manual-EN](http://www.sysresccd.org/Online-Manual-EN)

---

### Post by ashenrose on 2007-09-19
Thank you :-) I'll read up on those and attempt to use them both again.

---

### Post by Pumalite on 2007-09-19
You are welcome. Good luck.

---

### Post by ashenrose on 2007-09-19
My issue doesn't seem to be in the GParted documentation. I get to this part [http://gparted.sourceforge.net/larry/livecd/screenshots_0348/livecd-03.png](http://gparted.sourceforge.net/larry/livecd/screenshots_0348/livecd-03.png) and the GUI doesn't start, and startx doesn't work either.

---

### Post by Pumalite on 2007-09-19
Something is wrong with your computer then. Take it for repair.

---

### Post by ashenrose on 2007-09-19
The rest of it works fine, I;m accessing here with the same computer using the liveCD, Its the Hard Drive. I want to fix this by myself, so I'm going to try a few more things, then replace the hdd if all else fails.

Thank you for your patience and help though. :-)

---

### Post by Pumalite on 2007-09-19
You are welcome. Good luck.

---

