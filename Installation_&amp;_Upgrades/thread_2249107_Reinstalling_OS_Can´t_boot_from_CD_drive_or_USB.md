---
title: "Reinstalling OS: Can´t boot from CD drive or USB"
date: 2014-10-19
forum: Installation &amp; Upgrades
---

### Post by v.d on 2014-10-19
Hi,

Quick info:
[LIST]
[*]Laptop: Pavilion 15
[*]Newly upgraded ubuntu 14.04 LTS (didnt go so well and alot of things are not working properly)
[*]Trying to install Win7 for gaming reasons, to have ubuntu either as dual-Os or virtualized
[*]Cant get it to boot from CD (tried 2 diffrent Win7 CDs and one Ubuntu 12.04 CD)
[*]Cant get it to boot from USB (made a Win7 boot/install USB)
[/LIST]

Im trying to format my laptop but it ignores the boot order no matter if i set CD or USB first, I cant seem to get it to boot from either. Since i upgraded to 14.04 i had trouble with a couple of things not working, one of the things is that i cant watch movies anymore. Reinstalling VLC didnt work. My plan was to install Win7 as host OS and then reinstall the latest ubuntu either in dual-boot or through virtualbox but first thing first.

Im alittle bit worried it has something to do with the laptop because i got my stationary (thats running Win7) to boot from the CD, i dont understand why my laptop won´t.

Anyone got a tip on what to try next? Can i present any other info to make it easier for you?

---

### Post by v.d on 2014-10-19
The boot options i have available is:
OS Boot Manager
Internal CD/DVD ROM Drive
USB diskette on key/USB Hard Disk
USB CD/DVD Drive
! Network Adapter

And as i  said earlier, i tried putting both CD and USB as the top priority one.

---

### Post by Bas_Kooijman on 2014-10-19
On HP just click the ESC button during boot, choose F9 for Boot devices and chose your CD / USB with Windows ISO on it.

---

### Post by oldfred on 2014-10-20
Is system UEFI and you are trying to install Windows 7 in BIOS mode?
There are ways to convert Windows 7 DVD to flash drive and make it boot in UEFI mode.
How you boot installer UEFI or BIOS is how it installs.
But Windows only boots from gpt partitioned drives with UEFI.
Both Windows & Ubuntu only boot from MBR(msdos) with BIOS, but then Windows must be installed to a primary partition formatted NTFS with the boot flag.
Post this:
sudo parted -l

---

### Post by v.d on 2014-11-02
Hi, thanks for the answer!

Ok, i wasnt aware of that. I have only made one or two bootable sticks before and just did it "the old" way. Havent had much time working on it the last week but id like to get it done this week. Going to read through the link you gave me and see if anything there helps and get back to you as soon as i can.

This is what i got from the command, cant make much out of it though:

victor@JD:~$ sudo parted -l
[sudo] password for victor: 
Model: ATA WDC WD7500BPVT-6 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  99.6MB  98.6MB  fat32                 boot
 2      99.6MB  742GB   742GB   ext4                  msftdata
 3      742GB   750GB   8476MB  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

---

### Post by oldfred on 2014-11-02
Your sr0 is the CD or DVD drive. It of course is read only so error does not matter.

       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

Windows does not correctly see Linux partitions, so you have to either partition in advance or make room.
      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[URL="http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition"]http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition

      [/URL]
 [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

    [URL="http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition"]
[/URL]

---

### Post by v.d on 2014-11-03
I have read through the links but it didnt help. Iw tried to boot from both CD and USB stick but no matter how i config the bios it just starts ubuntu anyways. What the f* am i doing wrong?

---

### Post by v.d on 2014-11-03
Whats the easiest way to upload som pics for you to see? So i can show BIOS and bootorder

---

### Post by oldfred on 2014-11-03
If you have screen shots or shrink large photos you can easily attach them, forum has limits on sizes. Do not post in line. 
If you use the advanced editor, you can use the paperclip icon to attach photos. 
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

But I do not know Windows issues. Last version I installed was XP in 2006. 
Your installer does have to be bootable. How are you creating bootable installer. You cannot just copy files to it.

---

### Post by v.d on 2014-11-15
Hi guys! Sorry for late reply.

[SIZE=5]ISSUE FIXED

[SIZE=2]I reinstalled the stick, altough i was using a program last time i musthave done something wrong. I redid the bootable USB and went through the process from the start. Not sure what program i used last time, anyway this time i used rufus.

Thanks for the tips!
[/SIZE]
[/SIZE]

---

