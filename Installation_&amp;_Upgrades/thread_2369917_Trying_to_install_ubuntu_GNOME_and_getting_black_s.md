---
title: "Trying to install ubuntu GNOME and getting black screen with broken text"
date: 2017-08-28
forum: Installation &amp; Upgrades
---

### Post by gauss4563 on 2017-08-28
Hi,

I am trying to install Ubuntu GNOME 16.04.3 in a dual boot mode, using a flash drive, but when I try to install\verify files that's the screen I get:
[ATTACH=CONFIG]276531[/ATTACH]

I tried burning the installation ISO with both Etcher and Rufus on the same flash drive and I get the same screen. Now my flash drive isn't recognized by Windows 10. I think I killed it...
What can I do? Is it a problem with the flash drive? Anything else? Need to configure something else in the BIOS\UEFI?
I will install Ubuntu on M.2 Samsung 960 EVO, if that matters, but I didn't even get to the point of choosing a drive in the installation.

Thanks in advance!

**EDIT**
So I tried it with another flash drive and got the same thing. And while I get this screen, I think it also does something with the flash drive, because after I reboot into Windows 10 and go into disk management, most of the volume of the drive becomes "unallocated" for some reason

---

### Post by oldfred on 2017-08-28
What are rest of specs of system?
Brand/model/video card/chip? Or motherboard brand?

Often a video issue with nVdia or AMD cards/chips. And then you need nomodeset for installer & initial boot of install or until you install proprietary driver.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

Windows will not see Linux partitions, and depending on how you created flash drive may not see it. If you used dd or one of the installers that uses the hybrid DVD/flash configuration then flash drive is not a standard partitioned drive.

Is Windows UEFI? You need to make sure UEFI fast boot is off, better to have UEFI Secure boot off, and Windows fast start up off. And only use Windows to shrink the NTFS partition and reboot so it can run chkdsk which is required after any resize of NTFS partitions.

More details in link in my signature below.

---

### Post by gauss4563 on 2017-08-28
System info:
CPU: i5 6500
RAM: 16GB DDR4
GPU: GTX970 (ITX)
MB: Gigabyte ga-z170x-gaming 3

UEFI fast boot is off, UEFI Secure boot off, and Windows fast start up off. I plan to install Ubuntu on a new drive - Samsung 960 EVO 250GB. (still unallocated, if that matters)
I tried also installing clean Ubuntu 16.04.3 and got the same screen. Have yet to try what you suggested, but will do so now. Thanks!

---

### Post by oldfred on 2017-08-28
My second UEFI system is similar but no video card. 
I do not game & Intel video is all I really need.

 oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ)

---

### Post by gauss4563 on 2017-08-28
Will uninstalling the GPU for Ubuntu installation do any good?
Will I be able to reinstall the GPU after I installed the OS and then install all the necessary drivers?

---

### Post by oldfred on 2017-08-28
One or two users who found nomodeset or whatever did not work, did unplug nVidia and install using the default Intel video. But I think they installed the nVidia driver before switching back to the nVidia card. Very new nVidia cards also need the ppa as default in Ubuntu repository is not quite as new.

Many new UEFI systems have a setting to allow you to turn off video card, so you do not have to totally uninstall it, just switch connections & setting.

Any nVidia driver install will require a total purge before you install a different one. New install does not overwrite all of old install and then creates conflicts.

       Updated driver search by nVidia model, do not download, just check correct driver version
[URL="http://www.geforce.com/drivers"]http://www.geforce.com/drivers

[/URL]
 We typically do not suggest running the .run files from nVidia.
As then you have to rerun the dkms on every kernel update.
Where versions of nVidia installed from repository just work.
And if you have a very new nVidia card, and need a driver newer than in default repository, there is a ppa with all the new versions pre-configured. 

      
 # Shows standard repository versions, which is the same as gui 
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 

    [URL="http://www.geforce.com/drivers"]
[/URL]        
 [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 


 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by gauss4563 on 2017-08-29
So I removed the GPU and installed Ubuntu 16.04 and didn't install the drivers (tried to install manually from the nvidia site, but at the end it said something about the characters and corrupt file so I cancelled) and the OS won't load with the GPU installed. Will it download the appropriate drivers automatically ([COLOR=#000000]sudo apt-add-repository ppa:graphics-drivers/ppa) if the GPU isn't installed?

Thanks![/COLOR]

---

### Post by oldfred on 2017-08-29
You do not want to install the .run file from nVidia. If it partially installed I do not know if then you will have issues as different nVidia drivers conflict.

You have to manually install drivers, they will not install automatically. The open source drivers will automatically work, but for very new cards are not optimum. You should be able to boot with nomodeset boot parameter added at grub menu. If only Ubuntu installed, you will not get grub menu unless you press Escape right after UEFI (UEFI fast boot must be off or you do not have time to press any keys). Or you may be able to boot to command line using recovery mode, second boot option.

 sudo apt-add-repository ppa:graphics-drivers/ppa 

 sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by gauss4563 on 2017-08-29
> [COLOR=#000000]You should be able to boot with nomodeset boot parameter added at grub menu.[/COLOR]

What does it mean? I don't really understand how to do that

---

### Post by oldfred on 2017-08-29
See post #2 on nomodeset.

---

### Post by gauss4563 on 2017-08-30
At the end I just unplugged the GPU again and purged and installed the drivers through the terminal, as you instructed and it worked. Thank you very much!

---

### Post by oldfred on 2017-08-30
Glad you got it working. :)

You can change to [Solved].

---

