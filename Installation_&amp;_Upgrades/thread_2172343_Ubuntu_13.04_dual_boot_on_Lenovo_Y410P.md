---
title: "Ubuntu 13.04 dual boot on Lenovo Y410P"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by andrew30 on 2013-09-04
After much trial and error, I have gotten Ubuntu dual booting with Windows 8 on my Lenovo Y410P.  I did not find instructions that worked exactly in any one place, so here is the process I used as a reference for anyone installing on a similar machine:

1. Create USBLive flash drive in Windows, and shrink the windows partition so there is room to install ubuntu (instructions for this elsewhere)

2.  In terms of the UEFI firmware settings, I disabled Secure Boot, and changed the boot settings to Legacy- Support and Legacy First boot

3.  Boot from the USB in Legacy mode and do a legacy install of Ubuntu

4.  At this point, I had a lot of  problems with GRUB, so I ran boot-repair (from Ubuntu running in Live-mode from the flash drive), which broke it even more (when I tried to boot using the GRUB, it would not be able to find it)

5.  To fix this, I put rEFInd boot manager on a flash drive, and using this, I was able to successfully boot into both Windows and Ubuntu.

6.  To avoid having to use the flash drive every time I wanted to boot, I downloaded rEFInd onto the Ubuntu that was installed on my computer, and just followed the basic install.sh script.  This gave me errors, but it seems to have worked to some extent.

7.  At this point, to select which partition I want to boot to, during the boot, when the screen with lenovo appears, I press F12 and then if I select Windows boot, it boots to windows, and then Ubuntu appears farther down the list and when I select that, it takes me to a GRUB screen that allows me to boot to Ubuntu (but windows won't boot from this GRUB, so I have to boot it the way previously described).

I certainly don't understand why it started working once I installed the rEFInd to my computer (because the rEFInd screen never appears in my boot process) but it works.  

I hope this helps anyone who is in a similar situation.  I will try my best to answer any questions.

EDIT: I forgot to mention this before, but if you ever see a black screen and think something went completely screwy, just increase the brightness and something is actually there.

---

### Post by JabZero_ on 2013-09-05
Hi Andrew, 

I am installing 12.04, but I am experiencing a similar "black screen' problem. 

[COLOR=#333333][FONT=HelveticaNeue-Light]I changed the necessary BIOS parameters to avoid UEFI problems; however, when I try to install or (simply Try Ubuntu), the screen is dark. It is not a black screen, where one cannot see anything, rather it is seems that "color control" is off. If I use a flashlight on my screen (I know, this is hilarious [/FONT][/COLOR][IMG]http://forum.notebookreview.com/images/icons/icon10.gif[/IMG][COLOR=#333333][FONT=HelveticaNeue-Light]), I see the menu and everything. 

You mentioned that you got the same black screen; however, by increasing the brightness, you were able to install Ubuntu. What about the sound? I hear a pitch like the witches from hell broke loose [/FONT][/COLOR]:lolflag:[COLOR=#333333][FONT=HelveticaNeue-Light]  
Have you had a similar issue?





[/FONT][/COLOR]

---

