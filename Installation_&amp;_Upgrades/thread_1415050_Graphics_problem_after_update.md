---
title: "Graphics problem after update"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by PredatorOC on 2010-02-24
If there is one thing I've learned over the years of using Ubuntu, it's a healthy fear of updating Ubuntu.

Once again, after updating, something has gone wrong with the graphics. When starting the computer, the loading screen shows up, but the login screen is a mangled mess at the top of the screen. And after trying to automatic fix for graphics problems (xfix), the magled login screen simply vanishes after a few flickers.

At this point in the past I've simply reinstalled, but thought I'd ask if there was something to spare me this hassle.

I'm using 9.04 and the graphics card is ATI Radeon HD 4550.

Thanks in advance.

---

### Post by ajgreeny on 2010-02-24
Was there a new kernel, which might mean a reinstallation of the graphics driver for your ATI card?

---

### Post by khelben1979 on 2010-02-25
Have you tried to reinstall the ATi driver which is provided as a non free package in Ubuntu? (search in Synaptic Package Manager)

---

### Post by Mark Phelps on 2010-02-26
To get your screen back, follow the instructions in the link below for removing the ATI driver.  Then, go to hardware and apply the new drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

When the kernel gets updated, you have to remove and install the ATI drivers.

---

