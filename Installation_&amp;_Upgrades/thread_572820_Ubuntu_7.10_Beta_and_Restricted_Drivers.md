---
title: "Ubuntu 7.10 Beta and Restricted Drivers"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by DarKnyht on 2007-10-10
Have been using the beta of 7.10 since it was available for download.  While I have enjoyed most of the experience, there is one issue that I think needs attention.  The Restricted Manager for Drivers.

I was very happy to find that my Linksys wireles PC Card was detected and the drivers configured for me.  I was tired of having to carry around my ancient Linksys Wireless USB adapter I have been using, and it gave me back one of my USB ports (there are only two on the laptop).  Everything works great until there is a major upgrade that requires a reboot.

Once the machine reboots, I find that the restricted drivers are disabled.  That sole event took me a few hours because Ubuntu doesn't inform you that it disabled your drivers, but that is an entirely different issue.  The frustrating part is that when you go to enable them, it requires that you download the driver from the website.  This is the third time so far, and I feel that the average user will be pissed at having this happen and will not know how to do what I have done (plugged back into the router with a LAN connection and download it).  

My question is two part, why does Ubuntu do this in the first place and why doesn't ubuntu remember that you have previously downloaded the drivers needed?

---

### Post by Pumalite on 2007-10-10
If you have a new kernel, then you have to re-install the drivers because they have to be compiled into the new kernel.

---

### Post by DarKnyht on 2007-10-12
That I can understand.  What I cannot understand is the OS not storing the file downloaded when you set the card up the first time.  I know that I can download the file and save it somewhere for future use myself, but the average computer user is not capable of doing this.  In fact, the average end user will be quite crippled without a WLAN Adapter to get to the internet to access help.

Simply put, the average end user should not have to re-download the driver files every single time the kernel is updated.  The OS should be smart enough to store them somewhere if they were downloaded on the spot for future use, and it probably should notify the end user that it made changes to their configuration that disabled restricted hardware.

---

