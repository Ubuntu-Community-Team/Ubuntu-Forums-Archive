---
title: "Portable Updatable Ubuntu on Flash Drive"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by siabost on 2012-01-17
Hi,

I'm trying to create an Ubuntu 11.10 32bit Flash Drive that I can carry around from computer to computer i.e. ones with different hardware requirements.

The standard "Try or Install" Ubuntu Flash Drive, whilst it will work on any computer, is not updatable.

I have tried making a direct installation to the Flash Drive - treating it like a normal hard-drive - but this seems to work only on the machine it was created on. On other computers it seems to fail just before loading the X-screen. I have set the drive to auto-login.

Is there a way to make an installation to Flash Drive that is portable or have I missed something in the installation?

Many thanks.

---

### Post by jerrrys on 2012-01-18
A persistence install?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=persistence+install&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=persistence+install&sa=Search&cof=FORID:9)

---

### Post by siabost on 2012-01-18
Thanks jerrrys.

I'd seen & a few of the posts before, though - useful site, GoogleUbuntu - hadn't seen that before :D

I managed to create a Flash Drive install that worked perfectly on 3 out of 4 PC/Laptops I tried it on - the one it didn't run quite right on came up with "This computer cannot run OpenGL" error message which is odd as it runs a Hard Drive installed Ubuntu 11.10 with full effects.

Anyhow, I performed the successful Flash install via my Desktop PC after disconnecting its internal Hard Drives. This also seems to have made the boot time a lot quicker even on the original PC.

So apart from the OpenGL error mentioned above, it seems to work.

But it would be useful to know if changing the drive designation from sde (which is what the PC called it) to sda would make a difference to its performance.

Many thanks.

---

### Post by sudodus on 2012-01-18
Have a look at how I did a persistent usb drive
[[COLOR="Blue"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")

---

### Post by C.S.Cameron on 2012-01-18
siabost:

The Full install flash drives I've made seem to work on any USB bootable machine as long as I don't install any propriatary drivers.
I believe the drive designation of your flash drive depends on how many drives are already in the machine, if no other drives the designation should be sda.

sudodus:

Did you know that you can simply do a persistent install on the first, (FAT32), partition, delete the casper-rw file and then make an ext4 second partition named casper-rw, (and a third named home-rw if you want a seperate home partition).

These partitions can be of any size and are not effected by the 4GB FAT32 file size limits.

The drive is still not really updatable though.

---

### Post by ottosykora on 2012-01-19
An operating system running on any computer.., well this is rather big expectation.

Some kind of solution could be the 'pubuntu' , kind of portable ubuntu run via the colinux, slow, but nice toy (google for pubuntu)

Otherwise some kind of virtual install, quemu is rather portable, preconfigured portable launchers exist, kind of slow too, but could be used for simple things.

---

### Post by sudodus on 2012-01-19
> **C.S.Cameron said:**
> siabost:

The Full install flash drives I've made seem to work on any USB bootable machine as long as I don't install any propriatary drivers.
I believe the drive designation of your flash drive depends on how many drives are already in the machine, if no other drives the designation should be sda.

sudodus:

Did you know that you can simply do a persistent install on the first, (FAT32), partition, delete the casper-rw file and then make an ext4 second partition named casper-rw, (and a third named home-rw if you want a seperate home partition).

These partitions can be of any size and are not effected by the 4GB FAT32 file size limits.

The drive is still not really updatable though.
Thanks for the tip :-)

I have been considering trying with a ext2 or ext3 partition instead of fat32 as the boot partition to be able to have a bigger casper-rw file, but your solution is certainly better, to have an ordinary partition. How should I mount it and how-to mount the home-rw partition (do you have the syntax details?)

The reason I do not boot from the first partition is that I want that partition for data, that can be read by Windows XP.

But believe it or not, I have managed to make a complete update with
```
sudo apt-get update
sudo apt-get upgrade
``` without any problems. (Yes, I was warned that it does not work, but it actually did work, and with a big enough casper-rw file or partition, that might be a good option.) Maybe the limit is that the kernel cannot be updated.

Anyway, what would you suggest as the best alternative with a 16 GB or larger USB flash drive? A normal install with noatime (and without proprietary drivers)?

---

### Post by C.S.Cameron on 2012-01-19
sudodus:
I have previously posted how to's for persistent partitions on usb-creator builds and unetbootin builds. but do not have access at my current location.

If I recall correctly, using gparted:
The second partition should be ext2, 3 or 4 and the size you think you will need for additional programs and named casper-rw.
The third partiton, (optional), should be ext2, 3 or 4 and the size you think you will need for home, (settings etc) and named home-rw.
The first partition should allow 0.75GB for the O/S and what you want for storage and transfer,
(Partitions can be resized later with gparted).

Install to the first partition using usb-creator, (you can extract usb-creator.exe from the iso for use in Windows or run from Ubuntu).
Select the extra space, (persistence), option but delete the casper-rw file after install.

I have sucessfuly run an update once or twice but eventually the drive will not boot unless you mount the casper-rw file or partition and delete stuff. your right that the kernel can't be updated it is locked in the filesystem.squashfs file

If you are planning on keeping the portable O/S for a while I would go with a Full install on an 8GB or larger drive:

Following step by step for Full install of 11.10 to USB device.
Partition sizes given are for 8GB drive, adjust size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the USB drive.
Insert the Live CD or Live USB.
Start the computer, the CD / flash drive should boot, (you need to adjust BIOS to boot USB).
Select language
Select "Forward".
Select Download updates while installing and Select Install this third-party software.
(Notice that at least 4.4 GB drive space is required, 4GB bootable flash drive users must choose another distro for a full install).
Forward
If prompted unmount partitions.
Select "Something else"
Forward
Confirm "Device for boot loader installation:"is correct, (If you left your internal HDD plugged in make sure the USB drive root is selected - sdb not sdb1).
(Optional Windows data partition)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000
"Location = Beginning".
"Use as: = FAT32 file system"
And "Mount point = windows".
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and enable the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.

---

### Post by siabost on 2012-01-19
sudodus:
> But believe it or not, I have managed to make a complete update with
Code:
sudo apt-get update
sudo apt-get upgrade
without any problems. (Yes, I was warned that it does not work, but it actually did work, and with a big enough casper-rw file or partition, that might be a good option.) Maybe the limit is that the kernel cannot be updated.
Indeed, I'm afraid it won't update the kernel.

C.S.Cameron:
Yup, that's more or less what I did, disconnecting the internal hard drives and all. The Flash Drive install went fine but on reconnecting my drives a UUID Drive reference cannot be found and I end up at the Grub Rescue prompt! I've managed to boot in using various Grub2 commands but have yet to figure out how to make the fix permanent - sudo update-grub doesn't do it. I'll try it with the second HDD disabled then maybe edit fstab.
We'll see...
:)

---

### Post by sudodus on 2012-01-19
> **siabost said:**
> sudodus:

Indeed, I'm afraid it won't update the kernel.

C.S.Cameron:
Yup, that's more or less what I did, disconnecting the internal hard drives and all. The Flash Drive install went fine but on reconnecting my drives a UUID Drive reference cannot be found and I end up at the Grub Rescue prompt! I've managed to boot in using various Grub2 commands but have yet to figure out how to make the fix permanent - sudo update-grub doesn't do it. I'll try it with the second HDD disabled then maybe edit fstab.
We'll see...
:)
Strange error, if you refer to the partitions with UUID, it should work even if you swap the connections. Are you sure there is good electrical contact? Maybe you have to unplug and replug the disks again.

---

### Post by siabost on 2012-01-19
Hi sudodus,
> Strange error, if you refer to the partitions with UUID, it should work even if you swap the connections. Are you sure there is good electrical contact? Maybe you have to unplug and replug the disks again.

Agreed, that is my understanding too. Because of the nature of my PC my main hard drive is SATA and the 2nd is IDE which is linked in with the IDE DVD/ROM drive as there is only one IDE input on the motherboard.

It has happened before so the above slightly strange configuration may be the cause.

---

### Post by C.S.Cameron on 2012-01-19
> **siabost said:**
> sudodus:

Indeed, I'm afraid it won't update the kernel.

C.S.Cameron:
Yup, that's more or less what I did, disconnecting the internal hard drives and all. The Flash Drive install went fine but on reconnecting my drives a UUID Drive reference cannot be found and I end up at the Grub Rescue prompt! I've managed to boot in using various Grub2 commands but have yet to figure out how to make the fix permanent - sudo update-grub doesn't do it. I'll try it with the second HDD disabled then maybe edit fstab.
We'll see...
:)

Did you install using a flash drive? I wonder if it is looking for this.

---

### Post by siabost on 2012-01-20
C.S.Cameron:
Got it sorted, thanks.
Once I disconnected my IDE PATA Hard Drive (2nd Drive) it booted from my main SATA Hard Drive.
I checked my UUID Drive Nos with ```
sudo blkid
``` and they matched those listed in /etc/fstab. I then ran ```
sudo update-grub
``` in Terminal, reconnected my second driver and all is well.

No idea why the confusion happened, though.

:D

---

