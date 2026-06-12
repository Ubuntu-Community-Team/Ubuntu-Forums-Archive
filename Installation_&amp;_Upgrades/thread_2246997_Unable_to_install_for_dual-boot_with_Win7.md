---
title: "Unable to install for dual-boot with Win7"
date: 2014-10-04
forum: Installation &amp; Upgrades
---

### Post by jcrewjr11 on 2014-10-04
I just built a new desktop and am unable to install any distro, I have tried four so far. I have to have Windows for school, so I must dual-boot. Windows installed just fine, but now when I try install Ubuntu as I get to the option screen of trying or installing and the computer just reboots. I am essentially in a boot loop if I don't exit into the BIOS. I have been dual booting for years and this is the first I've had this issue. I am sure it is some small thing I forgeting. I have tried my boot order to usb first then SSD, and SSD first and then selecting usb from boot menu, same results each time. Win7 is on its own SSD and I would like this to be on its own as well.

---

### Post by Dennis N on 2014-10-05
Just a couple of thoughts:

Apparently the USB is booting, since you reach the options screen. Try using the "try before installing" option if you haven't yet, and when you reach the actual Ubuntu desktop use the Install icon on the Desktop. 

Is Windows installed in UEFI mode? If so, be sure to boot up the Linux installer in UEFI mode so it gets installed in the same mode as Windows.

---

### Post by oldfred on 2014-10-05
I also just built new desktop with an Asus motherboard. And had to change several UEFI/BIOS settings to get it to boot Ubuntu in UEFI mode. And strangely I had to go into the CSM mode to find the settings to turn on UEFI mode?? The only default was Windows which was secure boot UEFI only.

Post this to see how Windows is installed:
sudo parted -l

If in BIOS this will work, but if UEFI it just says drive is gpt as fdisk does not work on gpt partitioned drives.
sudo fdisk -lu

---

### Post by jcrewjr11 on 2014-10-05
Using the try option returns the same result. In my BIOS the only disk listed in UEFI boot list i the usb, which is also an option in the boot menu. My mobo is MSI so I am using ClickBIOS 4. Where can i use the sudo commands to see how windows is installed?

---

### Post by oldfred on 2014-10-05
What graphics card/chip? You may need nomodeset.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Are you booting by default in UEFI mode or in BIOS mode. This shows both screens, UEFI gives a grub menu like an install but with options to try or install, and BIOS screen is a purple screen.
You should have settings in UEFI/BIOS boot  that allow you to turn on/off secure boot, UEFI, CSM/Legacy/BIOS and other settings. Sometimes you need to change several just to get it to work.

Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

---

### Post by jcrewjr11 on 2014-10-05
I am running a AMD A8 5600 APU with no graphics card. I have had graphics issues with past systems and had to use nomodeset, but this seems totally different. Could it have something to with the fact that I am using a SSD? Here are some BIOS screenshots. 1. Overall boot order. 2. HDD boot order. 3. UEFI Boot order with only the USB listed.
[[IMG]http://s13.postimg.org/wtvoolw2b/MSI_Snap_Shot.jpg[/IMG]]("http://postimg.org/image/wtvoolw2b/")
[[IMG]http://s13.postimg.org/8sosn5h8z/MSI_Snap_Shot_00.jpg[/IMG]]("http://postimg.org/image/8sosn5h8z/")
[[IMG]http://s13.postimg.org/k3rgbio43/MSI_Snap_Shot_02.jpg[/IMG]]("http://postimg.org/image/k3rgbio43/")

---

### Post by oldfred on 2014-10-05
I do not know AMD graphics.

SSD should not make any difference. But you have to fully boot the live installer to be able to run any commands.

Did you install Windows in UEFI or BIOS boot mode. I think default is BIOS, but you can convert to UEFI.
       Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

    
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

But if you cannot boot live installer, it still may be graphics issues or other boot parameters are needed.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by jcrewjr11 on 2014-10-05
Apparently it is a known bug. I just found this. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1309578](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1309578) 
 I'll have to read through more in depth to figure out what to do. I'll update when/if I find a solution.

---

### Post by jcrewjr11 on 2014-10-06
So it has to do with the 3.13 kernel and supposedly the problem is fixed with 3.16 kernel. I am unsure how to update kernel so that I can install. Is there a way to do this from live USB before install?

---

### Post by oldfred on 2014-10-06
Post #98 said he still had issue with 3.16.
Post #100 says if you move mouse the entire time it will instal?

While not normally suggesting installing a pre-release version as a working system, have you tried 14.10?

---

### Post by jcrewjr11 on 2014-10-06
I was able to install 14.10 but upon boot I am getting kernel panic no working init found.

---

### Post by oldfred on 2014-10-06
Someone posted this on an upgrade, but since you have a new install, you do not have an older kernel to boot.

 "If the “apt-get upgrade” does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs –u -k command. Then run sudo dpkg –reconfigure. That should clear the upgrade flags and fix any broken packages."

Did install give any error messages?

You may have to chroot into system and try to repair or reinstall.

---

### Post by jcrewjr11 on 2014-10-06
Installation seemed to go just fine, no errors, although when it was finished it seemed to stall prior to reboot, just a minute or so.

---

