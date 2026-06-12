---
title: "no grub after mbr fix"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by sree88 on 2013-06-10
i have a dual boot laptop(toshiba) ubuntu 11.10 and win 7 home premium. the laptop suddenly started running very slow. when i restarted first it showed
grub rescue> console. from next restart it started showing "exiting pxe rom no bootable device insert boot disk...."

after searchin in internet i found that MBR is the problem and should fix it. so i booted from windows installation disc and did fix the mbr(used these commands bootrec /fixmbr and bootrec /fixboot). now the laptop starts, but no grub, takes very long time to boot. it freezes alsmost every minute. 
i tried to repair grub by "boot-repair" using 11.10 live cd  but it seems there is no support for ubuntu 11.10. please suggest me some solutions. 

Should i try upgrading to ubuntu12.04.

what can be the reason for laptop freezes..

thanks in advance
sree

---

### Post by prodigy_ on 2013-06-10
> **sree88 said:**
> the laptop suddenly started running very slow. when i restarted first it showed
grub rescue> console
Sounds like a possible hardware issue. Try booting from a Live media and use Disk Utility > SMART Data to check your HDD status. (SMART only monitors certain parameters though. If you want an exhaustive report, there's usually some diagnostic utility you can d/l from the HDD vendor website.)

---

### Post by fantab on 2013-06-10
Yes it does sound like a Hardware issue. Download and burn 12.04 on a DVD/USB and try what prodgy_ has suggested. Then also run MemTest from LiveUbuntu...

Good Luck...

---

### Post by sree88 on 2013-06-12
hi fantab and prodigy_ can u please guide me using SMART to fix this error. i am having ubuntu 12.04 cd.

---

### Post by fantab on 2013-06-12
Boot with Ubuntu CD and "Try Ubuntu without installing". After the desktop is loaded find and open 'DISK UTILITY'. After you choose your HDD you will see "SMART Data (View SMART data and run self-tests)". Run it and you will know if there are any errors on the HDD. SMART may not fix the Errors, to fix errors you will probably have use the disk tools provided by your HDD manufacturer.

---

### Post by grahammechanical on 2013-06-12
May I add something? You have fixed the MBR using Windows commands. That has removed Grub from the MBR. That is why you do not see a Grub Menu. If there is a hardware problem and you fix it then you will still not see a Grub menu. You will need to either put Ubuntu into a Windows loader menu or install Grub back into the MBR.

It is true that 11.10 is no longer supported. But that does not stop you from using it as a live session and running the necessary commands. The Linux commands to do this have not reached End Of Life.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Regards.

---

### Post by sree88 on 2013-06-13
hi all, i booted with Ubuntu 12.04 cd, **i repaired GRUB using Boot-repair**, and i used SMART to analyse the HDD. it showed hard disk has some bad sectors.
I "upgraded" 11.10 to 12.04, now the prooblem is the system is unresponsive all the times. the windows goes dim(blur) wen i try to do anything. Is it due to the incompatability of packages installed in the previous version. what should i do to install a fresh copy of 12.04 "removing" 11.10.

When i switch on **sometimes** "exiting pxe rom no bootable device insert boot disk...." error is displayed.
The grub menu now has an entry "Previous Linux versions"

also i dont have a swap space. How can i add it without disturbing windows.
my system is having 6 GB RAM.

Boot-repair generated this URL after repairing GRUB
[http://paste.ubuntu.com/5758235/](http://paste.ubuntu.com/5758235/)

---

### Post by prodigy_ on 2013-06-13
> **sree88 said:**
> it showed hard disk has some bad sectors.

Generally this means the HDD is not safe to use anymore. If it's still in warranty, ask for replacement. If not, you probably should buy a new one.

---

### Post by sree88 on 2013-06-13
any way to fix bad sectors? i m out of warranty :)

---

### Post by fantab on 2013-06-13
"Bad Secors" CANNOT be fixed, AFAIK. However, what we can do is to run some disk repair utility (most of the HDD manufacturers provide this) which will push the 'bad sectors' to the end of the disk and lock them out. But you must get a new HDD ASAP, as the disk will create more 'bad sectors' as it ages.

Check you HDD manufacturer's website and you will find a 'disk repair' utility. Most of the times the utility can be run from Windows only.

Good Luck...

---

### Post by sree88 on 2013-06-13
can u tell how can I assign a swap space and how to reinstall a fresh copy if ubuntu 12.04

---

### Post by fantab on 2013-06-13
Well to create SWAP you will have to create a partition of about 2-4GB and for filesystem choose SWAP or LinuxSWAP. You can do this with Gparted which is there on your Ubuntu install disk.

Reinstalling wil be same as it was when you installed Ubuntu first. This time choose "Something Else" option from the "Installation Type" select your present Ubuntu partition and hit 'change'. Then select format, Use as=ext4 and Mountpoint=/. That is all. If SWAP is already created then you have to do nothing more about it.

Do reinstall without taking care of those bad sectors...

Good luck....

---

### Post by sree88 on 2013-06-14
thanks a lot.. i reinstalled fresh copy ubuntu12.04. even now i m experiencing laptop freezes every 2-3-seconds. but sometimes it ll work fine. Harddisk is having some 174 bad sectors according to SMART data. any other options.

---

### Post by fantab on 2013-06-14
> **sree88 said:**
> thanks a lot.. i reinstalled fresh copy ubuntu12.04. even now i m experiencing laptop freezes every 2-3-seconds. but sometimes it ll work fine. Harddisk is having some 174 bad sectors according to SMART data. any other options.

Get a new HDD.

---

### Post by sree88 on 2013-06-14
thanks for all your support.. planning to get a new HDD..

---

