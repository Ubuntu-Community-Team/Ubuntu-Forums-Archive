---
title: "Ubuntu not detecting Windows 8 installation."
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by jonashendrickx on 2013-02-18
I installed Windows 8 and it created a 350MB partition and then the 550GB partition.

I have about 400GB left for Ubuntu.

But when i want to install using the wizard, I see a empty partition table.

I have disconnected all other drives, USB Sticks to make sure it was correct.

What do I do ?

If I install UEFI mode I screw up the previous installation every time.

The only solution seems to be to install Ubuntu on my second hard drive as a work around.

---

### Post by grahammechanical on 2013-02-18
You may need to read up on Microsoft Dynamic disks.

[http://msdn.microsoft.com/en-gb/library/windows/desktop/aa363785(v=vs.85).aspx]("http://msdn.microsoft.com/en-gb/library/windows/desktop/aa363785(v=vs.85).aspx")

If the installation of Windows created dynamic disk partitions on that hard disk then the Ubuntu partitioner will not see that empty space as Linux cannot read Microsoft dynamic disks. The format is proprietary.

Regards.

---

### Post by oldfred on 2013-02-18
Post this.

       sudo parted /dev/sda unit s print
    

But a couple of users in another thread, both found with a UEFI system, 12.04.2 only offered UEFI install. I think they were going to file a bug report.

You should get from the UEFI menu, the option to boot installer in UEFI mode or BIOS/legacy/CSM or whatever is not UEFI mode. How you boot it is how it installs.

---

