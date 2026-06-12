---
title: "Cannot boot Ubuntu Studio live USB"
date: 2015-07-20
forum: Installation &amp; Upgrades
---

### Post by SepLite on 2015-07-20
Please move this thread if it is post under the wrong category, thanks!.

Yesterday, I downloaded the Ubuntu Studio iso from their official website(very slow download speed, took more than a few hours). I installed it onto a usb drive using UNetBootIn, however when I tried to boot from it in UEFI, it says that it can't find "/casper/vmlinuz", however when looking at the files from the computer, /casper/vmlinuz does exist(without the .efi extension posted in many of the threads when I googled the error). I did a sha1 checksum of the iso, and it matches one of the sums listed on the Ubuntu Studio website. Can anyone help?

Update: Booting from legacy gives me a command line and two errors, posted in the picture below.

Booting in legacy mode
[ATTACH=CONFIG]263300[/ATTACH]

vmlinuz from another computer, no .efi extension
[ATTACH=CONFIG]263302[/ATTACH]

booting in UEFI, cannot find /casper/vmlinuz
[ATTACH=CONFIG]263301[/ATTACH]

---

### Post by sudodus on 2015-07-21
Please tell us which version of Ubuntu Studio that you have downloaded! I would recommend the version 14.04.1 LTS with long time support unless you have some (new) hardware, that needs a newer version. I guess that you are trying the 64-bit version, since you started installing in UEFI mode.

Anyway, when I know which iso file you have downloaded, I can try it (try with some tools).

Before knowing more about it, I would suggest that you try to install/copy/flash the iso file into a USB pendrive with another tool. Unetbootin is usually working, but sometimes you have better luck with another tool. I would recommend ***mkusb***.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

OK, I'm prejudiced, because I made it, but honestly, it has a high success rate :-)

See the following link for more details.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by SepLite on 2015-07-21
I used 14.04.2 64 bit download listed on [https://ubuntustudio.org/download/](https://ubuntustudio.org/download/). I tried using mkusb, however I had my drive partitioned, one of the partitions for data(although not anymore), but when I ran mkusb, it tried to install it on the entire drive and corrupted it :(. I reformatted the drive using GParted(without the unnecessary double partitions), and I am now trying the installation again.

---

### Post by sudodus on 2015-07-21
Yes, mkusb will 'use the whole drive', actually only the head end (size of the iso file), but the rest of the drive is not available. But it does not corrupt it, instead it simply clones the ISO 9660 file system, which works from CD/DVD disks, and also from USB drives. After using the pendrive like that, you need to make a new partition table and file system, if you want to use it for another purpose.

Did you try to boot from the pendrive, or did you give up without trying, when you did not recognize the file system?

---

### Post by SepLite on 2015-07-21
I just tried it now and it works! Sorry about that, I'm still kinda new to this kind of stuff, I've used ubuntu for less than a year, and it was also my first venture into booting from disks, file systems, partitions, etc... Thanks for the help!

---

### Post by sudodus on 2015-07-21
I've downloaded ubuntustudio-14.04.2-dvd-amd64.iso and flashed it to a USB pendrive using mkusb.

I selected language and after that 'Try Ubuntu Studio without installing' (and pressed the Enter key)

After maybe half a minute I arrived at the desktop, where I can try various commands and tools. If things work well enough for you too, you can double-click on the desktop icon for 'Install Ubuntu Studio 14.04...' and start installing.

-o-

I think there is a glitch with (your version of) Unetbootin, so that the vmlinuz file is not found.

---

### Post by sudodus on 2015-07-21
> **SepLite said:**
> I just tried it now and it works! Sorry about that, I'm still kinda new to this kind of stuff, I've used ubuntu for less than a year, and it was also my first venture into booting from disks, file systems, partitions, etc... Thanks for the help!

Congratulations :KS

You are welcome with other questions, if you have any. It is best to create a new thread for a new question, at least if it is not related to the old one. Make a good descriptive title in order to attract the people who are interested in and know about your problem.

---

