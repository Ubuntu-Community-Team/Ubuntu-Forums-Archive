---
title: "Ubuntu 10.4 wont boot"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by danacr94 on 2010-04-14
Hello,

I installed ubuntu 10.4 beta about a week ago it has all been working fine until I booted up my pc today, ubuntu goes straight to low graphics mode and when i try to configure it doesnt do anything, and when i try to continue in low graphics mode it stays on the splash screen and thats it.

i have dual boot win7 and ubuntu 10.4 beta.

i have a HP pavilion dv7

thanks danacr94

---

### Post by Sonsum on 2010-04-14
I have this too on my PC. With and without Wubi.

My netbook loves 10.04, but my desktop refuses to boot it. I have no idea why.

If you want some of the social features in 9.10, this blog post has made it so I can get by :)

[http://clintthewookie.wordpress.com/2010/04/01/get-ubuntu-10-04-beta-1-features-on-your-9-10-system/](http://clintthewookie.wordpress.com/2010/04/01/get-ubuntu-10-04-beta-1-features-on-your-9-10-system/)

---

### Post by garvinrick4 on 2010-04-14
> **danacr94 said:**
> Hello,

I installed ubuntu 10.4 beta about a week ago it has all been working fine until I booted up my pc today, ubuntu goes straight to low graphics mode and when i try to configure it doesnt do anything, and when i try to continue in low graphics mode it stays on the splash screen and thats it.

i have dual boot win7 and ubuntu 10.4 beta.

i have a HP pavilion dv7

thanks danacr94
Wubi install or partition install?

---

### Post by danacr94 on 2010-04-14
Windows was installed first and then I installed ubuntu on a 84gig partion. I am new to ubuntu.

i really need this fixed

---

### Post by danacr94 on 2010-04-15
I urgently need this fixed can somebody help?:(

thanks danacr94

---

### Post by garvinrick4 on 2010-04-15
I do not quite understand when you say configure it?

When you start up your computer do you get a boot screen that says
Ubuntu or Windows and you make your choice then hit enter key?

It then go's to Ubuntu splash screen of Purple and just stays there?

And you have rebooted and it still stays on Purple screen that says Ubuntu with 5 dots underneath it?

You do realize that you installed a Beta edition of the next OS instead of a stable version of Ubuntu.
Booting has been an issue with new "plymouth" a splash screen program. Has always been fixable for
me, we will get it going.

---

### Post by danacr94 on 2010-04-15
it was going into low grpahics mode and it was asking me if i wanted to configure it now restart x or run in low graphics mode. when i ran it in low graphics mode it would just stay on the splash screen with the circles under the ubuntu sign. now it doesnt go into low graphics mode for some reason. but the splash screen just keeps loading and doesnt do anything.



and yeah i knew it was a beta, but it has been working since saturday

thanks danacr94

---

### Post by danacr94 on 2010-04-15
oh yeah at startup of pc i do get to select if i want to go to ubuntu or windows

---

### Post by garvinrick4 on 2010-04-15
Have you used your install CD as a Live CD yet? Need to find out what your 
CODE:

sudo fdisk -l    (small L)

sudo blkid      (small L second letter)

So I can show you how to update and upgrade from Live CD and 2 add or remove a program.

Here is what mine looks like so you know what I want to see.
Put your install CD in tray and boot off of it. Pick just want to see what Ubuntu looks
like and NOT to install. When comes up click on network icon in right upper panel and get internet up and working. Then open a Terminal. Put the code in one at a time that I have given you. Like this.
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0xe7e8e0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       15985   128192511    7  HPFS/NTFS
/dev/sda3           15985       37111   169695772+   5  Extended
/dev/sda4           37331       38914    12709888    7  HPFS/NTFS
/dev/sda5           34548       37111    20595330   83  Linux
/dev/sda6           15985       18417    19529728   83  Linux
/dev/sda7           18417       20240    14647296   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8005 MB, 8005787648 bytes
247 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x000bcb0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         123      941780    c  W95 FAT32 (LBA)
/dev/sdb2             124        1021     6875986    b  W95 FAT32


ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="SYSTEM" UUID="C6EECCF3EECCDCB5" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="66B0BDBFB0BD95D1" TYPE="ntfs" 
/dev/sda4: LABEL="RECOVERY" UUID="524C43ED4C43CB05" TYPE="ntfs" 
/dev/sda5: LABEL="maverick" UUID="1fa6b366-0d18-442c-91cb-506460b1b9ab" TYPE="ext4" 
/dev/sda6: LABEL="lucid" UUID="c4c94121-65f4-40a3-8ce3-80c720438f6b" TYPE="ext4" 
/dev/sda7: LABEL="home" UUID="1adc1fb7-dd51-48e9-8fea-77d6c6a75e78" TYPE="ext4" 
/dev/sdb1: LABEL="kingston" UUID="51F5-A398" TYPE="vfat" 
/dev/sdb2: LABEL="KHOME" UUID="B362-CA30" TYPE="vfat" 
ubuntu@ubuntu:~$ 
Copy and Paste it this thread and we will know what to do.

---

### Post by danacr94 on 2010-04-15
thanks for your help.... i dont know what the problem was but i restarted the pc today and it has been working, i went and updated everything and it is working better than it was before. 

THANKS HEAPS danacr94:P:P:P

---

### Post by garvinrick4 on 2010-04-15
> **danacr94 said:**
> thanks for your help.... i dont know what the problem was but i restarted the pc today and it has been working, i went and updated everything and it is working better than it was before. 

THANKS HEAPS danacr94:P:P:P
When the system does a fsck at boot it freezes and is a known bug. Every 23 times it
boots or so it does a fsck? When mine freezes I reboot and it is fine. They will have it
fixed by release day.

---

### Post by danacr94 on 2010-04-16
ok i understand now... thanks:)

danacr94

---

