---
title: "Boots from USB but not HDD"
date: 2017-12-18
forum: Installation &amp; Upgrades
---

### Post by mypupdaisy on 2017-12-18
Created a self booting flash drive with Ubuntu 16.04.3 LTS. I have a MSI Laptop with a Nvidia GTX 1060 card. It boots fine to the USB version. I then told it to install to a 200GB partition. I reboot, press F11, boot to Ubuntu. It boots to the login screen. I login, it starts loading and never goes any further. I get no errors. 

Why does it boot and login fine to the USB thumbdrive but not the installed ver?

Thanks

---

### Post by oldfred on 2017-12-18
Probably related to video drivers.

It used to be you needed nomodeset for both Live installer and initial boot of installed Ubuntu or until you install a proprietary driver.

With nVidia, try nomodeset boot parameter.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

The 1060 is a newer card, so you may need newer drivers than in default Ubuntu repository. But do not install from nVidia, but add a ppa to get even the newest drivers reconfigured to work directly with Ubuntu.

      
 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 
   [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition and will show in System Settings also.
ubuntu-drivers devices 

      
 sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX  
        

If you have already installed one nVidia driver, do not attempt another without totally purging older driver version. New driver does not automatically do that and then you get major conflicts which can be difficult to resolve.

---

### Post by mypupdaisy on 2017-12-18
Did this. It stalls at:

NMI watchdog: BUG: soft lockup - CPU#0 stuck for 23s! gpu-manager:844

Repeats this over n over.

---

### Post by mypupdaisy on 2017-12-18
Ok, got it to boot up by adding:

nouveau.modeset=0

How to I add this in permanently? Wheres this file at?

---

### Post by mypupdaisy on 2017-12-18
Ok, found grub and modified. 

BTW - What is a “ppa”?

---

### Post by yancek on 2017-12-18
> BTW - What is a “ppa”? 		

Personal Package Archive which is software developed by third parties and not part of the official Ubuntu OS or in the repositories/servers for Ubuntu.

---

### Post by oldfred on 2017-12-18
A PPA is a way to add a repo from a trusted, cryptographically signed, location, to your ubuntu system. It is why we avoid downloading .deb files, avoid using install.sh and avoid tar.gz files to install software. With a trusted, updated PPA, managing software isn't any different than managing software from the offical repos. The only time it is complex is adding the PPA and when you do a release upgrade. The release upgrade process will remove unofficial PPAs (comment them out). 

You do not want the boot parameter if you install the nVidia driver.
Ubuntu has in its repository current nVidia drivers when ISO created, but nVidia released newer drivers regularly, so then you can use the ppa to add drivers. See link above on explanations of video drivers ppa.

---

### Post by mypupdaisy on 2017-12-19
FYI - It's booting great. Thank you for the help!

---

