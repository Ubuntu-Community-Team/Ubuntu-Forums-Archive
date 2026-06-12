---
title: "How to install Ubuntu remix from DOS partition"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by gillani on 2010-09-20
Issue:  I have a really old laptop that doesn't boot from USB, nor does it have a CD drive.  I want to install Ubuntu Netbook Remix on it.

I pulled the harddrive and connected it to my workstation via USB to Harddrive kit.  How can I install Ubuntu on it?

I can create to partitions, one dos and one other.  Can I run a dos installer of Ubuntu?

---

### Post by C.S.Cameron on 2010-09-20
Following is for an 8GB drive:


Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the USB drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

### Post by gillani on 2010-09-20
Won't this install Linux based on my workstation and not my laptop?  Will Linux be smart enough to reconfigure itself after?

---

### Post by snowpine on 2010-09-20
Your computer is not a "netbook"; are you sure Ubuntu Netbook Edition is the right tool for the job?

> If you have a netbook and a supported graphics card, using Ubuntu Netbook Edition  (formerly "Ubuntu Netbook Remix") is an interesting option. It has a nice interface adapted for smaller screens, and a selection of applications aimed at netbook users.

Ubuntu Netbook Remix is designed to run well on netbooks with typically minimal specs, i.e.:

    * Intel Atom processor @ 1.6 GHz
    * 512 MiB of system memory (RAM)
    * 4 GB of disk space
    * Screen of 1024x600 resolution
    * Graphics chipset with support for visual effects 

---

### Post by C.S.Cameron on 2010-09-20
> **gillani said:**
> Won't this install Linux based on my workstation and not my laptop?  Will Linux be smart enough to reconfigure itself after?

You can even install Ubuntu to a pendrive and it will work on any computer until a proprietary driver, (ie Nvidia), is installed.

---

### Post by gillani on 2010-09-20
> **snowpine said:**
> Your computer is not a "netbook"; are you sure Ubuntu Netbook Edition is the right tool for the job?

Sorry for the confusion.  I have a laptop but there is no boot from usb in the bios (really old) and no CD Drive.  Therefore, I wanted to do the following:

1.  Take out the harddrive from laptop (done)
2.  Install in Desktop workstation as a usb device (done as e:)
3.  copy ??? to the e:\ 
4.  Put harddrive back into laptop and run from dos -- an installer to install ubuntu

---

### Post by gillani on 2010-09-20
> **C.S.Cameron said:**
> You can even install Ubuntu to a pendrive and it will work on any computer until a proprietary driver, (ie Nvidia), is installed.

Thanks ... I will give it a try...

---

### Post by cooprocks123e on 2010-09-20
You could also install syslinux on there, copy over memdisk from the syslinux sources and the Plop bootmanager disk image, put the installer on the usb, then run memdisk with the plop image as initrd and boot from the usb.

Or you could run a network install if you have a supported nic.

---

### Post by gillani on 2010-09-21
It didn't work.  When I put the HD back on the laptop and rebooted, I get a blank screen with a cursor :(

---

### Post by gillani on 2010-09-22
> **cooprocks123e said:**
> You could also install syslinux on there, copy over memdisk from the syslinux sources and the Plop bootmanager disk image, put the installer on the usb, then run memdisk with the plop image as initrd and boot from the usb.

Or you could run a network install if you have a supported nic.

Thank you for the suggestion.  This worked!!!  So for all the other newbie's out there, this is what I did.

0. Created a usb stick with Ubunutu Netbook Remix unetbootin-windows-471.exe
1. Pulled Harddrive out of Laptop and added to another workstation using a USB2.0 TO IDE (SATA) kit.
2. Cleared off all partitions
3. Ran HP USB Disk Storage Format Tool and created formated and added DOS files which I got from the net as well.
4. Then deleted all the system files from the newly created drive
5. Downloaded Syslinux ([http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-4.02.zip](http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-4.02.zip)) and copied to the drive and ran the following command where f: is the new drive:
c:\syslinux\win32>syslinux.exe f:
6. copied the syslinux directory to the F:
7. Downloaded Plop Boot Manager ([http://download.plop.at/files/bootmngr/plpbt-5.0.10.zip](http://download.plop.at/files/bootmngr/plpbt-5.0.10.zip)) and extracted the files to f:\plpbt
8. Put the harddrive back into the laptop
9. When the laptop started, it came to a boot loader and I type the the following:
**Ensure the Ubuntu USB stick is plugged into the laptop
/syslinux/memdisk/memdisk initrd=/plpbt/plpbt.iso append iso

and voila it started up the USB stick just like it would have from the bios method :)

Again thanks ..

---

### Post by gillani on 2010-09-22
I finally got the USB drive to load Ubuntu, but after seeing the initial Ubuntu splash screen, the screen goes blank.  It looks like its running as the USB drive is going and clicking buttons on the keyboard seems to do something.

The machine is a Toshiba Protege 3020ct.  I think it is a video driver issue.  Is there a way to confirm or fix?

PS.  The same thing happens if I try to load Xubuntu.

---

### Post by snowpine on 2010-09-22
Toshiba Protege 3020ct:

> CPU: MMX 300 MHz 
RAM: 32 MB 
HDD: 6.05 GB
Screen: 800 x 600

Ubuntu Netbook system requirements:

> # Intel Atom processor @ 1.6 GHz
# 512 MiB of system memory (RAM)
# 4 GB of disk space
# Screen of 1024x600 resolution
# Graphics chipset with support for visual effects 

---

### Post by gillani on 2010-09-22
Thanks.  Any suggests on a distro?

PS.  It has 96MB of RAM.

---

### Post by snowpine on 2010-09-22
> **gillani said:**
> Thanks.  Any suggests on a distro?

PS.  It has 96MB of RAM.

Never installed Linux on hardware that old, personally. But I did find an account of a user who installed Damn Small Linux on your hardware:

[http://www.physics.mcgill.ca/~jcline/portege.pdf](http://www.physics.mcgill.ca/~jcline/portege.pdf)

---

### Post by cooprocks123e on 2010-09-29
Yeah, try DSL, or Windows 2000 or older. I had a laptop like that, except the processor was slower; and it ran W2K good enough.

---

