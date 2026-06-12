---
title: "restoring virtualbox vms and vdisks after Gutsy install"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by hise0001 on 2007-10-20
I had the personal use version of Virtualbox running on my amd64 Fiesty installation.  I copied the .vdi file and the virtual machine directory (containing the xml file and logs directory) to a backup drive.

I then proceed to do a fresh install of amd64 Gutsy and installed the OSE version of virtualbox from the repository.

I tried create a new vm that mounts my old vdisk; but, when it starts to boot, I receive the following WinXp boot error message "A disk read error occured Press Ctrl+Alt+Del to restart"

Is there anyway to get virtualbox to recognize my old virtual machine and disk so I don't have to go through another 7 hours of installs and updates of Win XP?

--Hise

---

### Post by gavinjb on 2007-10-20
Hi,

All I usually do I copy the disks back to the same location /home/yourusername/.VirtualBox/VDI and then reconfigure in VB Disk Manager

---

### Post by hise0001 on 2007-10-20
That's what I did... I wonder if I should have released the vdi file from the the virtual machine before I copied it to the backup drive.

Oh well... I'm in the middle of the SP2 update right now, so hopefully it'll be back to normal by the end of the day.

Thanks.

---

