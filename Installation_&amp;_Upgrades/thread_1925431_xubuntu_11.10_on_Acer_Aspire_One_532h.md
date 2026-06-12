---
title: "xubuntu 11.10 on Acer Aspire One 532h"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by 10nw21 on 2012-02-14
Hi all,
I am new to the linux/ubuntu world, and I am looking to ditch the clunky windows 7 Starter on my netbook, which is an Acer Aspire One 532h. It has an Intel Atom N450 CPU, which wikipedia leads me to believe is based on 64-bit architecture and uses (U)EFI, specifically the InsydeH2O version. The netbook has no disc drive, and I don't want to buy a drive just to install ubuntu. 

I am trying to put xubuntu 11.10 on here, and having no luck. I tried using both LiLi and Pendrive to make a bootable USB flash, and I set the BIOS ( or whatever the term for that is ) to boot from USB. When I start up the computer, the screen flashes a line of text saying something about syslinux, goes green for a second, and then all I see is a flashing underscore in the corner and nothing happens. 

The netbook has three options to boot from USB: USB HDD, USB CD-ROM, and USB FDD. Process of elimination tells me that it is booting the flash drive as an FDD. 

I have tried compiling the boot drive with both 32-bit and 64-bit xubuntu with no luck; it wont ever boot. 

I tried searching for how to install ubuntu on an EFI system, but I am still confused as to why it wont boot on my netbook. I really need to get it ready to go by Friday, so all help is appreciated!

Thanks!

---

### Post by Mark Phelps on 2012-02-15
I had a similar situation when I made a bootable USB with Ubuntu 12.04 Alpha 1 -- and the PC refused to boot into a desktop.

So, having made the USB using unetbootin, I remade it using Pendrive.  And this time, it booted.

Then recently, I did the same thing again using 12.04 Alpha 2, and this time, unetbooting made the working USB, and the Pendrive version failed.

So, it looks like the "bootable USB installer" stuff is very hit-and-miss.

---

### Post by cortman on 2012-02-15
Since you're installing on a netbook, may I recommend Lubuntu as an alternative to standard Ubuntu? I never was much a fan of Lubuntu or LXDE, until I installed it on a friend's netbook, which I've been using for the past month or so, and I am extremely impressed. It runs really fast and smooth on the (rather) low-spec hardware, is modern and intuitive, and really works good with the small screen. I used Lili USB creator to make a bootable flash drive in Windows, and it booted and installed flawlessly the first time.

---

### Post by 10nw21 on 2012-02-15
After a conversation with a friend who has a similar netbook to mine, I decided to run xubuntu over lubuntu because he expressed a rather fervent dislike of the interface. 

I *believe* I solved my problem. Since my netbook doesn't have a disc drive and the BIOS/EFI thing is weird, I pulled the HDD from it. It was a SATA drive which I knew I could use in my desktop, so I used Windows to burn the 64-bit .iso to a CD. I then pulled the side panel off of my desktop and hooked up the netbook hdd to the mobo and PSU, and disconnected the other hard drives to leave only the netbook HDD and the DVD-RW drive on the MOBO. 

I then proceeded to boot from the CD, and installed xubuntu onto the netbook HDD smoothly. 

When I reconnected the HDD to the netbook, it fired right up into xubuntu, saw my WiFi network, and when connected, proceeded to download like 200mb of updates. 

I have played with it for a day now, and I have only had one issue; when I go to play Runescape (don't judge, we all have our vices :P), the java applet loads the login screen, but then crashes when I try to start the game. It does this in both FF and Chromium. I am working on getting it all straightened out, as it is definitely a software issue.

---

### Post by OldAndTired on 2012-03-16
This thread is flagged as SOLVED.  I'm not too sure about that.  If the solution is to disassemble your PC and plug various parts into various computers and then attempt to reassemble the parts, I'm not sure I'm up to it.  

There seem to be two types of "install Ubuntu on AAO 532h" threads.  The first is "I installed Ubuntu and love it" and the other is "when I attempt to install Ubuntu I get a message on the screen from the BIOS and it just sits there".

I wish one of the successes would go through in painful detail how they did it.

FYI I've tried both unetbootin and Pendrive without success.

---

