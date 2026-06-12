---
title: "windows 10 and gnome new install in separate hard drives"
date: 2018-01-08
forum: Installation &amp; Upgrades
---

### Post by deusdementia on 2018-01-08
Hi everyone,

First of all thanks you to everyone that can help me.

Im trying to install gnome ubuntu along with windows 10 in two separate hard drives.

Currently i have four hard drives: 2 ssd working in raid 0, 1 hdd of 2 TB and other with 1 TB. Now i have windows installed on ssd hard drives, the 2 TB hard drive is used to users and programs for windows and i want to use the 1 TB drive to gnome.
So, during install, ubuntu recognizes all the hdd as:

- dev/mapper... -> ssd raid 0
- dev/sdc -> 1TB HDD
- dev/sdd -> 2TB HDD

I formated sdc hdd and create new partitions: /boot (1GB), /swap (20GB for hibernate), / (100 GB) and /home (everything else). Also i choosen boot sector to be installed in sdc.
I rebooted the PC and press F11 to entere on boot menu and i selected ubuntu to start (i will configure boot order when everything works fine), grub does not appear, instead of it gnome's logo shows up, seems to load but suddenly a black terminal appears and said to me tu use journalctl -xb to see what is happening.

I did not understand so much but what i could see was that the system was trying to read dev/mapper devices and it gave a time-out.
I'm going to try to get that report and post here also.

I don't know what i have to do next and if i installed it well.

Thanks you so much.

---

### Post by oldfred on 2018-01-08
Is system UEFI or BIOS?
And then is Windows installed in UEFI or BIOS boot? You Want Ubuntu in same boot mode.

There are some minor advantages of using gpt even if BIOS. Ubuntu can boot from gpt partitioned drive whether using UEFI or BIOS, where Windows only boots from gpt with UEFI.

Best not to have separate /boot nor large swap unless you are using LVM on Ubuntu install itself.
Most just use 2GB for swap. If faster drive or SSD, you can boot just about as fast as hibernation and if dual booting cannot use hibernation on either system.

If other drives were not connected, grub2's os-prober probably did not see Windows, so then you do not get grub menu, it sees one system and just automatically boots that.
If BIOS install, hold shift key from BIOS until grub menu appears.
You can also try recovery mode.

What video card/chip? 
You may need a boot parameter like nomodeset until you install a proprietary driver.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by deusdementia on 2018-01-08
[COLOR=#0000cd]Is system UEFI or BIOS?[/COLOR] UEFI, both windows and ubuntu.

[COLOR=#0000cd]Best not to have separate /boot nor large swap unless you are using LVM on Ubuntu install itself.[/COLOR]
[COLOR=#0000cd]Most just use 2GB for swap. If faster drive or SSD, you can boot just about as fast as hibernation and if dual booting cannot use hibernation on either system.

[/COLOR][COLOR=#000000]OK i will not use separate /boot partition, about large swap i think is necessary to wake up the pc when it is suspended, right? because i have 16GB of RAM i need the same o a little bit more to save all that was in memory on disk.
About SSD i'm not using them for ubuntu only for windows.

[/COLOR]

[COLOR=#0000cd]If other drives were not connected, grub2's os-prober probably did not see Windows, so then you do not get grub menu, it sees one system and just automatically boots that.[/COLOR]
[COLOR=#0000cd]If BIOS install, hold shift key from BIOS until grub menu appears.[/COLOR]
[COLOR=#0000cd]You can also try recovery mode.

[/COLOR][COLOR=#000000]I don't know why but the second time i tried to boot ubuntu grub shows up but windows is not there, there is not an entry to choose windows.
Again i have some kind of error i could see something like unsoported sprom revision 11.

[/COLOR][COLOR=#0000cd]What video card/chip?
[/COLOR][COLOR=#000000]Video card: GTX 1080
CPU: I7-7770K

I will try what you said about nomodeset and try to install propietary drivers.

Thanks you![/COLOR][COLOR=#000000][/COLOR]
[COLOR=#0000cd][/COLOR]

---

### Post by oldfred on 2018-01-08
Do not install proprietary driver direct from nVidia (the .run file). To get newest driver  you can add the ppa.
If you install one driver, but later want another you must totally uninstall & purge all traces of old driver or else you get conflicts.

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
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by deusdementia on 2018-01-11
Thanks you so much for the help, i'm going to apply this tips you gave me.
I will tell with the results.

---

### Post by deusdementia on 2018-01-24
Hi everyone,

I was trying to boot gnome with nomodeset and nouveau.modeset=0 but it gets stuck on a grey screen.

I tried to boot again and take photos of the errors.

[https://postimg.org/image/wsmfpjrpn/](https://postimg.org/image/wsmfpjrpn/)
[https://postimg.org/image/eptcybo57/](https://postimg.org/image/eptcybo57/)
[https://postimg.org/image/im6oub1ez/](https://postimg.org/image/im6oub1ez/)
[https://postimg.org/image/559qbge8r/](https://postimg.org/image/559qbge8r/)

It seems to be something related with the graphic card and the wifi card.

---

### Post by oldfred on 2018-01-24
Does recovery mode (which uses nomodeset) boot to its menu.
And then with Internet on install nVidia driver from Ubuntu repository?

Some have turned off nVidia card in UEFI and used Intel driver to boot. 
Then installed nVidia driver and reset in UEFI to use video card.
       Ubuntu 16.04 LTS installation problem with GA-Z170X-UD5 TH & GTX 1080
Go to the BIOS, Peripherals > "Initial Display Output": set it to IGFX (basically, this tells your computer to use your motherboard to display graphics)
[http://ubuntuforums.org/showthread.php?t=2327648](http://ubuntuforums.org/showthread.php?t=2327648) 
    
Since very new nVidia card, you will need ppa to get newest nVidia driver.
       Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 

 If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by deusdementia on 2018-01-24
I can't install nvidia drivers from ubuntu repositories because the wifi card does not work either...

I tried what you said abouit switching off PCI graphic card from BIOS but i get the same errors, so i imagine that also the integrated intel graphic chipset has problems with those drtivers.

I have to install broadcom drivers to make my wifi card work and the try to install nvidia drivers or maybe try to install nvidia drivers offline.

I don't know how to do any of those solutions. So while i'm witting of an answer i will google it also.

Thanks you

---

### Post by oldfred on 2018-01-24
Can you at least temporarily connect with Ethernet hard wired?
That is the simplest way to download all the extra drivers you need.

What brand/model system?

And Wireless issues are better in a separate thread as some know those issues more. With the title you have here, they may not even look at this thread.
[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)
Be sure to read the sticky threads first before posting.

---

