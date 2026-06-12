---
title: "Ubuntu 10.10 Netbook install problem"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by Richsheri4 on 2010-10-25
Hello, I'm having problems installing Ubuntu 10.10 Netbook onto my Asus 900.  I downloaded the .iso then used the "make startup disc" feature in my Mint 9 desktop machine to make a usb install disk.  All appears well at that point.  When I try to boot from the usb stick, I get an error message as follows:

"SYSLINUX 363 Debien-2008-07-15 ......
 Unknown Keyword in Configuration File

 boot: "

and the cursor just hangs there and doesn't respond to the keyboard.

I also tried it on another Asus and a Gateway Laptop with the same results.

My intention is to have this the sole OS on my little Asus 900.

'tis a headscratcher.  :confused:

---

### Post by SirBlain on 2010-10-25
Do you have a machine with Windows on it? I've had bad luck making bootable USBs in Linux. I've always run into some problem.

If you can get to a Windows machine search for a program called LiLi (Linux Live usb installer). It's automated, you can choose for it to use your .iso or download a new one. Give it a shot and let us know if it worked!

---

### Post by renehasekamp on 2010-10-25
I had the same problem when I made my USB-"live cd" using the utility, from Ubuntu 10.10. 
However, when I used the startup-USB maker from Ubuntu 10.04 everything went fine and the error messsage did not appear.
I suppose there is a bug in the startup-(USB)disk-maker in 10.10!

---

### Post by sikander3786 on 2010-10-25
Download unetbootin.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

You can use it on Linux Mint. Don't download it from the repositories as they contain the older version and I suspect it doesn't work with 10.10. Download from the webiste instead.

This page lists a few more options.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Richsheri4 on 2010-10-25
Thanks, I should add that I used the same procedure and the same equipment to make a bootable usb of Lubuntu 10.04 and it installed just fine (that's anecdote, not evidence).

I've tried Unetbootin and the Windows version worked quite well.  I had some problems with the linux version(s) but they may have been caused by me.

I have Windows machines available and a usb external CD R/W machine.  In fact, I burned a CD using the same .iso I had used previously, and am currently installing 10.10 netbook onto the little Asus.  But it is slooooow.

It's nice to know I'm not alone with my peculiar problems.  :)

---

