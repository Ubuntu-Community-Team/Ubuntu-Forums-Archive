---
title: "error 15, Super Grub"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by fattysfinest on 2008-02-22
Hi, I tried to install gutsy as a duel boot on one hard drive with xp.
at first I couldn't get anything to work but after using super grub I now have my xp working.
 But after trying every option on super grub except swap, I can not get ubuntu to load. Heres what i got when i ran the live disk
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb4d6b4d6

Device Boot Start End Blocks Id System
/dev/sda1 63 296222534 148111236 7 HPFS/NTFS
/dev/sda2 * 296222535 484199099 93988282+ 83 Linux
/dev/sda3 484199100 490223474 3012187+ 5 Extended
/dev/sda5 484199163 490223474 3012156 82 Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2008-02-22
Mount your partition:
sudo mkdir /media/linux
sudo mount -t ext3 /dev/sda2 /media/linux
Post:
cat /boot/grub/menu.lst

---

### Post by fattysfinest on 2008-02-22
I tried as you suggested, you did mean in terminal? This is what didn't happen
ubuntu@ubuntu:~$ sudo mkdir /media/linux
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /media/linux
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2008-02-22
You have to get menu,lst from the partition you just mounted
cat /media/linux/boot/grub/menu.lst

---

### Post by fattysfinest on 2008-02-22
thanks for your help and patience, How do I get the menu list from the partition I just mounted, I tried pasting your code into the terminal but no luck. I'm still running the live disc, should i reboot and try again without it?

---

### Post by confused57 on 2008-02-22
After you've made the /media/linux directory & mounted your Ubuntu partition, try copying & pasting this into a terminal:
```
gedit /media/linux/boot/grub/menu.lst
```

---

### Post by fattysfinest on 2008-02-22
hi thanks for the reply, I tried inputting your code and got bash: /usr/bin/gedit: Input/output error, not sure that i even have the direct. and mount done correctly, running short on time tonight but will check back later.

---

### Post by confused57 on 2008-02-22
> **fattysfinest said:**
> hi thanks for the reply, I tried inputting your code and got bash: /usr/bin/gedit: Input/output error, not sure that i even have the direct. and mount done correctly, running short on time tonight but will check back later.
Pumalite's directions should work with no problem:
```
sudo mkdir /media/linux
sudo mount -t ext3 /dev/sda2 /media/linux
gedit /media/linux/boot/grub/menu.lst
```

---

### Post by fattysfinest on 2008-02-23
Hi, I've tried as you suggested and I now have "menu.lst (/media/linux/boot/grub) -gedit" open to a tab that says "menu.list" that page appears blank. If i click open I get a bunch of mostly generic files listed under the boot tab. any thooughts? would it be better to try and re-install gutsy somehow? Thanks again for your help Brian
On another note I've had firefox and terminal refuse to open, I just got error screens. Seems ok this time.

---

### Post by Pumalite on 2008-02-23
Make sure you run the command right. If you in reality do not have a menu.lst, it's better to reinstal. confused57 and I have as clear as we can. confused57 suggested you copy and paste the volume in your Terminal. Run it again. If after all that you end up empty, reinstall.

---

### Post by fattysfinest on 2008-02-23
Still a blank page, how do I make sure my re-install goes to the right partition on my hard drive, sorry if this seems dumb but hey I'm trying to learn and there is just so much!

---

### Post by Pumalite on 2008-02-23
Go Manual and in the appropriate partition, create 10000MB for '/' 1 GB for /swap, the rest for /home and hit continue.

---

### Post by fattysfinest on 2008-02-23
Just a little confused.
Under prepare partitions i have /dev/sda
/dev/sda1 ntfs /media/sda1  151665 mb 56600mb
/dev/sda2 ext3 /media/linux 66254 mb 3400 mb
free space 29989 mb
/dev/sda5 swap 3084 mb
So I tried to create a new partion in the ext3 partition for a swap, said no space i changed the size of the ext3 and somehow created the free space. I cant find where to create  root mount point.
Can you help or steer me to  somewhere that can?
Fiesty was not a problem on my laptop but it wasn't dual boot.
this is a real brain twister for me

---

### Post by Pumalite on 2008-02-23
Post:
sudo fdisk -lu

---

### Post by fattysfinest on 2008-02-23
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb4d6b4d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   296222534   148111236    7  HPFS/NTFS
/dev/sda2       296222535   425626109    64701787+  83  Linux
/dev/sda3       484199100   490223474     3012187+   5  Extended
/dev/sda5       484199163   490223474     3012156   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2008-02-23
Go Manual and install Ubuntu in sda2. How many GB is that partition?

---

### Post by fattysfinest on 2008-02-23
I think about 80 gig in that partition
When I hit "forward" in that partition in says "no root file system"
" please correct this from the partitioning menu" How do I do that?

---

### Post by Pumalite on 2008-02-23
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

