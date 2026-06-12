---
title: "help on post installation"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by sdrakulich on 2008-04-09
ubuntu neradi....kao sve radi (pokaxe boot, ubuntu bar i kako ide preko ekrana pokazuje boot), i onda kaxe u komand-line-u da su 5 stvari ok, i onda ekran se umrayi

I installed everything correctly so that my system dual boots with xp and ubuntu, the latest (not the beta), and when I try and start from the dual boot screen, I get everything perfect, the bar indicating that ubuntu is loading, etc...after the bar completes, i get 5 command lines checking whether something is ok, and after that my screen goes black, it is still on, but it is as if the nothing is on...the live CD works fine, so it cannot be my configuration, at least I don't think so...PLEASE HELP ME! :(:(:(

---

### Post by Pumalite on 2008-04-09
Boot your Live CD and post>
sudo fdisk -lu

---

### Post by sdrakulich on 2008-04-09
I am sorry, but would you please be kind to elaborate on what the problem is, (screen, computer installation, etc) and how should I post the command line, where, etc

thanks so much for your help!!!

sdrakulich

---

### Post by sdrakulich on 2008-04-09
> **Pumalite said:**
> Boot your Live CD and post>
sudo fdisk -lu
I'm not sure i replied to you, so

I am sorry, but would you please be kind to elaborate on what the problem is, (screen, computer installation, etc) and how should I post the command line, where, etc

thanks so much for your help!!!

sdrakulich

---

### Post by Pumalite on 2008-04-09
Once you get to the Desktop, go to Applications>Accessories>Terminal. Copy and paste my command there, hit -Enter-. Copy and paste the out put here.

---

### Post by sdrakulich on 2008-04-09
> **Pumalite said:**
> Once you get to the Desktop, go to Applications>Accessories>Terminal. Copy and paste my command there, hit -Enter-. Copy and paste the out put here.
im sorry, but isnt fdisk formatting the disk, and what does sudo do?

---

### Post by Pumalite on 2008-04-09
No. It will show your drives/partitions.

---

### Post by sdrakulich on 2008-04-09
and after that, I did get a list of disc partitions and drives, but what after

---

### Post by Pumalite on 2008-04-09
Copy and paste here, so I can continue to help you.

---

### Post by macogw on 2008-04-09
Hey, I saw your comment on my article...

What do the 5 lines say they're checking?  What kind of graphics card do you have?

If you've got an IRC client (xchat's good... [windows](http://silverex.org) [mac](http://sourceforge.net/projects/xchataqua/)) you can find me in #ubuntu as macogw (as my sig says)

---

### Post by sdrakulich on 2008-04-09
i goes fairly quickly, so i cannot see...im sorry

this guy above told me to write sude fdisk, and this is what i have gotten back

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

---

### Post by sdrakulich on 2008-04-09
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

---

### Post by macogw on 2008-04-09
you need the -l

so it says
```
sudo fdisk -l
``` where the -l is a little L

---

### Post by sdrakulich on 2008-04-09
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81fc81fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16924   135941998+   7  HPFS/NTFS
/dev/sda2           21523       24320    22474935    f  W95 Ext'd (LBA)
/dev/sda3           16925       21522    36933435   83  Linux
/dev/sda5           21711       23015    10482381    7  HPFS/NTFS
/dev/sda6           23016       24320    10482381    7  HPFS/NTFS
/dev/sda7           21523       21710     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 


those are my results
thank you for your time while you are helping me on this!!!

---

### Post by macogw on 2008-04-09
Can you go to Places -> Computer and double click on the one that represents the Linux drive (sda3)?  In there, go into the boot directory, and in there the grub directory.  Open up menu.lst in a text editor and paste it here.

---

### Post by sdrakulich on 2008-04-09
the only drives i can go to are the following:

Floppy Drive
CD/DVD ROM Drive
CD-R/DVD-RW Drive
129.6 Gb Volume
35.2 Gb Volume
Data
Ubuntu (this is the name of the partition that contains Ubuntu [i installed it in the first place] and all this contains is a folder called "System Volume Information")
Filesystem

BTW is there any remote control for Ubuntu that you can fix remotely for me?
I thought i saw xvnc while browsing the net

---

### Post by macogw on 2008-04-09
Check that 35MB one.  That's the same size as your Linux partition.  I think that Ubuntu one might be the virtual file system from the live cd.

If you have port 22 on your router forwarded to your computer and have openssh-server installed, I could ssh in and look around (through the terminal).  VNC would require that you have working graphics, however.  If you don't have openssh-server, you can get it by hitting Escape when the GRUB thing comes up at the beginning and choosing the recovery mode.  You'll be taken to a text prompt where you can type ```
apt-get install openssh-server
```

---

### Post by sdrakulich on 2008-04-09
well, I'm off to bed, but if I contact you tomorrow, will you be able to talk?

---

### Post by sdrakulich on 2008-04-10
> **macogw said:**
> Hey, I saw your comment on my article...

What do the 5 lines say they're checking?  What kind of graphics card do you have?

If you've got an IRC client (xchat's good... [windows](http://silverex.org) [mac](http://sourceforge.net/projects/xchataqua/)) you can find me in #ubuntu as macogw (as my sig says)
I just read the five messages:

* starting anachronistic cron anacron
* starting deferred execution scheduler atd
* starting periodic command scheduler crond
* checking battery state
* Running local boot scripts (/etc/rc.local)

---

### Post by macogw on 2008-04-10
That's all perfectly normal stuff.  There's not a text prompt or anything?  Well, when you get a chance, hit ctrl+alt+f1 from the black screen to get to a text prompt if there isnt one and log in.  Then run ```
lspci
``` and see what video card you have.

---

### Post by sdrakulich on 2008-04-10
ironically im not asleep yet, but here it is...I pressed ctrl+alt+f1, and it gave me a login...I logged in, and it says it is correct.

this is the last line i see:
sdrakulich@stefan-Ubuntu:~$

It also gives me info on last login, warranty, open source software only, and mainly, 1 FAILURE SINCE LAST LOGIN...andyways, thanks!

---

### Post by sdrakulich on 2008-04-10
oh yeah and nothing about a video card...

---

### Post by macogw on 2008-04-10
Did you run lspci like I said?  The login wouldn't tell you that, but lspci lists your hardware.  Or if you just know off the top of your head what it is, that works too.

---

