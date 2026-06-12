---
title: "Uninstall Ubuntu"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by humanintrouble on 2007-03-03
How do I uninstall Ubuntu? If just reformat the partitions, the GRUB will not be reverted back to windows only right?

Thanks in advance.

---

### Post by ingo on 2007-03-04
No need to toy with grub, is there, apart from telling it that the default should be windowze. As for the rest, you got it in one.

Shame you decided against Ubuntu, might Kubuntu (much superior in my opinion) tickle your fancy?

---

### Post by azurehi on 2007-03-05
Linux/Ubuntu newbie here, currently dual boot with XP and 6.10 Edgy.  As a learning exercise, I have unistalled ubuntu using the live cd gparted:  deleting the linux partitions, leaving only the windows xp and unallocated space on NTSF.  I had read somewhere that before booting after the linux partitin removal, I needed to boot form the windows XP installation disc, go to "repair" and then to "fixmbr".  I did this and found on reboot that XP came up as usual.  I have not tried just rebooting without the "fixmbr" step.  Is this step necessary?
I enjoy ubuntu and am getting it set up to my liking.  However, having tried a number of live cd distros (not installing), I have been watching the progress of pclinuxos.  Test3 2007 was released yesterday and looks pretty good.  I am considerfing adding a 2nd sata HD to use for testing linux distros, leaving ubuntu/XP on the first until i can leave windows in the dust.

---

### Post by rsambuca on 2007-03-05
If you simply delete the ubuntu partitions you will get a grub error.  You will then need to use your XP disc and run the "fixmbr" command to wipe out Grub from the MBR.

---

