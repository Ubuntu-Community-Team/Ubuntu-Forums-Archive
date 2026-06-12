---
title: "Wireless configuration"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Stochastic on 2008-10-16
Hi, I just installed Ibex - looks nice, once that wallpaper and login screen are changed.

I'm trying to get my wireless network configured, but I'm having the hardest time ever!  I've got a broadcom 43xx chipset and the proprietary drivers are installed (the blue light is on and everything) but I can't see any networks in the drop down menu, and when I attempt to connect to my network it's not letting me.  Any hints?  any way to see all the networks that are in range?

---

### Post by techdude3177 on 2008-10-16
the network manager should pick up all the networks in range based on your drivers.  my intel drivers last time were proprietary drivers and didnt put up some of my neighbors wireless networks now with these new drivers i put them up no problem.

right click on the network-manger applet and click edit connections and manually enter in your network, it SHOULD connect automatically then once you fill in all the proper information.

---

### Post by Stochastic on 2008-10-16
I've even put the wireless connection in manually there.  It still doesn't show up in the drop down menu, and it fails to connect.

Here's a little more info about my chipset```
~$ lspci | grep Broadcom
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by Stochastic on 2008-10-16
ahh, I see the problem now, I have my network set to be a 64-bit WEP, but there's only 128-bit options in the network manager.  How can I fix this, I'd rather not have to change the network key on all the computers in the house?

---

### Post by techdude3177 on 2008-10-16
at my work they still use 64bit WEP, they figure whoever is gonna get on is gonna get on no matter what but this makes it harder for someone just driving by to get on. 

anyways. i still use the 128-bit selection in the network-manager and it still connects to the network automatically. 

if you have a passphrase try using that instead.

---

### Post by dracule on 2008-10-18
How do i find out if this is effecting me? I used the B43 driver in 8.04

I have a fresh install of 8.10 (the latest beta) and it says that the "wl" driver is installed; however, nothing shows up in nmapplet 0.7.0.

I know that the only router nearby (the one i am trying to connect to) uses WPA Enterprise.

---

### Post by burnetbj on 2008-10-18
Hi there

I had the same issues the other day after updates my wireless was hosed....put that sucker on hardwire and run your update manager the newest updates released fixed wireless right away.

Mine wouldnt even allow for wireless to show up as a option like it couldnt see the onboard wireless but after the updates it showed up properly again

---

### Post by dracule on 2008-10-18
> **burnetbj said:**
> Hi there

I had the same issues the other day after updates my wireless was hosed....put that sucker on hardwire and run your update manager the newest updates released fixed wireless right away.

Mine wouldnt even allow for wireless to show up as a option like it couldnt see the onboard wireless but after the updates it showed up properly again

crap, no wired internet is available to me :|

i guess ill have to sweet talk someone into sharing their wireless over ethernet.

---

### Post by dracule on 2008-10-18
> **burnetbj said:**
> Hi there

I had the same issues the other day after updates my wireless was hosed....put that sucker on hardwire and run your update manager the newest updates released fixed wireless right away.

Mine wouldnt even allow for wireless to show up as a option like it couldnt see the onboard wireless but after the updates it showed up properly again

but mine shows the option for wifi, but just no Access Points listed like OP. 

@OP how did you fix it to show others?

---

### Post by colinpat on 2008-10-19
I can only get wireless connection by using kernel 2.6.24-19 which has the iwl4965 driver.
Wireless won't work with any of the 2.6.27 kernels.
Acer TM 7720 with PRO/Wireless 4965 AG or AGN Network Connection.
Can anyone help me put the iwl4965 driver in the 2.6.27 kernel??

---

