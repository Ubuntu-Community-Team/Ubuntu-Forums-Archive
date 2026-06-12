---
title: "Boot from external drive, looks for NTLDR when it should be grub"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by Little Blue on 2010-05-28
Hi,

I've been working on a friends XP laptop today to install lucid on his external harddrive.

The install went ok but I had to use Super Grub Disk to repair the windows MBR to get the laptop to boot without the external drive plugged in (via [http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB)).

Before I fixed the laptop's MBR, the external drive booted fine, via grub etc. After the repair the external drive now refuses to boot. It comes up with an error about the NTLDR is missing. I don't understand why as it should be grub on the external.

When I try to repair it and install grub on the external drive via SGD following the instructions here: [http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub) I get a lot of funny errors ("Error 6 is ok") and ultimately it dies with error 18, too many cylinders. I guess this, [http://www.supergrubdisk.org/wiki/SGD_Howto_make#Common_errors](http://www.supergrubdisk.org/wiki/SGD_Howto_make#Common_errors), is related but its not the same point where I get the error.

If any of this makes sense, are there any suggestions on what I can do to get the external drive to boot.

My friends gone home with his laptop able to boot XP now and I won't be able to check for anything or have another attempt for another fortnight now, but any help or suggestions you can give will be greatly appreciated!

---

### Post by darkod on 2010-05-28
I might be harsh, but I don't like SGD at all. It just creates confusion, and often, a mess.
The ubuntu cd has all you need to reinstall grub, or even to repair the MBR to a generic mbr which can replace windows bootloader.

Without knowing what SGD actually did, I don't know what to say. Also, 9.10 and 10.04 come with the new grub2, while if you used the older version of SGD (they now have version for grub2 also, calling it SG2D or what ever), who knows what happened because grub2 uses different boot files than grub1.

And with the laptop not present, you can't even look inside, as you said yourself.

---

### Post by Little Blue on 2010-05-28
Thanks for your reply. I agree that SGD is confusing. And ah, I might have used an older version that I had from a few years ago.

I don't suppose you know, or can point me to, how to fix the external MBR with grub2 using the live disk or if I plug the drive into an existing install?

---

### Post by WinRiddance on 2010-05-28
This is what I like to use for disk and partition problems. Tons of built-in features, very graphical, fairly easy to use, been around for years, and it's just as free ... [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by darkod on 2010-05-28
Yes, but I don't know how experienced you are with ubuntu. You would need to know which is the ubuntu root partition on the ext hdd, and the device name of the hdd.

Lets assume:
ext hdd is: /dev/sdb
ubuntu root is: /dev/sdb5

Boot with the 10.04 cd in live mode and do:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

So, you first mount the root partition (because you are only in live mode), and then you tell grub2 to install on the disk MBR (/dev/sdb) with a parameter the mount point of the mounted root. That's it.

Also for future reference: when you have dual boot, as long as the boot flag is correctly set on the windows partition, grub doesn't work out of what ever reason, you can install generic mbr with:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

You can do that from live mode or full ubuntu install. It will issue some warnings but since you don't actually plan to use lilo to boot anything, just install a generic mbr, ignore them. That works as easy way to make windows boot directly again.

---

### Post by Little Blue on 2010-05-28
Cheers darkod, I'll try that when I next get my hands on the system. As an aside, the live disk takes an absolute age to load (the laptop's a bit low on RAM, enough to run ubuntu installed, but struggles with the live disk) can this be done by plugging into an existing system so long as I know the appropriate device names.

And thanks for the tip in the future.

---

### Post by darkod on 2010-05-28
> **Little Blue said:**
> Cheers darkod, I'll try that when I next get my hands on the system. As an aside, the live disk takes an absolute age to load (the laptop's a bit low on RAM, enough to run ubuntu installed, but struggles with the live disk) can this be done by plugging into an existing system so long as I know the appropriate device names.

And thanks for the tip in the future.

Yes, since you want to reinstall grub2 to the MBR of the usb hdd, and the ubuntu root is on that same hdd, you can do it on any computer. Just watch out for the device name and partition name.

And don't run update-grub by any chance while plugged into another computer because it will create the boot menu with the OSs it can find there. :)

---

### Post by Little Blue on 2010-05-28
hehe, cheers. Many thanks again. :D I just hope it works when I can work on it next!

---

### Post by Little Blue on 2010-06-17
Hey, thanks for all your help. Turns out we had to reinstall it anyway as something crazy had happened to the target partition since I started this thread that prevented us from accessing it to repair grub (SGD perhaps? I don't know). This time I ha remembered there's an option of where to install the bootloader to which I completely forgot about last time :oops: resulting in all this fuss, so I just installed the boot loader to the external drive and everything went swimmingly well.

Thanks again.

---

