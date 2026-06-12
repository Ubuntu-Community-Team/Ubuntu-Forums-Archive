---
title: "Multibootusb: Getting boot error"
date: 2013-09-29
forum: Installation &amp; Upgrades
---

### Post by amitst on 2013-09-29
I am trying to boot 12.0 Ubuntu using my 8GB usb stick. I installed MultiBootUsb software and installed 12.04 ISO on it. When I rebooted my desktop by setting usb boot option in my bios, I got "boot error" string on my screen.

What might be wrong? My current Ubuntu version:

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

Can you please let me know if I am missing anything?

---

### Post by TheFu on 2013-09-29
I've never been successful using Linux-based multi-boot creators.  This really sucks, since I use Linux for 99% of what I do, but have to use Windows to create multi-boot Flash drives?

Some flash drives will not work with some systems to boot too. Even from the same flash maker, there are differences and weirdness happens.

Anyway, if you have WinXP or later, [Yumi]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") is the tool that has **never** let me down.  This is from our friends at pendrivelinux.

Update: at the bottom of that page, it says > YUMI on Linux: YUMI should function via WINE from within a running Linux environment. However, the format drive option will not work.
There is hope!

---

### Post by C.S.Cameron on 2013-09-29
I have had good results using MultiBootUSB, (by Kumar and Sundar).
Computer USB boots vary, in my computer BIOS, I need to set the USB as my first hard drive.
MultiBootUSB must be set up on a computer running grub2.

---

### Post by sudodus on 2013-09-29
> **amitst said:**
> I am trying to boot 12.0 Ubuntu using my 8GB usb stick. I installed MultiBootUsb software and installed 12.04 ISO on it. When I rebooted my desktop by setting usb boot option in my bios, I got "boot error" string on my screen.

What might be wrong? My current Ubuntu version:

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

Can you please let me know if I am missing anything?

Please describe your computer: brand name, model, cpu, ram (size), graphics driver, and if you have standard bios or uefi. It will make it easier to help.

And are you trying to install the 32-bit or 64-bit Ubuntu (i386 or amd64)?

---

### Post by amitst on 2013-09-29
> **sudodus said:**
> Please describe your computer: brand name, model, cpu, ram (size), graphics driver, and if you have standard bios or uefi. It will make it easier to help.

And are you trying to install the 32-bit or 64-bit Ubuntu (i386 or amd64)?

Processor: Intel® Core™2 Duo CPU E4600 @ 2.40GHz × 2 
Graphics card: Intel® 945G x86/MMX/SSE2
32-bit current OS and trying to install 32-bit only.

How to find out the type of BIOS?

Please let me know the commands if you still want to find out certain information.

---

### Post by amitst on 2013-09-29
> I've never been successful using Linux-based multi-boot creators. This really sucks, since I use Linux for 99% of what I do, but have to use Windows to create multi-boot Flash drives?

Some flash drives will not work with some systems to boot too. Even from the same flash maker, there are differences and weirdness happens.

Anyway, if you have WinXP or later, Yumi is the tool that has **never** let me down. This is from our friends at pendrivelinux.

Thanks, your tip worked and I could boot using USB. Though I had to use my office laptop with Win7 to format the USB and run YUMI on it.

I am interested in All-Linux solution to the issue, as my home desktop only contains Ubuntu. I would like to add further distros on USB through Linux and not Win7.

Secondly YUMI didn't work well through Wine. It didn't show me the USB drive letter to copy the distro to.

---

### Post by TheFu on 2013-09-29
a) I'm glad we found a work-around. Yumi just works.
b) I'm with you in wanting a Linux-only solution.  I've tried 4 different methods and NONE of them worked on 3 different machines with 4 very different USB flash drives.  
c) yumi under WINE will not show "drive letters", since Linux doesn't use those.  Some programs work very well with WINE, but others require ... er ... coaxing.  I was one of the first people to get Quicken 2006 and later working under WINE, so I'm pretty familiar.  For my uses, WINE is a 20% solution - it works with 20% of the programs I'd like.

Yumi can be used to add at least 10 (perhaps many, many, many more) distros to a single Flash drive.  I've had over 15 on mine during InstallFests ... that includes gparted, clonezilla, SystemRecovery/Rescue and Boot-Repair versions, but also Ubuntu x32/x64 desktop/server LXDE, debian, CentOS, Fedora, SUSE, TinyCore, DSL, Puppy, and a few others.  It sorta just works, though I wish it let me queue up all the distros to be added, then did the copies all at once instead of 1-at-a-time.  Yumi has **never** not worked for me and I've never seen it fail at an installFest .... I'll take that back - it did fail trying to install a corporate Win7x64 ISO last week. Had to use the Microsoft tool for that. Meh.

I'd also point out that I tried to use MultiBootUSB last week - it seemed to work, but never would boot. I was using the same hardware that worked with Yumi (a dual boot Asus Eee).

---

### Post by sudodus on 2013-09-29
> **amitst said:**
> Processor: Intel® Core™2 Duo CPU E4600 @ 2.40GHz × 2 
Graphics card: Intel® 945G x86/MMX/SSE2
32-bit current OS and trying to install 32-bit only.

How to find out the type of BIOS?

Please let me know the commands if you still want to find out certain information.

It should be straightforward to install 32-bit linux system on that hardware, which you have also done while I was away from the keyboard :-)

It can be nice with multiboot pendrives, but not that simple to get it working, as pointed out by *TheFu*. An alternative is to keep the iso files and have a fast USB 3 pendrive, and flash the iso you want to use one at a time. It does not seem as fancy, but it has a higher success rate.

A problem with a multiboot pendrive is also that the iso files get old and need to be replaced, and the tweaks to boot from it might change from one version to the next one, so you need another version of YUMI or Multisystem.

Have a look at the following links for more details about making USB boot drives and booting from them.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by oldfred on 2013-09-29
I just install grub2 to all my flash drives and create my own grub.cfg. Then I can boot any ISO I copy to flash drive. 
Once you have grub2 installed to MBR, then it is just like the hard drive methods here but drive will always be hd0,1 (if first partition).  I sometimes boot from second or third partition on a flash drive. But boot drive is always hd0 and drive order can change when booting from one drive and you have several.

       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)


Examples below are where flash drive is labeled PrecideInstaller, grub2, or MC4GB. Just use your label for how flash drive is mounted.
 Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

      
 MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info, note that path for 12.10 and later to flash drive includes your $USER name
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Label partition if grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
[https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)

I have had this work for MBR(msdos) and gpt partitioned flash drives formatted FAT32, NTFS and ext4(with journal turned off).

---

### Post by amitst on 2013-09-30
Thanks oldfred.

At first I found the information provided by you overwhelming. However, I simply tried out the following commands and it worked, :)
> sudo grub-install --root-directory=/media/amit/MULTIBOOTUSB /dev/sdb
> Created isos dir in /media/amit/MULTIBOOTUSB/boot/isos and copied couple of isos (Ubuntu 11.04 and Ubuntu 12.04 LTS)
> Created grub.cfg and added two menu entries (Ubuntu 11.04 and Ubuntu 12.04 LTS) as mentioned at [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

I was able to boot into both ISOs.

Now I intend to put lighter Ubuntu flavor on an older desktop hardware at my relative's place (I guess it has older USB1 slot). I am thinking of putting Xubuntu. I have heard Lubuntu is lighter as well. Any suggestions about specific flavor?

I also want to get 12.04 LTS version there are they don't know much about computers and will not upgrade OS unless I go there and upgrade them.

I hope the menu entries for Xubuntu/Lubuntu/Fluxbuntu in grub.cfg are similar to what I have put for Ubuntu.

---

### Post by LukeMorrison on 2013-09-30
As an alternative, I have found that multisystem works extremely well.  Dragging and dropping of .iso files may not work, depending on the DE, but you can always select them from a file dialog menu.

[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/#more-5069](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/#more-5069)
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

### Post by oldfred on 2013-09-30
They like to change things just to keep us on our toes. Newest versions now use vmlinuz.efi not vmlinuz even if not UEFI.
Sometimes I just have to open ISO and look at what they use, often have to see parameters in isolinux/txt.cfg or other files.
Most Ubuntu desktops work with similar boot stanzas, but I never have gotten server or Alternative to boot with loopmount. 
I have added gparted, parted magic and others, but some just do not work.

---

