---
title: "Chromebook - Bootable USB Stick"
date: 2015-12-14
forum: Installation &amp; Upgrades
---

### Post by wamjones99 on 2015-12-14
So I'm going to begin by saying that I know this is a really noob question. I've been trying to create a bootable usb stick to install linux on my chromebook. I started out with unetbootin which creates unbootable drives, so I tried using dd, which corrupts the kernel and outputs something similar to:
```

1431620+0 records in
1431620+0 records out
732989440 bytes (733 MB) copied, 166.231 s, 4.4 MB/s


```
Lastly I tried using the Startup Disk Creator included with Ubuntu, which crashes once it tries to load the bootloader. The computer that I'm trying to install doesn't have a disc drive, but I did try an external one, but that doesn't work.

---

### Post by sudodus on 2015-12-14
Did you check with md5sum, that the download was good (that the downloaded iso file contrains what it is supposed to contain). See this link

[UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

***Unetbootin*** is a good tool and works most of the time. ***dd*** is a powerful tool and is probably able to do the job for you. But it does what you tell it to do without questions, even if you tell it to wipe your family pictures. [mkusb](https://help.ubuntu.com/community/mkusb) wraps a safety belt around dd.

But there are other problems and questions. You need a suitable linux distro and version for the chromebook even if you succeed in making a good boot drive.

- Which linux distro and version are you trying to install?
- Please specify the hardware in your chromebook!

I have no chromebook. I think you get the best help from someone who has installed Ubuntu (or some other linux distro) into such a computer ...

---

### Post by Bucky Ball on 2015-12-14
*Thread moved to **Installation & Upgrades**.*

Welcome. Launch Gparted, delete the partition on the USB, write a new partition table (this bit not essential), create a FAT32 partition, try UNetbootin again.

And as suggested by sudodus: Be VERY careful with dd. It has no mercy if you get things wrong. :| ... and Chromebooks may have particular quirks we aren't au fait with.

---

### Post by wamjones99 on 2015-12-15
So I used Parted to create a new partition table and fat32 partition then used unetbootin. I've tried ubuntu 15.10, Debian 8.2, Fedora, and Trisquel. I have a Debian box that also won't boot it, so I'm not sure that it's a hardware issue. But here is what The [Chromium Project]("http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/acer-c670-chromebook") says.

---

### Post by sudodus on 2015-12-15
I added 'Chromebook' to the title, and hope it will attract people with experience of Chromebooks

---

### Post by Bucky Ball on 2015-12-15
When you say you tried it but it won't work, do you mean you can select to boot from the USB and it doesn't? What actually happens then?

Or do you mean you can't boot from USB at all?

I just [found this]("http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/acer-c720-chromebook#TOC-USB-Boot"). Top of the page, 'USB Boot'. Maybe you need to get into developer mode to boot the USB. Might be irrelevant but never know. ;)

---

### Post by westie457 on 2015-12-15
@ wamjones99
Is there any files on the Chromebook you do not want to lose? If so back them up to either a cloud service: eg - Google Drive or to a usb device.
Enabling 'Developer Mode' wipes all personal information from the device and to all intents and purposes is **unrecoverable**
To boot a Chromebook into anything other than the installed version of ChromeOS, Developer Mode must be enabled.

I recently had to try usb booting on a Samsung Chromebook, after lots of reading and googling found these ideas.
[http://chromeos-cr48.blogspot.co.uk/](http://chromeos-cr48.blogspot.co.uk/)
[http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/](http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/)

On the Chromebook I was working with only the second posted link worked.

Which ever method works for you will be good however the device must always be run in Developer Mode.

Turning Developer Mode off is like performing a factory reset - that is back to how it came from the manufacturer.

If not already stated **back-up your files** and **_back-up the whole drive_** just in case you do something silly like wipe out ChromeOS.

---

### Post by SeventhGear on 2015-12-15
Not sure if this will work for you, but I needed to flash my BIOS on my Acer C7 Chromebook to get Ubuntu installed. It has been about 2 years since I did this, so if you have questions I might be able to pick my brain and remember something else. I remember that all the options I tried to get anything to install all failed. I came across this site ([https://johnlewis.ie/custom-chromebook-firmware/rom-download/](https://johnlewis.ie/custom-chromebook-firmware/rom-download/)) and was able to use that to be able to boot directly to Ubuntu.

---

### Post by wamjones99 on 2015-12-15
Well I used John Lewis' scripts to flash my BIOS, and I had successfully installed Debian on the system. When I try booting a stick on several different computers, I get the same error message, something along the lines of No bootable Operating System.

---

### Post by sudodus on 2015-12-15
How did you create USB boot drive? Which tool did you use? Maybe it works better with another tool. See post #2.

---

### Post by SeventhGear on 2015-12-15
After I flashed that BIOS I didn't have any issues getting the OS installed. I would check your boot disk. I used LiLi USB Boot Creator from a Win7 machine. I have also had luck with just dd'ing the ISO to the USB from other Linux machines.

---

### Post by TheFu on 2015-12-15
There are specific requirements to boot any OS on a chromebook. These are specific to the hardware. Usually there are instructions available for how to do this ... I have a C720 and found the steps over on the Arch forums to be sufficient. First I had to enter developer mode then enable "legacy boot" inside ChromeOS.  I think the chromeOS steps are identical regardless of the hardware, but don't really know.

After enabling legacy boot, I wiped ChromeOS completely from the system, swapped in a much larger m.2 SSD and loaded Ubuntu Server + openbox onto it.  Been running that way for 18 months until recently.

Warning - chromebooks don't have a separate CMOS battery, so if the main battery is allowed to run down or is disconnected, all the developer mode and legacy boot information will be gone. The only way I know to get that back is with ChromeOS, so it is best to keep the original SSD around and to practice reloading ChromeOS a few times before loading Linux. 1 or 2 years later when you need it, that memory will have faded, so take good notes specific to your system and your needs.  Wish I would have.  Right now, I either have a brick or a failed LCD display. Need to hook it up to an external display tomorrow to check that out.

As for making a bootable ChromeOS.  Google made a specific tool for that. Use it if you can.  [https://support.google.com/chromebook/answer/1080595?hl=en](https://support.google.com/chromebook/answer/1080595?hl=en)  In the end, it downloads the latest, correct, image for your specific chromebook, then uses dd to shove it onto either USB or SDHC card.  It overwrites everything - so having a fat32 isn't needed.  Not all USB flash drives are compatible with every USB port on every computer for booting.  Wish I could say more.  Cheap or expensive flash devices doesn't seem to matter. I've had both work and both fail on different systems.  I guess it comes down to the exact compatibility with the USB chips on the computer.  I've had better luck with USB2 ports for booting, than with USB3 ports.  Try a different port - you might get lucky.

If you don't see a "missing OS" warning after boot, then the display may be broken.  Hook up an external monitor and see what you can see.
Are there any beeps?  Mine beeped twice for a few days at boot. Now it doesn't beep at all. Looked up what 2 beeps meant for my hardware - no OS found.

Plus don't forget the magic keyboard stuff to boot off recovery media - on mine it is ESC+Refresh+Power.  YMMV.

If you need/want specific help, please post the exact model of the chromebook. That is the most important data we are missing.

---

### Post by wamjones99 on 2015-12-16
I've used Unetbootin, dd, and Start up disk creator to make the boot drive. [Here]("http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/acer-c670-chromebook") is my Chromebook. I don't believe that it's a hardware issue on the chromebook side, I think that the problem is with my main computer not writing the iso correctly.

---

### Post by sudodus on 2015-12-16
If you use dd correctly, it makes a working USB boot drive. ***Cloning with dd is very reliable when done correctly*** (***but risky***, because dd does what you tell it to do without questions. If you tell it to wipe your family pictures ..., and it is only a minor typing error away).

---

### Post by wamjones99 on 2015-12-16
So I would assume that I've been doing something wrong then. I had kinda figured since I've been using dd for a while, but now it's not working and giving me the message I've posted before:
```

1431620+0 records in
1431620+0 records out
732989440 bytes (733 MB) copied, 166.231 s, 4.4 MB/s

```

This is what I type:

```

sudo dd if=/Documents/ubuntu.iso of=/dev/sdb

```
Now I check to make sure that the path to the flash drive is correct.

---

### Post by Bucky Ball on 2015-12-16
Try with your target set to be a partition, the FAT32 partition, not the whole disk (sdb). :) So, make sure the FAT32 partition you created is sdb1 then:

```

sudo dd if=/Documents/ubuntu.iso of=**/dev/sdb1**
```

I didn't think dd required a partition pre dd-ing, but worth a try. Strange UNetbootin didn't work, though, as that should have found the FAT32 partition on the USB and used that. :-k

---

### Post by sudodus on 2015-12-16
It is obvious if you get the input file (if=...) wrong.

The size copied indicates that you have cloned Lubuntu. If it is an Ubuntu iso file, the downloading was interrupted before it had finished, because it should be bigger (except Ubuntu 12.04 LTS, but the size does not match exactly, which it should).

It is detrimental if you get the output file wrong. But if you have one internal drive and only one external drive, I think it is correct to use what you use, 

of=/dev/sdb

There should be no partition number (after b).

If the pendrive does not boot, something else is wrong,

- either the iso file does not fit for the computer,
- or there was a downloading error, this is probably the case, check with ***md5sum*** according to this link: [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
- or the pendrive does not work with the computer (electronically, hardware or firmware)
- or you have not found out how to boot this computer from a USB pendrive.

You can test if the pendrive can boot another computer.

***Edit:*** All partitions on the target drive should be **un**mounted.

---

### Post by sudodus on 2015-12-16
> **Bucky Ball said:**
> Try with your target set to be a partition, the FAT32 partition, not the whole disk (sdb). :) So, make sure the FAT32 partition you created is sdb1 then:

```

sudo dd if=/Documents/ubuntu.iso of=**/dev/sdb1**
```

I didn't think dd required a partition pre dd-ing, but worth a try. Strange UNetbootin didn't work, though, as that should have found the FAT32 partition on the USB and used that. :-k

No Bucky, that won't work. dd should clone to the device, not to a partition.

---

### Post by Bucky Ball on 2015-12-16
> **sudodus said:**
> No Bucky, that won't work. dd should clone to the device, not to a partition.

Cheers. What I was thinking and just remembering from when I've used it. Chucked it in there. :)

---

### Post by wamjones99 on 2015-12-16
This is what I have:

```

will@will-ThinkPad-T530:~$ sudo dd if=./Downloads/ubuntu-15.10-desktop-amd64.iso of=/dev/sdb1
[sudo] password for will:
1431620+0 records in
1431620+0 records out
732989440 bytes (733 MB) copied, 165.393 s, 4.4 MB/s
will@will-ThinkPad-T530:~$ 

```

---

### Post by sudodus on 2015-12-16
```
$ ls -l ubuntu-15.10-desktop-amd64.iso
-rw-r--r-- 1 sudodus sudodus 1178386432 nov 25 20:32 ubuntu-15.10-desktop-amd64.iso
```

Your download was not complete. That iso file should be bigger. Please download it again, or use torrent, which is more reliable. Anyway, please check the md5sum after you have downloaded it again.

```
$ md5sum ubuntu-15.10-desktop-amd64.iso
ece816e12f97018fa3d4974b5fd27337  ubuntu-15.10-desktop-amd64.iso
```

---

### Post by sudodus on 2015-12-16
> **wamjones99 said:**
> This is what I have:

```

will@will-ThinkPad-T530:~$ sudo dd if=./Downloads/ubuntu-15.10-desktop-amd64.iso of=/dev/sdb1
[sudo] password for will:
1431620+0 records in
1431620+0 records out
732989440 bytes (733 MB) copied, 165.393 s, 4.4 MB/s
will@will-ThinkPad-T530:~$ 

```

When you have a good iso file, please use

```

will@will-ThinkPad-T530:~$ sudo dd if=./Downloads/ubuntu-15.10-desktop-amd64.iso of=/dev/sdb

```

***Edit:*** or use [mkusb](https://help.ubuntu.com/community/mkusb) to wrap security around dd.

---

