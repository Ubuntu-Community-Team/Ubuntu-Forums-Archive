---
title: "32GB USB 3.0 Flash Drive, Greater than 4GB Persistence?"
date: 2013-04-20
forum: Installation &amp; Upgrades
---

### Post by edgex on 2013-04-20
Okay so I've tried and tried this: [http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)  and if i dont create a casper-rw in the first place when making the usb drive, it doesnt have any persistence at all, but still boots. If I say, make a 200mb casper-rw file when creating the drive, then delete it, as the guide suggests, it fails to boot. Either way that does not work for me.

So what I'd like to know, is how can I use this full 32GB flash drive with persistence??? I'm using 13.04 x64, and will want to do this once the final version comes out and keep it for a while to come.

I'm willing to do a full instal to the flash drive if that's what it takes. I just tried but it doesnt seem to boot, so I must have missed something. This talks about GRUB, which I didnt see any options for. [http://askubuntu.com/questions/32484/how-to-boot-from-ubuntu-live-usb-with-try-ubuntu-directly](http://askubuntu.com/questions/32484/how-to-boot-from-ubuntu-live-usb-with-try-ubuntu-directly)

Thanks a lot!

---

### Post by C.S.Cameron on 2013-04-20
Here is a method using Startup Disk Creator, If you require a method using UNetbootin, let me know:

You can have persistent ext2, 3 or 4, partitions named casper-rw and home-rw, of any size that will fit the drive.
Casper-rw stores your downloaded programs and home-rw stores your settings, email and downloads, etc.

Here is a step by step:

Boot Live CD.
Plug in flash drive.
Start Partition Editor, (gparted).
Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 4 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Startup Disk Creator", (usb-creator).
Select minimum Stored in reserved extra space, (128 MB).
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk and deleted the casper-rw file.
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by C.S.Cameron on 2013-04-20
Performance of a Full install is about the same as a Persistent install but boot faster and can be updated and upgraded:

Following is step by step for installing 12.04 on a 8GB flash drive on an Intel machine.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
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
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

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
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

---

### Post by edgex on 2013-04-20
I followed your second suggestion for installing straight to the flash drive. It works on my older laptop, but not on my newest one. I end up getting this. [https://www.dropbox.com/s/dqj06lzejo12lfb/2013-04-20%2015.29.33.jpg](https://www.dropbox.com/s/dqj06lzejo12lfb/2013-04-20%2015.29.33.jpg)
I'm not sure if installing it to my flash drive dropped the UEFI thing my pc needs to boot it or something, or did installing it the way i did mean it can only work on the PC it was installed on?  I get to the purple screen which asks me to boot ubuntu or run memtest and what not, but after that it gets the above error.

---

### Post by C.S.Cameron on 2013-04-20
Have you seen:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by edgex on 2013-04-21
So I was playing around, and I pressed E and typed [COLOR=#000000]nomodeset[/COLOR] but it said the command was bad but let me hit enter to continue anyways, and it ended up booting. So I don't think UEFI is the issue, it is just not working regularly and I'm not sure where to take it from here. I tried replicating what I did to get it to boot and no luck, but if it happened once, it can happen again right?

---

### Post by oldfred on 2013-04-21
If you have UEFI, did you install to flash drive with BIOS mode or UEFI mode?
Best to have main install & flash drive in same mode as UEFI & BIOS write system data differently. So then you can only change boot by going into UEFI/BIOS and switch to correct mode for your install.

Not many have done a full install to a flash drive, and only a few to a second drive with UEFI. You just about have to partition in advance to get gpt partitioning and an efi partition created as the first partition.

Just to create a boot flash drive:
 Manually copy efi files to efi partition on flash drive. Toshiba Satellite S855-5378
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)
On the Ubuntu filessystem, you should have the signed versions of the following: /usr/lib/shm/shim.efi.signed, /usr/lic/grub/x86_64-efi-signed/grubx64.efi.signed, and /usr/lib/grub/x86_64-efi-signed/gcdx64.efi.signed. 
Copy them all onto the USB stick .../EFI/ubuntu directory without the ".signed" extension. 
Then copy and rename the shim.efi to the USB .../EFI/Boot/bootx64.efi. 
Also copy the grubx64.efi to the EFI/Boot/grubx64.efi. 
There should be the working grub.cfg in the USB .../EFI/ubuntu/grub.cfg

      
 [https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT](https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
sudo grub-install --target=x86_64-efi --boot-directory=/mnt/sdb1/EFI/BOOT --efi-directory=/mnt/sdb1 --removable

Full install to UEFI flash would be the same as a full install to any second hard drive.
 Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

---

### Post by edgex on 2013-04-26
> **C.S.Cameron said:**
> Here is a method using Startup Disk Creator, If you require a method using UNetbootin, let me know:

You can have persistent ext2, 3 or 4, partitions named casper-rw and home-rw, of any size that will fit the drive.
Casper-rw stores your downloaded programs and home-rw stores your settings, email and downloads, etc.

Here is a step by step:

Boot Live CD.
Plug in flash drive.
Start Partition Editor, (gparted).
Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 4 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Startup Disk Creator", (usb-creator).
Select minimum Stored in reserved extra space, (128 MB).
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk and deleted the casper-rw file.
Shutdown, remove CD, reboot.
You are persistent.

tired this, and when i boot, somehow it says missing operating system. I'm giving it a second shot but have no idea why that would have happened. followed every step perfectly. used ext4 for the casper-rw partition if that matters

Tried again, used ext2 as the casper-rw partition this time, still says no OS found. Also just so I make sure i have this right, "nautilus" is just Files right? and I'm doing the instal from another usb drive, you state CD, but I didnt think that mattered right? using the official 13.04 x64. Other variables I'm making the casper-rw partition the rest of the drive, no home-rw, so its like 27GB, if that matters, I hope not.

Any help would be greatly appreciated.

---

### Post by C.S.Cameron on 2013-04-26
Is it working on your older laptop?

The casper-rw file needs to be deleted before trying to boot the drive.

---

### Post by C.S.Cameron on 2013-04-26
Is it working on your older laptop?

The casper-rw file needs to be deleted before trying to boot the drive.

---

### Post by edgex on 2013-04-26
> **C.S.Cameron said:**
> Is it working on your older laptop?

The casper-rw file needs to be deleted before trying to boot the drive.

It is not, both laptops say no boot device found. and I am deleting before first boot. No idea what the issue is still. I have been doing all of this on the older laptop just for testing just fyi.

---

### Post by C.S.Cameron on 2013-04-26
Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional, you can use excess to move files between computers)
Create a 1.5 - 31 GB ext2 partition to the right of this, label it "casper-rw". (ext3 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes,
Make syslinux.cfg writable and replace contents with:

```
default persistent
label persistent
  say Booting an Ubuntu persistent session...
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --

```

Above also removes Try/Install screen.
Shutdown, remove CD, reboot.

Above works for 12.04 & 12.10, I've noticed that persistent installs can be flakey in pre-release versions of Ubuntu.

---

### Post by edgex on 2013-04-27
I tried that several times, still the same result. trying everything I can think of. Tried 13.04 and 12.10. Tried doing the gparted stuff in ubuntu, but installing to the fat32 in windows with universal linux installer. Tried formatting the whole drive as fat32, put ubuntu on it in windows, rebooted to my other ubunbu stick, and unmounted the drive, changed the size of the fat32 partiton and added an ext4 partition labeled casper-rw. nothing. Driving me insane! I just cant figure out what I'm doing wrong. Your steps make perfect sense but it seems like any time I have an ext2/ext4 patition, linux never boots.

---

### Post by oldfred on 2013-04-27
With 32GB have you tried a full install? I have a 16GB and installed in 8GB with 8GB for data. 
If you want compatibility with Windows the first partition must be FAT or NTFS.

 Full install - C.S.Cameron post #2
[http://ubuntuforums.org/showthread.php?t=2116798](http://ubuntuforums.org/showthread.php?t=2116798)
Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)

It really is just the same as any install to a second drive. You have to use Something Else or manual install to get the option to install the grub2 boot loader to the external drive.
IF UEFI, you have to partition as gpt not MBR(msdos) and have to have the efi partition first or second.

---

### Post by edgex on 2013-04-28
> 
default persistent
label persistent
  say Booting an Ubuntu persistent session...
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --


I tried making the 2gb fat32 partition and the 27gb ext4 casper-rw partition in ubuntu on the flash drive, reboot back to windows, used unebootin to instal to the fat32 partition (with no persistence), and tried copying this to the syslinux file before rebooting but I still get the normal Try/Instal screen, and still no persistence, but I am at least closer because it boots on all of my devices! Any additional suggestions?

edit: I also tried installing with unebootin with a small persistence file, and then deleted it before rebooting. Stil no persistence. :C  Also, for some reason, even leaving the syslinux.cfg file untouched i get the normal try/instal screen, not even the unebootin one, which is weird.

---

### Post by sudodus on 2013-04-28
Try a full install, as indicated by *oldfred* and *C.S.Cameron* earlier :-)

With 32 GB, you have plenty of space to install any of the Ubuntu flavours to the USB 3 drive in the same way as if it were an HDD or SSD drive. This is probably easier and will give you a better system for long time use.

---

### Post by C.S.Cameron on 2013-04-28
> **edgex said:**
> I tried making the 2gb fat32 partition and the 27gb ext4 casper-rw partition in ubuntu on the flash drive, reboot back to windows, used unebootin to instal to the fat32 partition (with no persistence), and tried copying this to the syslinux file before rebooting but I still get the normal Try/Instal screen, and still no persistence, but I am at least closer because it boots on all of my devices! Any additional suggestions?

edit: I also tried installing with unebootin with a small persistence file, and then deleted it before rebooting. Stil no persistence. :C  Also, for some reason, even leaving the syslinux.cfg file untouched i get the normal try/instal screen, not even the unebootin one, which is weird.

Have you checked syslinux.cfg to make sure the script actually got written? You need to write to it as root.

---

### Post by ubfan1 on 2013-04-28
Check the actual command use to boot the kernel:
    cat /proc/cmdline
If you do not see the "persistent" argument, you are possibly experiencing bug 1159016 --              [12.10 64bit live-USB successfully boots, but without persistence on UEFI pc]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1159016")

---

