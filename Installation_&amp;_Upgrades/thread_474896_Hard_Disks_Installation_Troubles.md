---
title: "Hard Disks Installation Troubles"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by arranger1044 on 2007-06-15
Hi everyone

I've got some trouble in trying to install ubuntu on a desktop computer that has three hds: a sata harddrive with Windows vista on it, and two ide hds liked by a pci card.I'd like to put Ubuntu on an ide one (i guess it's the master). If the priority is set to the sata one i can't even install it (it stops after select 'Start or Install' saying it can't load or find a file), changed priority i am able to get through the installation but after the reboot a grub error appears and it stucks.....forever.....:)
i think it's an hw problem however i am not able to recognize how it is

---

### Post by maher_79 on 2007-06-15
> **arranger1044 said:**
> Hi everyone

I've got some trouble in trying to install ubuntu on a desktop computer that has three hds: a sata harddrive with Windows vista on it, and two ide hds liked by a pci card.I'd like to put Ubuntu on an ide one (i guess it's the master). If the priority is set to the sata one i can't even install it (it stops after select 'Start or Install' saying it can't load or find a file), changed priority i am able to get through the installation but after the reboot a grub error appears and it stucks.....forever.....:)
i think it's an hw problem however i am not able to recognize how it is


I had the same problem when intalled Ubuntu to dual boot with my vista.  I have one SATA that has Vista on it and another IDE that has all my files (music, movies, and so on).

Now my SATA is 160GB with 2 partitions.  60GB for Vista and applications and the other partition for saving data (i emptied this one as i wanted to install ubuntu on it).  So, what i did is this:

1.  Before I installed Ubuntu, I went to the Bois and disabled the IDE drive (Primary Slave)
2.  Rebooted from CD with Ubuntu and went through normal installation process.
3. When installed - removed CD (keept the IDE disabled) and restarted computer.  I made sure i can boot to both OS.
4. When all good, I enabled the  IDE HD, rebooted and all was good! :)

---

### Post by arranger1044 on 2007-06-15
> **maher_79 said:**
> I had the same problem when intalled Ubuntu to dual boot with my vista.  I have one SATA that has Vista on it and another IDE that has all my files (music, movies, and so on).

Now my SATA is 160GB with 2 partitions.  60GB for Vista and applications and the other partition for saving data (i emptied this one as i wanted to install ubuntu on it).  So, what i did is this:

1.  Before I installed Ubuntu, I went to the Bois and disabled the IDE drive (Primary Slave)
2.  Rebooted from CD with Ubuntu and went through normal installation process.
3. When installed - removed CD (keept the IDE disabled) and restarted computer.  I made sure i can boot to both OS.
4. When all good, I enabled the  IDE HD, rebooted and all was good! :)

ty....i'll try but i'd like to use one ide to keep ubuntu and leave vista on the sata alone....any suggestions to do so?

---

### Post by maher_79 on 2007-06-15
> **arranger1044 said:**
> ty....i'll try but i'd like to use one ide to keep ubuntu and leave vista on the sata alone....any suggestions to do so?

I would think it is possible but i followed this [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) when i did mine.  but remember i had to disable IDE for the above "How To" to work for me.

Good Luck!

---

### Post by arranger1044 on 2007-06-16
thank you i'll try and tell you next week :)

---

