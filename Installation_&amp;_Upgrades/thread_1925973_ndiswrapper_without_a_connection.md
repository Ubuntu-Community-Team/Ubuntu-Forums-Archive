---
title: "ndiswrapper without a connection"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by havenoname on 2012-02-15
I would like te know how to solve my problem.

I have a wireless card, and i want to use the newest ubuntu 11.10. My connection only works with ndiswrapper. So what is the easiest way to get ndiswrapper on my ubuntu 11.10 that comes without ndiswrapper. 

- I have a connection on another pc.
- The option to temporarily use a cable for internet is not an option.
- Take into consideration that i'm not an experienced ubuntu user, so dependencies etc are a big issue.

thanks

---

### Post by lkraemer on 2012-02-16
While it's possible your Wifi isn't supported out of the box, it's very unlikely.  If you can get access to the Internet with an Ethernet Patch
Cable, and do an Update, then try to enable the Hardware Drivers, you should find that most Wifi functions.

Other than that, you need to find out what the Wifi Hardware is, and if the Firmware has been installed for that Hardware.

**1. How do I know if I have Broadcom (OR XXXXX) Hardware?**

Open a Terminal Window (Console) and use these commands to get more information on your hardware, wireless, Windows loaded drivers, and Linux drivers that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the output of each command........

Since you are using ndiswrapper, if you want to use the DEFAULT Ubuntu Driver, you will need to REMOVE the Windows Drivers, and ndiswrapper,
because there will be conflicts.......

See this HOWTO:  (It's out of date but the Method is the same)
Just be aware that B43 is no longer the DEFAULT, so replace B43 with whatever your Ubuntu Version uses.

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom)

Keep us informed as to your progress.....

Google and Search are your Friends!

lk

---

