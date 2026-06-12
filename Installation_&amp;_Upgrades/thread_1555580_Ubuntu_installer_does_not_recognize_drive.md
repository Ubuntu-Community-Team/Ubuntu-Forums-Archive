---
title: "Ubuntu installer does not recognize drive"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by maxwevers on 2010-08-18
Hi,

I'm trying to install Ubuntu 10.04.1 AMD64 on my new system (i5-760, P55 Board). Unfortunately the installer does not recognize my drive, however Gparted does see the drive and I can manually setup partitions there, but those do not show up in the installer. The SATA controller is set to AHCI mode, but is not configured as RAID. Screenshot attached.

I also uploaded the debug output from ubiquity, but I couldn't find any clues in it.


Any help would be much appreciated!

---

### Post by Rubi1200 on 2010-08-18
The screenshot shows Ubuntu already installed. Are you trying to install over the current setup?

---

### Post by dabl on 2010-08-18
> **maxwevers said:**
> 

The SATA controller is set to AHCI mode



Change it to "Legacy IDE" or whatever the IDE mode is.  Then the installer should see the disk and partitions.  When you have finished installation and verified that the system is booting and running correctly, you can change the SATA mode back to AHCI, and it should boot and run right.

---

### Post by maxwevers on 2010-08-18
> **Rubi1200 said:**
> The screenshot shows Ubuntu already installed. Are you trying to install over the current setup?

No, I just setup the partitions manually, but it didn't help.

---

### Post by maxwevers on 2010-08-18
I will try to change back to IDE mode.

---

### Post by anubhavrocks on 2010-08-18
Try this:
sudo apt-get remove dmraid

And the run the installer.

---

### Post by maxwevers on 2010-08-18
> **anubhavrocks said:**
> Try this:
sudo apt-get remove dmraid

And the run the installer.

dmraid was indeed the problem. Strange, I thought I tried to unistall it before ;) However now it worked.

Thank you all very much!

---

### Post by Rubi1200 on 2010-08-18
Glad it worked out for you.

Please mark this thread Solved using the Thread Tools near the top of the page. That way others who have faced similar issues will have a starting point for how to solve their problems.

:-)

---

