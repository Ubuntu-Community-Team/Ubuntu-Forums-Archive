---
title: "grub problem"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by mururoa on 2006-03-12
I messed with setup and installed ubuntu before Windows XP.
All was ok after ubuntu installation and I did no more partitionning after.
Ofc after windows installation no more grub.
So I put the live-cd and get a console then I enter :

# sudo apt-get install grub
# sudo grub

grub>root (hd0,5)

there it says partition is type reiser wich is ok. There is only one linux partition with all ( /, /boot, /usr, ... ) in it.

grub>setup (hd0)

there all goes ok and end up with grub installed ( stage 1, stage 1_5 and stage 2 are found )

grub>quit

# sudo shutdown -r now

then it reboot and computer displays only boot sector OK and then ... nothing. It display that forever and whatever I can type.

Where am I wrong ?

---

### Post by Xian on 2006-03-12
Try going into rescue mode using the InstallCD, and when prompted select the Ubuntu root partition. Next, you should only need to issue the grub install command:

# grub-install /dev/hdx

Where x is the letter of your partition.

---

### Post by mururoa on 2006-03-13
Ok, gonna try that but it will destroy actual grub files.
Bah, I'll copy them before. If I can avoid to reinstall XP and then linux in the right order.
Anyway I dont understand why the computer display hd0 bootable OK and then stop.

---

