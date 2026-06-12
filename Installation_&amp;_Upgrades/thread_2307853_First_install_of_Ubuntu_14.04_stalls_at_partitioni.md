---
title: "First install of Ubuntu 14.04 stalls at partitioning"
date: 2015-12-29
forum: Installation &amp; Upgrades
---

### Post by eric103 on 2015-12-29
I am installing Ubuntu 14.04.3 on an old Dell running Windows 7. I want to partition the computer. During the partition step, after hitting "Continue" the cursor spinner starts and has not stopped. No buttons are active so the system is essentially frozen. I do not want to turn off the computer since I'm not sure whether that would damage anything. Any advice would be appreciate. Thanks.

---

### Post by Photon Blizzard on 2015-12-29
Greetings, 

It's hard to be positive that shutting down the computer at this stage won't have any issues.  However, after installing various Linux OS's about 500 times I would have no issues with shutting it down and making sure my Win7 was still intact.  If that's the case go into Control Panel, then security and you should see an option to Format/Partition Hard Drive.  Once there you should have the option the "shrink" the volume.  Shrink the volume and much as allowed and then make sure it's adequate space to install Ubuntu.  Doesn't take much.

Now that you have freed up some space on the drive, attempt to install again from the DVD.  Ubuntu should prompt you to install ubuntu in the free space and keep your win7 partition intact.  If this is the case you don't need to do any partitioning on your own.  Ubuntu will do everything for you.  When you reboot, the grub bootloader should appear and give you the option of booting Ubuntu or Windows.  Just cursor to your choice. 

Good luck captain.

Photon

---

### Post by eric103 on 2015-12-29
Ok, I rebooted my machine without any issues. I also confirmed that space is not a problem. When I go through the installation process again my system freezes during the partition phase, in the same manner as I described above. Could this mean that there's something wrong the hard drive? Thanks for the help, Photon.

---

### Post by sudodus on 2015-12-29
Welcome to the Ubuntu Forums :-)

Maybe the computer does not have enough RAM. Maybe there is some other problem. Many old computers do not work well with standard Ubuntu, but there are flavours of Ubuntu with lighter desktop environment (the graphical user interface), Lubuntu, Xubuntu and Ubuntu Gnome. Often these flavours work well with old hardware. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

it makes it easier for us to give good advice.

You can also find tips at the following links

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by grahammechanical on 2015-12-29
There is also something else you can do. Either

Use a Windows utility to show the partition layout and take a screen shot and post it in your thread.

or

Run the Ubuntu live session, open Gparted and take a screen shot and post it in your thread.

I think it would be helpful if we could see the partition layout for ourselves.

Regards.

---

### Post by eric103 on 2015-12-29
Dell Computer (not sure of model)
CPU: Intel Core, 2 CPU 4300 @ 1.80 GHz (x2) (same as [http://www.ebay.com.au/itm/331578518835](http://www.ebay.com.au/itm/331578518835))

RAM: 4 GB
Graphics card: ATI Radeon HD 5450
Wifi: Wireless N Nano USB Adapter, DWA-131 ([http://us.dlink.com/products/connect/wireless-n-nano-usb-adapter/](http://us.dlink.com/products/connect/wireless-n-nano-usb-adapter/))

Attached is a screen shot of [COLOR=#000000]Gparted.[/COLOR]

---

### Post by yancek on 2015-12-29
The reason your install freezes is because you do not have any free space on which to install Ubuntu.  You have three partitions, all of which are ntfs (windows filesystem) taking up the entire drive.  You can use Disk Management in windows 7 to shrink the largest partition to make room for Ubuntu.  I'm not sure what the red icon next to sda3 is.  You might run chkdsk from windows after shrinking that partition.  The 'used' size for the partitions doesn't seem large enough for a windows install and there doesn't appear to be anything on the largest partition?  You don't have windows 7 hibernated do you?

---

### Post by Geoffrey_Arndt on 2015-12-29
After shrinking Windows, you should have unallocated space of at least 12 GiB . . . preferably double that.    Immediately after shrinking, run chkdsk twice to confirm Win7 will still bootup normally.

EDIT:   Yikes . . . . after a second look, that disk does not look good.     What happens when you try to boot up Windows now . . .  sda1 looks too small to be your main Windows partition, and sda3 - while formated NTFS, doesn't seem to have any meaningful data.   If you restarted the computer "while" a partitioning operation was underway (as it seems likely) . . . . you've probably hosed your windows.

---

