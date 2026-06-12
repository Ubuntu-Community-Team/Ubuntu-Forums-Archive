---
title: "Is there a way to install Ubuntu from a Live CD via Terminal?"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by Cyberpawz on 2012-05-10
I am getting tired of the Live CD failing, I have tried 11 and 12, and it seems either I get bad media or the image is corrupt in some manner, I have gotten tired of this...

I am looking for a way to load the Live CD, download an ISO to a second partition, and install Ubuntu straight from that ISO via the terminal.  Is this possible?

---

### Post by wojox on 2012-05-10
[URL="https://help.ubuntu.com/community/Installation/MinimalCD"]Installation/MinimalCD
[/URL]

Put that on your Installation Medium of choice and try it out. :P

---

### Post by darkod on 2012-05-10
It's a bit strange not to be able to burn a good image.

If it gets corrupted during download, if the internet connection is so bad, installing in any way would be almost impossible because it will need to download packages over the net.

If on the other hand, this is only a result of your burner being bad, you can try making usb stick from the image for example.

---

### Post by sudodus on 2012-05-10
Hi Cyberpawz,

- Is this your first attempts with linux, or are you running an older version of Ubuntu or some other distro?

- Have you tested with md5sum, that the download was good?

- If the iso file is good, try Unetbootin to make a USB boot drive, if you have problems with boot CDs.

And if you post your hardware specs, cpu, ram and graphics chip or card, it will be easier to give you relevant tips.

Good luck :-)

---

### Post by oldfred on 2012-05-10
I do it from one hard drive to another using grub2's loopmount. I used to use the loopmount from flash where my system thought flash was another drive. I have had ISO & grub booting FAT & ext4 formats.

I think part of the issue is the new ISO are large and some software of CDs do not work with the oversize, although others do. I wrote a CD from my 12.04 - K3b and installed another 12.04 just to see how a CD works as I have not done it for ages and it just worked.

Hard drive:
Direct boot on hard drive - drs305:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)
Boot ISO from harddrive. To install it should have to be different partition or
sudo umount -lrf /isodevice

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by Cyberpawz on 2012-05-10
> **wojox said:**
> [URL="https://help.ubuntu.com/community/Installation/MinimalCD"]Installation/MinimalCD
[/URL]

Put that on your Installation Medium of choice and try it out. :P

Works perfectly, thanks.  I may start using this instead of the generic CDs... seems to install faster too.

---

### Post by Cyberpawz on 2012-05-10
> **sudodus said:**
> Hi Cyberpawz,

- Is this your first attempts with linux, or are you running an older version of Ubuntu or some other distro?

- Have you tested with md5sum, that the download was good?

- If the iso file is good, try Unetbootin to make a USB boot drive, if you have problems with boot CDs.

And if you post your hardware specs, cpu, ram and graphics chip or card, it will be easier to give you relevant tips.

Good luck :-)

I've been using Linux builds for a while, I am using the minimal CD only because it seems to work now. My computer can't boot from a USB stick, as much as I wish it could. 

Hopefully this will be solved soon... because I can't imagine I'm the only one having this issue.

---

### Post by sudodus on 2012-05-10
> **Cyberpawz said:**
> I've been using Linux builds for a while, I am using the minimal CD only because it seems to work now. My computer can't boot from a USB stick, as much as I wish it could. 

Hopefully this will be solved soon... because I can't imagine I'm the only one having this issue.
I think many people have problems because of poor hardware detection (often poor matching of the graphics chip or card). This is something that really needs to be improved in *ubuntu 12.04.

I'm glad it works for you with the minimal CD :-)

Are you sure, you cannot boot/install from a USB drive? Now that you have a working iso file (the minimal CD).

It might be worth looking at alternatives (in the bios menu). Sometimes a USB drive is regarded as a hard disk drive, and if you change the order of them (put the USB drive before the internal HDD), it will boot from USB. Maybe worth trying unless your computer is *very* old ;-)

Another option might be to boot from an eSATA drive (providing you have SATA ports on your motherboard or that you can and want to install a SATA/eSATA card). Or if you have only IDE: boot from a second IDE drive (mounted temporarily).

---

### Post by gunavara on 2012-05-10
I was about to start yet "another" installation-freezing-problem thread but i will give the minimal cd a try after viewing the posts you guys made. Will be back with a feedback (hopefully soon).

---

