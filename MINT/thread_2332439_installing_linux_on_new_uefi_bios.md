---
title: "installing linux on new uefi bios"
date: 2016-07-31
forum: MINT
---

### Post by LiefhebberLinux on 2016-07-31
[FONT=arial]Hi,

I am trying to install linux mint on a new laptop (self-constructed laptop from BTO;[www.bto.eu]("http://www.bto.eu/")) that came with windows 10 installed. I want to set up a dual boot as I still need windows from time to time. I have done this multiple times on several laptops without any difficulties. However, this time I can't even get the set-up USB to load it on the laptop. I get to the grub menu and select Linux Mint [tried compatibility mode as well] and it goes black after that instead of loading the system. It is unclear to me what the problem is. May be the hardware is not recognized [seems a bit unlikely to me] or I am having trouble getting the right setting in the BIOS with the new UEFI stuff [not too familiar with this]. I have attached some screen shots of my "BIOS" where I switch off secure boot and select the USB to start.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Any suggestions are more than welcome.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Cheers

[ATTACH=CONFIG]270486[/ATTACH][ATTACH=CONFIG]270487[/ATTACH][/FONT]

---

### Post by oldfred on 2016-07-31
Moved to Mint subforum.

Is the UEFI boot entry that says HP a HP flash drive?

Black screen is usually video driver related, but many laptops need other or additional boot parameters.
With UEFI boot you get grub menu and have to manually add boot entries on Linux line.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

What video card/chip do you have?

---

### Post by LiefhebberLinux on 2016-08-01
Yes, the hp flash drive is the uefi boot.

I have a [COLOR=#000000][FONT=Lato]NVIDIA GeForce GTX 970M 6GB  graphics card.

Thanks for those other tips. I'll check those out.[/FONT][/COLOR]

---

### Post by oldfred on 2016-08-01
Some have to use recovery mode (second line in grub) to boot to command line and install nVidia drivers from that. The drivers in the repository should be new enought for your chip, but you can also add a ppa to get the very newest driver. Do not install from nVidia.

       # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended  

If you installed any nVidia driver, you must purge before installing another or major conflicts.

 sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall 


 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) 

      
 # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices

---

