---
title: "Unable to install 10.10 or 10.04 on a Dell 1525 with a USB"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Mikhail.Inspired on 2010-10-13
I will say this now; I am still in high school, so forgive my stupidity. I am trying to install either 10.10 or 10.04 on a Dell 1525. It has no operating system on it, and the CD/DVD drive is nonexistent. I have tried to install 10.10 on it using a USB, with both UNetbootin and Pen Drive Linux. Using either one, both end up freezing at the "Preparing to Install" screen. When trying to install 10.04, it will not load, even after 24 hours. On the loading screen, I pressed F1 to view the terminal and got this output:

(process:352): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
Killed

I got all downloads from their home websites, [www.ubuntu.com](www.ubuntu.com), [www.pendrivelinux.com](www.pendrivelinux.com), and [www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net). I have spent all my spare time since the newest release trying to fix whatever problem there is, so does anyone know what I did wrong?

---

### Post by wilee-nilee on 2010-10-14
Look at the hard drive with gparted in menu-system-admin and see if maybe you need to set up the partition table. Click device-create partition table.

I would also download the ISO separately, and then use the thumb loader to install the ISO on the thumb. Make sure you also do a fresh format of the thumb as well to a fat type partition.

---

### Post by Mikhail.Inspired on 2010-10-14
The Dell I am trying to install on has no OS, and all other computers that I have access to are installed with Windows 7. :neutral:

---

### Post by wilee-nilee on 2010-10-14
> **Mikhail.Inspired said:**
> The Dell I am trying to install on has no OS, and all other computers that I have access to are installed with Windows 7. :neutral:

It sounded as though you could boot the live cd  with the thumb, that is where you would look at gparted to confirm there is a partition table, and build one if not.

Download the regular ISO to Windows then use unetbootin the latest version to load the thumb with the download. I have had simultaneous download and thumb loading go bad on several occasions.

---

### Post by Mikhail.Inspired on 2010-10-14
Thank you for your help. I will try it, and tell you if it works.

---

### Post by Mikhail.Inspired on 2010-10-14
It says that my hard drive is unallocated, but it also says that the drive has a msdos partition table.
I also downloaded the ISO separate from the bootloader.

---

### Post by wilee-nilee on 2010-10-14
> **Mikhail.Inspired said:**
> It says that my hard drive is unallocated, but it also says that the drive has a msdos partition table.
I also downloaded the ISO separate from the bootloader.

Not really sure where to go from here, I don't want to leave you hanging without a reply.

---

### Post by Mikhail.Inspired on 2010-10-14
It's alright. Someone's bound to have an answer. Thank you for your help, though. :D

---

### Post by mikewhatever on 2010-10-14
Check your .iso files for errors, and make sure Unetbooin and Universal USB istaller are the latest versions.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Mikhail.Inspired on 2010-10-14
Do you know if it is possible to use it for a USB? From what I saw in the article, you can only use it for a CD. If so, can you show me how?

---

### Post by tillerdemon on 2010-10-14
I would create a DBAN USB drive and nuke your hard drive this will remove the DOS partition. Installation should go smooth after that.

---

### Post by Mikhail.Inspired on 2010-10-14
Can you explain what you mean? :confused: And how to do it? I'm still only a freshman.

---

### Post by mikewhatever on 2010-10-14
> **Mikhail.Inspired said:**
> Do you know if it is possible to use it for a USB? From what I saw in the article, you can only use it for a CD. If so, can you show me how?

The iso file is the same for both cd and usb. I think the article is very clear on how to verify the file using Windows. There are also other operating systems and methods, but how are they relevant to you?
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

---

### Post by Mikhail.Inspired on 2010-10-14
Thank you for  verifying that.
[COLOR="Sienna"]EDIT: I checked the Wubi with MD5SUM, and it came up clean. I could not figure out how to check the entire usb.[/COLOR]

---

### Post by Ozitraveller on 2010-10-14
[http://www.md5summer.org/](http://www.md5summer.org/)

About MD5Summer
Windows MD5 Sum generator.

MD5summer is an application for Microsoft Windows 9x, NT, ME, 2000 and XP which generates and verifies md5 checksums.
Its output file is compatible with the output of the Linux GNU MD5Sum and it will also read Linux generated files.
It is released under the General Public License, the source can be downloaded from the downloads page (down the bottom).

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.howtoforge.com/easy-way-to-create-bootable-ubuntu-usb-pendrive](http://www.howtoforge.com/easy-way-to-create-bootable-ubuntu-usb-pendrive)
[http://helpdeskgeek.com/linux-tips/create-an-ubuntu-live-cd-on-a-usb-flash-drive/](http://helpdeskgeek.com/linux-tips/create-an-ubuntu-live-cd-on-a-usb-flash-drive/)

I hope these help :)

---

### Post by Mikhail.Inspired on 2010-10-14
> **Ozitraveller said:**
> [http://www.md5summer.org/](http://www.md5summer.org/)

About MD5Summer
Windows MD5 Sum generator.

MD5summer is an application for Microsoft Windows 9x, NT, ME, 2000 and XP which generates and verifies md5 checksums.
Its output file is compatible with the output of the Linux GNU MD5Sum and it will also read Linux generated files.
It is released under the General Public License, the source can be downloaded from the downloads page (down the bottom).

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.howtoforge.com/easy-way-to-create-bootable-ubuntu-usb-pendrive](http://www.howtoforge.com/easy-way-to-create-bootable-ubuntu-usb-pendrive)
[http://helpdeskgeek.com/linux-tips/create-an-ubuntu-live-cd-on-a-usb-flash-drive/](http://helpdeskgeek.com/linux-tips/create-an-ubuntu-live-cd-on-a-usb-flash-drive/)

I hope these help :)
Thank you.

---

### Post by oldfred on 2010-10-14
Your question on msdos (or MBR) partition table. This is the standard partition type used for PC since IBM started the PC. A newer partition type is now used by Macs and some windows servers called gpt.

MBR partitioning allows 4 primary partitions. One primary can be converted to an extended partition and as a container hold many logical partitions. The first install (and the bootable one) of windows has to be in a primary partition. Linux can be in a primary or in a logical as it does not care. Also some computers (BIOS) will not let you boot unless you have the windows boot flag on a primary partition, whether you are booting windows or not.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

[http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)

---

### Post by Mikhail.Inspired on 2010-10-14
In the end I used 2 USBs. I loaded one with Ubuntu 10.10 using Windows, and selected Try Ubuntu. Then, I downloaded another copy of the ISO using the the loaded "Try Ubuntu". I then used Ubuntu's Startup Disc Creator to make another one on a different USB. Booting from that one, I finally managed to finish the installation. I had also reset the partition table so that it used the gpt format (if that is the right word.). Thanks for all your help!

---

