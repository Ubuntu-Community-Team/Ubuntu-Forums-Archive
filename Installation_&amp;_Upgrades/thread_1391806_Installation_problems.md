---
title: "Installation problems"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by NardDawg on 2010-01-27
Hey!

So im new to this and so forth..
 
I have installed a clean install of Ubuntu 9.10 on my laptop and dualbooted with WinXP on the PC. (Had to install with wubi) I am very impressed naturally and decide to remove WinXP once and for all. 

WinXP was installed on the first partition on the first drive and ubuntu on the second partition. So I accidentally my whole MBR :P

I tried the whole day yesterday to fix grub2 and grub and tried to repair the xp bootloader but nothing worked.

So I finally decided to try to format and do a clean install.

**Tried the Live CD:**
It cant boot or install because it says
[I]"This kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU."[/I]

either that or it hangs

**Tried the Alternate Install CD:**
Everything works until it tries to install the base system.
I get an error saying that some files a corrupt
I have Burned 4 different discs on 2 different burners at high and low speed and the md5sum checks out ok! Weird!

I have a Penitum 4 HT 2.80ghz

Anyone have any ideas because im all out...
Worst case scenario I have to install XP again and install through wubi but I really dont want to dual boot. 

Well any help is greatly appreciated!!

---

### Post by Bartender on 2010-01-27
My first guess is that the optical drive on the PC you're trying to install to might be losing its tolerances.  We take for granted that our optical drives should "just work" without thinking too much about what they actually have to do, which is accurately read millions of miniscule transitions on the disc surface and translate those transitions to 0's and 1's.

Optical drives are relatively easy to move around.  Might want to try whichever drive you feel most confident about.

I would download a copy of GParted LiveCD (this can be done on any PC) and create a bootable CD.  Then format the drive to ext3 or ext4 before installing ubuntu.  Sometimes having the area pre-formatted makes a big difference.

Try spinning some of your CD's on another PC.  If you get errors, then there's something wrong with the CD, not the PC.  Did you use good-quality CD-R's, not RW?

---

### Post by NardDawg on 2010-01-27
Yeah now that say it I should try another Optical Drive.
Its very old and doesnt sound ok...im gonna try to borrow my room mates and ill get back to you..

im using pretty standard CD-R discs and i have tried one Ubuntu Remix DVD-R and had the same problem...must be the drive!!
thanks :)

any idea btw why i cant read live cds?
why does it say i have the x86-64 kernel when I downloaded the i386 release??

---

### Post by NardDawg on 2010-01-27
So I tried another optical drive and I got the same error again...
Just dont understand whats wrong...I´ve been spending 2 days with this now and nothing works!
Need help!!

---

### Post by darkod on 2010-01-27
The message about the kernel being x64 is strange, are you sure you downloaded i386? If you downloaded from torrent might there be an accidental mistake with the file name?

Also, I guess it's worth trying from bootable usb stick. If your internet allows it, I would download another i386 image directly from ubuntu (no torrents):
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Then find on google the free program unetbootin for creating bootable usb stick in windows. Run it as adminstrator (in vista and 7) and use the downloaded image. After it finishes ignore the message to reboot, just close unetbootin.
To get rid of the unetbootin menu and enable the standard ubuntu menu, open the stick and do:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the isolinux folder find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That enables the ubuntu menu.

---

### Post by NardDawg on 2010-01-27
Yeah the kernel thing is strange and Iam 100% that its not the release thats the problem because I checked the md5sum of the release to and it a perfect match...and I´ve checked and doublechecked that its the i386!

Im trying to get a hold of a memory stick but nobody has one when you really need it :/

I just partitioned the drive with ext4 using Gparted Live CD
Still doesnt work :(

---

### Post by darkod on 2010-01-27
> **NardDawg said:**
> Yeah the kernel thing is strange and Iam 100% that its not the release thats the problem because I checked the md5sum of the release to and it a perfect match...and I´ve checked and doublechecked that its the i386!

Im trying to get a hold of a memory stick but nobody has one when you really need it :/

I just partitioned the drive with ext4 using Gparted Live CD
Still doesnt work :(

Be careful when partitioning in advance. Linux doesn't just use the existing partitions as windows does. In fact, unless specifically told to use them, linux will ignore existing partitions as unavailable.

---

### Post by NardDawg on 2010-01-28
So have tried every possible sollution and nothing works...except for wubi >:(
I have tried different usb sticks and releases and still get the kernel error or it just hangs.
even tried downloading 9.04 and i get a kernel error there to..

I managed to install from wubi and move Ubuntu to its own partition, then i got cocky and formated the windows partition and tried to merge the two with a gparted boot cd....surprise surprise it couldnt boot anymore..

Is there anyway to force it to boot the kernel from the boot prompt?
or any other way?

---

