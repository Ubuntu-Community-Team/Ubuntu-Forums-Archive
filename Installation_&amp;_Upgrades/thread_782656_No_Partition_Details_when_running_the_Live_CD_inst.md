---
title: "No Partition Details when running the Live CD install"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by Paragtim on 2008-05-05
Hi all,

As a newbie I am stuck with this problem and don't know how to proceed.  I have run the install muktiple times now and can't get the software to work

I am trying to install Ubuntu 8 from the live cd via the install option.  Everything proceeds fine until I get to the partitioner screen where no details of the HD appear and the install cannot proceed.

I have also tried to install from the boot options and from Wubi.  These tell me that the system is installed correctly but when I reboot I only get the following prompt (initramfs) and can proceed no further.

I would really like to be able to install Ubuntu as the only operating system on this machine but it only seems to want to run from the live cd.

Any help you can give would be appreciated

Tim

---

### Post by Paragtim on 2008-05-09
Great Support Guys - Not 1 response in 4 days.  Ah well back to windows then.

---

### Post by Pumalite on 2008-05-09
You just got passed when we were busy. Post:
sudo fdisk -l

---

### Post by Paragtim on 2008-05-19
The solution that worked for me was:

Start system
Press Esc to enter GRUB
Use the lower kernel recovery mode option
The system came back up
Edit the GRUB config file and delete the higher kernel options.

Reboot and its working fine.

Hope this helps those that need it

---

