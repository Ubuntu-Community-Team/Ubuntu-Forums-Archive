---
title: "Suggestions for USB flash drive install?"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by andycivil on 2012-12-04
I installed Lubuntu on a USB stick with some success, but I frequently run into bus errors or I/O errors, and I can't shut down because 'sudo' is not found. I'm thinking that I should have followed instructions which were specifically designed for a flash drive. I have 8Gb RAM so I should be doing everything in RAM and only writing changes on shutdown (CasperFS???). Can someone suggest to me, some instructions that are reliable and will result in a suitable install? This must have been done already... thanks!

---

### Post by 2F4U on 2012-12-04
The "official" instructions on how to create a bootable USB stick with persistence option are here:

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

The persistence option allows you to store personal settings and other data on the drive.

---

### Post by Rex Bouwense on 2012-12-04
Try looking here.  It is installation to a 4 Gb flash drive but 8 Gb is better.
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

---

### Post by oldfred on 2012-12-04
How large is flash drive? If 8GB or more you can do a full install, otherwise persistence as posted above.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by andycivil on 2012-12-04
Thanks for the answers, the one Rex posted seems almost identical to what I actually did - the only difference is that I wanted NO swap (if it runs out of RAM then I'd rather it failed than start swapping out to the USB stick). I tried two different sticks, an 8Gb and a 16Gb, I got the same result both times: it did work, but frequently I'd come back to find that it had crashed with I/O errors or Bus Errors. (Visible by pressing ctrl-alt-F4 and watching a terminal.)

I'll try that "persistent" option posted, and see if that works better. Thanks!

I'll label this "solved", I don't know that yet, but I want to stall more solutions until I've tried out the ones you guys have given me...

---

### Post by andycivil on 2012-12-12
I'm having to mark this as not solved again, because it didn't work, and I'm lost. The computer "bert" boots from the Lubuntu installation I made previously (the subject of this thread: [http://ubuntuforums.org/showthread.php?t=2079739](http://ubuntuforums.org/showthread.php?t=2079739) ) but it will not boot from the 16GB drive which I had PenDriveLinux put Lubuntu on yesterday. The error is simply "boot error", nothing more. I don't even get the boot menu. However, this 16GB drive will successfully boot a different computer (Turtwig). I can also see that the drive is bootable, and seems to have all the right things on it.

I don' t know how to approach this, because I feel that the computer (Bert) is ok, because it will boot from my older stick, however, I also feel that PenDriveLinux should be ok, because I can boot Turtwig from it.

I do feel that PenDriveLinux is my solution, because Turtwig was working well, faster than Bert with the old version, despite that Bert is 4x faster computer than Turtwig is.

Any ideas how to approach this?

---

### Post by kurt18947 on 2012-12-12
Re "Boot error" and nothing else.  I find that whenever I create a FAT32 partition with gparted one one machine.  The problem machine is a Gigabyte MB with AMD785 chipset.  The same LiveUSB plugged into an older AMD desktop or Thinkpad laptop boots fine.  If I first format the USB drive in Windows - even quick format works - then create the LiveUSB, it boots fine on all machines.  I researched the problem and it seems certain modular BIOSes use boot code written by Microsoft.  The "boot error" problem shows up on boards with those BIOSes when used booting a LiveUSB.  That might be something to try.

---

### Post by C.S.Cameron on 2012-12-12
I have found that Startup Disk Creator, (usb-creator), works best for me, when making persistent flash drives.
Others suggest UNetbootin is best.
A lot of people have problems with Universal, (Pendrivelinux).

It is also possible to make a persistent drive that boots the original iso.

One note:

DO NOT TRY TO UPDATE THE DRIVE USING UPDATE MANAGER.

It will quickly fill the max 4GB of persistence space and the drive will then not boot.

---

