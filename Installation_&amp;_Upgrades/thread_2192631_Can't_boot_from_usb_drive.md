---
title: "Can't boot from usb drive"
date: 2013-12-08
forum: Installation &amp; Upgrades
---

### Post by infamous45 on 2013-12-08
I created a bootable disk with Unbuntu 12.04 using unebootin.  When I put the usb in my 2006 Gateway laptop and start up, I go to the boot menu and click the boot from USB storage stick option.  Then the screen goes black and nothing happens or it says operating system missing.  I have tried installing on  2 different flash drives and have downloaded Unbuntu twice.  What am I missing?  Please help.

---

### Post by Eugene King on 2013-12-09
The best way I found for instaling the operating system on a USB drive it to first burn a DVD with the ISO image.

Then boot up on the DVD. After which select making it a permenant install. 

After you select it for install follow the custom option and select your USB stick. Format it with ETH4 selected and don't forget to select "/" for the boot. Then install.

This is from memory so it may not be 100% but this should get you through the install.

In fact I'm on my USB Linux Box as I'm typing this.

[https://www.youtube.com/watch?v=5Z4zm27ZGW4](https://www.youtube.com/watch?v=5Z4zm27ZGW4)

---

### Post by james2b on 2013-12-09
This site may help here; [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) , or here; [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by infamous45 on 2013-12-09
My dvd player does not work on my p.c. so using a dvd is not an option.  I did use the usb installer and unebootin and it's still not working.  I'm going to check the md5 sum and also try loading it onto another p.c.

I'm still open to more suggestions.

---

### Post by infamous45 on 2013-12-09
Well, after spending almost a full day trying to figure out why Unbuntu wouldn't boot on my p.c. from a usb, I tried it on my GF's computer and it loaded right up.  Why can't my p.c. see the operating system?  I don't have a working dvd drive on my p.c., is there any other way I can load Unbuntu on my p.c.?  I want to do a clean install.  Thank you.

---

### Post by rwan.work on 2013-12-15
Hi,

If your computer cannot boot from your USB drive, the first thing to check is if the USB drive is bootable.  As you've tested that, then that's one less problem to worry about.

The next thing you want to check is if the USB drive is in the "boot order".  There are a series of devices the computer checks to see if there is an OS.  There could be two reasons why it doesn't boot from the USB drive:

1)  The USB drive isn't in the list of places to look for an OS.
2)  It is on the list, but at a lower order than the hard disk, which already has an operating system.

You need to enter your BIOS and look for these two items and change them so that USB drive is on the list and that it is higher on the list than the hard disk.  Some systems have it purposely omitted for security reasons (so that someone can put in a USB drive to boot the computer).  So, after you're done with what you need, you might want to change the settings back.

When the computer starts up, enter BIOS.  Usually, it'll ask you to hit a key like F11 or F12.  It varies from computer to computer.  You'll just have to look for it when the computer starts up, but *before* it starts up the operating system.

Good luck!

---

### Post by Eugene King on 2013-12-16
If I made a USB ubuntu stick off my XP work computer using a DVD and while running off the DVD do the perminent install on the USB stick I could not boot up on it on my Windows 7 laptop at home to do updates. 

Why? I havent a clue. I even tried repairing the boot protion and enede up wrecking the hole thing

I can however use my windows laptop to make a USB stick and it will boot up on both XP and Win 7.........

Problem with installing Ubuntu on a USB stick using PenDrive is that its not the perminant install.......You can brows the net save sites to favorates etc....and when you boot up to it again its like the first time......every time.

I've made a bunch of [B]USB drives. And the best way is to start with the DVD and do the instal on the USB. 

Ignore the Bold type I hit a wrong option.....I'm not yelling.
[/B]

But in the end its up to you...Use your GF's PC to burn a DVD and create a USB Ubuntu stick........

---

### Post by Eugene King on 2013-12-16
My USB Ubuntu and tethering with my iPhone is my freedom on my long 12hr work days with no equipement brakedowns.

Plus I can bring work from home and work on it.......

Now if i could only get OpenOffice to work......

---

### Post by sudodus on 2013-12-16
> **james2b said:**
> This site may help here; [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) , or here; [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

+1

There are many useful tips at those links :-)

> **infamous45 said:**
> My dvd player does not work on my p.c. so using a dvd is not an option.  I did use the usb installer and unebootin and it's still not working.  I'm going to check the md5 sum and also try loading it onto another p.c.

I'm still open to more suggestions.

0. Did you check the md5sum of the iso file?

1. What about your computer? It will be easier, if you specify

- CPU
- RAM (size)
- Graphics chip/card
- Wifi chip/card

1a. Maybe standard Ubuntu with Unity needs more horsepower. Try ***Xubuntu 12.04 LTS 'Precise***' with a lighter desktop environment :-)

1b. Maybe there are problems with the graphics driver. Try some [boot options]("https://help.ubuntu.com/community/BootOptions"). Start with ***nomodeset***.

3. You can also try cloning the iso file. Use ***mkusb*** to reduce the risk to write to the wrong device according to the [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

> **infamous45 said:**
> Well, after spending almost a full day trying to figure out why Unbuntu wouldn't boot on my p.c. from a usb, I tried it on my GF's computer and it loaded right up.  Why can't my p.c. see the operating system?  I don't have a working dvd drive on my p.c., is there any other way I can load Unbuntu on my p.c.?  I want to do a clean install.  Thank you.

Yes there is also the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), that can make clean installs in an easy way.

---

### Post by sudodus on 2013-12-16
> **Eugene King said:**
> My USB Ubuntu and tethering with my iPhone is my freedom on my long 12hr work days with no equipement brakedowns.

Plus I can bring work from home and work on it.......

Now if i could only get OpenOffice to work......

Have you tried ***LibreOffice***? [COLOR=#696969]I think that package is better than OpenOffice today.[/COLOR]

---

### Post by Rex Bouwense on 2013-12-16
I am not sure if this applies here but I will mention it here.  Some computers think that a flash drive is accually another hard drive so you have to check the Bios and insure that if it is recognized as a hard drive that it boots ahead of the computer hard drive and if that doesn't work try another flash drive.

---

### Post by Eugene King on 2013-12-17
Things I create in OpenOffice get wrecked if I edit them in Liberoffice then go back to openOffice. Its my software thats the same between windows and my Linux Boxes................

---

### Post by sudodus on 2013-12-17
Some of the text and picture editing/formating features are not portable between the office suites. That is too bad; many of the basic features are portable, but not all of them. It is a good idea to distribute documents as pdf files, which is easy with Open Office and Libre Office.

Edit: If you want a thorough discussion about this problem, ***please open an own thread about it with a good descriptive title***. It will attract people who are interested in that particular subject.

---

### Post by Eugene King on 2013-12-17
> **sudodus said:**
> Some of the text and picture editing/formating features are not portable between the office suites. That is too bad; many of the basic features are portable, but not all of them. It is a good idea to distribute documents as pdf files, which is easy with Open Office and Libre Office.

Edit: If you want a thorough discussion about this problem, ***please open an own thread about it with a good descriptive title***. It will attract people who are interested in that particular subject.

Yes it should be its own toppic. Just answering his question............Also Just installed OpenOffice 4.0.1 on my USB drive.........

---

### Post by Eugene King on 2013-12-17
I hope the OP gets this figured out. I pulled my hair out trying to figure out why a USB stick loaded with Ubuntu on my XP computor at work will only work on that computer. While a USB stick loaded with Ubuntu from my Laptop a home using windows 7 will operate on both my laptop and the Dell work computer. I wrecked one install trying to repair the boot sector with a repair disk.

I made a bunch of these over the last few years and by far the best preforming ones were running Ubuntu off the DVD and then selecting Install and making the perminant installation on the USB drive instead of the computer by selecting Other.(I think Other is the option)

---

### Post by sudodus on 2013-12-17
I think I understand. I often do something similar: Make a boot USB drive, and from that ***make a full installation into another USB drive***. It can be done from an iso file or with the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971").

-o-

There could be several reasons why a USB stick loaded with Ubuntu on your XP computor at work will only work on that computer.

1. It is a 64-bit system that won't work in 32-bit systems.
2. You have installed some proprietary driver (maybe for graphics or wifi).
3. The operating system version is too new or too old to fit the hardware of the other computer(s); also a driver problem.
4. The pendrive (hardware) is not compatible with the hardware of the other computer.

---

### Post by Eugene King on 2014-01-01
Its a Dell Optiplex 980 PC with the biggy CPU

If I understand these PC's have Windows 7 installed and All they did to do the new PC install was first copy the OS off the older Dell PC when create a virtual envoiroment to run the XP OS off of.

Did I say that correctly? That may be the reason.......

---

