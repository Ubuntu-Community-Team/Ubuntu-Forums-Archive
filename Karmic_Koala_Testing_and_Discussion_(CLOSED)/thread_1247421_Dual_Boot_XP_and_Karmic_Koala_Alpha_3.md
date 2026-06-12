---
title: "Dual Boot XP and Karmic Koala Alpha 3"
date: 2009-08-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Dare2DoIt on 2009-08-22
Hi All,
I have a problem dual booting XP and Karmic Koala alpha 3
I installed Ubuntu in a seperate partition by creating / partition of 10GB and swap area of 1GB and /home partition of 5GB. 
After restarting my pc, i am not able to find an option to boot to XP
Also i am not able to find /boot/grub/menu.lst file
In the terminal i tried to give the command gksudo gedit /boot/grub/menu.lst.
It shows an empty file.
Can anyone tell what went wrong during the installation
Also during my installation i once got an error saying ubuquity encountered a problem.
Does it have any impact?......
Ubuntu is not able to recognize my monitor as well. In the Display options it is showing unknown Monitor

---

### Post by zkriesse on 2009-08-22
Well to start with Karmic Koala is NOT!!! STABLE!!! yet...so that is VERY likely to cause problems. Second, how exactly did you set up the system to dual boot?

---

### Post by Dare2DoIt on 2009-08-22
This is what fdisk -l shows
Device Boot      Start         End       Blocks          Id  System
/dev/sda1   *           1        2057     16522821     7  HPFS/NTFS
/dev/sda2            2058        9733    61657470    f  W95 Ext'd (LBA)
/dev/sda5            2058        4114    16522821    b  W95 FAT32
/dev/sda6            4115        6426    18571108+  b  W95 FAT32
/dev/sda7            6427        7770    10795648+  b  W95 FAT32
/dev/sda8            7771        9002     9896008+  83  Linux
/dev/sda9            9003        9125      987966     82  Linux swap / Solaris
/dev/sda10           9126        9733     4883728+  83  Linux

Firstly, I have four partitions in Windows XP one partition is NTFS and the rest are FAT32
During Ubuntu installation, through manual partition i divided the fat32 partition into two fat32 and ext4 partitions. Thereafter in ext4 partition, i made room for / partition, swap area and /home partition and formatted this partitions and installed ubuntu.

---

### Post by overdrank on 2009-08-23
Moved to Karmic Koala Testing and Discussion

---

### Post by Nburnes on 2009-08-23
Karmic Koala uses Grub 2 (1.94 or something like that.) It doesn't use conventional menu.lst anymore.

In Terminal type

```
sudo update-grub
```

And it should automagically update and add the XP partition.

---

### Post by Dare2DoIt on 2009-08-23
Ok.. i will give it a try......
How about my Monitor. My desktop background doesn't fit to the entire screen. In Display preferences i am not able to configure to more 1152*864........
Also i have lost the audio.........

---

### Post by Nburnes on 2009-08-23
> **Dare2DoIt said:**
> Ok.. i will give it a try......
How about my Monitor. My desktop background doesn't fit to the entire screen. In Display preferences i am not able to configure to more 1152*864........
Also i have lost the audio.........

Do you have any hardware drivers running?

---

### Post by VMC on 2009-08-23
> **Dare2DoIt said:**
> Ok.. i will give it a try......
How about my Monitor. My desktop background doesn't fit to the entire screen. In Display preferences i am not able to configure to more 1152*864........
Also i have lost the audio.........

What's the output of this terminal command: ```
lspci -nn | grep VGA
```

Also, output: ```
cat /boot/grub/grub.cfg
```

---

