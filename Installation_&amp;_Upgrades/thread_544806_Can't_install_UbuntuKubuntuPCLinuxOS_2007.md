---
title: "Can't install Ubuntu/Kubuntu/PCLinuxOS 2007"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by DownTown22 on 2007-09-06
I'm currently having big problems trying to install Ubuntu....or Kubuntu or PCLinuxOS2007.

While using the LiveCD, I get his error message (this also happens when I try Kubuntu 7.04 and PCLinuxOS2007):

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
(initramfs)_

And when I use the Alternate Install CD (Ubuntu 7.04), my DVD drive(s) aren't recognized and won't mount.

I currently have WindowsXP installed and want to install Ubuntu 7.04.  The LiveCD worked with no problems on another laptop (Toshiba Satellite A100)

My hardware is as follows:
CPU: Intel Core 2 Duo E4400 @ 2.0GHz
Motherboard: ASUS P5K SE with Intel P35 chipset
Video Card: EVGA 8500 GT - 256Mb (PCI-e)
RAM: 2x1.0Gb OCZ DDR2 800Mhz
HDD: Seagate 160Gb
DVD 1: LG Super Multi Write (GSA-4167B)
DVD 2: LG DVD-ROM (GDR8163B)
Floopy: Ultra 3.5" Floppy/Media Card Reader

Any help would be greatly appreciated!

---

### Post by DownTown22 on 2007-09-06
As much help as possible would be great as I won't be back home to try any of the suggestions for at least 3 weeks.

Thanks in advance!

---

### Post by Pumalite on 2007-09-06
[http://ubuntuforums.org/archive/index.php/t-470786.html](http://ubuntuforums.org/archive/index.php/t-470786.html)

[http://ubuntuforums.org/showthread.php?t=459459&page=5](http://ubuntuforums.org/showthread.php?t=459459&page=5)

[http://bbs.archlinux.org/viewtopic.php?pid=276755](http://bbs.archlinux.org/viewtopic.php?pid=276755)

---

### Post by DownTown22 on 2007-09-08
Will check those out..thanks!

Anybody else have any other suggestions?  Maybe why the DVD drive(s) won't mount with the alternate install disc?

---

### Post by Pumalite on 2007-09-08
Latest off the line:

UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.


f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!
__________________

---

### Post by rileyrg on 2007-09-08
Just to be sure here : this is supposed to fix the cd rom not mounting on the asus p5k SE mobo?

---

### Post by Pumalite on 2007-09-08
This for people that is trying to boot or install from Live CD and get confronted at the end with the message: 'can't access tty; job control turned off'

---

### Post by DownTown22 on 2007-09-08
Thanks Pumalite!

Hopefully this works next time I'm at my computer.  You wouldn't happen to know anything about the DVD-drive not mounting with the Alternate Install disc would you?

---

### Post by Pumalite on 2007-09-08
I have fixed this problem in the past setting the DVD drive to 2nd master in the computer and to 'Auto' in BIOS

---

### Post by rileyrg on 2007-09-08
Just in case anyone can help:

I have an Asus P5K SE mobo. It uses a Marvell controller. I have an OPTIAC DVD RW AD-5170A DVD.

When I try to install I get "No CDRom found". When I tried the "break=top" fix, then I got prompt but was unable to type. Probably because of no USB driver loaded for the kbd?

Can anyone please help?

I have tried alternate CDs (Ubuntu and Kubuntu), etch-custom, pretty much anything I could find. This is proving to be very frustrating.

---

### Post by Zenham on 2007-09-10
> **rileyrg said:**
> Just in case anyone can help:

I have an Asus P5K SE mobo. It uses a Marvell controller. I have an OPTIAC DVD RW AD-5170A DVD.


Try using a SATA drive, according to those who've gotten installs to work on this mobo. I'm picking one up today myself.

---

### Post by Pumalite on 2007-09-10
A long shot for sure, but you might try going into your BIOS>IDE Configuration>Set to 'Enhanced Support for SATA+PATA'

---

### Post by Zenham on 2007-09-18
Please see the following post. There are multiple requirements, one of which will be either all IDE devices, or all SATA. Welcome to the bleeding edge!

[http://ubuntuforums.org/showpost.php?p=3372889&postcount=47]("http://ubuntuforums.org/showpost.php?p=3372889&postcount=47")

---

### Post by DownTown22 on 2007-09-18
Not so sure about that solution....both my drives (HDD and DVD) were set up as IDE to begin with and it didn't work.

---

### Post by Zenham on 2007-09-18
Right, but I bet you're using SATA configured as IDE, not a real IDE drive. Real, physical, 40-pin, old school, IDE.

---

### Post by Zenham on 2007-09-18
I've edited the other post for clarity. 

I am certain that this works, as I spent two days working on testing multiple configurations on my new motherboard. This one worked flawlessly while testing, and perfectly during the OS installs as well.

Now, my only remaining problem is the conflicting Nvidia kernel driver version issue... bah :)

---

### Post by DownTown22 on 2007-09-18
So, you're saying that I can't use an SATA HDD and an IDE DVD drive?  I either have to have an SATA HDD and DVD **or** an IDE HDD and DVD?

---

### Post by Zenham on 2007-09-18
Yes, precisely, unless you'd like to wait for an installer version that doesn't have this issue. You've just found yourself on the bleeding edge of technology with this chipset, and sometimes the bugs take a little while to become apparent.

But, with the current 7.04 installer, yes, you will need to have the same interface for your boot drive and the optical reader, to be able to install directly.

Of course, you might have success with devices on other interfaces, say, like a USB key or an external USB optical device. I'm just telling you what worked for me, and that was the only way to get it working with this new chipset on my motherboard (P5K WS) in two days worth of testing.

---

### Post by DownTown22 on 2007-09-18
Thanks a million!  Can't wait to get home to try all this out!

---

