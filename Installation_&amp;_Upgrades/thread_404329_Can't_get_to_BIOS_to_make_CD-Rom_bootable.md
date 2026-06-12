---
title: "Can't get to BIOS to make CD-Rom bootable"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2007-04-08
I've got this desktop where upon booting, I do not see the usual booting text (memory test, list of slaves, masters, ...). It just goes directly to the choice of O/S  (French XP and recovery console). On that screen, I only have the F8 options (safe mode and other choices).

Pressing DELETE upon booting has no effects.

How do I get to the BIOS then ?

---

### Post by camorri on 2007-04-08
Your hardware has a hot key to enter the BIOS. If you are seeing the prompt with F8 for recovery console, the windoze boot record already has control. 

What is the make and model of your hardware? If you have documentation, the hot key should be in there. Often manufacturers web sites have online doc, you could look there also.

---

### Post by cheatr on 2007-04-08
All you have to do is to search for your motherboard on google and you should find the BIOS it uses, and from that you can find out what hotkey to use. For example i have an asus motherboard which has Phoenix-Award BIOS on it, and i use delete to enter BIOS.

---

### Post by Browser_ice on 2007-04-08
PC manufacturer is IBM. Its a Netvista model.

Its an office PC by the way (we are at work right now and playing around this PC to install Ubuntu while theire is nothing to do).

---

### Post by Browser_ice on 2007-04-08
I found out on the net what the key is. Its F1.

I managed to get to the BIOS and make the CD-Rom the first Bootable device.

Problem is, I think the CD-Rom is defective as it says alot of I/O block errors on the CD.

Tried with Ubuntu, Xubuntu and Kubuntu cds and its the same for all 3.

---

### Post by camorri on 2007-04-08
Did you do a md5sum check on the ISO image before you burned any of the CD's? Were they burned as ISO images?

---

### Post by Browser_ice on 2007-04-08
The Ubuntu and the Kubuntu CDs are the ones I ordered. They are working because they were used on home PCs. The Xubuntu is one I burned.

---

### Post by camorri on 2007-04-08
Well, since the CD's are known to be good, that leaves the hardware. Either its defective, possibly dirty, since the system sites around a business, or the correct driver for the hardware is not on the CD. That would take some investigation. 

IBM's doc is good. You can get the hardware manuals online for most of their systems. That would tell you exactly what drive you have, a little googling and you should be able to determine if this is a driver issue. 

Does the drive work under the install OS?

---

### Post by Browser_ice on 2007-04-08
Unfortunetly, we don't have the XP logon password of the default user.

It is a desktop that was siting on a desk that no one was using. They told us we can take it.  They knew we wanted one to install Linux on it and whipe out XP so they didn't bothered checking the logons on XP.

---

