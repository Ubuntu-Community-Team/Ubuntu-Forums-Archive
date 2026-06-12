---
title: "No root File System Defined during installation"
date: 2017-05-31
forum: Installation &amp; Upgrades
---

### Post by sariel111 on 2017-05-31
Hello, So I am a total Noob when it comes to Xubuntu but I will try to describe the problem as best as I can. 

So I want to build a mining rig and got all the parts, I heard that I can use a USB stick to boot Xubuntu to my computer which is otherwise totally blank no other operating system or anything. 

I turn my computer on after making my computer accept usb boot drives from bios. It turns on and the Xubuntu install screen comes on, I go through the first couple screens ultimately getting to this screen [IMG]https://i.stack.imgur.com/UGMTd.png[/IMG]


now here is where it gets weird I tried hitting the change + and - buttons and it crashes, if I hit install  it wont work either. If I am correct its not even recognizing the usb?  I tried hitting sudo parted -l and the dmraid code in the terminal. but nothing works... If you can please help...

---

### Post by Geoffrey_Arndt on 2017-06-01
I think your USB thumbdrive iso is OK.   The installer is running, so your PC "sees" the USB.

What may help is to know if your PC is UEFI & GPT (which replaced standard BIOS with MBR (master boot record) partitioning.   your installer on the boot stick has to be running in UEFI mode if your firmware is UEFI also.

Another thing I personally would do is to use the live installer USB thumbdrive to run "Gparted" and setup your partition table with an EFI partition (if it doesn't already exist - - about 250 MB is fine), and then create a ext4 linux file system on one of your other partitions (so, a really basic setup would be . . . efi partition, ext4 OS partition and a swap partition of 4GB or so).

Note:   IF you're not planning on running WIndows as a dual-boot, you may want to consider enabling "Legacy" mode on the firmware.    Is just a bit more basic and easy to configure as then you can tell the installer to put the Grub bootloader on sda (not sda1 or sda2 or sda3).

Excellent tutorials re using gparted on youtube btw.

---

### Post by efflandt on 2017-06-01
Do you have any drive on the computer? Normally if the installer sees a drive it would offer to install on the drive, either to overwrite whatever is there and use the whole drive or possibly alongside another OS if there was an OS on the drive. But since you ended up in the "Other" screen where you would manually configure partitions and what looks like the "New Partition Table" grayed out, it appears that Linux does not see any drive on the computer. So does it have an M.2 flash drive or any drive at all?

It is possible to install to USB flash or drive, but that would need to be a separate one from the one the installer is on.

As mentioned, boot the installer to a live system instead of starting the install and see if gparted from there sees any drive besides the USB you booted from.

---

### Post by coffeecat on 2017-06-01
*Thread moved to **Installation & Upgrades**.*

@sariel111, is the internal hard drive that you used for your computer one that was once used in a RAID? I don't know whether this is still the case, but this used to be a common reported problem where residual RAID metadata on the hard drive confused the installer, and caused a blank on installation type page to be shown. If this is the case for you, post back confirmation of this, and how many hard drives are in your setup, and someone will be able to help you.

---

### Post by Frogs Hair on 2017-06-01
I had a drive that had been used in a Raid setup and used the following command from the live session and was able to install on the next reboot. Don't use the command which removes Raid meta data if you are currently running Raid on an installed operating system !

```
  [COLOR=#000000][FONT=&quot]sudo dmraid -E -r /dev/sda[/FONT][/COLOR]
```

---

