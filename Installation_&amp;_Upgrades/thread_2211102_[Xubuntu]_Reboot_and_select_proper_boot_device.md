---
title: "[Xubuntu] Reboot and select proper boot device"
date: 2014-03-14
forum: Installation &amp; Upgrades
---

### Post by Xubuntist on 2014-03-14
I just had what is called a 6 o'clock in the morning magic moment after 24 hours of pain and grief.

I have an ageing customer with an ageing Windows XP MAXDATA PC*and I'm fast weaning most of my WinXP people over to Xubuntu, mainly because Xfce is nicer (IMHO) than Unity and it's nice and lean, and of course the customers are often won over by the fact that they can continue to get mileage from their ageing hardware and don't have to upgrade to Windows *xx* and/or buy a new PC. The well-publicised mess that is Windows h8 has made that task considerably easier.

[SIZE=1]* AMD Sempron 3200 1,8Ghz, 2Gb ram, 160Gb 5200 HDD, GeForce 6150 onboard [/SIZE]

After lugging around a CD case of installation and diagnostic discs for years, I now have a little wallet of USB flash drives, and I have one for Xubuntu 13.10 i386 Desktop and one for AMD64 Desktop install. Today I spent 6 hours at a customer's house trying to get her blasted PC to boot off the flash drive. It didn't help that she was peering over my shoulder the whole time either asking if I wanted another coffee or reminding me that she must have Word and Excel on her revitalised Microsoft Zoobootoo computer *sigh*. But every time I tried a different configuration (I tried putting the install onto a 1Gb partition on the disk, formatting to EXT2, recreating the boot drive from scratch using a different SD card, setting the USB boot config to forced FDD, checking that the SD card booted on other PCs, different distros, different versions etc. I mean I tried **everything** and a lot more besides!) I repeatedly got the message "Reboot and select proper boot device". And it was driving me insane.

Anyway, to cut a long story short, after 6 hours of this I couldn't stand it any more and I took the machine home with me. I fiddled with all sorts of solutions I found on this website, most of which involved tweaking the BIOS but none of which, unfortunately worked. I even found a Xubuntu 12.04 CD which, I decided, was a lot better than nothing, but Mr MAXDATA was having none of it and spat the CD out. I didn't know if it was the CD-ROM or the DVD drive, but the question was academic because I don't have any blank discs lying around. 

However, after going round and round in circles for ages I spotted a Hiren's Boot CD lying around so I snuck it in the CD drive and it spun and booted off it! On the opening menu of that Hiren's CD is Parted Magic 6.7, a Linux rescue environment, and what I did was to open it up, run the partition manager and copy the boot partition from the SD card to the by now thoroughly cleaned and formatted solitary IDE drive. I checked that the boot flag was set and rebooted the PC, choosing the IDE drive from the boot menu. Blistering barnacles, another failure, another "Reboot and select proper boot device". So, by now properly deflated, I rebooted the PC and, by default, it booted back into Hiren's start menu. I sat and stared at it, fairly desperate this time for some kind of inspiration. And there it was, staring at me: **PLoP Boot Manager**. I ran it, and selected the partition SDA1 and waited. All of a sudden I saw the beautifully wonderful screen I was so desperate for:

[CENTER][IMG]http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png[/IMG]

[/CENTER]

And that was the end of my nightmare.

---

