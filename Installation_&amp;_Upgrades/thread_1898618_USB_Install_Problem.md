---
title: "USB Install Problem"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by mightymouse3062 on 2011-12-21
Good Evening, 
I am trying to install Ubuntu from a USB stick and I have not had any success. I have tried several favors including Ubuntu 10.04, 11.04, 11.10, Xubuntu 10.04 alt, Xubuntu 11.04 alt, and Xubuntu 11.10 alt. 

I am using unetbootin under windows to create the bootable USB, in which it boots without a problem but during installation it will error out at the detecting the cd-rom. The syslog shows 
CD-ROM mount failed: device=/dev/sr0/ 

I am not sure how to fix this problem. Any assistance? 

Thanks,
Mike

---

### Post by xXQuadPolarXx on 2011-12-22
Yeah,

I have had the same problem for some reason it the setup works fine to install the needed files to the USB drive but once its tine to run from the USB stick & install it just doesn't work. I know this use to work fine because I use to use the USB for my other PC which has no HDD in it & that was my plan to do again to have the 2nd PC for use but for some reason it bugs out on me every time now.

:confused:

---

### Post by mastablasta on 2011-12-22
> **mightymouse3062 said:**
> CD-ROM mount failed: device=/dev/sr0/ 
 

 
what model of "CD-ROM" are you using? how is it connected to motherbaord (SATA or ATA).
 
can you skip this error and continue with install?

---

### Post by sikander3786 on 2011-12-22
I hope you are receiving this message while installing from an alternate disc only and not from the Desktop version. Do you really need to install from the alternate disc? I mean, if yes, you would need to mount your USB device as a CD-ROM for successfully proceeding with the install.

If the intention is to simply get a working desktop, you should probably stick with Desktop edition of Ubuntu as that is lot easier to install. Just make sure the downloaded image is not corrupt by comparing the MD5SUMs.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you want to stick with the alternate or server install disc, a few working workarounds are mentioned here:

[http://ubuntuforums.org/showthread.php?t=1750464](http://ubuntuforums.org/showthread.php?t=1750464)

---

### Post by mightymouse3062 on 2011-12-26
Good Evening, 
I have tried all of the suggestions in both of topics with no luck. I see my usb drive on /dev/sdb1 and in /var/log/syslog it is saying CD-ROM mount failed: device=/dev/sr0 fstype=iso9660. 
I tried to mount sdb1 to /cdrom using 
mount -t vfat /dev/sdb1 /cdrom 

Once I do that, in syslog I get two lines: 
cdrom-detect: Unmounting CD just to be sure
cdrom-detect: CD-ROM mount failed: device=/dev/sr0 fstype=iso9660

I am currently trying Xubuntu 10.04 alt. 

Any suggestions? 

Thanks,
Mike

---

