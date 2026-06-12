---
title: "Can install Ubuntu 16.04, but can't get to live usb environment"
date: 2016-04-20
forum: Installation &amp; Upgrades
---

### Post by plotor2 on 2016-04-20
[COLOR=#000000]I bought a new laptop yesterday, a MSI GS60 Ghost Pro-002 with a Core i7 (6700HQ 2.60 GHz) and an Nvidia Geforce GTX 970M, 128GB SSD and 1TB HD. Came installed with Windows 10 obviously, and for the sake of trying, I figured I would dual boot this machine instead of wiping Win10 off completely. I got last nights build of the amd64 install of 16.04 and got it installed to a USB drive. No matter what I tried, I [/COLOR][COLOR=#000000]couldn't get to live desktop, but selecting "Install Ubuntu" straight from the boot menu worked.[/COLOR]

[COLOR=#000000]When attempting to get to the live environment, I tried every combination of nomodeset, i915.preliminary_hw_support=1, pci=nomsi, nouveau.modeset=0, and anything else I could find on Google that seemed relevant. The pci setting actually prevented the wireless firmware from working, so that was out. The i915 and nouveau settings didn't make much difference. Nomodeset was the only really helpful setting, although it still didn't get me all the way in. It stopped the live environment from hanging while booting up, and got me to point where I could see the default 16.04 desktop background, but none of Unity would load in, and I could kind of see the "Unity ran into an unexpected problem" dialog pop up where it wants to send an error report. The problem was, any window that appeared would be flashing in two places, one in the upper left corner, and again somewhere near the middle of the bottom of the screen. Effectively unusable. After trying to solve this for nearly two hours, I gave up and simply chose to try to install Ubuntu (with nomodeset) and to my surprise, it worked perfectly (relatively speaking.) 

So I can install just fine, but if I need a live environment, I'm out of luck.  Any ideas that I can try just in case I need it?  Thanks.[/COLOR]

---

### Post by grahammechanical on 2016-04-20
When you installed Ubuntu did you tick the box labelled "Install third party software?" If you did then that explains the difference between the live session & the installed session. It is a proprietary video driver. The live session uses an open source video driver.

Regards.

---

### Post by plotor2 on 2016-04-20
Yes, I did tick the "[COLOR=#000000]Install third party software" option, so you're right about that.  Does that mean I have no live solution for the time being until a future release of Ubuntu's video driver catches up to the hardware?  Thank you.[/COLOR]

---

### Post by oldfred on 2016-04-20
Some of these are now the older version.

       [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

### Post by mborgnia on 2016-07-08
I got my MSI 60GS 6QE today. I had a hard time trying to boot anything. The one live CD that I could boot was Mint 17.1, but the wireless network card would not work. I am now installing openSuse Leap 42.1, which worked only after passing acpi=off to the kernel. Still no wireless card, and no mousepad

---

### Post by oldfred on 2016-07-08
Some other MSI threads. 
Issues are often common across most models of a brand.

 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

