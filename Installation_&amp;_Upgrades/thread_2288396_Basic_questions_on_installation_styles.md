---
title: "Basic questions on installation styles"
date: 2015-07-26
forum: Installation &amp; Upgrades
---

### Post by arunb on 2015-07-26
Hi,

I have been using Ubuntu for some years now, but I am still confused about the installation options available in Ubuntu/Linux OS.

I know Ubuntu can be installed on a USB drive and run like a Live CD. Is it also possible to install the OS on the USB pen drive instead of the hard disk of the computer ?? What about GRUB does this also get installed on the USB drive ??

I am looking for a solution that allows me to run my usual Ubuntu OS -14.04 (installed on hard disk), but I would also like to install the same OS on the USB drive, but I dont want to keep it inserted in the computer, I will insert it only when required, reboot the computer, change boot preference then select USB drive.

For normal operation the USB drive would not be inserted...

Is this kind of installation possible ??

Also what is the difference between a live CD running and a full installation ?, which is faster ??

Un related to OS (software) are USB pen drives reliable ?? Some I have are defective is this usual with USB pen drives ??

thanks
a

---

### Post by oldfred on 2015-07-27
USB flash drives do not have the life that a SSD or hard drive has. But or occasional use or just booting where most activity is reading it works reasonable well.
You do want to change a few settings to reduce writes both for speed & life.

I have several flash drives, Ubuntu installer on smaller flash drives. Some also add persistence which allows some data to be saved, but Ubuntu is not updateable as it still installs the version it is.
I have full installs of Ubuntu on larger flash drives and I have a grub only flash drive with multiple ISO to use as a repair flash drive or installer of different version. I use flash drives just as another smaller drive.

Grub defaults to install its boot loader to sda, which usually but not always is the internal hard drive. You do have to use the slightly more advanced Something Else install option where you create, format and choose a mount like / (root) or swap for each partition. On same screen is the combo box for where grub boot loader will be installed and you must change to flash drive.

Also now there are older BIOS based systems & newer UEFI based systems. Install is basically the same, but boot loader install and initial boot of install flash drive or DVD is different.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

I have full install on USB2 & USB3 flash drives. My house brand MicroCenter flash drives have worked well on my BIOS with only USB2 ports and better on newer system with USB3 ports.
I did find the even on older system with USB2 ports, a USB3 flash drive was about 10% faster.


 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
USB flash drives Pendrive lifetime sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

I prefer to have same version on flash drive, but some suggest the lighter weight Lubuntu or Xubuntu work better as they are not as large to load.

---

### Post by sudodus on 2015-07-27
Welcome as a USB booter :-)

Oldfred gave you a very good overview of the available options. I can add a link to what I have been doing recently in order to make pendrives, that are truly portable:

[One pendrive for all PC (Intel/AMD) computers - single boot, dual boot, multi boot](http://ubuntuforums.org/showthread.php?t=2259682)

---

