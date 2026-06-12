---
title: "/dev/cdrom not found on install of 10.04.1 LTS from CD"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by jboris on 2011-01-03
Sorry if this question has been posed on the forum but I have searched using a ton of variants. I have an HP DL 180 G5. I am trying to install Ubunto Server 10.04.1 LTS 64 bit from iso I downloaded and bruned to a DVD.
 
I already installed the Desktop version by accident (Sorry just didn't see the server version available) so I downloaded the Server iso and burned the DVD. The installer starts just fine and asks me all of the questions. The HP has 3 RAID-1 volumes with the Desktop Version installed on the first RAID volume. I want to start from scratch and start over with the Server version.
 
As I said the installer starts fine, asks me Language and keybard but when it tries to load the files from the CD it fails saying it can't detect the drive. I then tried the manual part and that doesn't work either. I know under the desktop it mounted the CD at /dev/sr0. The DVD drive is a PATA interface.
 
The installer wants to look at /dev/cdrom but for some reason it doesn't find it and set it.
 
Can anyone point me to a way to get this accomplished? I figured mabye I have to use a USB so I downloaded the USB installer but that wants to install the server to the USB stick which I didn't want to do.
 
Thanks in advance.

---

### Post by jboris on 2011-01-03
I thought I solved the problem. I booted the system to the desktop version that was on my first RAID volume and then downloaded usb-creater. Copied the server iso to my directory and then created the usb version using the Create startup disk option in System->Adminitration. 
 
Well when it said remove the media and reboot I did that (I took out the usb drive) and when it went to reboot the screen just had a blinking cursor. It stayed that way for 5 minutes. I then put the usb drive back in and heard a beep and then it started up. So I guess the boot system was installed to the usb disk instead of the first RAID volume.
 
 
Back to the drawing board.
 
##############
Solved. Hit F6 at main install screen and selected options that caused the installer to search the entire SCSI and ATA bus for CD.

---

