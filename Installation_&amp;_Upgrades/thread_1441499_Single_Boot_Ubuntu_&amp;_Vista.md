---
title: "Single Boot Ubuntu &amp; Vista"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by coolbeanscoolbeans on 2010-03-28
hi everyone! :D well im new here and to ubuntu and i need some help please?

well i installed ubuntu single boot only (which wasnt smart of myself) and i really do like ubuntu it's just that it's difficult for myself to not live without itunes and photoshop. :( so now what im going to explain might be a bit confusing but here goes... im trying to reinstall vista on my dell 1525 laptop. while installing vista the first part says "pick a driver for vista to install on" (somthing like that) and then on the bottom it says "Windows can't be installed because it requires partition formatted as NTFS" and so it won't let me move on. 

so in general... How do i remove Ubuntu 9.10 Single Boot and replace it for Vista Home Premium SP1?

Thank you so much in advance!:biggrin:

btw: my computer specs-
Dell 1525 Inspiron
Ubuntu 9.10
Windows Vista Home Premium SP1
Single Boot for Ubuntu

---

### Post by presence1960 on 2010-03-28
> **coolbeanscoolbeans said:**
> hi everyone! :D well im new here and to ubuntu and i need some help please?

well i installed ubuntu single boot only (which wasnt smart of myself) and i really do like ubuntu it's just that it's difficult for myself to not live without itunes and photoshop. :( so now what im going to explain might be a bit confusing but here goes... im trying to reinstall vista on my dell 1525 laptop. while installing vista the first part says "pick a driver for vista to install on" (somthing like that) and then on the bottom it says "Windows can't be installed because it requires partition formatted as NTFS" and so it won't let me move on. 

so in general... How do i remove Ubuntu 9.10 Single Boot and replace it for Vista Home Premium SP1?

Thank you so much in advance!:biggrin:

btw: my computer specs-
Dell 1525 Inspiron
Ubuntu 9.10
Windows Vista Home Premium SP1
Single Boot for Ubuntu

To reinstall a Vista only system boot from the Ubuntu Live Cd, choose 'try ubuntu without any changes." When the desktop loads open a terminal and run ```
gksu gparted
```

This will open gparted so you can remove any ubuntu partitions by right clicking them and choosing delete. Then click the green check mark on tool bar at top to apply. Let gparted complete-when it is done your whole disk should be unallocated space(grey). Leave the disk as unallocated space. Reboot without the Live Cd and then boot with the Vista DVD to install Vista.

If your only issues are itunes & photoshop you may want to consider setting up a dual boot with Ubuntu/Vista. You will need more detailed instructions on how to set that up. If that is what you want to do post back.

***_P.S. Back up any data you don't want to lose prior to doing any of the above._***

---

### Post by Timmer1240 on 2010-03-28
Google G parted live download that burn it to a cd put that in the drive of the laptop and reboot that will let you keep the ubuntu by resizing that partition creating anew one format the new partition to ntfs.Then your windows cd will see the newly created partition and should beable to install along side Ubuntu.Gparted live its a great tool!

---

### Post by coolbeanscoolbeans on 2010-03-29
> **presence1960 said:**
> To reinstall a Vista only system boot from the Ubuntu Live Cd, choose 'try ubuntu without any changes." When the desktop loads open a terminal and run ```
gksu gparted
```

This will open gparted so you can remove any ubuntu partitions by right clicking them and choosing delete. Then click the green check mark on tool bar at top to apply. Let gparted complete-when it is done your whole disk should be unallocated space(grey). Leave the disk as unallocated space. Reboot without the Live Cd and then boot with the Vista DVD to install Vista.

If your only issues are itunes & photoshop you may want to consider setting up a dual boot with Ubuntu/Vista. You will need more detailed instructions on how to set that up. If that is what you want to do post back.

***_P.S. Back up any data you don't want to lose prior to doing any of the above._***

Thanks this helped! :) I used the gparted using the live disk and I formated the whole ubuntu partition to NTFS I installed vista (it worked!) Then I think I went to command prompt in vista and typed in fix /mbr to get rid of the grub loader. :D

---

### Post by presence1960 on 2010-03-29
Glad you got it the way you wanted! Enjoy.

---

### Post by DanOD1000 on 2013-03-01
Hi.

I tried doing that and the only thing that happened was when I turned on my computer (after doing what you said) it just keeps on restarting over and over again????

Thanks in advance

---

