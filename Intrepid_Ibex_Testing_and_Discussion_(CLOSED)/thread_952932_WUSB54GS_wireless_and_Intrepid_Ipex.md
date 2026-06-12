---
title: "WUSB54GS wireless and Intrepid Ipex"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Shaded Spriter on 2008-10-19
I am currently backing up my files to upgrade to Intrepid and remembering my installation of hardy I need to make sure one thing is working "out the box" and that is my wireless USB dongle.

It is the linksys WUSB54GS and to get it to work on hardy I had to use the instrctions [mentioned here.](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB) (I also just noticed how out of date them instructions are).

I have also heard that Intrepid has imrpoved wi-fi support.

---

### Post by Shaded Spriter on 2008-10-20
Sorry I have to do this but...bump.

---

### Post by lonniehenry on 2008-10-20
The new kernal for Intrepid will see your wusb54gc and just work. I just plugged it in and it worked with no problem.  The only problem is that when my laptop sleeps, it doesn't wake up with the wireless card inserted.  I just pull it out, sleep the machine. On waking I just plug it in and the wireless then automatically connects.

---

### Post by beartard on 2008-10-20
I use this dongle with my desktop.  It works without any coaxing.

---

### Post by PinkFloyd102489 on 2008-10-20
> **lonniehenry said:**
> The new kernal for Intrepid will see your wusb54gc and just work. I just plugged it in and it worked with no problem.  The only problem is that when my laptop sleeps, it doesn't wake up with the wireless card inserted.  I just pull it out, sleep the machine. On waking I just plug it in and the wireless then automatically connects.


This means the wireless card is generating activity that keeps the machine from sleeping.

---

### Post by lonniehenry on 2008-10-20
Unenabling wireless before suspending doesn't let it return.  It must be the usb part of the wireless card causing it to not work.  Pulling it allows sleep and return to awake. Interesting but not a major problem.

---

