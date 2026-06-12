---
title: "How to boot Ubuntu 11.04 ?"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by Amoranemix on 2011-08-07
Dear Ubuntu community members,

I am trying to use Linux to copy a hard drive for the sake of gaining a little practice with Linux. I was given an Ubuntu CD which was probably downloaded and burned.

My machine is an E 6750, with 1 Windows Vista partition on the Master drive called C (475GB) and 1 XP Pro partition on the slave drive called D (90 GB). Another 365G of D is free.

I asked the installer to install Ubuntu along the other Oses. It created what it called an 8GB swap file on D (it shows as green). I don't know whether it installed anything. The 'installation' ended with the enigmatic “ready when you are...” and and only way to proceed was by cutting power or resetting (but the interface was still response, so it didn't seem to have crashed).

In Vista I asked EasyBCD to add a GRUB2 entry in the bootloader.

Restarting and choosing the new entry in a few seconds gives me the
GRUB>
prompt.
On the internet somewhere it says that means that it couldn't find some file.

I again tried the installer. Picked the something else option, meddled a bit with partitions (not really knowing what I was doing since the installer provides no explanation), but when asked to install the installer only produced an error I believe about a missing root file. So asked it to do an automatic install again. This time the installer asked me to distribute the remaining 360GB or so of free space between Ubuntu 11.04 and Ubuntu (again without explanation). I decided for 60GB for Ubunto 11.04. After the installer was ready when I was I reseted the computer.

In Windows I asked EasyBCD to add a LILO entry to the bootloader. When restarting and choosing that new entry it only produces a blinking cursor.

According to the computer manager in Vista drive D has following partitions :
88GB : system, active, primary partition
56GB : primary partition
305GB : primary partition
8GB : primary partition
8GB : primary partition

Can anyone please tell me how to boot Ubuntu with a GUI ?

---

