---
title: "Recovery mode  boot log Ubuntu Karmic"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by tlcstat on 2010-01-26
Greetings, 
I was troubleshooting a network problem and rebooted my Ubuntu Karmic 2.6.31_17 in recovery mode. While booting I noticed a long list of software modules that the kernel was suggesting that I manually uninstall using apt. Problem is I couldn't get a list of the modules. Does anyone know where that recovery boot might be logged? I have checked the Log File Viewer and can't find it or have overlooked it.
Thank in advance.
tlcstat

---

### Post by mörgæs on 2010-01-27
If you want to remove unneeded packages, you can do it straight from apt-get. You don't need a log file for that. 

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get) 
[http://wiki.linuxhelp.net/index.php/Apt-get_Guide](http://wiki.linuxhelp.net/index.php/Apt-get_Guide)

---

### Post by tlcstat on 2010-01-27
Greetings,
Thanks, I did the apt-get check, then clean, then autoclean. That seemed to be the right process. Thanks for two very good links. I printed them to pdf. Glad I didn't have to do it manually which was the direction I was headed. I have broadband but it did say to avoid deleting archives if you are a dial-up user. Makes sense, you might have to do the download all over again. Everything is working very good but I you think I need to do something else, I would appreciate the feedback.
tlcstat

---

### Post by mörgæs on 2010-01-27
You are welcome. I don't think that you need anything more. 

In general Linux does not need much maintenance. If you just download the bugfixes when they show up in your system and take care that the hard drive always has at least 20 % free space, then you should be all fine.

---

