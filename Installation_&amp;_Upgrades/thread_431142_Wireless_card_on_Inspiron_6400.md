---
title: "Wireless card on Inspiron 6400"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by bcollins on 2007-05-02
Hello everyone,

My company recently decided to switch from Vista to Ubuntu.  I avidly promoted this and got what I wanted.  We still have a Mac or two around, but we're basically permanently switching to Ubuntu.

I've installed Ubuntu on all of our systems without any problem, except for the Inspiron 6400 laptop.

I was an avid Linux user five or six years ago, and due to my time away, have a fairly slim idea of what I'm doing these days.  I'll catch on again quickly, but for now, I need help. :) 

So, I tried to install Ubuntu on the 6400 and everything worked fine except the WLAN card.  I don't know about the Bluetooth card, but I really don't care either.

The WLAN card in question is the Intel 4965AGN.

I searched around this forum and seem to find answers for a different wireless card.  I found a HOWTO somewhere else on the Web and tried it out when I tried to install Ubuntu on the systme, but to no avail.  

If anyone happens to have clear-cut instructions on how to get this working, it would be greatly appreciated.  Then I can get the last system switched over. :) 

Thanks for your time!

---

### Post by TheOriginalH on 2007-06-23
> **bcollins said:**
> Hello everyone,

My company recently decided to switch from Vista to Ubuntu.  I avidly promoted this and got what I wanted.  We still have a Mac or two around, but we're basically permanently switching to Ubuntu.

I've installed Ubuntu on all of our systems without any problem, except for the Inspiron 6400 laptop.

I was an avid Linux user five or six years ago, and due to my time away, have a fairly slim idea of what I'm doing these days.  I'll catch on again quickly, but for now, I need help. :) 

So, I tried to install Ubuntu on the 6400 and everything worked fine except the WLAN card.  I don't know about the Bluetooth card, but I really don't care either.

The WLAN card in question is the Intel 4965AGN.

I searched around this forum and seem to find answers for a different wireless card.  I found a HOWTO somewhere else on the Web and tried it out when I tried to install Ubuntu on the systme, but to no avail.  

If anyone happens to have clear-cut instructions on how to get this working, it would be greatly appreciated.  Then I can get the last system switched over. :) 

Thanks for your time!


Sadly I have the same problem. From base install, the wireless network symbol was showing, but no networks were being detected. I tried the method mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=257684&page=2](http://ubuntuforums.org/showthread.php?t=257684&page=2) , but to no avail (now no wireless networks showing),

Any advice greatly appreciated. The speed increase of Ubuntu over Vista is amazing, I just wish my wireless was working!

TIA,

H

---

### Post by strangedata on 2007-06-27
Me too.

I've just got a Sony Vaio VGN-FZ140E with an Intel Wireless WiFi Link 4965AGN card.

Ubuntu only shows the wired interface, and I don't have access to the wireless card.

Thanks for any input.

---

### Post by Ayuthia on 2007-06-27
Here is a how-to that I found in the Absolute Beginner Talk forum:

[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%28WifiDocs%2FDriver%29)

The walk-through for installing ndiswrapper is nice and it looks like they have a driver that might work for you.

---

### Post by p0wd3r on 2007-06-30
Awesome guide!

I tried using the driver from [http://intellinuxwireless.org](http://intellinuxwireless.org) and for some reason the part of the mac80211 install where you have to "make menuconfig", I was unable to get it working.  I'm a n00b to linux now, since I haven't used it for so long, and I got some help from a member that I see as a rather advanced user, and together we were unable to get that package to work.  I assume at this point it's useless to continue down that path, as the Intel driver package should be out soon (hopefully) which will render the ndiswrapper solution and the third party driver solution useless.  However, it is still interesting to see the errors and problems we ran into while trying to install that driver.

Some of the errors I would get regularly pointed to the makefile and make commands pointing to the /lib/modules/2.6.20-16-generic/source directory instead of /lib/modules/2.6.20-16-generic/build directory.  In my install, there was no source directory in /lib/modules/2.6.20-16-generic/ and I kept getting errors stating "$SHELL not set to /bin/bash", and suggested I run make SHELL=/bin/bash.  However showing the variable, it stated that SHELL=/bin/bash and the cycle continued.

I challenge any knowledgeable Ubuntu user to try a fresh install on a Dell Inspiron e1505/6400 with an Intel 4965AGN card and get it working with the driver at intellinuxwireless.org and see what you come up with.

Sorry for the long winded install, I'm glad it's working as it is, and thanks for the tutorials.  Now, to tackle BlueTooth :D

---

