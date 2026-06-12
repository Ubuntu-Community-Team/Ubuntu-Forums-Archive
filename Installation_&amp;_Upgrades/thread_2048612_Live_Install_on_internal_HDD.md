---
title: "Live Install on internal HDD"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by Finnius on 2012-08-27
I know how to install a live ubuntu on a USB flashdrive using various tools in windows and ubuntu.

However i want to install a live version of ubuntu on the internal hdd of my laptop, which is a ssd.

Any way to do this? Would be nice if ubuntu's "Startup Disk Creator" could do it, but it only looks like it will let you make bootable OS installs on USB devices...

Any help, or a point in the right direction would be much appreciated.

Cheers :)

---

### Post by Futant on 2012-08-27
I thought 'live' meant run off a cd or usb stick? You can [make a cd]("http://www.ubuntu.com/download/desktop") and run Ubuntu live from that, or from a usb, or you can install it, but then you are not running it live...

---

### Post by Finnius on 2012-08-27
Yep thats what live usually means. But i want to run it live off a internal ssd hdd.
Any ideas? I cant install it because my hdd is not big enough.

Thanks

---

### Post by mparillo on 2012-08-27
> **Finnius said:**
> I know how to install a live ubuntu on a USB flashdrive using various tools in windows and ubuntu.

However i want to install a live version of ubuntu on the internal hdd of my laptop, which is a ssd.

Any way to do this? Would be nice if ubuntu's "Startup Disk Creator" could do it, but it only looks like it will let you make bootable OS installs on USB devices...

Any help, or a point in the right direction would be much appreciated.

Cheers :)
I think you are looking for a Frugal Install:
[http://sourceforge.net/apps/trac/unetbootin/wiki/installmodes](http://sourceforge.net/apps/trac/unetbootin/wiki/installmodes)

---

### Post by Finnius on 2012-08-27
Hey,

Thanks for the info. I already use unetbootin. 
The problem is, it is not on my laptop as there is no windows OS. 
I cant remove the hdd as it is a mini-pci ssd hdd i think.

EDIT: Is there some type of portable unetbootin that is usb bootable? Or is this asking too much!

---

### Post by C.S.Cameron on 2012-08-27
I run my EEE from a frugal install.
I installed to flash drive using UNetbootin, (I prefer the opening screen to usb-creator).
Then I cloned the system from the flash drive to the internal drive using dd.

---

### Post by Cheesemill on 2012-08-27
You could always boot from a Live CD and install unetbootin, then download the .iso and use unetbootin to install this onto your HD.

---

### Post by mparillo on 2012-08-27
> **Cheesemill said:**
> You could always boot from a Live CD and install unetbootin, then download the .iso and use unetbootin to install this onto your HD.

Be careful: When you download the .iso, it will default to your filesystem which is stored in RAM. I have frozen my live USB sessions doing something like this.

---

### Post by Futant on 2012-08-27
Hooray for learning new things :D

---

### Post by Finnius on 2012-08-27
Thanks for the help.

I like the sound of Cheesemill's idea to run a live usb, then get unetbootin, however instead of downloading the .iso - i should be able to just have the .iso on another flashdrive and point unetbootin to it?

> Hooray for learning new things :grin:

Thanks to all you guys! I will try this ASAP.

---

### Post by Cheesemill on 2012-08-27
> **Finnius said:**
> I like the sound of Cheesemill's idea to run a live usb, then get unetbootin, however instead of downloading the .iso - i should be able to just have the .iso on another flashdrive and point unetbootin to it?
Yep.

---

### Post by oldfred on 2012-08-29
You can just use grub to loop mount the ISO. That is how I do all my Desktop installs. I originally used flash drives but now just have ISOs on hard drive. I normally put as many ISO on one flash drive as it holds, but you can use persistence also.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

---

### Post by Finnius on 2012-08-30
I have put Unetbootin on a live ubuntu usb system.
However when i go to 'select disk image' unetbootin cant see my flashdrive.
The only drive visible is the internal HDD! 

Any ideas?

Thanks

---

### Post by Finnius on 2012-08-30
Ok, solved the flashdrive problem.

However the live usb seems to be using the internal hdd for swap and when i unmount it, it freezes...

I need to unmount the internal hdd so i can repartition it and do the live install on it.

Any thoughts?

EDIT: Got those problems sorted, and have formatted the internal ssd as FAT32. However unetbootin cannot see the drive. Under 'Hard Disk' in unetbootin it has a drive called "/". I think that is the system drive on the usb flashdrive isn't it?

So the problem now is that i cant use unetbootin to install to the internal hdd... as it cant see it!

---

### Post by C.S.Cameron on 2012-08-31
> **Finnius said:**
> Ok, solved the flashdrive problem.

However the live usb seems to be using the internal hdd for swap and when i unmount it, it freezes...

I need to unmount the internal hdd so i can repartition it and do the live install on it.

Any thoughts?

EDIT: Got those problems sorted, and have formatted the internal ssd as FAT32. However unetbootin cannot see the drive. Under 'Hard Disk' in unetbootin it has a drive called "/". I think that is the system drive on the usb flashdrive isn't it?

So the problem now is that i cant use unetbootin to install to the internal hdd... as it cant see it!

When booted from the flash drive look in filesystem/cdrom.

---

### Post by Finnius on 2012-09-01
> **C.S.Cameron said:**
> I run my EEE from a frugal install.
I installed to flash drive using UNetbootin, (I prefer the opening screen to usb-creator).
Then I cloned the system from the flash drive to the internal drive using dd.

Yup. This is the best solution for me and my eee PC.
Thanks for the advice!

And wow isn't the boot time of ubuntu on an internal ssd FAST!


:guitar:

---

