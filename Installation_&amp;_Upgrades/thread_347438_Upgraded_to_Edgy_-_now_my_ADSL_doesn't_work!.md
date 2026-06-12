---
title: "Upgraded to Edgy - now my ADSL doesn't work!"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by John E on 2007-01-27
I'm currently using a Speedtouch 330 ADSL broadband modem. I remember from when I installed Dapper that it isn't very well supported and it was quite traumatic to get it to work. Now I've upgraded to Edgy and the Speedtouch ADSL modem has stopped working. Do I need to install a new driver or change a config file or something?

---

### Post by John E on 2007-01-31
Can anyone help with this? I just need to know whether the (10 week old) driver for Dapper will still work for Edgy - or should I be looking somewhere for a new driver?

---

### Post by frodon on 2007-01-31
Think to use the forum search function first, it looks that many users asked this so you should find easily the answer in the forum searching a little bit ;) :
[http://ubuntuforums.org/showthread.php?t=339845](http://ubuntuforums.org/showthread.php?t=339845)
[http://ubuntuforums.org/showthread.php?t=302879](http://ubuntuforums.org/showthread.php?t=302879)
[http://ubuntuforums.org/showthread.php?t=317352](http://ubuntuforums.org/showthread.php?t=317352)
[http://ubuntuforums.org/showthread.php?t=315029](http://ubuntuforums.org/showthread.php?t=315029)
[http://ubuntuforums.org/showthread.php?t=308057](http://ubuntuforums.org/showthread.php?t=308057)
[http://ubuntuforums.org/showthread.php?t=303585](http://ubuntuforums.org/showthread.php?t=303585)
[http://ubuntuforums.org/showthread.php?t=291904](http://ubuntuforums.org/showthread.php?t=291904)
[http://ubuntuforums.org/showthread.php?t=302879](http://ubuntuforums.org/showthread.php?t=302879)

---

### Post by John E on 2007-02-01
Well, after reading those threads I realised that the offical Ubuntu instructions are the same as [these instructions]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html") which I've already followed. I figured out that my VP & VC numbers are 0 & 38 respectively and that my ISP uses PPPoE.

After following the (six pages) of setup instructions I've arrived at a stage where the SpeedTouch modem appears to work (i.e. the LED's flash in the way they're supposed to flash) but I can't connect to any web sites.

Page 3 of the instructions says that I can enable a "Debug" mode which will write some info to the system log. However, it doesn't say what that log file is called. If I enable the Debug option, where would I need to look to find the relevant information?

---

### Post by usererror on 2007-02-01
are you actually getting an IP from your ISP?  ( ifconfig eth0 )

Is your DSL modem connected directly to the NIC on the back of the PC?  Do you not have a router in between the PC and the DSL modem?

---

### Post by John E on 2007-02-01
Thanks for the response. My modem is connected to my PC by USB (no router in the chain). I assume that my ISP is providing an IP address because the same hardware works under Windows. In fact, it was also working under Dapper until I upgraded to Edgy so I'm guessing that the problem must be a configuration issue at my end.

---

### Post by John E on 2007-02-02
I found a log file called **/var/log/syslog**. It's quite lengthy but towards the end, it seems to load the Speedtouch drivers successfully. There are two drivers called **speedtch-1.bin** and **speedtch-2.bin**. I assune that one gets loaded into the PC and one into the actual modem.

The modem LEDs flash, exactly as described in the setup instructions - so I assume that the drivers are loading correctly. However, further down the file, it says that the Speedtouch device cannot be found. Any ideas anyone?

---

### Post by usererror on 2007-02-02
Is it possible for you to connect your PC to your DSL modem with a Network cable instead of USB?  That way you dont need any drivers, etc, so much easier in my opinion.

---

### Post by John E on 2007-02-03
In case anyone else has this problem, it was caused by the change from Dapper to Edgy. Basically, there are 2 types of driver for this device. Dapper uses a "user mode" driver whereas Edgy uses a "kernel mode" driver. Unfortunately, whilst Edgy does install the kernel mode driver, it doesn't uninstall any previous user mode driver - so I had 2 drivers both fighting over the same hardware. I'm quite surprised that nobody seemed to know about this. I had to go to a different web forum to find out about it.

---

