---
title: "Where is my GRUB (dual boot with XP) ?"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by Dreamerman on 2008-07-07
Was at an educational fair some last month. Someone there insisted that I try out Ubuntu 8.04 LTS Desktop & told me not to be afraid. Anyway, I gave it a go & have this little problem.

Before Ubuntu, I am running WinXP (sigh) on a home-made-cannibalised-parts P4 1.8MHz 1G RAM with 2x 500G SATAs, 2x 300G PATAs, 1x 80G PATA & 1x DVD writer. I boot XP in SATA. All my HDDs are “whole disks” & not partitioned. I had a bad experience in disk partitioning in the distant past.

I popped in Ubuntu CD after changing boot sequence in CMOS. I used the entire 80G PATA under “prepare disk space” & everything else on default. I rebooted after installation & it went straight to XP without the boot option menu (GRUB ?). Ubuntu will only run after I boot up using the Ubuntu CD & selected “boot from first hard disk”.

I am sure there is something I missed, perhaps I should have done something different during installation under “advanced options”, “boot loader” & change the default option under “device for boot loader installation”.  I can’t remember what was the default option.

I am willing to reinstall & change the default boot option but I need to know what to change to. Can anyone help ?

Many thanks

---

### Post by falcon61102 on 2008-07-07
It sounds like Ubuntu installed the GRUB to the 80G PATA drive but that drive is not marked Active.  Since I'm guess you are in windows now, go to your drive manager and check if its marked active there.  Depending on the setup, you may be able to activate it there otherwise, boot Ubuntu and use qtparted.

---

### Post by Dreamerman on 2008-07-07
> **falcon61102 said:**
> It sounds like Ubuntu installed the GRUB to the 80G PATA drive but that drive is not marked Active.  Since I'm guess you are in windows now, go to your drive manager and check if its marked active there.  Depending on the setup, you may be able to activate it there otherwise, boot Ubuntu and use qtparted.
Falcon, thanks. Does that mean I will have 2 active drives - one for Xp & one for Ubuntu ? Will check out what is qtparted.

Many thanks

---

### Post by Dreamerman on 2008-07-08
> **falcon61102 said:**
> It sounds like Ubuntu installed the GRUB to the 80G PATA drive but that drive is not marked Active.  Since I'm guess you are in windows now, go to your drive manager and check if its marked active there.  Depending on the setup, you may be able to activate it there otherwise, boot Ubuntu and use qtparted.
Hi. Seems qtparted is used to partition hdd. I am happy to dedicate my 80G PATA for Ubuntu. Not sure how qtparted will help. Do you mind explaining a bit more ? Thanks for your patience.

---

### Post by falcon61102 on 2008-07-08
qtparted will also allow you to select which drive is active.  Your HD should already be partition appropriately if Ubuntu is already installed on it.  You should just need to activate it.

---

### Post by falcon61102 on 2008-07-08
In reference to your question earlier... No, you won't have two active drives.  You will be switching which drive is active on boot.  You can view this in Vista but I don't think you'll be able to change it.  qtparted can change it in Ubuntu.  Once you change it and reboot, you should go right to the GRUB.

---

### Post by Dreamerman on 2008-07-08
Falcon, thanks. Will try when I get home later. By the way, I drive a Ford Falcon :-)

Cheers

---

### Post by smo0th on 2008-07-08
> Ubuntu will only run after I boot up using the Ubuntu CD & selected “boot from first hard disk”.


so you manage to run both systems, that's good.. well, in ubuntu open a terminal and post the results of ```

sudo fdisk -l

```
and ```
cat /boot/grub/menu.lst
```

this helps to see how your system should be configured

---

### Post by Dreamerman on 2008-07-08
> **falcon61102 said:**
> In reference to your question earlier... No, you won't have two active drives.  You will be switching which drive is active on boot.  You can view this in Vista but I don't think you'll be able to change it.  qtparted can change it in Ubuntu.  Once you change it and reboot, you should go right to the GRUB.
Is qtparted available in Ubuntu CD ? I think installing & running qtparted is quite an involved process ([http://qtparted.sourceforge.net/download.en.html](http://qtparted.sourceforge.net/download.en.html)). Sorry to sound like an idiot.

Thanks again

---

### Post by falcon61102 on 2008-07-08
> **Dreamerman said:**
> I drive a Ford Falcon :-)


Lol... that's funny.  My SN isn't because of the car, it's just an old tag I continue to use but that is funny.  Good luck.

---

### Post by falcon61102 on 2008-07-08
> **Dreamerman said:**
> Is qtparted available in Ubuntu CD ? I think installing & running qtparted is quite an involved process ([http://qtparted.sourceforge.net/download.en.html](http://qtparted.sourceforge.net/download.en.html)). Sorry to sound like an idiot.

Thanks again

You can install it from within Ubuntu through the Package Manager and it's no problem to install/use.

---

### Post by Dreamerman on 2008-07-08
Hi. I have new information about my Ubuntu setup. Following is how Ubuntu identifies my HDDs:-

SCSI1 (0,0,0) (sda) 300G PATA master
SCSI1 (0,1,0) (sdb) 300G PATA slave
SCSI2 (0,0,0) (sdc) 80G PATA slave (Ubuntu installed here)
SCSI3 (0,0,0) (sdd) 500G SATA master (XP installed here)
SCSI4 (0,0,0) (sde) 500G SATA master

In CMOS, SCSI3 is the first boot-up HDD.

Ubuntu created the following during installation:-

Partition #1 SCSI2 (0,1,0) sdc ext3 (size 78G)
Partition #2 SCSI2 (0,0,0) sdc swap (size 3G)

The GRUB us by default is installed in hd0. I googled it & found out that hd0=sda, hd1=sdb & so on.

I would like to know how I can move the GRUB/boot loader to the correct spot so that I can boot-up my machine & see the GRUB menu.

Any help is appreciated.

---

### Post by Dreamerman on 2008-07-08
> **falcon61102 said:**
> You can install it from within Ubuntu through the Package Manager and it's no problem to install/use.
Hi. I installed it via terminal screen & ran it. A message came up after I executed it saying there is no disk & that perhaps I need sudo privileges. I am already logged in as admin. Not sure what I did wrong.

Thanks

---

### Post by upchucky on 2008-07-08
you can download qparted and burn to a cd to live boot, cause you cant have partitions mounted to do stuff in qparted, if you do not mind a larger download then get knoppix, it has qparted, and gparted, there are times when having both was a lifesaver.

plus getting advanced supergrub to fix mbr is essential tool to have just in case.


being logged in as admin still means you have to enter sudo before commands in the terminal to do root admin stuff

---

### Post by Dreamerman on 2008-07-08
> **upchucky said:**
> you can download qparted and burn to a cd to live boot, cause you cant have partitions mounted to do stuff in qparted, if you do not mind a larger download then get knoppix, it has qparted, and gparted, there are times when having both was a lifesaver.

plus getting advanced supergrub to fix mbr is essential tool to have just in case.


being logged in as admin still means you have to enter sudo before commands in the terminal to do root admin stuff
Thanks but I am hoping someone can help me on my earlier query, reproduced below. If I can fix that, maybe I can escape using qtparted.

Hi. I have new information about my Ubuntu setup. Following is how Ubuntu identifies my HDDs:-

SCSI1 (0,0,0) (sda) 300G PATA master
SCSI1 (0,1,0) (sdb) 300G PATA slave
SCSI2 (0,0,0) (sdc) 80G PATA slave (Ubuntu installed here)
SCSI3 (0,0,0) (sdd) 500G SATA master (XP installed here)
SCSI4 (0,0,0) (sde) 500G SATA master

In CMOS, SCSI3 is the first boot-up HDD.

Ubuntu created the following during installation:-

Partition #1 SCSI2 (0,1,0) sdc ext3 (size 78G)
Partition #2 SCSI2 (0,0,0) sdc swap (size 3G)

The GRUB us by default is installed in hd0. I googled it & found out that hd0=sda, hd1=sdb & so on.

I would like to know how I can move the GRUB/boot loader to the correct spot so that I can boot-up my machine & see the GRUB menu.

Any help is appreciated.

---

### Post by smo0th on 2008-07-08
first of all, make > SCSI2 (0,0,0) (sdc) 80G PATA slave (Ubuntu installed here) your first boot-up HDD, if you reply to my last post I could help you further

---

### Post by Dreamerman on 2008-07-08
> **smo0th said:**
> first of all, make  your first boot-up HDD, if you reply to my last post I could help you further

Thanks. Will post the result tonight. Cheers

---

### Post by Dreamerman on 2008-07-09
> **smo0th said:**
> first of all, make  your first boot-up HDD, if you reply to my last post I could help you further

smo0th, here's the terminal resuts:-

master@ubuntu-codegen:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x264370c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36483   293049666    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7bcff8e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    7  HPFS/NTFS

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ddf8ddf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9587    77007546   83  Linux
/dev/sdc2            9588        9964     3028252+   5  Extended
/dev/sdc5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1fcf1fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1fcf1fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001    7  HPFS/NTFS

master@ubuntu-codegen:~$ cat /boot/grub/menu.1st
cat: /boot/grub/menu.1st: No such file or directory

Unfortunately, cat /boot/grub/menu.1st did not return any results.

Thanks for your help.

---

