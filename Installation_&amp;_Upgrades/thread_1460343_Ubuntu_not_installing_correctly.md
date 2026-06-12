---
title: "Ubuntu not installing correctly"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by Tlawrence on 2010-04-22
I recently installed Ubuntu onto my laptop, and decided to make the switch on my desktop as well. The installation ran identically as it did on the laptop. However, after the installation was complete and I restarted to complete the process The OS didn't wouldn't load. The message the repeated was something along the lines of "media not found". I restarted but with the installation disk in the drive, and was able to load Ubuntu. Problem was it wasn't functioning correctly. On the desktop there is an icon that says "instalation", and in the top right corner the account name reads "ubuntu". I ran the installation the second time using the icon and still, same problem. I restarted again, and the original Windows Vista OS loaded.


Yeah. Seems both OS are on there, Ubuntu half installed or installed incorrectly. 
Is there anyway I can correctly install Ubuntu and remove Vista, or remove Ubuntu, leaving Vista available and restart the process?

I'm sure once I sort this out, looking back I'll be able to laugh at this.

---

### Post by Anthon on 2010-04-22
I have had the same problem on some desktop machines with mixed IDE, SATA drives in the past.
Have you tried to boot from CD and in the CD startup menu to select boot from harddrive? 
That has helped me out a number of times.
The solution probably lies in checking the output of the normal bootprocess and finding which drive is allocated to what device and than changing the /boot/grub/menu.lst file on the harddisk (after booting from CD and mounting the drive).

---

### Post by Tlawrence on 2010-04-26
Yeah I have no idea, is there any step by step process for fixing this?

---

### Post by Tlawrence on 2010-04-27
Bumping. 
Can anyone explain how to correctly remove either windows or ubuntu, and correctly install Ubuntu with the current situation on the computer.

---

### Post by varunendra on 2010-04-27
What are the specs of your desktop? Branded or assembled, original os it came with, BIOS' boot-sector antivirus status, etc.?

I had similar problem with an IBM PC years ago. Turned out to be Auto-Recovery mechanism provided by IBM.

---

