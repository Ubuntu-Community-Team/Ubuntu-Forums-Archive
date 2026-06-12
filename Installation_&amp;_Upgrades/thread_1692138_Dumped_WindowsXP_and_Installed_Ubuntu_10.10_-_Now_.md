---
title: "Dumped WindowsXP and Installed Ubuntu 10.10 - Now Unable to Connect to the Internet"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by LovetoScrapLeslie on 2011-02-21
After successfully installing Ubuntu 10.10/Netbook on my son's netbook, I decided to install  Ubuntu 10.10 desktop on our old Windows XP computer (NOT dual boot, but 100%) with a  disk.  The desktop has a 2Wire modem connected to it.  The installation went well, but now I have 2 internet connection problems:

(1) If the desktop is off, all of our laptops (Linux + Windows XP) can connect to the internet with the wireless router, but the moment that I turn on the desktop (with the new Ubuntu 10.10 software installed), all internet connections are lost even though I cannot connect to the internet on the desktop.

(2) The "Wireless Network Disconnected" message is grayed out with a red exclamation point on the old desktop with new Ubuntu 10.10 software.  

Please help!!!  I know some about Linux (we had one of the first EEEpc's), but need step-by-step instructions as a newbie.  THANKS!!!!

Leslie

---

### Post by thefasterblueone on 2011-02-21
Did you get all the updates for the desktop?

After installing all updates check System> Administration> Additional Drivers and see if there are any proprietary drivers available.

Then run this in terminal:

```
sudo lshw -C network
```

and post results.

---

### Post by deconstrained on 2011-02-21
> **LovetoScrapLeslie said:**
> After successfully installing Ubuntu 10.10/Netbook on my son's netbook, I decided to install  Ubuntu 10.10 desktop on our old Windows XP computer (NOT dual boot, but 100%) with a  disk.  The desktop has a 2Wire modem connected to it.
Are the 2Wire modem and the wireless router you described the same thing?

This (I'm making a shot in the dark about exactly what kind of devices you're using here) is the way it should be set up:

[DSL line]
|
|
V
[Modem]
|
|
V
[Wireless Router]
|  |  |                           
|  |  V               
|  |  [Computer 1]
|  V
|  [Computer 2]
V
[Computer 3]

(sorry for the bad illustration)

The broadband modem connects via the PPPOE protocol to your internet service provider and leases an IP address. The router connects to the modem and uses it as a gateway (a router in and of itself) via DHCP. Then the router creates a subnet, to which the computers connect (whether wirelessly or via ethernet cables), using the same protocol (DHCP) for obtaining IP addresses.

If the wireless router stops providing internet connections when you turn on/off a computer, something in the works here is set up **terribly** wrong; the connections of each computer to the router and of the router to the modem should be completely independent of one another. For one, check the cabling on the back of the router, and that the port marked "internet" has a cable plugged into it that goes to the modem.

---

### Post by LovetoScrapLeslie on 2011-02-21
> **thefasterblueone said:**
> Did you get all the updates for the desktop?

After installing all updates check System> Administration> Additional Drivers and see if there are any proprietary drivers available.

Then run this in terminal:

```
sudo lshw -C network
```and post results.


When In went to Systems - Admin-Addt'l Drivers, this message appeared:

   "Downloading package indexes failed. Pls
    check Network Settings", and then

    "No Proprietary Drivers are in Use in this
      System".

I cannot connect to the internet -- pls help! TKS!!

---

### Post by thefasterblueone on 2011-02-21
> **thefasterblueone said:**
> Then run this in terminal:

```
sudo lshw -C network
```

and post results.


This maybe helpful.

---

### Post by deconstrained on 2011-02-21
I still think that calming down and double-checking the cabling is in order. **No, Ubuntu could not possibly have messed up your router and modem;** *they're designed to work independently of your computer, as network appliances,* and if they're not happy with a generic LAN client instead of some Windows machine with special software then they're not doing their job properly or were poorly designed. They are not peripherals or computer parts.

Also, a two questions that might be relevant/help diagnose:
- Does the desktop have a wireless device in it, and does it really need to be enabled (since you've indicated it's connected via ethernet cable to the router/modem/whatever)
- Have you tried connecting TO the router - i.e. by [navigating to its IP address in your web browser](http://compnetworking.about.com/od/workingwithipaddresses/f/getrouteripaddr.htm), to check its settings/status? example: if it's 192.168.1.1, then [http://192.168.1.1](http://192.168.1.1)

---

### Post by gordintoronto on 2011-02-21
There seems to be some confusion about what a "2wire modem" is. Could you describe it, please? I went to Google, but I couldn't get any useful information, because "2wire" has been taken over by Pace.

Is it possible to connect to your router with an Ethernet cable, even if it is just temporary?

---

### Post by deconstrained on 2011-03-04
Any luck at all?

---

