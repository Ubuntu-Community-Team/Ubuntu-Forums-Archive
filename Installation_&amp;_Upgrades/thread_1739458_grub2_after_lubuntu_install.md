---
title: "grub2 after lubuntu install"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by Zaytuun on 2011-04-26
Hey guys, new to the forums, wondering if anyone could help me out with a problem I'm having.

I just installed lubuntu 10.10 onto my desktop and while on my first bootup I had the option to boot windows through grub, it's disappeared from the boot menu since then.

When I installed I created a partition for lubuntu and installed onto that. I can still access and see my windows partition.

"fdisk -l" outputs the following:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           2       16033+  11  Hidden FAT12
/dev/sda2   *           3        2433    19527007+   7  HPFS/NTFS
/dev/sda3            2434        4865    19533825    5  Extended
/dev/sda5            2434        4758    18672640   83  Linux
/dev/sda6            4758        4865      860160   82  Linux swap / Solaris

and "grub-install -v" outputs the following:

grub-install (GRUB) 1.98+20100804-5ubuntu3

Any help guys? Much appreciated in advance.

---

### Post by wilee-nilee on 2011-04-26
Have your run
sudo update-grub

---

### Post by Zaytuun on 2011-04-26
> **wilee-nilee said:**
> Have your run
sudo update-grub

Yes, to no avail.

---

### Post by wilee-nilee on 2011-04-26
Lets make sure the os-prober is installed in the terminal
sudo apt-get install os-prober
If it was missing or reloads run the update-grub

The os-prober looks for the other OS's. If this doesn't work follow this.

Lets see the bootscript read out,(can be run from the lubuntu) in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by Quackers on 2011-04-26
+1 for the os-prober. 
For some reason lubuntu can fail to install it.

---

### Post by Zaytuun on 2011-04-27
Sorry for the late response, I've had final exams the past couple of days. I will try OS-prober and let you guys know what happens. Thank you!

---

### Post by Zaytuun on 2011-04-27
OS-prober did the trick. Thanks so much guys! Solved!

---

