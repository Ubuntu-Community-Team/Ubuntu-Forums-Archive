---
title: "Installing Ubuntu on Toshiba Satellite L50t-A"
date: 2015-09-19
forum: Installation &amp; Upgrades
---

### Post by alessandro-mininno on 2015-09-19
Hello there,
Sorry for my english but I'm italian but I'd like a more international answer to my "problem".
I have a Toshiba Satellite L50t-A with Windows 10 Home Edition installed. 
My PC information are:

CPU Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz
RAM 4096MB
Video NVIDIA GeForce GT 740 / Intel(R) HD Graphics 4000
Sound Realtek High Definition Audio / Audio Intel(R)

Network Qualcomm Atheros AR8161 PCI-E Gigabit Ethernet Controller (NDIS 6.30) / Qualcomm Atheros AR956x Wireless Network Adapter

I didn't find a guide for installing Ubuntu on this computer but I have already disabled the Secure Boot on BIOS. I appreciate some suggestion about how I can install Ubuntu in Dual-Boot, also if someone has the same computer, I'd like if he shares his experience, because I don't want to lose something (for compatibility) during the installation.

Thanks

AM

---

### Post by grahammechanical on 2015-09-19
The best we can offer until someone updates the wiki page based upon their experiences of Windows 10 is this page:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

My advice based on seeing the problems that people have dual booting with Windows and on newer hardware and then seeing the suggestions offered, is to

1) Use Windows utilities to defrag the hard drive. Do it more than once and check that Windows restarts correctly each time.
2) Use Windows utilities to resize Windows partitions to create unallocated space that the Ubuntu installer can use to create Linux partitions for Ubuntu.
3) Take Windows out of hibernation. To speed up the loading of the OS Microsoft has set Windows to hibernate instead of completely shutting down. This prevents the Ubuntu installer from reading the Windows partitions and gaining important information about the partitions.
5) Have Windows repair utilities at hand to make it possible to restore Windows if needed.
6) backup your data
7) Install Ubuntu in EFI mode. Windows 10 if pre-installed would have been installed in EFI mode. So, Ubuntu must be installed in EFI. See the wiki page.
6) There are several posts on this forum about Windows 10. Look for them. Read them. Those posts already record people's experiences in dual booting Windows 10 and Ubuntu as well as upgrading to Windows 10 and what may or may not happen.

[http://ubuntuforums.org/showthread.php?t=2292645](http://ubuntuforums.org/showthread.php?t=2292645)

[http://ubuntuforums.org/showthread.php?t=2280643](http://ubuntuforums.org/showthread.php?t=2280643)

[http://ubuntuforums.org/showthread.php?t=2291463](http://ubuntuforums.org/showthread.php?t=2291463)

[http://ubuntuforums.org/showthread.php?t=2289134](http://ubuntuforums.org/showthread.php?t=2289134)

There are so many threads about Windows 10 that I am starting to think that this forum has become a Microsoft support forum. :)

Regards.

---

### Post by oldfred on 2015-09-21
Toshiba now seems to need a work around to get it to boot to grub menu.

 Toshiba L50-A-1EH laptop - used bcd edit
[http://ubuntuforums.org/showthread.php?t=2295628](http://ubuntuforums.org/showthread.php?t=2295628)
Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)

And nVidia needs the proprietary nVidia driver from repository or a ppa. Do not install from nVidia the .run file.
Does system let you set which video you use, or is it automatic?


 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset, if booting with nVidia. Nomodeset does not work with Intel & other options requried.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1 - see intel options if booting with Intel
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)



 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa.

---

### Post by alessandro-mininno on 2015-09-23
And nVidia needs the proprietary nVidia driver from repository or a ppa. Do not install from nVidia the .run file.
Does system let you set which video you use, or is it automatic?


The system chooses which video I use automaticaly.

---

### Post by alessandro-mininno on 2015-09-23
Thanks for the answers. I'd like to keep the thread open for another day  or two more for some other suggestion from any Toshiba users. I don't  know when I will use these informations because I think it's not simple  for the moment. You have been very clear, I will use every link some  day!

Bye

---

