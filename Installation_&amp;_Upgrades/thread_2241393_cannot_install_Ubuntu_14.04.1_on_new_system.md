---
title: "cannot install Ubuntu 14.04.1 on new system"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by geomcd1949 on 2014-08-25
The simplicity of Ubuntu installation seems to have disappeared! 

Just built a new computer. Motherboard is ASRock x79 extreme6.

When I try to install Ubuntu 14.04.1, I get through a few screens, then am stuck with a blinking cursor, after which, nothing happens.

This is the first attempt to install ANY OS on the motherboard and brand new SSD.

Advice greatly appreciated.

~George

---

### Post by Ksiencha on 2014-08-26
What source do you use for installing Ubuntu - DVD version, LiveCD, USB stick? Maybe you didn't write the image file right? After downloading .iso did you check md5 sums? 
Anyway check out [**how to md5sum**]("https://help.ubuntu.com/community/HowToMD5SUM"), and here is the [**list of md5sums**]("http://releases.ubuntu.com/trusty/MD5SUMS").

---

### Post by ibjsb4 on 2014-08-26
If all else fails, try the mini iso.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by fantab on 2014-08-26
> When I try to install Ubuntu 14.04.1, I get through a few screens, then  am stuck with a blinking cursor, after which, nothing happens.
What screens do you see?

blinking cursor could mean that 
1. it could be a case of bad burn... the .iso didn't write well to the medium.
2. check the boot priority in BIOS/UEFI menu and set it to boot your install medium first.

---

### Post by geomcd1949 on 2014-08-26
Maddening!

14.04.1 disk passes checksum. Also tried using a 12.04 disk that was used in previous successful installs. Same problem

Tried the mini.iso. That (4 times) always hangs up when it gets to the 'checking disks and hardware' point. 

With the 14.04 disk, after the language screen, I hit F6 and selected 'nomodeset.' Still the same problem.

My sense, after much Googling the problem, is that it is the UEFI thing interefering with installing any OS other than Windows. I see that many others are having similar problems with UEFI boards. I wonder if there is a step-by-step set of instructions that can be understood by an average user that tells how to install Ubuntu?

Thanks.

~George

---

### Post by priyesh2 on 2014-08-26
@geomcd1949

try : [http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

---

### Post by Ksiencha on 2014-08-26
Oh my, yes it is a problem. These two article below might be helpful:
1. [http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)
2. [http://discourse.ubuntu.com/t/installing-ubuntu-desktop-14-04-lts-on-a-contemporary-uefi-acer-notebook-with-windows-8-1-dual-boot/1690](http://discourse.ubuntu.com/t/installing-ubuntu-desktop-14-04-lts-on-a-contemporary-uefi-acer-notebook-with-windows-8-1-dual-boot/1690)

---

### Post by geomcd1949 on 2014-08-26
Just to be clear - this is a fresh install on a brand new motherboard and SSD. No Windows OS has been used on either, and it won't be a dual boot. Just Ubuntu 14.04.1 LTS  -- if I can get it to install.

Thanks for the advice so far.

~George

---

### Post by Dennis N on 2014-08-26
>  I wonder if there is a step-by-step set of instructions that can be understood by an average user that tells how to install Ubuntu?

I did an Xubuntu install last week to a UEFI system, and (mostly) followed these steps given by SuperFreak in the link below - differences noted below. This is starting with an empty disk - no Windows present.

[http://ubuntuforums.org/showthread.php?t=1958383&p=11906060#post11906060](http://ubuntuforums.org/showthread.php?t=1958383&p=11906060#post11906060)

Differences: I didn't make the 1 mB partition in 6c) since it is not required if you plan to use UEFI. Also, since that partition was not used, there was no "bios_grub" flag to set in 6f. And I didn't bother with a separate home partition.

Ubuntu works with Secure Boot enabled so you don't disable that.

My install was also to a newly built system.

---

### Post by Ksiencha on 2014-08-26
Sorry for the wrong references. Try to read [**this article**](http://nithinaneeshsct06bt.blogspot.com/2014/02/UEFI.html).

---

### Post by rickm1945 on 2014-08-26
I have a new Asus i7 16GB DDR3 Ram and a 1TB HDD. I currently have Ubuntu 14.04 LTS on a 160 GB usb HDD and it's running flawlessly, but I'm thinking of putting it on the Winodws 8.1 Asus as the only OS. This is a UEFI system. I had to make changes to boot order and disable fast start, enabled Legacy, and enabled CSM. If I install Ubuntu 14.04 on the Windows C: Drive and wipe Windows should I change the UEFI back to the way it was before I made changes?  I have a recovery disk for Windows 8.1 made just in case, as my Asus is still under warranty.

---

### Post by fantab on 2014-08-26
When you change HDD with installed OS from one machine to another, there will be boot problems.
For one, the HDD's UUID changes and you will have to manually change the UUID in fstab.
Secondly, you will have to re-install grub for the above reason.
Thirdly, if there a major difference in the hardware of the two machines, especially Graphics, then too the OS may not work optimally.
If its the graphics card then you will have to use 'nomodeset' kernel option and install and setup the correct driver for your graphics...

UEFI is the replacement for the BIOS. Installing any OS in UEFI is a good idea.

---

