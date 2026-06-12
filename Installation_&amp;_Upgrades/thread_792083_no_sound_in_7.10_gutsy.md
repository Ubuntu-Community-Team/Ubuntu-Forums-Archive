---
title: "no sound in 7.10 gutsy"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by Zerophase on 2008-05-12
hey all! im a new user on a acer travelmate 2480. i am dual booting with windows xp. i installed ubuntu and i dont have any sound. can anyone help with this problem? thanks in advanced.

---

### Post by Pumalite on 2008-05-12
Post:
lshw -C sound

---

### Post by Zerophase on 2008-05-12
*-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

thanks for the quick reply

---

### Post by Pumalite on 2008-05-12
Type in your Terminal:
alsamixer
Turn all the volumes to 100%

---

### Post by Zerophase on 2008-05-12
i did it but i still get no sound.

---

### Post by Pumalite on 2008-05-12
Go to system>Preferences>Sound and see what you have there.

---

### Post by Zerophase on 2008-05-12
i tested all that i could and got no sound. before i made this thread i look at the forums and i read something about linux backports modules. could that be a issue. also i havent done all the updates yet. im in iraq and the internet is really slow here. i installed all the updates i thought were important. what do you think?

---

### Post by Pumalite on 2008-05-12
Absolutely. Go to System>Administration>Software Sources>And enable ALL your repos. Then:
sudo apt-get update
sudo apt-get upgrade.

---

### Post by Zerophase on 2008-05-12
here is my read out:

202 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 266MB of archives.
After unpacking 75.5MB of additional disk space will be used.
Do you want to continue [Y/n]? 

right now i download at most 10 kbps so for me this will take forever. do you know of a quicker way to just work on the sound or am i doomed to installing for a day?

---

### Post by Pumalite on 2008-05-12
Keep on going. If after your upgrade you still don't have sound; post back.

---

### Post by Zerophase on 2008-05-12
thank you for your help i will install all the updates

---

### Post by Pumalite on 2008-05-12
You are welcome. Good luck.

---

