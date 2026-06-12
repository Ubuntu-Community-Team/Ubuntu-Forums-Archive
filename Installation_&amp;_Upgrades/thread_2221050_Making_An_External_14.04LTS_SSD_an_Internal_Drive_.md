---
title: "Making An External 14.04LTS SSD an Internal Drive Without Reinstalling?"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by siabost on 2014-04-30
Hi All,

I've recently set-up my Dell Laptop to run Ubuntu 14.04LTS from an SSD fitted in an external USB Case.
Currently, an Internet-isolated instance of Windows XP resides on the internal HD and the Grub Menu gives the option of booting the XP install upon start up as well as Ubuntu.

Having run this way for a while, I'm now looking to install the SSD in the laptop and run XP in an Internet-isolated VM in Ubuntu. Thus simplifying things a lot.

The question is, can I turn the external Ubuntu SSD into an internal successfully by making the physical change then updating grub via a live Ubuntu DVD rather than having to reinstall everything?

If I recall, the procedure would be:
1. Install external Ubuntu 14.04 SSD in laptop.
2. Boot off an Ubuntu 14.04 Live DVD
3. Open Terminal
4. Mount the SSD's Ubuntu partition via the command: ```
sudo mount /dev/sda1 /mnt
``` [is this correct, as when the drive was external Ubuntu would have been on sd**b**1? Mind you, I suppose I could just click on the relevant drive partition on the Launch Bar?]
5. In Terminal: ```
sudo grub-install /dev/sda --root-directory=/mnt
``` [do I need this step as Grub is already installed?]
6. In Terminal: ```
sudo reboot
```
7. Upon reboot, in Terminal: ```
sudo update-grub
```

Do I have this right?

The laptop is a 5-year old Dell Inspiron with a 2Ghz Intel Core2Duo & 4Gb of RAM.

Many thanks.

---

### Post by oldfred on 2014-04-30
If an external, did you install grub to sdb or the external? 
Any auto install option would have installed grub to sda, but with Something Else you can install to any MBR.

If you can boot SSD, you can easily install grub to sdb.

       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Even if you run your reinstall from the DVD, you should run the dpkg reinstall. Many doing upgrades are having huge issues as the drive grub wants to reinstall to is incorrect.

---

### Post by siabost on 2014-04-30
Thanks oldfred,

Oops, forgot to mention that:

The external SSD would have been sdb at the time of installation and I did install Grub to the external (sdb) drive MBR via the "Something Else" option.
Originally I had 13.10 on the external drive and upgraded to 14.04 without any issue, so far - grub seems to have been updated to 14.04 correctly to the external sdb drive.

When I swap the external SSD drive into the laptop it will then be the only bootable drive on the system.

At what point in the process I mentioned above would I run the dpkg command?

Many thanks for your help.

---

### Post by oldfred on 2014-04-30
As long as grub is in MBR of SSD, you should just be able to plug it into system and have it work.

And if grub was originally installed to sdb or SSD at that time you probably do not have to run the dpkg.

Look at this and if SSD then you are ok. It shows a bunch of settings, but you should get a line like this with your SSD shown.

> * grub-pc/install_devices: /dev/disk/by-id/ata-SSD_G2_series_64GB_10000000000000000251


#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

---

### Post by ubfan1 on 2014-04-30
The grub.cfg file mostly uses UUIDs, which should work, but where you see things like (hd1,..  those should now be hd0.  If you get to the grub menu, you can type "e" to edit, and change what's needed, then after the successful boot, just run sudo update-grub.

---

### Post by siabost on 2014-05-01
Thanks oldfred & ubfan1.

That clarifies things a lot.

---

