---
title: "stuck at &quot;Preparing to Install&quot; and then stuck when trying to get to LiveCD"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by Aullios on 2012-04-26
I'm trying to install 11.10 on a Dell XPS m1330 and I can't even get started.  I put in the CD, it boots up, and I click "Install Ubuntu".  I have the power cord plugged in, enough HDD space, and wired internet installed.. but when I click "next" it just sticks forever.

I tried again and did "Try Ubuntu" to get into Live CD, and this time it just sticks from the start.  

I'm pretty sure my CD is good, so what's next?

---

### Post by Aullios on 2012-04-26
Used the check disk tool and confirmed my CD was good.

---

### Post by sikander3786 on 2012-04-26
Welcome to the forums! :)

You said you are quite sure that the CD is good, you still need to check it against any defects. For doing so, as soon as the computer starts booting from the CD, press any key and gain access to 'Boot Options' page. Choose 'Check disc for defects' and see if it is ok. More info here:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

You might also want to check your downloaded image against any possible corruption during download:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If both of them are ok, choose 'Try Ubuntu' from the menu where you were previously choosing 'Install Ubuntu' and get to the Live desktop. Press <Super> (Windows logo key) and search the Dash for 'Terminal' and open it. Now run this command and please post the output:

```
sudo fdisk -l
```

There are also a couple of things which you can try like adding 'boot parameter' (details on the same page linked above).

---

### Post by sikander3786 on 2012-04-26
Another thing I forgot to mention, you can wait for a couple of hours and grab the latest Ubuntu 12.04 which is scheduled to be released today. It is a Long Term Support release and will be supported for 5 years whereas 11.10 is already a 6 month old release and will be supported for another 1 year.

If Ubuntu 11.10 is having some hardware issues with your machine, those might well be fixed in 12.04 already. ;)

---

### Post by Aullios on 2012-04-26
managed to get into live cd from the basic menu... then when I press winkey and type "sudo fdisk -l" I get no output

---

### Post by Aullios on 2012-04-26
that's really tempting... getting ready for bed anyway...

I'll just try hitting install from the live cd desktop and quit if that doesn't work.

---

### Post by sikander3786 on 2012-04-26
> **Aullios said:**
> managed to get into live cd from the basic menu... then when I press winkey and type "sudo fdisk -l" I get no output
It should be a lower case 'L' and not 'I'. And you need to open 'Terminal' after pressing the <Super> key and run the command in the Terminal.

---

### Post by Aullios on 2012-04-26
ok I lied,  I'm still trying.  As my previous actions confirmed, I'm a linux noob, but it's not in my nature to quit trying to figure things out :)

Here's the output from terminal:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeada2245

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    96258047    48128000    7  HPFS/NTFS/exFAT
/dev/sda2        96258048   976771071   440256512    7  HPFS/NTFS/exFAT

```

the smaller part is a windows partition, but I'm looking to format the whole thing and start clean with ubuntu.

---

### Post by Mark Phelps on 2012-04-26
Given your output, I'm guessing that you have two existing NTFS partitions -- and the first one is your Windows boot loader partition.

IF that is true, then I'm also guessing that you are running Win7.

If that is the case, do NOT use the Ubuntu installer without first creating space on your drive -- unless you want to get rid of Win7.

Read through the details below:

If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by Aullios on 2012-04-26
It's Windows Vista and I have two NTFS partitions.  I assumed the installer would let me format and repartition before installation.  I'm not looking to dual boot.

Is there a way to do that prior to installation with Live CD?

Also, my next attempt will be tonight after 12.04 finishes downloading.

---

### Post by Aullios on 2012-04-26
Still having the same problems with 12.04.

and I'm bluscreening whenever I try to boot into Vista (thus the reason I'm trying Ubuntu :) )

---

### Post by techsupport on 2012-04-26
> **Aullios said:**
> Still having the same problems with 12.04.

and I'm bluscreening whenever I try to boot into Vista (thus the reason I'm trying Ubuntu :) )

Did you resize Vista's partition inside windows first and do a couple of full power cycles?  So your drive isn't marked dirty or whatever?  I hate windows. Gparted in Ubuntu is good at shrinking partitions, but windows if not shut down properly before using gparted can cause this to happen, unfortunately. You would need the repair disc for Vista to fix that.

---

### Post by Aullios on 2012-04-26
> **techsupport said:**
> Did you resize Vista's partition inside windows first and do a couple of full power cycles?  So your drive isn't marked dirty or whatever?  I hate windows. Gparted in Ubuntu is good at shrinking partitions, but windows if not shut down properly before using gparted can cause this to happen, unfortunately. You would need the repair disc for Vista to fix that.

I found a thread on formatting hard disks, so I'm just going to reformat it to .ext3 first (sudo mkfs.ext3 -L data /dev/sda) and see if that works, since I can't get into vista to make a repair disk in the first place.

---

### Post by techsupport on 2012-04-26
> **Aullios said:**
> I found a thread on formatting hard disks, so I'm just going to reformat it to .ext3 first (sudo mkfs.ext3 -L data /dev/sda) and see if that works, since I can't get into vista to make a repair disk in the first place.

You don't have an OEM disc for Windows Vista? There you go.

---

### Post by Aullios on 2012-04-26
> **techsupport said:**
> You don't have an OEM disc for Windows Vista? There you go.

Not on me.  I'm working on a computer at my girlfriend's house and won't be back home for a few more days, so I'm trying to work with what I have.

GParted is actually recognizing the disk now that I've formatted it to ext3, so now I'm partitioning it out for a ubuntu install... hopefully I'll get a little further now.

---

### Post by techsupport on 2012-04-26
> **Aullios said:**
> Not on me.  I'm working on a computer at my girlfriend's house and won't be back home for a few more days, so I'm trying to work with what I have.

GParted is actually recognizing the disk now that I've formatted it to ext3, so now I'm partitioning it out for a ubuntu install... hopefully I'll get a little further now.

What I have done in the past that worked is do a backup of everything in Win, wipe the entire hdd with Ubuntu, and install Virtualbox and install Winxp virtually. Or you can use VMWare instead, which is better in some ways too.  It is down the list:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

It sure can save you a headache that way. :)

---

