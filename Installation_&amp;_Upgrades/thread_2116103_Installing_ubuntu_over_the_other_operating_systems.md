---
title: "Installing ubuntu over the other operating systems by mistake cleared my hard drive"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by aminghz on 2013-02-14
I had a dual boot system with windows7 and ubuntu 12.04. I was trying to upgrade my Ubuntu with  a CD, and I mistakenly chose to install it over the other operating systems. I think it started a quick format and cleared all the partitions and I noticed and canceled the setup. Now it only boots in a blank black screen with a blinking cursor. I have some important data and I don't have the backup of those.

Is there a way I can recover my data? I tried to boot the system with ubuntu CD and I chose try ubuntu. I can see my hard drive existing there but it shows 450GB free and 20GB used.

---

### Post by ibjsb4 on 2013-02-14
You can try testdisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Mark Phelps on 2013-02-14
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by aminghz on 2013-02-14
> **ibjsb4 said:**
> You can try testdisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Im trying to install testdisk from live ubuntu CD. I see this message:

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree
reading state information... Done
E: Unable to locate package testdisk

do you have any idea?

---

### Post by ibjsb4 on 2013-02-14
You need to stay off your broken computer, you risk further damage by using it.  Use another computer to create a cd.

---

