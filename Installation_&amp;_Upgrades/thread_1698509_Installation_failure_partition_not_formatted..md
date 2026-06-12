---
title: "Installation failure partition not formatted."
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by FleshGordon on 2011-03-02
I tried to install mythbuntu version 8.10, I set the swap partition (sad6), and the root partition (sda5), which is a currently occupied ext3 partition. I ticked the format box to clear the existing data.
Installation proceeded without any errors, except for the read_error on dev/sr0 message at the end.
After installation and reboot, the partition was not formatted, and still contained all the original data :confused:
What do I need to do to ensure the installation runs correctly?
T.I.A.
 
Carlton.

Solution: I had to set the HDD as slave, and the cdrom to Cable Select Master. Installation performed correctly:).

---

