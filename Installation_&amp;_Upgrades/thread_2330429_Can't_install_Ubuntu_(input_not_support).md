---
title: "Can't install Ubuntu (input not support)"
date: 2016-07-11
forum: Installation &amp; Upgrades
---

### Post by n172 on 2016-07-11
First of all, it's not a misspelling. It's "input not support". I have an AOC monitor, and an ASUS STRIX 1070.
I create the bootable usb stick in win10, reboot, and when I press "Install Ubuntu" then it just goes black screen with a floating "input not supported". I had ubuntu before (before having the VGA), same version (16.04), and everything worked just fine.

What can I do?

---

### Post by yancek on 2016-07-11
What software did you use on windows to create the bootable usb?
Have you tested the bootable usb on another computer to see if you get the same result?
Before creating the usb on windows, did you do an md5 checksum to verify the download?
If I understand correctly, you are saying the flash drive boots until you get to the point of selecting 'Install Ubuntu' and then you get the error?
That would be unusual.  I've seen this error on installed systems but it is immediately on boot and the solution I've used won't work on a flash drive as the file to edit doesn't exist.
What graphics card do you have?  That might help someone to help you.

---

### Post by n172 on 2016-07-11
> **yancek said:**
> What software did you use on windows to create the bootable usb?
 I tried both unetBooting and rufus.
> 
Have you tested the bootable usb on another computer to see if you get the same result?
correct. I tried right now on my laptop, and it seems to work (Integrated VGA, i5 6200U).
> 
 Before creating the usb on windows, did you do an md5 checksum to verify the download? 
No, but I highly doubt that it's the case, since I tried with two different software and it also worked on my laptop.
> 
If I understand correctly, you are saying the flash drive boots until you get to the point of selecting 'Install Ubuntu' and then you get the error?
 Yes, I reboot the computer, change the boot loading order, reboot, it appears the normal grub screen, I select Install ubuntu and what happens next is that screen.
> 
That would be unusual.  I've seen this error on installed systems but it is immediately on boot and the solution I've used won't work on a flash drive as the file to edit doesn't exist.
What graphics card do you have?  That might help someone to help you.
I Have An ASUS STRIX GTX 1070 (As I wrote before... Did you ask because you missed it or because you wanted more info about it? In case, please do specify what more you want to know, since I have no idea what else to include!)

---

### Post by grahammechanical on 2016-07-11
I was not aware that an Asus STRIX 1070 was an Asus branded Nvidia GTX 1070. So, I was just about to web search for information on it. Which I should not really need to do. What Video inputs does the AOC monitor have and what input are you using to connect to the video card? Is the AOC monitor digital or CTR? I ask because I am confused by this statement:

> before having the VGA

I know what VGA is. I go back to the days before VGA was invented. But I do not understand what you mean by that statement. 

The Ubuntu live session uses an open source video driver. A proprietary video driver gets installed during the Ubuntu install process and is loaded when the installation is finished and we restart. You may need to set the nomodeset boot parameter. Go to the section Changing the CD's Boot Options - Section 6 - F6 and follow the instructions to use the F6 key to add nomodeset to the installer's boot options.

I do not know if it will fix this problem. May be.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards

---

### Post by n172 on 2016-07-12
> **grahammechanical said:**
> I was not aware that an Asus STRIX 1070 was an Asus branded Nvidia GTX 1070. So, I was just about to web search for information on it. Which I should not really need to do. What Video inputs does the AOC monitor have and what input are you using to connect to the video card? Is the AOC monitor digital or CTR? I ask because I am confused by this statement:



I know what VGA is. I go back to the days before VGA was invented. But I do not understand what you mean by that statement. 

The Ubuntu live session uses an open source video driver. A proprietary video driver gets installed during the Ubuntu install process and is loaded when the installation is finished and we restart. You may need to set the nomodeset boot parameter. Go to the section Changing the CD's Boot Options - Section 6 - F6 and follow the instructions to use the F6 key to add nomodeset to the installer's boot options.

I do not know if it will fix this problem. May be.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards


I'm really sorry for the mess, I honestly am perplexed in my ignorance! 


Let's try to be more clear. Yes, nVidia gtx 1070. (There i used vga as synonymous to graphic card, i don't know if it's correct). Before (up to a month ago) I had a dual boot with Ubuntu  16.04 and win 10,  but I had only the integrated graphic card, in an i5 4460. I connect to the monitor through a HDMI cable. The monitor is led, 1080p and 60 fps. 

I will try to follow the instructions this evening when I come back home, and I will get back with a feedback!

---

### Post by n172 on 2016-07-13
It worked, thank you!

---

