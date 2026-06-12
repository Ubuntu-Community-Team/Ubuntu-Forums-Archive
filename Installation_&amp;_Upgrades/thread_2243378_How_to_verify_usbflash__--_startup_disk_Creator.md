---
title: "How to verify usbflash  -- startup disk Creator"
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by sara5 on 2014-09-08
[h=2][/h][h=3][/h][h=2]I used "startup disk Creator" and created a bootable USB stick (ubuntu-13.10-desktop-i386)[/h][h=2]How to verify my usbflash ?  (md5sum and sha256sum)[/h]

md5sum for livedvd (ubuntu-13.10-desktop-i386)  :  d0508f909c2c71d96aeac5efb0329b33
AND 
 
sha256  livedvd (ubuntu-13.10-desktop-i386)  :

a7f7fcb03e5323a3619b84218c935dd9e54a348ee6ebd55748d81886a3272171

---

### Post by yancek on 2014-09-08
If you are checking from a Linux system, open a terminal and change to the directory in which the iso file exists and run the command:  md5sum ubuntu-13.10-desktop-i386

You need to have the exact name of the iso file.  shasum, see the link below.

[http://askubuntu.com/questions/61826/how-do-i-check-the-sha1-hash-of-a-file](http://askubuntu.com/questions/61826/how-do-i-check-the-sha1-hash-of-a-file)

---

### Post by tgalati4 on 2014-09-08
Besides just checking the md5sum, when you boot the stick, you will have an option to check the media.  Run this and any errors will be noted.  This checks individual file md5sums against a master list.  This also verifies  the entire, written USB stick and will give you confidence that the install will happen properly.

---

### Post by kansasnoob on 2014-09-08
> **sara5 said:**
> [h=2][/h][h=3][/h][h=2]I used "startup disk Creator" and created a bootable USB stick (ubuntu-13.10-desktop-i386)[/h][h=2]How to verify my usbflash ?  (md5sum and sha256sum)[/h]

md5sum for livedvd (ubuntu-13.10-desktop-i386)  :  d0508f909c2c71d96aeac5efb0329b33
AND 
 
sha256  livedvd (ubuntu-13.10-desktop-i386)  :

a7f7fcb03e5323a3619b84218c935dd9e54a348ee6ebd55748d81886a3272171

You don't want to install 13.10 because it's already EOL:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You'd be better off using Trusty.

---

### Post by nerdtron on 2014-09-08
> **tgalati4 said:**
> Besides just checking the md5sum, when you boot the stick, you will have an option to check the media.  Run this and any errors will be noted.  This checks individual file md5sums against a master list.  This also verifies  the entire, written USB stick and will give you confidence that the install will happen properly.

This is one also a must. Sometimes (well most times) I have a good copy of ISO but every time I install the server version of Ubuntu using a live USB, it always fails. Then I ran the check media for defects on the boot screen of the installer, it cam up with an error. Problem was solved after formatting the usb drive and re-creating the startup disk.

---

### Post by tgalati4 on 2014-09-08
There are several steps in the installation process that can go wrong.  You need to mindful of all of them.

---

### Post by sara5 on 2014-09-08
> **tgalati4 said:**
> Besides just checking the md5sum, when you boot the stick, you will have an option to check the media.  Run this and any errors will be noted.  This checks individual file md5sums against a master list.  This also verifies  the entire, written USB stick and will give you confidence that the install will happen properly.

this option   check cd for defects for verify Burnt files but i  want  verify  md5sum( and sha256sum) for usb    ( Made with startup disk Creator).


sha256sum /dev/cdrom
a7f7fcb03e5323a3619b84218c935dd9e54a348ee6ebd55748d81886a3272171

But

sha256sum /dev/sdb

c2e0faef3fe8db053f405b2c910c0a9093333161296e6c8e9e12f9933333f405b2


Why are not  equal  ?

---

### Post by uRock on 2014-09-08
> **kansasnoob said:**
> You don't want to install 13.10 because it's already EOL:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You'd be better off using Trusty.

This!

---

### Post by sara5 on 2014-09-08
> **sara5 said:**
> this option   check cd for defects for verify Burnt files but i  want  verify  md5sum( and sha256sum) for usb    ( Made with startup disk Creator).


sha256sum /dev/cdrom
a7f7fcb03e5323a3619b84218c935dd9e54a348ee6ebd55748d81886a3272171

But

sha256sum /dev/sdb

c2e0faef3fe8db053f405b2c910c0a9093333161296e6c8e9e12f9933333f405b2


Why are not  equal  ?


????

---

### Post by uRock on 2014-09-08
You MD5SUMed a whole drive. It is not going to match a CD ROM.

On the DVD it sees 101010101110
On the USB it sees 101010101110000000000000000000000000000000000000000000000000000000000000000000000 Plus any alterations that USB Creator does to make the USB file system bootable.

---

### Post by sudodus on 2014-09-11
Please tell us what is your main problem!

Can you boot your computer from the USB drive?

- In that case you can run the check as described by tgalati4 in post #3. In the menu starting with 'Try Ubuntu' there is a line, which you select to check that the files are correct in the drive.

- Otherwise you must focus on

. copying/cloning/flashing to the USB drive
. booting (that the computer really boots from the USB drive)

And please tell us about your computer, at least the following items

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier to give relevant help.

-o-

See also the following links (and links from them)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by sara5 on 2014-09-14
> **uRock said:**
> You MD5SUMed a whole drive. It is not going to match a CD ROM.

On the DVD it sees 101010101110
On the USB it sees 101010101110000000000000000000000000000000000000000000000000000000000000000000000 Plus any alterations that USB Creator does to make the USB file system bootable.

Is there any way to equality ?   :(   [COLOR=#ff0000]By any method [/COLOR]

---

### Post by sara5 on 2014-09-14
> **sudodus said:**
> 
Can you boot your computer from the USB drive?

yes . BIOS has the capability

> **sudodus said:**
> 
copying/cloning/flashing to the USB drive
. booting (that the computer really boots from the USB drive)


How to do this?

> **sudodus said:**
> 
Please tell us what is your main problem!


I want  : sha256sum ubuntu live in cdrom = sha256sum ubuntu live in my usbflash

Is there any way to equality ? [COLOR=#ff0000]By any method [/COLOR]

---

### Post by sudodus on 2014-09-14
Why is it so important to get the sha256sum ubuntu live in cdrom = sha256sum ubuntu live in my usbflash?

- Are you thinking about security issues, that some 'man in the middle' might have done something to the iso file? In that case it is enough to check the iso file, you need not check the installed system in a CD/DVD disk or USB pendrive.

- Do you want to check the success of the copying/cloning/flashing to the USB drive? Unless there is an obvious and serious problem with the USB pendrive, this operation will be successful. The success rate is much higher than for burning an iso to a CD/DVD disk, and most of us never bother to check it. We just try to boot the computer from the USB pendrive.

If there is a problem to boot, it almost always depends on something else.

1. The iso file is bad - can be checked with md5sum, shasum ...

2. The pendrive is bad (physically bad, 'bricked')

3. The pendrive is ill-formatted (bad partition table or bad file system) - important if the installation is made with Unetbootin or the Ubuntu Startup Disk Creator and similar tools. These tools like a partition with the FAT32 file system. mkusb needs no partition or file system, it comes with the flashing.

4. The computer cannot boot from USB - the settings in the UEFI/BIOS menus must be tweaked. This can be the most difficult part in some computers, and in some cases chainloading is necessary - but you seem confident that it is not a problem for you. Please explain: Can you boot other operating systems from USB?

5. The computer actually boots from the USB pendrive, but it does not work properly, gets stuck or goes to a black screen or another colour screen - this is usually due to a problem with a driver. Drivers are the interface between the linux kernel and the hardware. Often these things work automatically, but some hardware are not recognized properly, and the booting process gets stuck. The cooperation with a graphics chip or a wifi chip is often causing such problems.

-o-

And please get a supported version of Ubuntu. Trying to get Ubuntu 13.10 to work is like going along a dead-end street.

---

### Post by sudodus on 2014-09-14
> **sara5 said:**
> [QUOTE=sudodus;13119696]
Can you boot your computer from the USB drive?

yes . BIOS has the capability
[/QUOTE]
This is good. But how do you know? Can you boot from a USB drive with another operating system?
> 
> **sudodus said:**
> 
copying/cloning/flashing to the USB drive
. booting (that the computer really boots from the USB drive)


How to do this?

I think ***Unetbootin*** will help you do the trick (for supported versions of linux operating systems). You can install Unetbootin for Windows as well as for Ubuntu and other linux operating systems. So you can make a pendrive bootable with Ubuntu from Windows using Unetbootin - this is the starting step for many beginners.

See this link [Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")
> 

> **sudodus said:**
> 
Please tell us what is your main problem!


I want  : sha256sum ubuntu live in cdrom = sha256sum ubuntu live in my usbflash

Is there any way to equality ? [COLOR=#ff0000]By any method [/COLOR]

As explained by *uRock*, it is not easy, and probably not relevant at all, so I repeat: I don't understand why you want it because I don't think that you really need it.

---

