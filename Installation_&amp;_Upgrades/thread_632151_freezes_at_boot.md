---
title: "freezes at boot"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by Dabrorius on 2007-12-05
after clean installation of ubuntu gutsy it freezes when it's loading at about 1%
I read something about that could be problem with sata disk but im'n not sure what to do now

computer is laptop acer aspire 5520 

p.s. it runs normally from cd

---

### Post by Pumalite on 2007-12-05
Did you do md5sum before burning your CD? Could you please post your specs?

---

### Post by dhergott on 2007-12-14
I am having the same problem. I am using an Acer 5520 with AMD 64 dual core.   I am using the AMD 64 bit version 7.10 Ubuntu.  

Dan

---

### Post by Pumalite on 2007-12-14
> **dhergott said:**
> I am having the same problem. I am using an Acer 5520 with AMD 64 dual core.   I am using the AMD 64 bit version 7.10 Ubuntu.  

Dan
Try the 32 bit Alternate CD.

---

### Post by foppeh on 2007-12-15
Same laptop, description [here]("http://www.dev.hemminga.net/acer.html") same problem after fresh install. I tried both 32 bit standard CD and alternate, 
System hangs at startup, the very beginning of the bar. In 'recovery mode' it may hang at various stages, but noticeable more often at ' Uniform CD-ROM driver Revision: 3.20.

Her comes the funny part: eventually after many tries it does start up.This seems completely random, it may be the second attempt, it may be the tenth.

---

### Post by Pumalite on 2007-12-15
This is for 5100, but, it might help understand the problem:
[http://ubuntuforums.org/showthread.php?t=595979](http://ubuntuforums.org/showthread.php?t=595979)

---

### Post by foppeh on 2007-12-15
@Pumalite: I read the page, but i can't destill the information that is relevant to me. Can you be a bit more precise as to where I need to look?

Tx

---

### Post by foppeh on 2007-12-16
I somehow got a step further. From the suggested post I recognized at least the splash error so I did:
```
sudo nano /etc/usplash.conf
```
I changed the splash settings from 1280x1024 to 1024x768. The screen is a 17" wide 1440x900. After saving I did
```
sudo update-initramfs -u
```

This should and could solvesome problem, but not the startup at boot error. Whereas It first gave notices about splash screen sizes tried and failed, it now reports:
> Check root= bootargs cat /proc/cmdline
or missing modules, device: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/9c183c8d-2249-4669-974d-dd4deb9c5241 does not exist. Dropping to a shell!

Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initranfs)
I sincerely hope some one can help with this.

Tx

---

### Post by Pumalite on 2007-12-16
Get in there and do:
blkid, and
cat /etc/fstab
And compare UUID's

---

### Post by foppeh on 2007-12-16
Hi Pumalite,

What do you think of this:

blkid:
```
/dev/sda1: UUID="CE40944BE49BED2A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="7C8C775C8C770FBE" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="9c183c8d-2249-4669-974d-dd4deb9c5241" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="84528c8a-4a96-48b8-b7f1-237e894272b2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="cfead6cb-ecb4-44f4-9680-920e118bbc55" TYPE="swap" 
```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=9c183c8d-2249-4669-974d-dd4deb9c5241 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=84528c8a-4a96-48b8-b7f1-237e894272b2 /home           ext3    defaults        0       2
# /dev/sda1
UUID=CE40944BE49BED2A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=7C8C775C8C770FBE /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=cfead6cb-ecb4-44f4-9680-920e118bbc55 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

It does give these type of errors at boot, but they scrolled away too fast to notice.
Can you give any advise as to continue from here?

Tx

---

### Post by Pumalite on 2007-12-16
It says your sda3 does not exist, but is not true. I ran out of ideas. Someone will chime in.

---

### Post by foppeh on 2007-12-16
I have re-installed Ubuntu and I get the same error. Quite frustrating.

I have one 120Gb harddisk. 
10GB: ACER/VISTA recovery (hidden in Windows)
50GB NTSF Windows Vista
50GB originally NTSF, now available for Ubunyu.

This time before the setup, I went to Vista and used it's disk manager to wipe the data disk (then Ubuntu EXT3) and created a 10 GB NTSF. So there was 40GB available.

In the Ubuntu setup I choose 'Guided setup on largest available space' -I retranslated this part, it's in Dutch at my setup- So it installed on the 40GB that's left.

Is there anything I can do to prevent the error at boot of a fresh Ubuntu install? Do you have any suggestion on setting things up differently?

---

### Post by foppeh on 2007-12-17
I now installed 64 bit version with same result :confused:

I found this: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256)
Can somebody have a look at it and advise me if this bug is the same as mine, and if it is, guide me to the steps I want to take to solve it.

Tx

---

### Post by foppeh on 2007-12-17
[http://ubuntuforums.org/showthread.php?t=282956]("http://ubuntuforums.org/showthread.php?t=282956")

I tried ```
sudo update-initramfs -u -k 2.6.22-14-generic
``` and so far the laptop boots flawless. :). I hope this stays that way. For others reading this post, you find your kernel number through: ```
uname -a
```

Wish me luck

---

### Post by Pumalite on 2007-12-17
> **foppeh said:**
> [http://ubuntuforums.org/showthread.php?t=282956]("http://ubuntuforums.org/showthread.php?t=282956")

I tried ```
sudo update-initramfs -u -k 2.6.22-14-generic
``` and so far the laptop boots flawless. :). I hope this stays that way. For others reading this post, you find your kernel number through: ```
uname -a
```

Wish me luck

Good luck.

---

### Post by squeky on 2007-12-17
> **foppeh said:**
> [http://ubuntuforums.org/showthread.php?t=282956]("http://ubuntuforums.org/showthread.php?t=282956")

I tried ```
sudo update-initramfs -u -k 2.6.22-14-generic
``` and so far the laptop boots flawless. :). I hope this stays that way. For others reading this post, you find your kernel number through: ```
uname -a
```

Wish me luck

I have the same laptop and same issue (without the Vista rescue partition or Vista).  I did the command above and got one good boot, then back to being stuck at the beginning of the boot.  This is a super annoying problem, has anyone fixed this consistently?  foppeh--did this fix your consistantly?  Thanks for the help.

---

### Post by foppeh on 2007-12-17
> **squeky said:**
> I have the same laptop and same issue (without the Vista rescue partition or Vista).  I did the command above and got one good boot, then back to being stuck at the beginning of the boot.  This is a super annoying problem, has anyone fixed this consistently?  foppeh--did this fix your consistantly?  Thanks for the help.
I now have three good boots out of three which is far better than the one out of four I am used to. I don't dare to boot too often, but I'll keep you updated.
In the thread I linked to there is another command, to satisfy another kernel. Don't ask me what's it about. This is the code:
```
sudo update-initramfs -u -k 2.6.17-10-386
```
Change the 2.6.17-10 to your kernel number, leave the -386 intact.

The issue is quite common and nearly only reported by users of an Acer Aspire laptop. But not every body seems to experience troubles.

Have a look at my blog: [http://www.blog.hemminga.net/index.php/tutorials/](http://www.blog.hemminga.net/index.php/tutorials/) and also have a look at the two larger threads in this forum (do a search yourself) about the Acer Aspire 7520 and the 4520, that seems to have similar hardware.

Good luck

---

### Post by foppeh on 2007-12-18
I had a 5/5 succes at boot, but now it's all bad again. I turned the laptop of and after an hour or so tried again and it booted.
I wonder if temperature can have something to do with it.

---

### Post by foppeh on 2007-12-18
According to [http://ubuntuforums.org/showthread.php?t=624974](http://ubuntuforums.org/showthread.php?t=624974) it is a acpi problem.

---

### Post by igknighted on 2007-12-18
> **foppeh said:**
> According to [http://ubuntuforums.org/showthread.php?t=624974](http://ubuntuforums.org/showthread.php?t=624974) it is a acpi problem.

Try compiling a fresh kernel from source (search for the master kernel thread, the instructions are foolproof). I did this and it is booting happily every time now.

---

### Post by nvshaji on 2007-12-19
Try adding the kernel option "all_generic_ide" for those who are not able to boot at all. You need to edit the grub prompt by pressing "e", select kernel and press "e" again. Now append this option "all_generic_ide".

---

### Post by Niej on 2008-02-19
I have noticed that this is a very common problem on acer laptops, I'm suffering the same problems.
In my case, aspire 7520 athlon64 x2 2gb ata160gb an nvidia7000m running gusty 7.10amd64
Is there a final solution? 
I will appreciate any post on this subject.
hejda

---

### Post by squeky on 2008-02-19
> **Niej said:**
> I have noticed that this is a very common problem on acer laptops, I'm suffering the same problems.
In my case, aspire 7520 athlon64 x2 2gb ata160gb an nvidia7000m running gusty 7.10amd64
Is there a final solution? 
I will appreciate any post on this subject.
hejda

I gave up and went back to XP :confused:

---

### Post by LuisPT on 2008-02-25
I have also an Acer Aspire 5520.

[B]The SOLUTION is very simple:

- just add the option all_generic_ide to the grub boot option[/B]

We will never have that problem again.

---

