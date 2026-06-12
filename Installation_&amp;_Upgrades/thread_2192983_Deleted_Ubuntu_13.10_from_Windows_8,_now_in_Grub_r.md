---
title: "Deleted Ubuntu 13.10 from Windows 8, now in Grub rescue"
date: 2013-12-10
forum: Installation &amp; Upgrades
---

### Post by tausch86 on 2013-12-10
Hello,

I have deleted my Ubuntu 13.10 partition from Windows 8 but the Ubuntu partition that I deleted was the primary partition and now I'm stuck in Grub Rescue. My laptop is a SONY VAIO VPCSB. It came preinstalled with Windows 7 but I made ubuntu my primary OS. and windows 7 is no longer being used on my laptop.
 
I have a USB with a 13.10 ISO loaded onto it and I would like to install 13.10 as my primary partition once again. In the BIOS of my laptop I have External Device Boot enabled and for my boot priority I have it as External Device as being the top priority, followed by Internal Optical Disc Drive. When I boot up my laptop with the USB inside I find myself in grub rescue with

```

grub rescue> ls

(hd0) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)
```

I feel extremely silly ending up in this situation and I will not be managing my linux partitions externally again. 

Thanks!

---

### Post by necromonger on 2013-12-10
do you want to dual boot linux and windows 8?

---

### Post by tausch86 on 2013-12-10
Hi Necromonger,

Yes. Windows 8 and 13.10. I would still like to boot into grub if that's possible. 

Thanks!

---

### Post by oldfred on 2013-12-10
It seems like flash drive is not being recognized as a boot able device. How did you install ISO to flash drive? 

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by tausch86 on 2013-12-12
So that was the issue. I followed this tutorial

[http://students.washington.edu/jtbull/usbboot.php](http://students.washington.edu/jtbull/usbboot.php)

now when I insert the computer that I'm using now, it wants to install ubuntu meaning that it worked. but when I insert it into my grub-rescue computer it responds 
"Remove Disks or other media. Press any key to restart". then it just goes back to normal grub rescue.

I am using a 64-bit 13.10 ISO which I put onto the USB drive but I noticed that, in the tutorial, it calls for **format fs=fat32** which could mean 32-bit? IDK. Any idea on how to proceed?

---

### Post by oldfred on 2013-12-12
Those instructions look like they are for a Windows disk.

Post this link, but you need to boot Ubuntu live installer and add Boot-REpair or download Boot-Repair for flash drive or CD/DVD which you install the same way as other Linux ISO.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

FAT32 is a format for smaller devices that is compatible with just about everything. But for Windows compatibility on a larger shared data partition NTFS is recommended.

FAT32 for standard installer is used for both 32bit & 64 bit installs. And unless computer is pretty old, you should be installing 64 bit. Most computers that now need 32 bit installs will only work with Lubuntu not full Ubuntu.

      
 LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

