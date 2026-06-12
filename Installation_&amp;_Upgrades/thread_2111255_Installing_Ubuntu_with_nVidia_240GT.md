---
title: "Installing Ubuntu with nVidia 240GT"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by Musent on 2013-02-01
I have tried and tried to install Ubuntu 12.10 on this video card and get the dreaded nouveau driver issues. I then installed 10.4 and then tried to upgrade to 12.10 after getting the updated nVidia drivers from xorg, but only get a black screen now. 

Is there anything else I can do?

---

### Post by oldfred on 2013-02-01
I have an older nVidia 9600GT and have to use nomodeset on install and on first boot by editing grub menu with e and add nomodeset in place of splash quiet.

But with 12.10 I also had to add headers to get the Ubuntu version of nVidia driver to install correctly.

       [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 
sudo apt-get purge nvidia*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

    
More details on nomodeset:
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Musent on 2013-02-01
Thanks for the reply oldfred.

Would I do this on a new install for 12.10 or an upgrade from 10.4? Sorry, I'm new to Ubuntu and Linux.

EDIT: I'm using a USB boot drive for installation. Not sure if this is important or not.

---

### Post by oldfred on 2013-02-01
That is for a new install of 12.10. 

I do not remember 10.04, but somewhere they added video to the kernel and since then with every version I have had to use nomodeset. Older versions did not need the addition of the headers as they seemed to automatically be installed, only 12.10.

---

### Post by Musent on 2013-02-01
Just so I'm straight on this, when installing from the USB stick, I get to the advanced menu to set the nomodeset by pressing any key when I see the keyboard + guy...right?

---

### Post by oldfred on 2013-02-01
That is how it usually works. 

Although UEFI installs are different as you get a menu more like the grub menu when you boot. I think with those you edit more like when booting the first time.

I have not actually used the flash drive installer in ages as I boot installer from another hard drive with grub2's loop mount to boot ISO directly.

---

### Post by Musent on 2013-02-01
Update: I got it to install by pressing F6 and changing to nomodeset. Not sure where to go from there. When I boot into Ubuntu now, I get the nouveau error. How do I "editing grub menu with e and add nomodeset in place of splash quiet" like you say?

Thanks for the all the help.

---

### Post by oldfred on 2013-02-01
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

    
Has screen shots:
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Musent on 2013-02-01
Ok, getting there...

I did what you said and installed the latest nvidia driver from Xorg in Ubunut. Now, I can log into Ubuntu but all I see is my mouse pointer and background. Any ideas?

---

### Post by oldfred on 2013-02-01
Does not sound like you have nVidia installed or installed correctly.

Try right click and it opens a edit screen, open system setting and try to install nVidia drive from there. 

Or alt f2 and see if you get a terminal to run the install commands.

---

### Post by bogan on 2013-02-01
Hi!, **oldfred**,

A bit off topic, but just to let you know I have Posted an update to my Nvidia driver 'How To', with some corrections, and new instructions for removing old drivers.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)  Post#1126

Chao!, **bogan**.

---

### Post by Musent on 2013-02-03
Finally got it working. Thanks for all the help oldfred.

---

