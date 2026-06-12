---
title: "Trying to get started"
date: 2015-06-27
forum: Installation &amp; Upgrades
---

### Post by steve207 on 2015-06-27
I am new to ubuntu. This is what I have done so far. I downloaded ubuntu onto a second drive, then unzipped and installed to drive. When I reboot, computer prompt me to chose an operating system. I chose ubuntu. Then I am asked which product, where I chose xubuntu. It starts to load then I get a list where I see some error messages and the installation fails. I have to admit the my computer is old. I am running a pentium3. I would like to try ubuntu. I am so tired of windows. I took some screen shots of the error messages and will try to attach them if possible. Hopefully someone can help me get ubuntu up and running.

Thanks

---

### Post by ubfan1 on 2015-06-27
Where did you download from?  "...unzipped???? ...select a product?????"  Does not sound like a standard iso file download, burn image to install media, and install to disk.  You do look like you have a disk problem though.

---

### Post by robhad on 2015-06-27
It's best to download the iso file from the official source. The zip file sounds dubious. Second, how did you install it to a drive? Did you use YUMI or the Universal USB Installer?

---

### Post by sudodus on 2015-06-28
Welcome to the Ubuntu Forums :-)

Yes, your computer is old. With a Pentium 3 CPU you must use the flavour of Ubuntu with the lightest foot-print, Lubuntu. There will still be difficulties if there is less than 512 MB RAM. So please tell us more about your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card

and it will be possible to give you better advice.

Until then, please read the following links.
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

If you can burn a DVD-rom and boot from it, you can [download Lubuntu 14.04.2 LTS]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS").

If you have can only burn a CD disk (not a DVD), I suggest that you get the ***alternate*** 32-bit iso file, which fits into a CD disk. The alternate ISO is also better if you have less than 512 MB RAM.

[download Lubuntu 14.04.1 LTS alternate ISO file]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO/14.04.1")

---

### Post by steven_scott on 2015-06-28
I downloaded from what seemed to be the official Ubuntu site. If you have the correct link please send it. I tried to install directly to one hdd then moved files to the hdd I want to use the used the wubi icon to install

---

### Post by steven_scott on 2015-06-28
The computer is a compaq deskpro x86 with 512 memory and a Rage Fury Pro/Xpert graphics card.
I was trying to load directly from a slave drive instead of  from a DVD or CD.
Can that be done? If so do I have to partition the C:/ drive that I want to use first?

---

### Post by RobGoss on 2015-06-28
Hello and welcome, There's no unzipping needed it's a ISO file and needs to be burned to a DVD or USB drive, Your computer looks very old

---

### Post by steven_scott on 2015-06-28
Ok, so I have to grab a blank DVD. How big of a USB should I have and since my computer is old is lubuntu a better option. And I am already running xp so there's no way to use an installer instead of DVD or USB?

---

### Post by sudodus on 2015-06-28
> **steven_scott said:**
> I downloaded from what seemed to be the official Ubuntu site. If you have the correct link please send it. I tried to install directly to one hdd then moved files to the hdd I want to use the used the wubi icon to install

[Please avoid wubi. It is no longer supported]("http://ubuntuforums.org/showthread.php?t=2229766"). Test running from the CD (or a USB pendrive if you can boot from USB). And then you make a real installation.

1. I suggest that you save your personal files (documents, pictures, video clips ... maybe also mailbox files), because installing an operating system is risky.

2. Decide if you want to keep Windows XP. You can use it off-line to play Windows games, but avoid connecting to the internet, because there is no support, not even security updates.

3. Install Lubuntu. Yes, Lubuntu should be working in your computer. The CPU is old and slow, but works with Lubuntu. You can enough RAM and I have a Rage grahics card, that works with Lubuntu :-)

If you want more details, and want to know what to expect from this computer, please read the following thread, the first and last posts
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

[General tips, that may help if you come here and your computer is around ten years old (or older)]("http://ubuntuforums.org/showthread.php?t=2130640&page=7&p=13311591#post13311591")

---

### Post by sudodus on 2015-06-28
> **steven_scott said:**
> Ok, so I have to grab a blank DVD. How big of a USB should I have and since my computer is old is lubuntu a better option. And I am already running xp so there's no way to use an installer instead of DVD or USB?

The Lubuntu 14.04.2 32-bit iso file is exactly at the limit to fit in a standard CD disk (703 Mibibytes).

Notice that you should not create a data CD and copy the iso file to the CD. Instead you should ***burn the iso image***. The result should be that you can see several files and directories if you mount the CD. If you see only one file, the iso file, you used the wrong method.

And it works with a DVD disk, and a USB pendrive with at least 1 GB too. If the computer won't boot directly from USB, you can get a Plop boot manager.

You boot the computer with ***Plop***, and select  USB (in complicated cases via alt + u). Plop can boot from floppy disk,  CD/DVD or HDD and from there start a driver for the USB system. I used a  Plop CD and it could help boot via USB in 2 of 3 old computers that I  tested. The one where Plop did not work has an Athlon XP CPU and nVidia  graphics and can boot directly from USB. This link describes the Plop  boot managers.

[http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)[URL="http://www.plop.at/en/bootmanagers.html"]
[/URL]

*Edit:* 'An installer'

- The program to burn the iso image in an installer.

- There are several installers to create USB boot drives. See the following link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

- and the CD/DVD/USB drive will contain a whole operating system that runs live, and in turn contains an installer, that can install Lubuntu into your hard disk drive. That installer will give you the option to use the whole drive (and overwrite Windows), or to borrow some space from the Windows partition (if it is not full), and create a dual boot system, that can run both Lubuntu and Windows.

---

### Post by steven_scott on 2015-06-28
Okay. Right now I do not have a blank DVD or suitable usb. (mine is only 1gb) I have been thinking about clone drive software such as Daemon tools or virtual clone drive. Could that be an option?

---

### Post by sudodus on 2015-06-28
I know of Daemon tools but I don't think that they work during booting. I know  of many alternatives, when you have linux running, but it is tricky the  first time, that you want to go from Windows to linux. You make things complicated if you select a non-standard method the very first time you do it.

If you live near a place where you can buy CD disks, that is the  best alternative. Don't buy one, but at least a pack with five CD or DVD  disks in case you might burn it the wrong way the first time. It can be standard 700 MB CD-R disks. If you can't burn in your CD drive, go to a friend and borrow the computer to burn the Lubuntu iso image to a disk.

The Lubuntu iso files are smaller than 1 GB, so a 1 GB USB pendrive should work without problems. From Windows you can use the method with Win32 Disk Imager according to this link

[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

You can also try ***Unetbootin***.

It is worth trying, but you may still need a CD with ***Plop*** to boot from, if the computer does not want to boot from USB directly.

If you have a ***second hard disk drive***, that you can connect internally and boot from, that is also an alternative. 

If you have a ***second computer***, or can borrow a desktop computer, which is a few years newer and can boot from USB, then you can connect the hard disk drive from the pentium 3 computer to the newer computer and install Lubuntu, and after that move the hard disk drive back to this computer with pentium 3. In that case you should ***avoid*** installing any extra drivers or other programs before moving the drive back.

---

### Post by RobGoss on 2015-06-28
> **steven_scott said:**
> Ok, so I have to grab a blank DVD. How big of a USB should I have and since my computer is old is lubuntu a better option. And I am already running xp so there's no way to use an installer instead of DVD or USB?


Here is break down of distrubtion files sizes

[COLOR=#111111][FONT=Ubuntu]**13.10:**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ubuntu 13.10 - Desktop X86-64 = 883 MB[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ubuntu 13.10 - Desktop X86-32 = 895 MB[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ubuntu 13.10 - Server X86-64 = 672 MB[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ubuntu 13.10 - Server X86-32 = 658 MB[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Lubuntu 13.10 - Desktop X86-64 = 702 MB
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**12.04:**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ubuntu 12.04 - Desktop X86-64 = 698 MB[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ubuntu 12.04 - Desktop X86-32 = 701 MB[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ubuntu 12.04.3 - Server X86-64 = 665 MB[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ubuntu 12.04.3 - Server X86-32 = 648 MB[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Lubuntu 12.04 - Desktop X86-64 = 697 MB[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Kubuntu 12.04.3 - Desktop X86-64 = 707 MB[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Xubuntu 12.04.3 - Desktop X86-64 = 712 MB
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**14.04:**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ubuntu 14.04 - Desktop DAILYBUILD-JAN-21-2014 X86-64 = 912 MB

As you can see the ISO files do not require much space to burn the file to the USB thumb drive, it's always a good thing to have more space on the drive is case you might want to add something else.[/FONT][/COLOR]

---

