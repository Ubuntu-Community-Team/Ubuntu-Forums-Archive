---
title: "How to boot multiple ISO's into USB Drive"
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by Traxster on 2013-08-25
Hello to all,


     I am looking for a solution that will allow me to be able to create a USB drive with multiple ISO boot images, and choose anyone I want, say from a GRUB Menu or any menu that can handle the task. I've been to penndrivelinux and also messed with unetbootin, but they don't seem to accomplish exactly what I want.  How would I customize a solution like this? Any help would be greatly appreciated.


Traxster

---

### Post by oldfred on 2013-08-25
I thought pendrive had a version and there are several scripts that automate the process. But I prefer to do it myself but I started before scripts became available.
You just need to partition flash drive and label so auto mount is by label, install grub to flash drive, manually create boot stanza(copy examples & edit slightly for your path) and add as many ISO as flash drive will hold.

It really is the same as the hard drive version except for the install of grub to the flash drive.
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)
    
       MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info, note that path for 12.10 and later to flash drive includes your $USER name
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Label partition if grub2 & mount - older version where user not in default mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
This was me (fred) and flash drive was MC4GB when mounted as sdb from newer version where user is in mount.
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
[https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)
Reported to have a few typos? But shows process on one page
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

    
       These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
[https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Traxster on 2013-08-25
> **oldfred said:**
> I thought pendrive had a version and there are several scripts that automate the process. But I prefer to do it myself but I started before scripts became available.
You just need to partition flash drive and label so auto mount is by label, install grub to flash drive, manually create boot stanza(copy examples & edit slightly for your path) and add as many ISO as flash drive will hold.

It really is the same as the hard drive version except for the install of grub to the flash drive.
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)
    
       MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info, note that path for 12.10 and later to flash drive includes your $USER name
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Label partition if grub2 & mount - older version where user not in default mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
This was me (fred) and flash drive was MC4GB when mounted as sdb from newer version where user is in mount.
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
[https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)
Reported to have a few typos? But shows process on one page
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

    
       These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
[https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Excellent,

Thanks for the resources, I will look them over, and try  to work a solution.


Traxster

---

### Post by Traxster on 2013-08-27
> **oldfred said:**
> 
Reported to have a few typos? But shows process on one page
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

    
       

I attempted to run the commands in the above tutorial and here are the errors I received..

```
root@xxx:~# mkdir /mnt/USB && mount /dev/sdd1 /mnt/USB 
mkdir: cannot create directory &#8216;/mnt/USB&#8217;: File exists
```  

and

[COLOR=#ff0000]"Before proceeding, take note[/COLOR]:
 Old versions of grub used --root-directory=/mnt/USB
 while current versions use --boot-directory=/mnt/USB/boot" <-- This is a warning that appears in the tutorial 

 I am running Ubuntu 13.04 I tried the command both ways, just in case  there was a chance that i might I have an old version of grub, however I still receive the same error. 




```
root@xxx:~# grub-install --force --no-floppy --boot-directory=/mnt/USB/boot /dev/sdd
Path `/mnt/USB/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.


```


I too am getting errors with these commands. Does anyone know how to modify these commands so they work?


traxster

---

### Post by oldfred on 2013-08-27
I think they all rely on the label or assume you substitute  the label of your USB for USB in command.

My first example, I had labelled my flash drive's partition as grub2 or a 'grub2' boot partition.
In my second example I labelled it as MC4GB or my MicroCenter 4GB flash drive.
I try to label all partitions when I create them with gparted or go back and use Disks (or Disk utility) to add labels. If you do not have labels it may use UUIDs or whatever mount point you manually assign.

mount

Shows this now for my flash drive from 12.04.
/dev/sdb1 on /media/MC4GB type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

If I do the same from 13.04 it is /media/fred/MC4GB.

---

### Post by VMC on 2013-08-27
[YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") is my favorite multi ISO booter.

---

### Post by Traxster on 2013-08-27
> **VMC said:**
> [YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") is my favorite multi ISO booter.


Looks good, however, the list does not include all the iso's I want to use, and it requires windows to build. I did look at the article and it does have some good information I can use. 

Thanks for the link

***UPDATE***

I see their is an option to try to use ISO's.

I would still prefer to do it the manual way, but how hard is it going to be to learn how to input the menu entries? Am I going to have to take apart the ISOs to this?

Traxster

---

### Post by VMC on 2013-08-28
Actually, I made a mistake. I use to use YUMI, and was looking for what I replaced it with and thought it was YUMI, but its not.
I couldn't find the exact program, but I found a great replacement if you have Windows. Its called RMPrepUSB. The only reason I'm mentioning it, is it has a great feature. QEMU is built in, so you can test you USB device before you reboot. In the past, sometimes I make mistakes, and it takes several re-tries to get it right. QEMU booted the virtual device right before my eyes.

That aside, what I used it for was to load grub4dos as the boot loader, and menu.list to point to my ISOs. It works exactly as the one I use to have, and building it yourself is easy.

The only thing the program that I can't find had, was the ability to drop your ISOs into a gui and it did the work for you. But there are payoffs. It had some odd menuing system that I managed to remove - Along with its name :)

---

### Post by oldfred on 2013-08-28
Most of the ISO that we usually boot have sample entries in the link on the hard drive boot of ISO. And a few will not boot directly from ISO no matter what.

Some change a lot from one version to the next, and I do open ISO with Archive Manager and check what boot parameters it uses. And sometimes file or paths change and have to be updated. One version of Ubuntu used a .efi even for the BIOS boot version.

Best to start with one known like Ubuntu and make sure path & settings work and build from that. Example from mine below. I have an iso folder in my /boot where grub exists so that is my path. I also have nVidia and have to have nomodeset as a parameter to boot.

```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 13.04" {
set isofile="/boot/iso/ubuntu-13.04-desktop-amd64.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile nomodeset 
initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 12.04.3 Precise ISO 64bit" {
    set isofile="/boot/iso/ubuntu-12.04.3-desktop-i386.iso"
    loopback loop (hd0,1)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}

```

Two corrections added to above. first entry did not have(hd0,1) See posts below.
And 13.04 & later use vmlinuz.efi for the 64 bit to boot in BIOS or UEFI mode.
12.04 still uses vmlinuz
Thanks vmc and Werne for noticing the missing .efi.

---

### Post by monkeybrain20122 on 2013-08-28
This is the easiest
[http://liveusb.info/dotclear/index.php?pages/install](http://liveusb.info/dotclear/index.php?pages/install)

---

### Post by Traxster on 2013-08-29
> **oldfred said:**
> Most of the ISO that we usually boot have sample entries in the link on the hard drive boot of ISO. And a few will not boot directly from ISO no matter what.

Some change a lot from one version to the next, and I do open ISO with Archive Manager and check what boot parameters it uses. And sometimes file or paths change and have to be updated. One version of Ubuntu used a .efi even for the BIOS boot version.

Best to start with one known like Ubuntu and make sure path & settings work and build from that. Example from mine below. I have an iso folder in my /boot where grub exists so that is my path. I also have nVidia and have to have nomodeset as a parameter to boot.

```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 13.04" {
set isofile="/boot/iso/ubuntu-13.04-desktop-amd64.iso"
loopback loop $isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset 
initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 12.04.3 Precise ISO 64bit" {
    set isofile="/boot/iso/ubuntu-12.04.3-desktop-i386.iso"
    insmod part_gpt
    loopback loop (hd0,1)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}

```

Starting from scratch. 


1. Deleted existing partition from USB. 
2. Created a new (type W95 FAT32 (LBA) (Bootable) partition using disks utility.
3. installed grub using ```
grub-install --boot-directory=/media/$USER/MULTIBOOT1/boot /dev/sdc
```

4. mkdir /boot/iso
5. cd /media/$USER/MULTIBOOT1/boot/grub 
6. gedit grub.cfg and pasted code below.
```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 13.04" {
set isofile="/boot/iso/ubuntu-13.04-desktop-amd64.iso"
loopback loop $isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset 
initrd (loop)/casper/initrd.lz
}
```
 
7. copied ubuntu-13.04-desktop-amd64.iso to /boot/iso

8. Set BIOS to boot from USB HDD


When I reboot I am getting a grub menu with a list. 

Ubuntu 13.04

<enter>

error: file 'casper/vmlinuz not found.
error: you need to load the_kernel first.

Press any key to continue...

<enter>

dumps me back to grub menu. 


Thanks



Traxster

---

### Post by oldfred on 2013-08-29
I do not think my first entry was correct. Missing drive & partition.
Change to this.
loopback loop (hd0,1)$isofile 

If you only have one partition. The drive you boot from is hd0 and the only time that is different is if you boot your hard drive and a different drive is where the files are.
And the partition should be 1 if it is the first (or only) partition on drive.

---

### Post by Traxster on 2013-08-30
> **oldfred said:**
> I do not think my first entry was correct. Missing drive & partition.
Change to this.
loopback loop (hd0,1)$isofile 

If you only have one partition. The drive you boot from is hd0 and the only time that is different is if you boot your hard drive and a different drive is where the files are.
And the partition should be 1 if it is the first (or only) partition on drive.

ok, here is what the grub.cfg file looks like now

```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 13.04" {
set isofile="/boot/iso/ubuntu-13.04-desktop-amd64.iso"
[COLOR=#ff0000]loopback loop (hd0,1)$isofile[/COLOR]
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset 
initrd (loop)/casper/initrd.lz
}


```

Still getting the same errors..

thanks again,

traxster

---

### Post by VMC on 2013-08-30
I think the problem is your missing "efi"
```
l[COLOR=#000000][FONT=Ubuntu Mono]inux (loop)/casper/vmlinuz.**efi** boot=casper iso-scan/filename=$isofile nomodeset[/FONT][/COLOR]
```

edit: also you may need to assign root:
```
set root='(hd0,1)'
```

---

### Post by Werne on 2013-08-30
> **Traxster said:**
> ```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 13.04" {
set isofile="/boot/iso/ubuntu-13.04-desktop-amd64.iso"
loopback loop $isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset 
initrd (loop)/casper/initrd.lz
}
```

That one won't work, 13.04 uses vmlinuz.efi so the linux line needs to be
```
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile nomodeset
```

I have 13.04 AMD64 on a multi-boot USB, but I use the following entry to boot into a live session directly instead of going through the prompt:
```
menuentry "Ubuntu 13.04 AMD64" {
 loopback loop /img/ubuntu-13.04-desktop-amd64.iso
 linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=/img/ubuntu-13.04-desktop-amd64.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}
```
The entry is based on [this how-to]("http://ubuntuforums.org/showthread.php?t=2119881"), I experimented with GRUB2 and multiboot before but I never got the entry right.

Also, for different distros you can mount the iso, check for vmlinuz/initrd paths there and modify the entry accordingly.

---

### Post by Traxster on 2013-08-30
> **Werne said:**
> That one won't work, 13.04 uses vmlinuz.efi so the linux line needs to be
```
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile nomodeset
```



that was it. the grub.cfg file looks like this now. 

```
set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

menuentry "Ubuntu 13.04" {
set isofile="/boot/iso/ubuntu-13.04-desktop-amd64.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile nomodeset
initrd (loop)/casper/initrd.lz
}
```

  
My next question would be, where do I go to learn more about customizing these menu entries for other ISOs? As mentioned by another poster, I know, I will probably have to use archive manager to take apart the ISO, I'm not sure of what to look for though...



Thanks to everyone for your help



Traxster

---

### Post by Werne on 2013-08-30
> **Traxster said:**
> My next question would be, where do I go to learn more about customizing these menu entries for other ISOs? As mentioned by another poster, I know, I will probably have to use archive manager to take apart the ISO, I'm not sure of what to look for though...
Well, I just duplicate an existing one, change the menuentry name and point it to the right iso, initrd and vmlinuz. As for taking it apart, you can mount it instead of using archive manager with this command:
```
sudo mount -o loop /path/to/iso /path/to/mountpoint
```
You'd have to look where vmlinuz and initrd are located on the iso, for Ubuntu that's usually /casper/vmlinuz (or /casper/vmlinuz.efi for 13.04 and beyond) and /casper/initrd.lz. For Debian 7.0.0 Live the location is /live/vmlinuz and /live/initrd.img. For Arch it's /arch/boot/i686/vmlinuz and /arch/boot/i686/archiso.img for 32-bit, and for 64-bit it's /arch/boot/x86_64/vmlinuz and /arch/boot/x86_64/archiso.img (that's on archlinux-2013.08.01-dual.iso and 2013.07.01 images).

And so on, and so on, you get the picture.;)

---

### Post by VMC on 2013-08-30
Traxster -

It depends on the vendor. pmagic, dsl, acronis, etc, all have some quirks to looping their ISOs. If you find one that doesn't quite work, you can open it up and look at the syslinux menu or go to their web page and see if they have a how to on loop-back.

Another oddity I have come across, was kubuntu saucy ISOs didn't work until I added "*maybe-ubiquity"* on the linux line. The display was borked if I didn't use that option. I only found that by opening up the iso.
I have't looked at it since, so maybe delving deeper into the menu would reveal how to boot just the live itself.

---

### Post by oldfred on 2013-08-30
I will edit my first post just in case someone else looks at thread and does not read further down on correction.

Some examples here again adjust for your paths:
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

Most ISO have text files with the syslinux boot loader and/or grub files. Syslinux seems to have several text files and I always look at the wrong one and each calls another so I usually look at most.
Look in /isolinux/ with Ubuntu but others may not be the same. For example from Ubuntu's isolinux.cfg calls (includes) menu.cfg which includes text.cfg which has the actual menu & append with the boot parameter it uses. It also shows the kernel so you know if it needs the .efi or not.

---

### Post by steve63752 on 2013-09-11
On the RMPrepUSB site there is Easy2Boot.
This is a grub4dos set of files which you just copy to a grub4dos bootable USB drive (which you can make using bootlace under linux or RMPrepUSB under Windows).
Once the bootable USB drive is made, just copy all your linux liveCD ISO files to the \_ISO\MAINMENU folder and then boot the USB drive.
There is also a way to boot from many of the ISOs with persistence too (even from an NTFS formatted USB drive and even if many of the ISOs all use casper-rw as the persistent volume).
There is a YouTube video here [http://www.youtube.com/watch?v=MBKh_jDyTmQ](http://www.youtube.com/watch?v=MBKh_jDyTmQ)

---

