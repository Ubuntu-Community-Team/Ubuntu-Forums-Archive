---
title: "ubuntu 6.10 install from iso"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by loclei on 2006-11-06
can someone tell me how to install ubuntu 6.10 from an iso image which is on hdd?

what i'm trying to do is use this ubuntu-6.10-desktop-i386.iso to install ubuntu without having to burn a cd..

i mean if i could boot into dos or something.. with a boot disk made for linux.. like the ones for redhat ... then i would just type install from hdd.. show the iso and  after that the install would begin

---

### Post by fiveseven on 2006-11-06
Id like to know if its possible aswell, i dont have a cddrive and i dont want to do a netinstall (lack of bandwidth atm).

Its fairly easy with the debian installer, is it possible in ubuntu?

---

### Post by fljoemon on 2006-11-06
Download ISOBuster from [http://www.isobuster.com](http://www.isobuster.com)

Drag the ubuntu.iso file to the ISOBuster icon on the desktop and unpack the files to a directory on your hard drive. Look for the installer program in the directory you unpacked the files and then click on it to install the OS.

PS: I have never tried this ... Just guessing here and if it works for you, please post it.

---

### Post by subzero79 on 2006-11-06
I believe VMware can do that. Beside VM to create a Virtual HD partition it can also use a phisical one. Hope it helps.

---

### Post by fiveseven on 2006-11-06
Thanks for the replies but i dont think you guys quite get what i (and i think the OP) mean.

With the debian installer you can place a "hd-boot" bootable imagine on a partition, along with the corresponding debian .iso image. 

When you boot to that partition using GRUB/LILO the hd-boot installer would search for an (the) .iso file and check to make sure its a proper debian cd image, and if it is, you can continue the installation like normal from the .iso without ever having to use a cdrom drive.

However id rather ubuntu than debian, so if its possible with ubuntu id really like to know :)

---

### Post by subzero79 on 2006-11-06
You are right. But i believe the Ubuntu hd-boot loads the installer and then then performs a network installation retrieving the packages from the mirror. I've once try that thing you are trying to acomplish with no success. The installer searched for an image in the hd to perform the install but it didn't work (it said the image was damaged or something). I believe the problem was that the edgy iso i've downloaded was the standard iso. I think you should use the alternate iso. Like this one

[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso)

The alternate cd does not provide the Live mode. The installer is text mode based.

---

### Post by fiveseven on 2006-11-06
Thanks for the info subzero,

Do you know where i can download an ubuntu hd-boot image? I cant seem to find one on my local ubuntu mirror nor under the downloads page at ubuntu.com .

Cheers
fiveseven

---

### Post by loclei on 2006-11-07
or maybe there is a way to install ubuntu from linux mandrake 10.1

so i managed to install mandrake 10.1 
and maybe it's possible to install ubuntu from the iso  after i boot into mandrake ?

---

### Post by subzero79 on 2006-11-07
There are only 3 boot installer images: cdrom, hd-media and netboot.

if hd-media if what you are looking here it is.

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current//images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current//images/hd-media/)

Also from my first reply, try considering VMware if you are using windows.

BTW: There is a lot of people complaining always because of their lack of CD drive, searching for different methods for install (PXE, netinstall, hd-boot, etc), now you have a CD drive but you don't want to burn a CD. Come on a CD is like what....25 cents?. Maybe use a cd-rw.8)

---

### Post by loclei on 2006-11-07
it's not the money i had a cd-rom but i didn't have the iso then 

then i had the iso but it was the wrong one

now i have the iso and no cd-rom
 it would be great if i could boot into linux with a floppy then do a hdd-install command and point the iso on the win partition and from there the install would go niceley

---

### Post by fiveseven on 2006-11-07
> **subzero79 said:**
> There are only 3 boot installer images: cdrom, hd-media and netboot.

if hd-media if what you are looking here it is.

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current//images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current//images/hd-media/)

Also from my first reply, try considering VMware if you are using windows.

BTW: There is a lot of people complaining always because of their lack of CD drive, searching for different methods for install (PXE, netinstall, hd-boot, etc), now you have a CD drive but you don't want to burn a CD. Come on a CD is like what....25 cents?. Maybe use a cd-rw.8)

Thanks this is what i was after :) 

Its not about the money for me, im using a DP965LT motherboard with an ICH8 southbridge that doesnt support IDE. So there is some 3rd party IDE chip connected to the southbridge, and to cut a long story short many linux kernels cant see my IDE drives, including almost all versions without the "all-generic-ide" driver compiled in.

This is why i cant install linux from cd-media :(

---

### Post by subzero79 on 2006-11-07
> **loclei said:**
> it's not the money i had a cd-rom but i didn't have the iso then 

then i had the iso but it was the wrong one

now i have the iso and no cd-rom
 it would be great if i could boot into linux with a floppy then do a hdd-install command and point the iso on the win partition and from there the install would go niceley

Believe me it would be very nice. So why don't you download the alternate cd image and try an hd-media boot. For what i said earlier i believe it didn't work use i was using the normal cd, that comes with livecd. Once the installer starts try looking for options to search images on the hard drive (i think, i am not sure that the image has to be in partition with ext3 FS). Otherwise i would recomend you a net install, but i believe you don't have enough bandwidth.

---

### Post by loclei on 2006-11-07
i've been searching on the net and i think that an alternate way to do this hdd-install would be from a floppy with lilo.. made with fdutils

what can you say about this solution?
----------------------------------------
and i can't understand why there isn't a floppy image to boot from and perform a hdd install

---

### Post by subzero79 on 2006-11-07
I started to use linux about a year ago, i never saw lilo (because is very old) i always used grub. Also i never used floppies with linux (i hate floppies, i use a pendrive) the last time i used a floppy was installing a nforce raid driver for windows (i still can't believe we have to do it with a floppy). So i can't extend more my help. I will search for more available info.

PD: do you have a pendrive, you can make it bootable if your mobo supports it, if that helps.

---

### Post by loclei on 2006-11-08
see that's the problem  i don't have a pen drive neither a mobo that supports booting from usb i think

i have a KT6V-LSR msi mobo
one floppy drive
512mb ddr 3200
ati radeon 9000 proII 128mb
druon 1300
------------------------------
why i'm trying to install linux is because i want to be able to play wow and counter-strike from linux so i can delete my windows

---

### Post by subzero79 on 2006-11-08
You have to check your bios or your MB manual for usb boot. If it has an integrated NIC it  probably supports PXE boot, that means you can boot from an image running a tftp server on another computer atached to the network. That's another option.

---

