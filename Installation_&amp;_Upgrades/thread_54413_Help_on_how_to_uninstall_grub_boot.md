---
title: "Help on how to uninstall grub boot"
date: 2005-08-04
forum: Installation &amp; Upgrades
---

### Post by Schmoozer3348 on 2005-08-04
Hello,

I'm a linux n00b, so this question won't be too hard. Before I installed Ubuntu I found a great program to partion hard drive space, create free space, etc., which allowed me to keep Windows on my laptop. I found that the disk editorer also had a dual boot option which I like much more than Grub Boot. My question is two fold, How do I uninstall Grub Boot, and is it a good idea to do this? The reason i ask is becuase Grub Boot has 4 or 5 kernal start up options along with XP where as the other dual boot program only gives me the option of XP or Ubuntu. Are these extra kernal startup option used/nesicarry/important?

Thanks,
Logan

---

### Post by hod139 on 2005-08-04
The reason grub lists many kernels at boot is because you have them installed.  You can use synaptic to remove older kernel images, and it will automagically remove them from the grub listing.

Search for 'linux-image' and remove the ones you no longer want.

---

### Post by Schmoozer3348 on 2005-08-04
[QUOTE=hod139]The reason grub lists many kernels at boot is because you have them installed.  You can use synaptic to remove older kernel images, and it will automagically remove them from the grub listing.

Search for 'linux-image' and remove the ones you no longer want.[/QUOTE]

Ok, good to know, but I have plenty of diskspace. I'm more interested in uninstalling Grub (Dual-boot).

---

### Post by hod139 on 2005-08-04
First, the easy way assuming 2 things, you installed grub to the master boot record, and the other OS is WindowsXP.

Boot off of the XP cd and go to the recovery console by pressing 'R'.  Use the command 'fixmbr'

That will wipe grub off the system.

Just did a quick google search, and if you don't have windows XP you can follow the instructions [here](https://www.redhat.com/archives/redhat-list/2002-September/msg02704.html)

---

