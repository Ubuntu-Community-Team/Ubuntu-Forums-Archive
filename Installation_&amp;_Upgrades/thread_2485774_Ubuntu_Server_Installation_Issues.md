---
title: "Ubuntu Server Installation Issues"
date: 2023-04-09
forum: Installation &amp; Upgrades
---

### Post by stanstan10 on 2023-04-09
I downloaded the x64 file from the Ubuntu site and flashed it to my SD card. Put it in my Pi400 but I am having some issues. I am getting multiple errors such as the ETX4-fs and the ERRNO 30. 
I tried to find a solution for the ERRNO 30 and I found a previous answer to use:
> $ phablet-config writable-image
Once I do that it prompts me to login, however, I cannot. I tried the default ubuntu username and password but it tells me its incorrect. What do I do?

---

### Post by TheFu on 2023-04-09
Raspberry Pi computers are ARM CPUs, not x86-64.
I suspect there is much background information that is not being shared, but necessary.  We will generally assume an Intel x86-64 CPU here, so if you use **anything** else, be very, very clear about it and where you got the installation media (a link).  For example, there are many different Ubuntu images and some only work with a SSO account previously enabled.  The Canonical SSO requires a registered account with Canonical.

---

### Post by MAFoElffen on 2023-04-10
Raspberry Pi devices generally, out-of-the-box boot from ARM system images burned to MicroSD Cards. The first thing is to get an Ubuntu Raspberry Pi Image. So not just an install image for ARM, but specifically for Raspberry Pi...

Instructions:
RE: [https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)

---

### Post by ActionParsnip on 2023-04-13
[https://ubuntu.com/download/raspberry-pi/thank-you?version=22.04.2&architecture=desktop-arm64+raspi](https://ubuntu.com/download/raspberry-pi/thank-you?version=22.04.2&architecture=desktop-arm64+raspi)

---

