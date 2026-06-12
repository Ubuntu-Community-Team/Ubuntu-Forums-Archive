---
title: "Wubi Installation to Blank Screen"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by SchecterHC on 2010-03-27
Hello,

I just tried to install both Ubuntu and Kubuntu via the wubi binary.  After both installations I reboot, select Ubuntu, get the splash screen and then a blank screen.  I've tried to boot into safe graphics mode as well on both installations but it does nothing as well.

I had previously tried to install Ubuntu Studio with the same results.  Thinking that perhaps that installation or disk was corrupt I tried wubi with the same results.

I'm not very familiar with anything Linux and I'd like to fix that but I have no idea where to start with this.  Any ideas on what I can do to fix this?

:-|

---

### Post by stlsaint on 2010-03-27
I say to remove all instances of wubi and start with only one install of whatever distro you choose either ubuntu or kubuntu.
You can start here: [Wubi]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20uninstall%20Wubi?")

That will put you at the uninstall section but that entire document will be able to guide you through uninstall and install of wubi.

---

### Post by SchecterHC on 2010-03-27
Sorry if I was confusing.  I had already done that.  I have my main Windows 7 installation and a wubi installation of the latest Ubuntu and thats it.

---

### Post by stlsaint on 2010-03-27
Do you get any error messages?

---

### Post by SchecterHC on 2010-03-28
No, I get nothing which is frustrating.  The screen just goes blank after the Ubuntu symbol.  Each time I've rebooted it tells me to continue the installation before the symbol pops up.  Once the symbol goes away it never progresses beyond that blank screen.

---

### Post by phaed on 2010-03-28
I'm having the same problem.  I install Ubuntu with Wubi and reboot.  It takes me to the boot menu where I select Ubuntu, then it says it's going to finish the installation.  Then I get a blank screen for about 10 minutes, although the light for the hard drive blinks, indicating that it's reading/writing to the hard drive, then it reboots.

This time I select Ubuntu and it takes me to Grub.  When I select Ubuntu again it goes to a blank screen and stays that way.  The hard drive light doesn't blink.  Booting into safe graphics mode does the same thing.

---

### Post by SchecterHC on 2010-03-28
Is there no one else who's had this issue?  Anyone that has fixed it?

---

### Post by Luke S on 2010-03-28
I have the same problem, made a post here about it: [http://ubuntuforums.org/showthread.php?t=1440755](http://ubuntuforums.org/showthread.php?t=1440755)

---

### Post by R_K100 on 2010-03-28
I'm having a similar problem and have notice a few other threads aswell. No one seems to reply

---

### Post by bluebadger on 2010-05-12
Similar problem here on my Dell Inspiron 1520. I'm fairly sure it's a graphics/display driver or configuration issue. I've tried both Ubuntu and Kubuntu like others here. Once I select Ubuntu it says it's completing the installation but then it goes to a screen that looks like it should be a logo or boot/startup screen but is really corrupted and mostly just a blank scren. I often just have a big vertical strip of an image visible with the rest blank. I have to force the shutdown. 

I've installed wubi/ubuntu to my D drive but I doubt that would cause the problem. The resolution should be 1440x900 for my screen. 

There is no IGP on the laptop as it has a dedicated video card and isn't one of the newer mixed mode types. Is there some issue with the newest version of Ubuntu or is it strictly a problem with Wubi? I'm not sure and I'd really like to know. I'm interested in getting back into using Linux. It's hard to have confidence in it when it starts off with a poor experience but I will give it a shot once I can give everything up and running.

---

