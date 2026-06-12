---
title: "How do I format my harddrive and reinstall Ubuntu"
date: 2015-08-18
forum: Installation &amp; Upgrades
---

### Post by chris393 on 2015-08-18
So far I have tried...
1) Downloaded uBuntu, burnt to disk, select boot from cd, install cd just gets bypassed and goes into Ubuntu. Set in bios to boot from cd, and also manually selected from boot menu.
2) Tried downloading gparted, constantly get unable to fetch, wired connection will not stay connected, the reason I want to reinstall.
3) Tried removing harddrive, attaching to windows 7 via usb, error says harddrive will not initialize

Already tried fixing the wired connection. Just want to format this harddrive, and start from the beginning.

Frustrated

---

### Post by oldfred on 2015-08-18
You cannot boot Windows from an external USB drive. It only works from drives seen as internal.

So what is working? Can you boot Ubuntu? Windows? Live installer? Windows repairCD?
How then are you downloading?

Did you actually copy Ubuntu to CD, as that is too small now for Ubuntu. Lubuntu may fit on a CD still?

---

### Post by chris393 on 2015-08-19
I have a laptop I downloaded Ubuntu version 14.04.3 and burnt the iso, and tried the hdd with windows(hdd won't initialize), wanted to format it there, on my windows 7 laptop. 
My old desktop, started dropping the wired connection a few weeks, now it has permanently dropped the connect. Just want to format the hdd and start again. Can't even get the dvd to boot from the boot menu it just loads the exisitng Ubuntu on the hdd that I would like to format.

---

### Post by markf2 on 2015-08-19
> **chris393 said:**
> Can't even get the dvd to boot from the boot menu it just loads the exisitng Ubuntu on the hdd that I would like to format. 

I have the option to press F12 during power on and it lets me choose which device to boot from. It seems like I've seen circumstances where, even though my boot order is specified in the BIOS/setup, I still have to do the F12 choice to make it happen.

Can you use the free tool unetbootin to write the install ISO to a USB thumb drive? It only needs to be 2g in size. Maybe there's a problem with the DVD you burned? I use little thumb drives for this stuff.

---

### Post by oldfred on 2015-08-19
Are you able to boot DVD on laptop you made it from?
If neither system boot it then either download was not correct, or not written correctly.
You can check that download is correct with md5sum.
I also prefer flash drives, the are faster & reusable, so when you upgrade you can also update the flash drive with the new version.
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by chris393 on 2015-08-19
There was an error during the writing of the iso, I noticed it said something like end of file error when I clicked on the iso. I chose to get 15.04 and it's installing crrently. I also downloaded a bootable gparted iso and formatted the hdd in the computer after burning the iso with my laptop...unfortunately it's looking more like the actually onboard nic is busted.

---

### Post by Geoffrey_Arndt on 2015-08-19
Chris393 . . . (formatted the "desktop" hdd I assume you mean).

Update your NIC and consider creating an inexpensive wireless network (including usb-wireless adapters for backup of wired hardware).

The key will be to check out compatible hardware (ubuntu friendly such as Panda Ultra USB Wireless Adapter)

---

