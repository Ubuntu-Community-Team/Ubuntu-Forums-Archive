---
title: "Unable to install Ubuntu Server 14.04.1"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by marcelo14 on 2014-11-23
I've been trying to install Ubuntu Server to a Dell Notebook, since it has no CD Drive, I'm forced to use an SD card (more on that later), I can boot from the SD card, but when it comes to detect the CD, it finds no CD:

[COLOR=#000000][FONT=monospace]There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD-ROM.[/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]Failed to copy file from CD-ROM. Retry?
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR]I've tried multiple solution I've found here, and askubuntu.com but none of them have worked.


Here's a recollection of the things I've tried:
[COLOR=#000000][FONT=monospace]
[/FONT][/COLOR]> 
[COLOR=#000000]1. When you get the error, Alt-F2 to a second console.[/COLOR]
[COLOR=#000000]2. Find out which device your USB stick is (tail -n 100 /var/log/syslog)[/COLOR]
[COLOR=#000000]3. Then mount it to /cdrom (mount -t vfat /dev/sd[abcd] /cdrom[/COLOR]
[COLOR=#000000]4. Alt-F1 to get back to the install console, and try detecting again[/COLOR][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR] 
This gives me the error:

mounting /dev/sdb on /cdrom failed: No such file or directory

I'm sure the SD card is /dev/sdb, so I'm not sure what's causing this problem.

> [COLOR=#000000]I had the similar problem with ubuntu 10.04 and I managed to solve it using documentation from ubuntu site. There is an issue described [/COLOR]
[COLOR=#000000]"If you get "Incorrect CD-ROM [/COLOR][COLOR=#000000]detected" error on detection stage, [/COLOR][COLOR=#000000]reboot, press F6 and then ESC to go [/COLOR][COLOR=#000000]to manual boot line editing, and [/COLOR][COLOR=#000000]add the option 'cdrom-detect/try-[/COLOR][COLOR=#000000]usb=true'." [/COLOR][COLOR=#000000]so I did similar thing but at the start of installation. On the main screen I pressed TAB button and added the line from the citation and instalation worked just fine. I hope that someone will find this useful.[/COLOR]

This gives me the error:

Could not find kernel image: cdrom-detect/try-usb=true

> Check [http://cirrus.ucsd.edu/~pierce/fix_ubuntu_usb/](http://cirrus.ucsd.edu/~pierce/fix_ubuntu_usb/).
There is a script that fixes truncated names in the USB.

Essentially, what this script does is to rename the files that were longer than 64 characters, and were then truncated by the CD-ROM's name size limit. (Two, UDEB files that were .UDE files)

This was suggested on another thread (renaming the .UDE files to .UDEB) which I can't find as of now.

Also, for some reason my computer is giving an error when I try to use USB drives:

An operating system wasn't found. Try disconnecting any drives that don't containg an operating system.
Press Ctrl + Alt + Delete 

I've tried them on all my USB ports, but I keep getting the same error..

I really need some help. Thanks!

PS: I used UnetBootin to make the USBs/SD bootable.

---

### Post by Gerry_Duprey on 2015-05-08
The problem was that the ISO image isn't designed to be used with unnetbootin or the USB creator tools.  Instead, a direct dd to the USB device is all you need.

 [h=1]dd if=ubuntu-14.04.2-server-amd64.iso of=/dev/sdb bs=16M[/h][COLOR=#111111][FONT=Ubuntu](obviously, replace /dev/sdb with your USB key, but don't use any partitions (i.e. don't use /dev/sdb1, /dev/sdb2, etc -- just the whole device)[/FONT][/COLOR]

---

