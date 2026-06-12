---
title: "Full installation on USB ?"
date: 2015-11-29
forum: Installation &amp; Upgrades
---

### Post by F35Blackbird on 2015-11-29
Hi, 
Using UUI (Universal USB Installer), I installed Ubuntu 15.1 on my USB stick. When I boot my computer using USB, I get options similar to following:

1. Try Ubuntu without installing
2. Install Ubuntu

What would option 2 do? Will it install Ubuntu completely on my USB drive?

I also want to know how can I increase the Persistant partition size on my USB stick?

Thanks.

---

### Post by egeezer on 2015-11-29
What you installed was the live iso, not the regular version; the Install Ubuntu option will let you install it somewhere else (i.e. the box where you're running it!).

If you want to install a workable, running version onto a hard drive, with all the persistence your USB can hold, there is a way:

Boot the live version on your regular drive (e.g. from a DVD)

Plug in the USB drive you want to use.

Find the name of the device (will be some sdx) that is your USB drive (use dmesg or Gparted).

Then just install to that drive.  

It would be best to use the "Something else" version of partitioning and just install to a single partition (/), because a swap space would limit your USB lifetime.

---

### Post by sudodus on 2015-11-29
I can add a couple of links with some more details:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by grahammechanical on 2015-11-29
> What would option 2 do? Will it install Ubuntu completely on my USB drive?

No. It will start the usual process for installing Ubuntu to a hard disk.

> I also want to know how can I increase the Persistant partition size on my USB stick?

From the little I know about this the size of persistence varies according to the size of the USB memory stick. The greater the size of the USB memory stick the greater the amount of persistence. So, the answer to your question would be: Get a bigger USB memory stick.

Regards.

---

### Post by sudodus on 2015-11-29
You should also know, that it is possible to store the data in a casper-rw ***partition*** instead of a casper-rw file. It is easier to manage a big partition, for example backup compared to a file. An alternative is to use ***mkusb*** to install a persistent live system in a ***fast USB 3 pendrive***.

---

### Post by F35Blackbird on 2015-11-29
Thanks for all your replies. 

I'm actually trying to install Ubuntu "completely" on a USB drive, so it become computer independent. 

How do I do that?

After installing Ubuntu, I'm planning to install VirtualBox and have Windows installed in the VirtualBox. 

Thanks.

---

### Post by oldfred on 2015-11-30
Full install to a flash drive is just like a full install to any second drive as it is seen as another hard drive.
If USB3 on USB3 port it should work reasonably well. On USB2 it will be slower than a hard drive install. Either way to improve speed somewhat you want to minimize writes by changing some settings. Also Lubuntu has a lighter weight GUI and will load faster than full Ubuntu with Unity GUI.

Do you want UEFI or BIOS boot from flash drive. Basic install is the same, but how you boot and particularly grub install issues are different.

       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[URL="https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode"]https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode
[/URL]
 UEFI install,windows 8 with Something Else screen shots
[URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html

      [/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not highlight changing boot loader to sdb, if external drive, but shows other install screen shots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)

    
More info & many links on UEFI and UEFI installs in link in my signature.



[URL="https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode"]
[/URL]

---

### Post by C.S.Cameron on 2015-12-01
I just posted the following to another thread:

For what it is worth the following is how I make a Persistent flash drive:

Boot Live CD or Live USB.
Plug in flash drive.
Start gparted.

Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).

Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).

Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition).

Close gparted.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.

For 64 bit use the following instead:

    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz.efi
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --

---

### Post by C.S.Cameron on 2015-12-01
Following is step by step how to do a Full install of 14.04 on a 8GB flash drive:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language.
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4500 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hibernation)

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".

Select your location.

---

### Post by F35Blackbird on 2015-12-10
Thanks a lot guys, I followed steps outlined in the replies and am good now. 

USB data transfer rate is the only bottleneck in this case, everything else is working good.

---

### Post by C.S.Cameron on 2015-12-11
Yes, it takes some time when opening a program for the first time in a USB session.
Once that program has been opened, it seems to load in RAM and opens much faster subsequent times in the session.

---

### Post by oldfred on 2015-12-11
The other thing I change in fstab is to add noatime. That is a time stamp write on every access. One or two applications (mutt), but I have not had issues.
Also I use ext4, but turn off journal. Others may suggest ext2. Since partition is small and most data is system, use of journal to aid data recovery is not as required. If saving vital data also, you may want it on.

If Solved please change status to [Solved].

---

