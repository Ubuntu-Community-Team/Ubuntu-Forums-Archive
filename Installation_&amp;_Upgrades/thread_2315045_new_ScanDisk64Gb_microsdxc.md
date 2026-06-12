---
title: "new ScanDisk64Gb microsdxc"
date: 2016-02-25
forum: Installation &amp; Upgrades
---

### Post by Weatherlawyer on 2016-02-25
(Sorted, thanks.)

I have no idea what I need for this or how to put Ubuntu on it. I have an old laptop that will need 32 bit operating system I want to play the occasional DVD and have no idea which version to select. Nor how to go about it. I think it need a format, because I can't get anything else besides that one to even see it.

---

### Post by grahammechanical on 2016-02-25
Spam's off. Deary. :)

What is the question? Is it, What version of Ubuntu can I install on this old laptop? If that is the question then what are the hardware specifications? Especially the video adapter and the amount of video memory it has.

Is it, Can I install Ubuntu on a 64GB microsdxc memory card? I have no idea. Is it your purpose to fit this memory card into that old laptop and use it like a hard drive?

To install Ubuntu on any machine whatever the internal storage device we first need to download the ISO image and burn the ISO image to a DVD disc or a USB memory stick. Then we run the Ubuntu live session and from there we select Install Ubuntu and then allow the installer to install Ubuntu to the appropriate storage device.

Perhaps you want to install the Ubuntu ISO image on the 64GB microsdxc memory card and then install Ubuntu onto the laptop from the memory card. I am not sure what you want to do.

Regards

---

### Post by efflandt on 2016-02-25
SD (or microSDXC) cards larger than 32 GB use exFAT file system by default: [https://en.wikipedia.org/wiki/Secure_Digital#SDXC](https://en.wikipedia.org/wiki/Secure_Digital#SDXC)
To enable Linux to use exFAT see [http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04](http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04)

I know that my Android phone (Samsung S3) uses exFAT for its internal storage, but I have not worked with any memory devices with exFAT yet. So not sure if you could use Startup Disk Creator to put bootable live/install iso on it, but you could probably do a regular install to it using a Linux file system.

But do you have a USB memory card reader that works with SDXC? The built-in slot in a laptop is often a different type of block device that cannot be booted from (unless it is internally USB connected). And if the laptop cannot handle 64-bit, it might not even support SDHC, much less SDXC.

---

### Post by Weatherlawyer on 2016-02-26
I have no idea what I am doing with this thing but:

An error occurred while accessing '59.5 GiB Removable Media', the system responded: The requested operation has failed: Error mounting /dev/sdd1 at /run/media/michael/3134-3536: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdd1" "/run/media/michael/3134-3536"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat' 

Just a cheap investment gone wrong is it?

I tried it in my  Presario and it wanted to format the thing which frightened me off. Just tried it in an emachine from a similar era and it got the above.

I just wanted to be able to boot up an alternative OS in them, never having tried a USB before. I just thought it was time to move up from DVD installations. I am afraid it was a matter of monkey see monkey do. I had no idea about :
And if the laptop cannot handle 64-bit, it might not even support SDHC, much less SDXC.
at the time. I was actually looking for a larger than my usual USb pocket recorder that I carry to the local library anr etcetera just carrying homework around and I saw this thing so damn cheap and thought "Why not (clot!)". I had no need of it yet and thought I may as well do the other thing I wanted to try. So can I just pop it and drop it?

---

### Post by sudodus on 2016-02-26
Your only problem with the SDXC *might* be the *exfat* file system.

After backup of whatever files you have on the card, you need not be afraid of formatting it. If it fails because you can't write to it nothing happens. If it fails because it is not a useful partition table or file system, you can re-format it :-)

I can boot my computers from various SD cards in some adapters via USB, but not in other adapters. The electronics and firmware in the adapters are also important.

It is also very important for us to know about your computer in order to suggest a suitable version and flavour of Ubuntu. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It will also help us suggest tools and methods to make the computer boot from the selected version and flavour of Ubuntu.

---

### Post by Bucky Ball on 2016-02-26
You WILL have an issue with exFAT with the 64bit sdxc. I wouldn't be using one. You need to install these:

exfat-utils
exfat-fuse

That's it. No how-to or tutorial required. Just find them in the Software Centre and install them. Trouble is, I have no idea how you're going to do that if you can't boot to a live session because you can't get the ISO onto the sdxc card to boot to a live session.

I'd grab a 4Gb USB stick and make life easy, but again, as mentioned earlier, it is still fairly unclear what it is you're actually wanting to do. :-k

---

### Post by Weatherlawyer on 2016-02-26
Thanks all; eminently sensible advice. I bought a large external drive intending to load an operating system on it then got lazy and loaded too many files. I have some smaller simpler stuff I should play with, just clean them off first. And keep this thing for Sunday best.:)

---

### Post by Bucky Ball on 2016-02-26
Essentially, those 64Gb sdxc cards work best for video/audio recording. I'm using one for some work in a 1080p camera at the moment. :)

If you're happy, please see the first link in my signature. Enjoy! ;)

---

