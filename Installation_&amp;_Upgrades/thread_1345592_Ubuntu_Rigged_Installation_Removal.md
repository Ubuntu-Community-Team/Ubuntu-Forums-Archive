---
title: "Ubuntu Rigged Installation Removal"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by sarbaraj101 on 2009-12-04
Hello,

An improper shutdown led to corruption of graphics drivers in Ubuntu 9.10 (upgraded from 9.04) after an update. So, I installed ubuntu 9.10, by creating in a new partition through the Live CD. 

I currently have 2 Ubuntu OSes installed, one healthy and the other rigged. The rigged one does not let me access ANYTHING at all... not even the CUI.

I tried to reclaim the space used up by the rigged install and it turns out that I can not delete the main linux directories (of the rigged install) directly (for eg, the bin, usr, media etc.) from the clean install.

How do I delete those folders of the rigged install?

(NOTE: I do not wish to format the partition and I have about 100 GB of useful data there, but I have only a CD-Writer, and no other source of media to back the data up :( )

Thanks in Advance

-- Sarba

---

### Post by coffeecat on 2009-12-04
The directories and contents that you are trying to remove are owned by root, so you need to invoke sudo powers. See:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

There are two ways, but both require **great care**. You can do irreparable damage and delete all your useful data if you make a mistake.

Either use the terminal and 'sudo rm...', but check, double-check and check again that you are entering the right options and that you have got the path right.

The other way is to 'gksudo nautilus' from the terminal. This will give you a Nautilus file browser with root powers. You must then navigate to where you need to delete stuff. So, if the  root partition of the damaged installation is mounted on /media/mountpoint, navigate there first. But be careful. The root directory structure of your damaged Ubuntu is going to look the same in a Nautilus browser as the root directory structure of your healthy Ubuntu. Check, double-check and check again before deleting anything. You don't get a second chance! If you haven't navigated to the right place it is possible to delete the /usr, /etc, and so on folders and contents of your running healthy Ubuntu. Then you will have two unusable Ubuntu installations.

---

### Post by sarbaraj101 on 2009-12-04
Thanks a lot.

Stupid of me to try to remove it from the GNOME gui...

Thanks again...

---

