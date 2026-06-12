---
title: "Windows dual boot installation problems"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by clericclark on 2007-04-24
Hi I wanted to install windows so that i could dual boot them on my computer, but when i insert the windows cd and start up my computer it never reaches the windows insallation screen, it just goes to grub. is there any way for me to install windows without uninstalling ubuntu?

---

### Post by will_in_wi on 2007-04-24
You probably need to set your bios to boot from cd.

---

### Post by raja on 2007-04-24
If you reach grub without booting off the cd, it is because your bios is set to boot from the hard drive first. You have to change the bios settings to allow the system to boot from the cd first. However, windows will overwrite the MBR and you will have to reinstall grub to boot into Ubuntu again.

---

### Post by clericclark on 2007-04-24
how would i go about changing the boot so it boots from cd first and reinstalling grub?

---

### Post by raja on 2007-04-24
You have to enter the bios settings by pressing some key (varies between systems) before it starts booting up. There you can change the order in which devices are booted. 

I suggest you read [this]("http://computer.howstuffworks.com/bios3.htm") to learn something about the bios and [this]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") to fix MBR after windows 'corrupts' it.

---

### Post by clericclark on 2007-04-26
i went to bios and the cd rom is already selected to boot first and then the hard drive. windows installation still does not show up, any ideas?

---

### Post by raja on 2007-04-26
What windows cd is that exactly. I guess it is not a bootable disk. If that is the case, you can use something like Barts PE builder to make a bootable disk to install from.

---

### Post by clericclark on 2007-04-26
its a windows xp with service pack 2 cd. it should work since its the same cd i used to install windows before i had ubuntu.

---

### Post by raja on 2007-04-26
If the boot order is indeed set such that cd boots first, the only reason why that would not happen is that the cd is not bootable. 
Check the bios settings again. Can you see the the light in the cd drive lighting up before grub comes up, suggesting that the cd is searched first? 
Check in another computer if you can to see if you can boot from the cd. Cant think of anything else to do.

---

### Post by clericclark on 2007-05-02
yeah the lights on and the cd works. this is really weird. anyone have any ideas?

---

