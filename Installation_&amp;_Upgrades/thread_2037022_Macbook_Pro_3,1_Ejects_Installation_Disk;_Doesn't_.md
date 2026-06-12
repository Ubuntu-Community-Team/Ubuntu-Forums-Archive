---
title: "Macbook Pro 3,1 Ejects Installation Disk; Doesn't Recognize Bootable USB"
date: 2012-08-03
forum: Installation &amp; Upgrades
---

### Post by ejenks on 2012-08-03
Hey all - first off, I wasn't sure whether to post this in the Apple  forum or in the Installation and Upgrades forum, so if you see fit to  move me, I won't complain. Now, here's my problem; 

I originally  installed Linux Mint 13 on my Macbook Pro 3,1 about two or three days  ago. I was able to install it easily enough using [rEFIt]("http://refit.sourceforge.net/").  However, I decided to switch over to ubuntu. I burned a 64-bit Ubuntu  installation DVD (it's a DVD-R) and inserted it into the superdrive  while I was still in Linux Mint. This was when the problem first arose;  the superdrive promptly ejected the disc after about 15-30 seconds of  trying to decide whether it recognized the DVD or not.

I rebooted  into Mac OS X (snow leopard) and retried inserting the DVD. However, I  had the same issue; the superdrive ejected the DVD and it never showed  up on the desktop. By now, I was thinking that it was an issue with the  DVD. I inserted it into a Windows machine and it prompted me to install  Ubuntu; I had burned the disk correctly, so that wasn't my problem. I  decided to erase the hard drive and start again; after reinstalling Mac  OS X (Snow Leopard), I am still having the same issue. Also, I've  noticed that upon insertion of a blank DVD, the superdrive spits that  out as well. Another point of confusion for me was the fact that the  superdrive was now rejecting the Linux Mint 13 installation DVD that I  had just burned the other day (this may illustrate a problem with the  superdrive, although seeing how it was working fine with the Linux Mint  installation, I don't believe that's the case).

I soon tired of  attempting to install via CD and tried booting from a bootable USB drive  that I had created through the terminal as per [these]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx")  instructions. After I finished, I tried to reboot holding option to  display the bootable drives, and the USB didn't even show up. When I  booted into OS X, it threw up a message about not recognizing the USB  device. I also tried using instructions here to create a bootable USB  drive using the ISO-2-USB EFI-Booter for Mac 0.01 Beta; I got as far as  being able to see the drive in the boot options, but ISO-2-USB got stuck  at "Fasten your seatbelts, we are loading the kernel" which leads me to  believe that the kernel was never actually loaded.

It is also probably worth mentioning that I tried burning the 32-bit Ubuntu to a DVD, along with the 64-bit mac amd version [here]("http://cdimage.ubuntu.com/releases/12.04/release/"). I also tried the mini.iso version, but to no avail. In all cases, the disc was ejected.

I  am at a loss; I don't know what else to try. As far as I know, it could  be a superdrive issue, it could be an EFI issue, I don't know. I've  tried to recreate my system to the point before I installed Linux Mint  13, as that was when I was actually able to insert discs. But even after  OS reinstalls and hard drive wipes, I'm getting nowhere. It also may be a problem where OS X is not even recognizing the ISO, even though other systems are. I have no other Mac system to try it out on, only Windows systems. Any help is  greatly appreciated. I will be happy to provide any additional  information you may need. Thanks in advance!

---

### Post by fhsjaagshs on 2012-08-03
Is the disk formatted with the GUID partition map?

Pop a disk into your mac, open Disk Utility. Mount the Ubuntu ISO.

Now format the disk to Mac OS Extended (Journaled). Make sure in the options it is a GUID partition map. Now try copying the contents of the Ubuntu ISO to the disk. If this doesn't work, use the "restore" option in disk utility.


If all else fails, convert the ISO to a DMG and try again.

---

### Post by ejenks on 2012-08-04
Sorry for the lack of updates, been working night and day to try and solve this problem. It's driving me nuts.

I am unable to mount the ubuntu iso; when I double click it, I get the error message "no mountable file systems." I googled that error, and used the information here (specifically this post) to extract the iso into a new one. This was marginally successful, as the ISO now mounted. I tried burning the new ISO to a disk, but when I rebooted, neither holding option nor going into rEFIt would display the new disc. I used the same procedure to try burning the new ISO to a USB drive, but had the same issue with the drive not being recognized. 

I have broken out an old external DVD drive that I had laying around, and inserted the original Ubuntu x64 disk that I had burned. When I got to the rEFIt menu, it now gave me many options; boot from the disk, or boot from boot.efi (which would throw up a "prefix not set" error, and then give me three options: "try ubuntu without installing", "install ubuntu", or "check disk for errors"). When I chose any one of those three, a black screen would show up and not give way to anything else (after waiting about a half an our). Booting from the disk got me nowhere; first I got an error saying that there was "no bootable device" in the drive. I restarted, sync'd up the partitions using the rEFIt partition tool (as per these instructions) and tried once again to boot into the CD. I got a different error this time, saying that the disk in the drive is a "non-system disk: press any key to reboot." That is as far as I've gotten, and I am at wit's end. Any ideas? Thanks!

---

### Post by gifford on 2012-08-05
It has been a long time since I have used a mac, but if I remember correctly, if you hold down the "c" key while starting the computer up, it will boot from the cd/dvd drive.

---

