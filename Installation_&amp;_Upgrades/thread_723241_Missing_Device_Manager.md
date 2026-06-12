---
title: "Missing Device Manager"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by Mike C on 2008-03-13
I just installed Ubunto 7.10 and I'm in the process of trying to get my wireless connection to work.  Going through the Ubuntu wireless troubleshooting document and the first step is, Check for device recognition: Open Device Manager (System &#8594; Administration &#8594; Device Manager).  I try to do that but I do not see Device Manager listed on my menu.  Is there some reason why I would not have Device Manager?  Is this an indication that I had a problem during installation?  Do I need to do something to manually install Device Manager?

Thanks

---

### Post by taurus on 2008-03-13
Do you mean System -> Administration -> Restricted Drivers Manager?

---

### Post by Mike C on 2008-03-13
> **taurus said:**
> Do you mean System -> Administration -> Restricted Drivers Manager?


I coped this directly from the 7.10 troubleshooting doc:

-------------------------------
Troubleshooting
This troubleshooting guide is designed to be carried out in order.

Check for device recognition
Open Device Manager (System &#8594; Administration &#8594; Device Manager).

Check to see the hardware is recognised if it is then the section called “Check for driver”

If your device is not displayed then there ma be a hardware problem. Ensure if it is PCMCIA or PCI that it is inserted correctly.
---------------------------------

I assume this is different from the Restricted Drivers.  The only restricted driver that I have listed after install is a driver for my software modem, and that isn't something I am concerned about.

---

### Post by Rob Hodge on 2008-03-17
I couldn't find the device manager either... and my wireless wasn't working too.

but, i dragged out a cable and got cabled eithernet working. then, i had ubuntu update it's package sources and connect to the mothership... and it prompted me for 199 security and recomended upgrades to the base install... once i let it do that, there was a device manager where the instructions said it was. although the name was phrased slightly different. 

Cheers,
Rob Hodge

---

### Post by ufadkdc on 2008-03-26
If you run the "System/Preferences/Hardware Information" you'll see that the title of the window is "Device Manager", perhaps that is where it disappeared to...

---

