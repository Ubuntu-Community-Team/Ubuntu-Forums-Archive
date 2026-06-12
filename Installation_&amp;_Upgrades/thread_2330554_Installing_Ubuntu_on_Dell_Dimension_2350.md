---
title: "Installing Ubuntu on Dell Dimension 2350"
date: 2016-07-12
forum: Installation &amp; Upgrades
---

### Post by yolkarolka on 2016-07-12
I picked up a Dell Dimension 2350 from a neighbor. It's a very old computer. It has Windows XP installed on it currently. I'm trying to install Lubuntu on it, but I run into issues.

What I've done so far:
The BIOS version is A01, and I can't boot from USB in the BIOS. It isn't even an option. I tried a CD, but it wouldn't work either. Yes, the boot order was correct.

So then I found software called Plop Boot Manager. I installed Plop onto my Windows XP and tried to use it to boot from CD. No success. It read out errors. So I tried a USB. That didn't work either.
I found a setting in Plop relating to forcing USB 1.1. I set it to mode 1 and then my USB worked and booted the menu. Yay!

First, it was giving overheating messages so some new thermal paste fixed that right away. Problem solved.
But now when I click anything on the Lubuntu menu, the computer freezes and I have to restart it.
I thought maybe it's the USB. So I tried Ubuntu 16.04, 14.04, and Lubuntu. I tried creating the USBs with UUI, Live USB Installer and Rufus. I tried booting Same problem across the board. The menu freezes when I click anything.
Doesn't matter which software I use to create the USB or which version of Linux I try to test run or install on it, the menu freezes every time and it's incredibly frustrating.
+Tried integrated and PCI graphics, same problem.
To be clear, it doesn't freeze during install process, it freezes the moment I click anything on the USB menu.

I'm out of ideas and I don't know where to go from here. Any advice is appreciated.

---

### Post by Rex Bouwense on 2016-07-12
Your USB is probably identified as another hard drive.  Check the BIOS and if there are two hard drives (indicated by a + sign) make sure that the USB flash drive is ahead of the main hard drive.  My old Dell Inspiron is like that.

---

### Post by yolkarolka on 2016-07-12
> **Rex Bouwense said:**
> Your USB is probably identified as another hard drive.  Check the BIOS and if there are two hard drives (indicated by a + sign) make sure that the USB flash drive is ahead of the main hard drive.  My old Dell Inspiron is like that.
Nope. It doesn't detect a second hard drive. I'm thinking maybe it has something to do with this?
[https://help.ubuntu.com/community/InstallingUbuntuOnADellDimension2350](https://help.ubuntu.com/community/InstallingUbuntuOnADellDimension2350)

---

### Post by mörgæs on 2016-07-12
Before erasing Windows I suggest that you upgrade the BIOS.
[http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=R58200](http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=R58200)

---

### Post by yolkarolka on 2016-07-12
> **mörgæs said:**
> Before erasing Windows I suggest that you upgrade the BIOS.
[http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=R58200](http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=R58200)
Flashed the new bios using Rufus FreeDOS. I'm now on version A02. But I have a black screen on boot. I removed CMOS battery and put it back in, still nothing.

The monitor is receiving a signal, but the screen is black. Also, it has ABCD lights that were all green. Now the A and B lights are yellow. Not sure what that means.
I looked it up on Dell website and it says memory problem. I reseated the RAM and I now have a display again.

I tried to flash bios again. It says successful. But then when I reboot I get a black screen and I have to remove CMOS battery again.

Edit: PROBLEM SOLVED! It seems that updating the bios to AO2 enables onboard graphics. So I just had to switch it to onboard and it worked. I'm on A02 and it's working.

---

### Post by yolkarolka on 2016-07-12
Whenever I click an item on the menus, it is actually switching the display to onboard graphics, and that is why it freezes and goes black. I'm going to see if I can get it to work by only using onboard graphics.

Not having any success. Any further advice or suggestions would be appreciated.

Edit: Solved! I removed the graphics card and it worked. It was a problem with the graphics card of course. I am now installing Ubuntu.

---

### Post by grahammechanical on 2016-07-12
The minimum requirements for Lubuntu are 256 MB to 384 MB of RAM. To install Lubuntu 384 - 800 MB RAM is needed. According to this web site that machine has 256 MB RAM

[http://www.cnet.com/uk/products/dell-dimension-2350/specs/](http://www.cnet.com/uk/products/dell-dimension-2350/specs/)

[https://help.ubuntu.com/community/Lubuntu](https://help.ubuntu.com/community/Lubuntu)

See how things go but do not expect too much. And from the hardware issues that you have come against it seems that the machine has been knocked about a bit.

Regards.

---

### Post by DuckHook on 2016-07-13
Perhaps my opinion is another option than you neither need nor want, but if I were you, I would consider installing Ubuntu Server on that machine and using it purely as a server of some kind. grahammechanical is right: if you are working with the original RAM, there really isn't enough there to run any kind of DE and get real work done. On the other hand, there isn't a single component in a machine that old that is worth spending a nickle on for upgrades. If you can lay your hands on an extra 256 MB for nothing, then Lubuntu begins (just begins) to make some sense.

On the other hand, by taking all graphics load off of the video card, it becomes a decent server. You could use it for as a server for torrenting, printing or, with the addition of a cheap external USB HDD, as a secondary backup for your data. There are any number of additional server uses that it would be good for.

The biggest hurdle for new users would be working only with the command line. Only you can decide whether you want to wrestle that bear.

---

### Post by yolkarolka on 2016-07-13
> **DuckHook said:**
> Perhaps my opinion is another option than you neither need nor want, but if I were you, I would consider installing Ubuntu Server on that machine and using it purely as a server of some kind. grahammechanical is right: if you are working with the original RAM, there really isn't enough there to run any kind of DE and get real work done. On the other hand, there isn't a single component in a machine that old that is worth spending a nickle on for upgrades. If you can lay your hands on an extra 256 MB for nothing, then Lubuntu begins (just begins) to make some sense.

On the other hand, by taking all graphics load off of the video card, it becomes a decent server. You could use it for as a server for torrenting, printing or, with the addition of a cheap external USB HDD, as a secondary backup for your data. There are any number of additional server uses that it would be good for.

The biggest hurdle for new users would be working only with the command line. Only you can decide whether you want to wrestle that bear.
I'm quite new to Linux. And I've never set up a server before. It's running Ubuntu now, but it's really slow graphically and impractical. Also, I have to keep the graphics card out to get the PC to start. I'm still trying to find a fix for that.
I'm not really sure what to use the computer for, but I am open to ideas. And it doesn't exactly match the specs Grahammechanical mentioned.

More information on my system:

Memory: 493.3 MiB
Intel Pentium 4 CPU 2.00 GHz
Intel 845G x86/MMX/SSE2
Disk: 58.4GB

Edit: I've decided to remove the graphics card to avoid headache.

---

### Post by DuckHook on 2016-07-13
> **yolkarolka said:**
> I'm quite new to Linux. And I've never set up a server before.You are correct that this makes it tougher to run a pure command-line server.> It's running Ubuntu now, but it's really slow graphically and impractical.Correct again. Ubuntu is impractical on that machine. Lubuntu is about the only thing that will work.> I'm not really sure what to use the computer for, but I am open to ideas.If you don't want to run it as bare-bones server, then the aforementioned Lubuntu is about the only option within the 'buntu family. Outside of the 'buntu family, you can try Puppy, Slitaz or Tiny Core. These are all designed for very limited HW such as yours and you may prefer the results. They don't come with GIMP, LibreOffice or any games, but that's not realistic on such an old box. The biggest common resource hog is the browser. You will have to settle on a simpler browser without all the bells and whistles of the heavyweights.> I've decided to remove the graphics card to avoid headache.Probably a smart move in your situation. Your HW specs show enough RAM to run Lubuntu, though, as already mentioned, you will have to run very light browsers.

---

### Post by mörgæs on 2016-07-14
Are you sure the graphics card is completely dead, not just had a loose connection? 

Try to rearrange it in the slot to see if it gives a picture.

---

