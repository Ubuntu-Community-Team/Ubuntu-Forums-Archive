---
title: "Update-Initramfs Problem"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by ThePol1 on 2011-07-13
I'm doing a fresh install of Ubuntu 11.04 (amd64) on my machine. It was running Ubuntu 11.04 (amd64) just fine for a month or two until I tried to do an apt-get dist-upgrade this afternoon to pick up the latest kernel (2.6.38-10-generic). During the upgrade process, the update hung on the following line:
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic

Now, when I try to do a fresh install, it hangs on the *same* line:
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic

I've let it go overnight and it never comes back.

Please help. :(

---

### Post by ThePol1 on 2011-07-14
Bump. Please help. This is my main computer and really needs to be working.

Any suggestions on how to debug this problem?

Does it sound like a RAM problem? Should I try installing from a CD (instead of a USB drive)?

---

### Post by ThePol1 on 2011-07-14
Is there any additional information I can provide to help diagnose this problem?

In terms of my system:
CPU: Intel i7 2600k
MB: GIGABYTE GA-Z68X-UD3P-B3 LGA 1155 Intel Z68 SATA 6Gb/s USB 3.0 ATX
RAM: Crucial 8GB (4 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10600) 
Video: EVGA 01G-P3-1452-TR GeForce GTS 450
HD: 1 TB Western Digital Blue
DVD: Samsung DVD-RW
eSATA: Rosewill Sil3132 R5

---

### Post by dino99 on 2011-07-14
it always take a while to generate it, on all systems. But you still can purge headers & image then reinstall in case of troubles.

clean your system first:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

only use genuine ubuntu repo

then update

sudo apt-get install -f
sudo dpkg --configure -a

and watch logs , maybe you will find usefull errors to help you :)

---

### Post by matt_symes on 2011-07-14
Hi

This is during a fresh install, where update-initramfs is failing ? 

Did you format the drive before or during installation ? If not, format the entire drive.

I would also check your hardware as a matter of course. Check the hard disc's SMART status. You can do this using disc utility from the LiveUSB. Run a long test and then check the results. 

Also, make sure every thing is seated inside the box.

Kind regards

---

### Post by ThePol1 on 2011-07-14
> **matt_symes said:**
> Hi

This is during a fresh install, where update-initramfs is failing ? 

Did you format the drive before or during installation ? If not, format the entire drive.

I would also check your hardware as a matter of course. Check the hard disc's SMART status. You can do this using disc utility from the LiveUSB. Run a long test and then check the results. 

Also, make sure every thing is seated inside the box.

Kind regards

That is correct -- after the apt-get dist-upgrade failure, I decided to do a fresh install. I am formatting the drive during installation. Should I try was to format the drive using the LiveUSB and *then* do the install?

Good idea about the SMART check -- I'll do that as well.

After the format and SMART check, my next step will be to make sure everything is seated properly.

Thank you and dino99 for your responses!

---

### Post by ThePol1 on 2011-07-14
[SOLVED]

After trying a new hard drive, removing the DVD-RW, multiple installation media, etc., etc, etc. I found the problem to be my RAID card based on the Sil3132 chipset. I added that card a couple weeks ago (after my initial OS install). Once I removed that, the OS install went swimmingly and the upgrade to the latest kernel went well. :D

---

### Post by matt_symes on 2011-07-14
Hi

Excellent :D And thanks for posting back your fix and, more importantly, the card chipset.

Kind regards

---

