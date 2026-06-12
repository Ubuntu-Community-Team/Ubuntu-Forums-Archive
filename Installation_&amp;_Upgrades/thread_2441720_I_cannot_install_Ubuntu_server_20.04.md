---
title: "I cannot install Ubuntu server 20.04"
date: 2020-04-26
forum: Installation &amp; Upgrades
---

### Post by mattb55 on 2020-04-26
I have been trying for two days now to install Ubuntu server on my old pc. It runs a gigabyte mobo with an 8 core ryzen cpu. First errors are listed when booting from the cd bios. E.g mounting failed. Can not connect to Plymouth etc.

Eventually it loads to install and when I reach the network connections it cannot find any even though I have a Ethernet plugged in directly

---

### Post by TheFu on 2020-04-26
Create a USB flash drive with a desktop Ubuntu, so you can boot that any run "Try Ubuntu", then install and run **inxi -Fz**.  Post the results here.

Did this hardware run any Linux previously? If so, which releases?
I remember seeing the "Cannot connect to Plymouth" text on an install yesterday. Don't recall which. It didn't seem to matter.

The ethernet device appears to not have drivers for the server.  How experienced with Linux are you?  Ubuntu Server doesn't have any GUI, will that be a problem?  I ask because this is your first post.

---

