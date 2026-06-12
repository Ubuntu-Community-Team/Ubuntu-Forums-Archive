---
title: "live CD doesn't work"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by tzg6sa on 2007-11-19
Hi!

My 7.10 live cd doesn't work. After I choose live cd or intall in the menu the kernel will be loaded, but after that i get a black screen and some seconds later the CD stops. I searched in foeum but I didn't manage to choose the appropiate keywords. I have similar experiences with 6.10 with the same machine. The solution was that time, that I had to write in the "boot options" line. I tried noapic and nolapic, but these didn't help me. I have an ASUS A6R notebook with a video card ATI Radeon Xpress 200M.

What should I write in the boot options field?

Thanks!

Zoli

---

### Post by Budly on 2007-11-19
I get the same thing. I am trying to install Ubuntu 7.1 desktop edition. I boot my machine from the installation CD, I get the initial installation menu with the 30 second clock (or whatever), I pick the regular installation and away it goes. At first I get the back-and-forth progress bar just fine but then the screen characters start to look funny. It seems that there is some sort of monitor problem in that the characters become just horizontal lines that appear to be out of synch with each other across the screen. Then, the screen goes blank and nothing happens after this. After 20 minutes or so I just reboot again and the same process starts all over again. 

BTW. I use a boot manager since I have both Linux (old Mandrake version) and Windows 2000 Pro on my machine. I am presuming that Ubuntu will make it possible to keep my boot manager, right?

---

### Post by jrjr on 2007-11-19
I have issues as well.... mine goes through the initial processes but it eventually says something like - The video server has reset 6 times, waiting 2 minutes.   Then it does it again and again....
I checked the cd for defects and it says its ok.

---

### Post by tzg6sa on 2008-01-15
The solution was the switch "acpi=off" in the boot line. You can invoke it by F6.

ps: sorry for the late answer. I have just found this thread :)

ps2: I don't think, that it is the best solution, because some thing need the acpi. So we are waiting for new ideas!

---

