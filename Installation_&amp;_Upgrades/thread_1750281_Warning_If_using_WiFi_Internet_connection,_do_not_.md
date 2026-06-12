---
title: "Warning: If using WiFi Internet connection, do not install Ubuntu 11.04"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by micsu on 2011-05-05
I thought I would share my experience here as I have lost a lot of efforts due to this bug in Ubuntu 11.04. One should consider twice before installing the new release as it doesnt work with WiFi-connection. During these 5 days, no bug fix has been released and there is no easy way to overcome the issue. The same problem occurs in several computers with different hardware.

So please avoid 11.04 if using internet through WiFi!

---

### Post by nlz on 2011-05-05
solutions:

[http://ubuntuforums.org/showthread.php?p=10720776#post10720776](http://ubuntuforums.org/showthread.php?p=10720776#post10720776)

[https://www.linuxquestions.org/questions/ubuntu-63/wifi-not-working-after-upgrade-to-ubuntu-11-04-a-876157/](https://www.linuxquestions.org/questions/ubuntu-63/wifi-not-working-after-upgrade-to-ubuntu-11-04-a-876157/)

[http://ubuntuforums.org/showthread.php?t=1742112](http://ubuntuforums.org/showthread.php?t=1742112)

---

### Post by Jordanbadangayon on 2011-05-05
> **micsu said:**
> I thought I would share my experience here as I have lost a lot of efforts due to this bug in Ubuntu 11.04. One should consider twice before installing the new release as it doesnt work with WiFi-connection. During these 5 days, no bug fix has been released and there is no easy way to overcome the issue. The same problem occurs in several computers with different hardware.

So please avoid 11.04 if using internet through WiFi!
i have upgraded to natty on it's second day of release but i had no problems with internet connection using WiFi. perhaps there is something not right in your system or in your router.

---

### Post by zappadragon on 2011-05-05
> **micsu said:**
> I thought I would share my experience here as I have lost a lot of efforts due to this bug in Ubuntu 11.04. One should consider twice before installing the new release as it doesnt work with WiFi-connection. During these 5 days, no bug fix has been released and there is no easy way to overcome the issue. The same problem occurs in several computers with different hardware.

So please avoid 11.04 if using internet through WiFi!

What was the experience? Did it work at all? Some of the time? Not at all? 

I upgraded from 10.10 to 11.04 using my wi-fi and had no problems other than not liking Unity. So I just logged out and logged in using Classic and life is good. I have had no problems.

---

### Post by MBybee on 2011-05-05
> **Jordanbadangayon said:**
> i have upgraded to natty on it's second day of release but i had no problems with internet connection using WiFi. perhaps there is something not right in your system or in your router.

I've been on Natty since Alpha and it has done fine with my Broadcom (eww) WiFi. 

There are always issues, which is why you should always try a LiveCD before doing an upgrade.

---

### Post by micsu on 2011-05-05
The driver works and connection seems to be on, but is extremely slow. So slow that in reality it doesnt work. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1742537](http://ubuntuforums.org/showthread.php?t=1742537)

I tried every possible trick I could find but nothing helped. Only re-installation of 10.10 solved the problem.

Btw, the live CD works fine, the problem starts after installation.

---

### Post by khushalb on 2011-05-14
My Acer laptop I too cannot connect


iwconfig into terminal, which yields: 

lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID: off/any 
Mode:Managed Access Point: Not-Associated 
Tx-Power= 0dBm
Retry long limit:7 RTS thr: off Fragment thr: off
Power Management: off

---

### Post by Dale61 on 2011-05-14
I initially lost wi-fi when I upgraded my Acer laptop, but still had full access via ethernet.  I do have wi-fi now, but I had to install the Wicd program to get any sense out of it.

If you run with Wicd, you will have to remove network manager, as recommended, as they don't like each other.

---

