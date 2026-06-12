---
title: "Modem disconnects LTS 10.04 Live USB"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by jwalling on 2010-10-15
I use an analog modem and wifi to access the internet.

I am using Ubuntu LTS 8.04 on a laptop and have an analog modem connected via USB serial cable.  _The dialup feature and the modem work flawlessly._

I am testing LTS 10.04.1 on a live USB drive that I purchased preinstalled from On-Disk. 

On the live USB drive, I am able to get a dialup connection with my ISP long enough to pull up a web page with the browser.  However, the analog modem disconnects within minutes with exit codes 16 or 17. 

Man pppd:
16     The link was terminated by the modem hanging up.
17     The PPP negotiation failed because serial loopback was detected.

**My questions are**, how to do I track down the dialup setting(s), or file configuration(s) that is causing the disconnects?  Is the problem likely due to a poorly worded AT modem command?

I want to get this problem resolved before I proceed with upgrading from 8.04 to 10.04.1.  Thanks for your suggestions.

===============
I found a possible solution: pppd nomagic
I am using Gnome PPP.  Where/how do I add the nomagic option to pppd?

---

### Post by mörgæs on 2010-10-16
Maybe a little off topic: 

Any Ubuntu release will need a steady stream of downloaded bugfixes, often more than 20 MB in one go. I would not recommend trying this over a dial-up modem.

---

### Post by jwalling on 2010-10-16
> **mörgæs said:**
> Maybe a little off topic: 

Any Ubuntu release will need a steady stream of downloaded bugfixes, often more than 20 MB in one go. I would not recommend trying this over a dial-up modem.

I don't use dialup for Ubuntu updates. I use wifi for large downloads.  
I use dialup in one location that doesn't have wifi or broadband access.

---

### Post by jwalling on 2010-10-17
I reproduced the error message
"The PPP daemon has died. (exit code = 17)"
on the laptop running 8.04 by using the wvdial command and Gnome-PPP

The error doesn't occur when running pppconfig & pon/poff on the same platform under running Ubuntu 8.04.

wvdial command uses /etc/wvdial.conf.  

It looks like pppconfig & pon/poff does not have the same problem as Gnome-PPP/wvdial.

---

