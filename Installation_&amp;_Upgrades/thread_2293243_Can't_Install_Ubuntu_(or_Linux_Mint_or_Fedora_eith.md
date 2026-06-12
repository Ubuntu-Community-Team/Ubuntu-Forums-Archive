---
title: "Can't Install Ubuntu (or Linux Mint or Fedora either)"
date: 2015-09-03
forum: Installation &amp; Upgrades
---

### Post by Max_Kunstler on 2015-09-03
I tried installing Ubuntu 3 times. After installation, Ubuntu boots up and shows
some icons on the left side of the screen, but they're totally inoperable. I have a 
mouse pointer that I can move. If I double click on the icons, nothing happens. 
The only graphics on the screen are the icons on the left side and the red background.
Ubuntu doesn't seem to completely boot up. 
Ubuntu also fails to run from DVD.

I also tried running the latest Linux Mint from DVD. It showed some garbage text on the screen
and said that it couldn't connect to the x server (the graphical interface). It showed me
a couple of error messages and the details about the errors. Then it quit to the command prompt. 

Then I tried running Fedora 22 from DVD. After installing, the only things on the screen were
a blue wallpaper and the mouse pointer. No icons or anything. 

Here's my system: 

* CPU: AMD Athlon II X4 630 95W AM3 2MB 2800MHz Retail 
* MOBO: Asus M4A77TD motherboard
* RAM: 8 gb
* GPU: EVGA GeForce GTX 8800
* HD: Western Digital Black 2TB hard drive (this is my new one for installing linux on)
* HD: Seagate 2TB ATA/100 (my old hard drive)
* SSD: Corsair SATA II 3.0Gb/s 128 GB Performance Series Internal Solid State Drive
* Currently running Windows 7 on the Corsair SSD

Is the problem the old graphics card? I bought it in 2008. It only has directx 9 features, as far as I know. 
Should I buy a Zotac graphics card?

I must find a solution for this because I absolutely don't want to use Windows anymore.

---

### Post by Bashing-om on 2015-09-03
Max_Kunstler; Hello;

Yeah, I could accept this as a graphics driver issue. Let's Try and boot the liveDVD using the fall back driver.
Boot up  the liveDVD:
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> F6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is also available.
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
Is the desktop usable ? If so we can install a proprietary driver .

We make it work in the liveDVD environment, we know what we have to do in the install.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Max_Kunstler on 2015-09-05
I did what you said. It booted to a desktop that only had the mouse cursor and the taskbar icons and nothing else. 
There was nothing on the black bar on the top of the screen. When I clicked on the taskbar icons, nothing happened. 

By the way, I don't think my bios has UEFI.

---

### Post by yancek on 2015-09-05
Did you do an md5 checksum on the downloaded iso file of the different systems before burning them as an image to the DVD?  This is to verify the download was correct.

---

### Post by Max_Kunstler on 2015-09-06
Since my last post I switched to version 15.04 because 14 didn't work. I did the md5sum on them. They were correct. Version 15.04 works well if I boot liveDVD with nomodeset. If I don't use nomodeset it boots up to a totally black screen. Now how do I install it on my hard drive and also install a driver for my EVGA GeForce GTX 8800? Also what's the difference between versions 15 & 14? Is 15 a beta?

---

### Post by Bashing-om on 2015-09-06
Max_Kunstler; Humm ...

I am surprised there is any problem with graphics. The GeForce GTX 8800 is supported by both open source and Nvidia will continue to be supported through special "Legacy GPU" drivers that will be updated periodically. In your case the 340.xx  version.
What returns from terminal commands:
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list

``` and we see about installing a proprietary graphics driver.

As to 15.04, it is a stable release but is a radical departure from the traditional initiate system. 14.04 and before were "upstart" now with 15.04 that system is "systemd" . systemd takes some re-adjustment in the thought processes.

I would expect that if you install with "nomodeset" set , the install will proceed. Once installed one could also then install that proprietary driver.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Max_Kunstler on 2015-09-06
OK Thanks Guys

---

### Post by yancek on 2015-09-06
Another major difference between 14.04 and 15.04, 14.04 is long term support until April, 2019 while support for 15.04 ends in January, 2016.  After installing, if you have graphics problems boot with nomodeset or select the Recovery option and when you get to the Desktop,  click the System Settings icon in the left panel then click Software & Upgrades and then click the Additional Drivers tab, wait and select the recommended driver;

---

