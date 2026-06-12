---
title: "Unable to install anything instead of Win11"
date: 2023-11-14
forum: Installation &amp; Upgrades
---

### Post by yarosan on 2023-11-14
I want to ged rid of Win11, so i tried to install Ubuntu 23.10.1 instead of it. Installation process goes into GRUB, starts to boot, cursor shows up and it reboots. Already turned off secure boot, tpm etc. Didn't help at all.
My specs: Ryzen 5 5500, GTX 1060, Gigabyte B550M DS3H. Tried to install Deepin, Elementary and Ubuntu with same result.

---

### Post by yancek on 2023-11-14
What is the installation process you are using?  After downloading the Ubuntu iso file, did you verify the download was not corrupt (explained on the Ubuntu site)?  Did you write it to a USB?  What method/software did you use to do this?  Do you have another computer to test boot the USB or whatever you are using?  Is the problem you are referring to after what seemed to be a successful install and then attempting to reboot?  Is that where you see Grub?  Do you see a grub prompt (grub>) or grub rescue?  Did the computer have any other operating system on it before you tried to install Ubuntu?  Review the steps at the link below to see if that is what happened when you tried to install.

[https://www.linuxteck.com/how-to-install-ubuntu-22-04-lts-step-by-step/#google_vignette](https://www.linuxteck.com/how-to-install-ubuntu-22-04-lts-step-by-step/#google_vignette)

---

### Post by yarosan on 2023-11-14
Ok, sorry, i already spent half a day on it. Yes, i verified iso file. I tried several distros (deepin, elementary etc), tried Rufus, Etcher, even some app from Deepin, forgot the name. The problem is that i can't even get to the installation process. I boot into USB, GRUB shows up. I press "try or install Ubuntu", it loads a little bit, screen goes blank and it goes back to restart. Now my PC has Windows 11

---

### Post by MAFoElffen on 2023-11-16
That is because of your Nvidia GTX 1060 GPU. At the Grub menu of the Installer LiveCD, use Try with SafeGraphics.

On the reboot after the install, at the Grub2 menu, press the <E> key, then <Arrow-Down> to the line that starts with the word "linux". <Arrow-Right> after the words "quiet splash" and add the word "nomodeset". Then press the keys <Cntrl><X> to boot. 

Once it boots, start "Software & Updates" > Additional Drivers" and install your NVidia drivers.

---

### Post by ActionParsnip on 2023-11-16
Trying Deepin and Elementary are all Ubuntu based. So you didn't really try much different.

Are you wanting to remove Windows fully and have Ubuntu as the only OS on the system or are you wanting a dual boot?

---

