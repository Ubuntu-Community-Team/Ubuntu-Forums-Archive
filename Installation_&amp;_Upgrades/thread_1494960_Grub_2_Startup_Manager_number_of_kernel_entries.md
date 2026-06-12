---
title: "Grub 2 Startup Manager number of kernel entries"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by Euphorion on 2010-05-27
Hello

Before Grub 2, one could use the Startup Manager to configure the Grub Menu and in particular limit the number of kernel entries. Since Grub 2 Startup Manager has become very limited and the tab allowing one to limit the number of kernel entries is no longer present.

With Grub 2 you have to be very careful which file you edit when trying to do the above manually and I have not yet found out how to edit the menu in Grub 2.

Can anyone tell me how to edit a or the grub config files in order to limit the number of kernel entries and to configure my own menu, I would like to change the order in which my operating systems are listed.

Thanks in advance

---

### Post by wojox on 2010-05-27
Have a look at Grub2 [Creating the Custom Menu]("https://help.ubuntu.com/community/Grub2#Creating%20the%20Custom%20Menu")

---

### Post by darkod on 2010-05-27
Another option is to simply remove older kernels. Not all of them of course, I always recommend keeping at least two (the latest and the previous that worked fine). But no need to keep all the kernels especially if doing upgrade after upgrade.

Search for linux-image-2.6.xx-yy and mark for complete removal in Synaptics. Run update-grub and the list is smaller right away.

---

