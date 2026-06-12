---
title: "Installing 11.04 server via USBstick"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by willywilly on 2011-05-05
I'm trying to install Ubuntu 11.04 x64 Server onto a Shuttle XS35GT. The PC has no CD-ROM drive so I have to install via USB.

1. Copy the files to a USB-stick via UNetbootin (WinXP, OSX) or Universal-USB-Installer.exe (WinXP)
2. Boot to the USB-stick in order to install Ubuntu
3. The installer halts at "[!!] Detect and mount CD-ROM" - "Your installation CD-ROM couldn't be mounted. Try again to mount the CD-ROM? (Yes/No)"
4. Selecting either option does not help further the install

What I tried:
- Manually fix truncated filenames in /pool/l/linux/*.udeb (see [http://ubuntuforums.org/showthread.php?t=1503083](http://ubuntuforums.org/showthread.php?t=1503083) )
- Alt+F2, mount the .iso as a virtual CD-ROM under /media/iso (no use since the 11.04 installer does not allow manual chosing of the CD-ROM) (see [http://ubuntuforums.org/showthread.php?t=1550317](http://ubuntuforums.org/showthread.php?t=1550317) )
- Expert mode install (does not show anything special) (as suggested at [http://ubuntuforums.org/showthread.php?t=1737345](http://ubuntuforums.org/showthread.php?t=1737345) )

PS: I had this exact same problem with 10.10 but someone was able to lend me a USB-CD-Drive that time.

---

### Post by willywilly on 2011-05-06
So installing Ubuntu server via USB is not actually possible?

I filed this as a bug [https://bugs.launchpad.net/ubuntu/+bug/778319](https://bugs.launchpad.net/ubuntu/+bug/778319) and am giving up on Ubuntu for now.

---

### Post by LarsVinter on 2011-05-17
> **willywilly said:**
> I'm trying to install Ubuntu 11.04 x64 Server...

3. The installer halts at "[!!] Detect and mount CD-ROM" - "Your installation CD-ROM couldn't be mounted. Try again to mount the CD-ROM? (Yes/No)"


I have the same issue. I was able to solve it the following way:

1) Copy the server-iso file to another usb stick
2) Insert that usb stick into the new box
3) ALT+F2 to another console and:
4) Mount the usb-stick to /mnt/usb:
     a) mkdir /mnt/usb
     b) mount -t vfat /dev/<your_usb_device> /mnt/usb
5) Mount the server-image file to /cdrom
     a) mount -t iso9660 -o loop /mnt/usb/ubuntu-11.04-server-amd64.iso /cdrom
6) exit from the terminal and ALT+F1 back to main installer screen
7) Press ESC to avoid trying to mount cd-rom
8) In main installer menu chose "Detect and mount CD-rom"

This time it will actually detect your USB stick as the CD-rom.

It works for me now and I was able to install the server fully.

Lars
5

---

### Post by spin-dizzy on 2011-07-27
Slightly quicker way, works for me on 11.04, created by unetbootin:

1. When you get the error, Alt-F2 to a second console.
2. Find out which device your USB stick is (tail -n 100 /var/log/syslog)
3. Then mount it to /cdrom (mount -t vfat /dev/sd[abcd] /cdrom
4. Alt-F1 to get back to the install console, and try detecting again

It saves needing the extra USB drive.

---

### Post by divot_powell on 2011-08-18
Hi all,

I've just had a very similar issue with this when using the alternate install disk. I tried the other options here, but believe it or not the solution was even more simple. I changed which port the usb install disk was inserted into, and hey presto problem solved. I moved it to a slot that was on a completely seperate bus, so I suspect the issue is with ubuntu's support of the usb controller. It's fine while the bios is emulating things, but the moment ubuntu tries to take over it could no longer actually see my stick. It didn't even show up anywhere in /dev/sd*.

I might just be lucky here.

Cheers.

---

### Post by m1losh on 2011-10-05
I had the similar problem with ubuntu 10.04 and I managed to solve it using documentation from ubuntu site. There is an issue described 
"If you get "Incorrect CD-ROM
detected" error on detection stage,
reboot, press F6 and then ESC to go
to manual boot line editing, and
add the option 'cdrom-detect/try-
usb=true'."
 so I did similar thing but at the start of installation. On the main screen I pressed TAB button and added the line from the citation and instalation worked just fine. I hope that someone will find this usefull.

---

### Post by Zealhybrid on 2012-01-02
> **spin-dizzy said:**
> Slightly quicker way, works for me on 11.04, created by unetbootin:

1. When you get the error, Alt-F2 to a second console.
2. Find out which device your USB stick is (tail -n 100 /var/log/syslog)
3. Then mount it to /cdrom (mount -t vfat /dev/sd[abcd] /cdrom
4. Alt-F1 to get back to the install console, and try detecting again

It saves needing the extra USB drive.
Thanks a lot! :D

---

### Post by selectiverepo on 2012-01-14
Thanks for the mounting tip.

This is how I found mine and verified that it was working:
$ ls /cdrom
$ dmesg | grep SCSI
Block Layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
sd 0:0:0:0 [sda] Attached SCSI disk
sd 2:0:0:0 [sdb] Attached SCSI removable disk

$ mount -t vfat /dev/sdb /cdrom
$ ls /cdrom
boot      dists     md5sum.txt     pool     README.diskdefines     Uni-USB-Installer-Copying.txt
cdromupgrade   doc      ldlinux.sys      pics      preseed      syslinux   Uni-USB-Installer-Readme.txt

---

### Post by m3ld4r10n on 2012-02-19
> **m1losh said:**
> I had the similar problem with ubuntu 10.04 and I managed to solve it using documentation from ubuntu site. There is an issue described 
"If you get "Incorrect CD-ROM
detected" error on detection stage,
reboot, press F6 and then ESC to go
to manual boot line editing, and
add the option 'cdrom-detect/try-
usb=true'."
 so I did similar thing but at the start of installation. On the main screen I pressed TAB button and added the line from the citation and instalation worked just fine. I hope that someone will find this usefull.


^ works

---

### Post by vdawork on 2012-12-02
thanks alot!!!!

> **spin-dizzy said:**
> Slightly quicker way, works for me on 11.04, created by unetbootin:

1. When you get the error, Alt-F2 to a second console.
2. Find out which device your USB stick is (tail -n 100 /var/log/syslog)
3. Then mount it to /cdrom (mount -t vfat /dev/sd[abcd] /cdrom
4. Alt-F1 to get back to the install console, and try detecting again

It saves needing the extra USB drive.

---

### Post by howefield on 2012-12-02
Old thread closed.

---

