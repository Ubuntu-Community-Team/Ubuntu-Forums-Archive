---
title: "Trackpad Stopped Working After Update"
date: 2009-01-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by iaskedalice09 on 2009-01-24
I use the trackpad quite a lot and this morning, I updated the computer. After I rebooted, it didn't work. I'm not sure what package could have caused this. It's a bit of a pain to have to use the spacebar, but I'm doing it anyway.

I'm just posting it here so the community knows about it. If I find a fix I'll post it. I'm sure I'm not the only one out there with this problem.

System Info:
Dell Inspiron 1525n
Kernel Linux 2.6.28-5-generic

Please let me know if you need more info, and/or if this would be more appropriate on Launchpad

---

### Post by iaskedalice09 on 2009-01-24
Launchpad report by me: [Bug #320979 in Ubuntu: &#8220;Trackpad crashed on Jaunty update&#8221;](https://bugs.launchpad.net/ubuntu/+bug/320979)

---

### Post by skinnie on 2009-02-04
I installed a daily build of 3/02/2008 (yesterday lol) and my synaptics touchpad doesn't work too...how can I report that problem?or solve it :D

---

### Post by JohnJackson on 2009-02-04
A new xf86-input-synaptics driver was released the other day, perhaps that's what caused it?

---

### Post by inportb on 2009-02-04
For some people it's a problem with the new driver not recognizing some touchpads as supported devices.

Here's the bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882)
Here's a working hack cited in the bug report: [http://launchpadlibrarian.net/21331801/xserver-xorg-input-synaptics_0.15.2-0ubuntu8%2Brebuild_i386.deb](http://launchpadlibrarian.net/21331801/xserver-xorg-input-synaptics_0.15.2-0ubuntu8%2Brebuild_i386.deb)

---

### Post by spimby on 2009-02-07
Hmmm.. I'm on 8.10 ubuntu...and mine just stopped working.  A mouse connected via the USB port works fine.

---

### Post by olskar on 2009-02-08
You have read this, do you have that installed?

The X.Org synaptics driver is absent from the liveCD, which may prevent touchpad devices from working on laptops. As a workaround, use Ctrl+Alt+F1 to switch to console, log in, run sudo apt-get install xserver-xorg-input-all to download the drivers from the network, and then return to your session with Alt+F7.

---

### Post by dshuck on 2009-02-12
@olskar - you are my hero.  

Thanks for the info.  You just saved me from going back to a previous release.

---

### Post by ormandj on 2009-02-12
> **olskar said:**
> You have read this, do you have that installed?

The X.Org synaptics driver is absent from the liveCD, which may prevent touchpad devices from working on laptops. As a workaround, use Ctrl+Alt+F1 to switch to console, log in, run sudo apt-get install xserver-xorg-input-all to download the drivers from the network, and then return to your session with Alt+F7.

This worked for me, thank you!

---

### Post by iaskedalice09 on 2009-03-07
> **olskar said:**
> You have read this, do you have that installed?

The X.Org synaptics driver is absent from the liveCD, which may prevent touchpad devices from working on laptops. As a workaround, use Ctrl+Alt+F1 to switch to console, log in, run sudo apt-get install xserver-xorg-input-all to download the drivers from the network, and then return to your session with Alt+F7.
Thanks, this worked! Posted the fix to Launchpad.

---

