---
title: "Lost usb Keyboard + Mouse on upgrade to 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by secretrosegarden on 2011-04-29
Hi Forum Members,

I upgraded my system today from Kubuntu 10.10 (or whatever the last full release was) to 11.04 using the automated web process. I know, I know, I should have tested off a live cd or a thumb drive, foolish mistake.

On upgrade the video card works, and it boots fine... but I have no keyboard and mouse. I checked the forums and realized that maybe it was a problem with the brand of keyboard and mouse I was using. so I've tried four manufacturers (even tried switching between wired and bluetooth) to no avail.

I've also tried starting in recovery mode, but the problem persists.

To be specific, my bios sees the hardware just fine, and I'm able to hold down shift and pull up the selection options pre-OS, and select which one to run... and I can see the red optical light on the mouse no problem, so it's not a defect of either the motherboard or the input devices themselves. 

However, once in the OS, in recovery mode, or anything else, I'm left without a keyboard or mouse. As my system only has USB ports and not PS2, I can't check a hardware spec beyond what I've tried.

Also, it doesn't work if I select the "boot into an older version of linux" which is odd.



HARDWARE SPECS:

Computer - Dell Vostro 200

Keyboard and mice tried:

Dell Bluetooth keyboard + mouse
Microsoft Comfort wave (usb)
Belkin cheapo thing (usb)
Dell wired set.

Can someone make a recommendation? Is there a way to get a liveboot cd of the previous version of Kubuntu that worked?

Thanks!

---

### Post by zambiandreams on 2011-04-29
I am now having the exact same problem, although I had a brief period of 11.04 working fine.  

My keyboard works fine to get into the BIOS and about 50% of the time to try and boot to an older version, but as soon as I get to a startup screen I get an error message saying it could not communicate with the USB devices.

---

### Post by comport2 on 2011-04-30
I'm having the exact same problem.
USB mouse and keyboard stopped working after upgrade to Ubuntu 11.04.

There is something that stops working after an Ubuntu upgrade! Webcam, sound, wifi, graphics, card reader, kernel... I never expected something so basic like keyboard!!!

---

### Post by benfindlay on 2011-05-04
Also having this problem, but with plain ubuntu (not with any of the variants).

Specifically, the keyboard and mouse work fine prior to the OS loading, but get a blank screen after OS starts to load, until logon screen appears, at which point I can't do anything as keyboard and mouse won't work

Anyone got any ideas?

---

### Post by mörgæs on 2011-05-04
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by tmeier on 2011-05-04
Upgraded from 10.10 to 11.04 and the upgrade worked fine and computer worked fine.  Today (May 4th, 2011) I did the normal updates from the update manager.  I rebooted after and now Keyboard and Mouse do not work.  Both are USB and am assuming other USB items will not work as well.

---

### Post by mörgæs on 2011-05-04
Try booting into an older kernel.

---

### Post by mooreted on 2011-05-04
Same problem. Tried booting to an older kernel and just lines and lines of code. Wouldn't boot at all.

---

### Post by rts on 2011-08-07
Upgrading from Ubuntu 10.10 to 11.04 today, on the most plain, basic machine you can imagine (where everything worked before), and I've hit this problem.

Mouse and keyboard work find with Live CD, but once upgraded, no keyboard and mouse at the login screen.  Shift doesn't bring up a GRUB menu; I can't get a terminal with Ctrl-Alt-Fn, I can't ssh in to the machine, I can't do anything.

A lot of Google searching and I see absolutely no solutions.  This is unbelievably poor.

---

### Post by mooreted on 2011-09-03
> **AlexOnVinyl said:**
> Same issue here. Please help

I did a clean reinstall, now it's working and points out why I never do upgrades.

---

### Post by mörgæs on 2011-09-03
Good. If only more people would do so, the forum would be half the size.

---

### Post by rtoodtoo on 2011-10-19
Hi,
 I have hit the same problem. After upgrade to 11.04 now keyboard
and mouse don't function. Machine isn't reachable via network either. Do we have any solution without going for the clean install option?
   I searched in google but I haven't found any solution so far.

thanks a lot.

---

### Post by goldfishplus on 2012-02-18
I had a similar problem with USB keyboards in Ubuntu 11.10 (Oneiric Ocelot) on a Sony Vaio laptop.  I tried an Apple (aluminum) & Dell keyboard, neither worked; in the terminal (Ctrl+Alt+F2) I saw something about "hid: Unknown parameter 'pb_fnmode'" when plugging the keyboard in.  After searching forums I ended up messing around with the file /etc/modprobe.d/alukbd to no avail. 

Finally, once sufficiently frustrated, I "fixed" the problem by simply deleting every line in /etc/modprobe.d/alukbd (after backing up the file, of course).  I have no idea what the problem was and why this fixes it, but whatever, it works now. =^D

Before I cleared it, my /etc/modprobe.d/alukbd file contained the following: 
options hid pb_fnmode=2
options hid_apple fnmode=2

---

