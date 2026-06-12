---
title: "Installation and Partitioning Issues (USB)"
date: 2022-04-15
forum: Installation &amp; Upgrades
---

### Post by hermes-33 on 2022-04-15
Hi All, 

Thrilled to be back on the Linux wagon again after what must be six or more years.

I've so far been able to install 21.10 onto a 64GB USB stick; messed about with it and came to the conclusion that I definitely want to use it on the regular. 

The problem I'm finding is that Ubuntu wont let me install itself onto my USB. I've been able to create a bootable USB that I can access from my boot menu (on a Lenovo Ideapad 310 - into the side of which I had to stick a pin to access).
I understand I need to partition the USB Drive however GParted/Ubuntu in general cant allow me access to as its the (for lack of the technical lingo) source for the Ubuntu files, thus is mounted.

Given this I tried to partition my USB within Windows 10 instead, however Windows wont allow me to. 
I then formatted the USB (thinking I should format it to NTFS, partition it then reinstall the Ubuntu Setup onto one of the partitions, install it onto the USB and be enjoying it once again after an almost 10 year absence...alas not.

Windows wont even let me partition the USB Drive for some reason. I fully realise this isn't a windows forum too, however has anyone any idea what this issue may be? 

I have another 5 days off work and would just LOVE to get back on the Linux train again, but I'm at a loss here. I've even tried installing the Ubuntu ISO onto my other (8GB) USB drive via Rufus so that I could use that to access GParted to partition the 64GB USB, however the ISO doesn't seem to properly install on it.   

Anyway -- I would be very grateful for any help and shall answer any questions asked asap. It seens as though its likely something simple enough, but as I said, its been a good many years since I've delved into Linux and the solutions I may have once known escape me due to how long its been.  
 
Kind Regards,
Hermes

---

### Post by grahammechanical on 2022-04-15
The first thing to take note of is that Ubuntu 21.10 will reach the end of its support life in July 2022. Better to wait until the End of April 2022 when Ubuntu 22.04 Long Term Support (up to 5 years with an option to have Extended Security Maintenance (ESM) for another 5 years) is released.

These are the official instructions for creating a bootable USB memory stick with the Ubuntu installer on it. Put the 22.04 ISO image on the 8 Gb memory stick.

[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview)

Run the Ubuntu installer live session from the 8 GB memory stick and use it to install Ubuntu on the 64 GB USB memory stick as if it was a hard drive. Make sure that the installer is going to install on the 64 GB USB stick and use the Erase Disk and Install Ubuntu options.

Regards

---

### Post by hermes-33 on 2022-04-15
Grahammechanical, my sincerest thanks. As it's 01:23 and I've just fallen asleep/dozed off momentarily and spilled beer all over my lap (and almost my laptop) I believe its wise to shut-down and call it a day for now, however no doubt I will test your suggestion first thing in the morning after which I'll report back as regards wither it worked or not. Very much appreciated Graham - many thanks and all the best. [COLOR=#E8E6E3]
[/COLOR]

---

