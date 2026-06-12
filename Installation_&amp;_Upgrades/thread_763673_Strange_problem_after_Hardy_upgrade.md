---
title: "Strange problem after Hardy upgrade"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by rivera151 on 2008-04-23
Hey guys.  I have a problem after my Hardy install with my network interfaces.  Basically, my OS can't see the internet.

This might actually be two issues, 'cause my madwifi driver is having troubles with Hardy, but lets get to the essential stuff, let's start with my Ethernet card.

I use wicd as a network manager, and I can connect fine to the network (I get an IP address assigned, I can get one through ifup too), but as soon as I run a command in the terminal I get the following:

```

ricardo@chupalaptop:~$ sudo ifup eth0
sudo: unable to resolve host chupalaptop

```


So I can't resolve my own hostname.  I also try pinging my home router (which just gave me an IP address), but pinging is also unreachable, which also discards (I think) DNS issues.  Weird, huh?

While were at it, If there's any tricks to getting madwifi compiled in Hardy, throw me a bone please!

Thanks guys!

---

### Post by Pumalite on 2008-04-23
Here is some reading material:
[http://ubuntuforums.org/showthread.php?t=618596&page=2](http://ubuntuforums.org/showthread.php?t=618596&page=2)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
[http://ubuntuforums.org/showthread.php?t=586387](http://ubuntuforums.org/showthread.php?t=586387)
[https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
[http://ubuntuforums.org/showthread.php?t=612065](http://ubuntuforums.org/showthread.php?t=612065)

---

### Post by rivera151 on 2008-04-23
> **Pumalite said:**
> Here is some reading material:
[http://ubuntuforums.org/showthread.php?t=618596&page=2](http://ubuntuforums.org/showthread.php?t=618596&page=2)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
[http://ubuntuforums.org/showthread.php?t=586387](http://ubuntuforums.org/showthread.php?t=586387)
[https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
[http://ubuntuforums.org/showthread.php?t=612065](http://ubuntuforums.org/showthread.php?t=612065)

Thanks for the reading material.  Most links there are for setting up a wifi card with ndiswrapper, which although functional (and necessary in some unfortunate cases), it is nevertheless a hack.  I'd like to stick to madwifi, I know it works on my system since I compiled the driver for source on my Gutsy and it worked great.  

I'd like to know if anybody has run into problems compiling madwifi under Hardy, and if they fixed those problems, how did they do it.

**But most importantly, I'd like to get my eth0 interface working.  If I can't use my eth0 interface (even though it obtains an IP), then something (probably trivial and stupid) is up, and if I don't get that fixed, something tells me my wireless won't work either.**

Once again, thank you for your quick reply and interest in helping me.

---

### Post by rivera151 on 2008-04-23
OK.  Solved.  A bridging setup that was not giving me issues in Gutsy was causing D.O.S.  Tweaked /etc/network/interfaces and got back my eth0.

Then uninstalled custom madwifi driver and installed from repos (now that eth0 works) linux-restricted-modules-generic and linux-restricted-modules-i386 and madwifi-tools (Ubuntu madwifi compilation included in these).  Network is back to normal.

ALSA is now screwed, but I think I can handle that.  Thanks for everything.

---

