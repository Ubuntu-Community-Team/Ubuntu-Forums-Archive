---
title: "i need help with installation of ubuntu 6.06 LTS dvd"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by DCDraco on 2006-09-23
I am want to install Ubuntu linux on my laptop it is a Toshiba sat P100 PSPA. I had installed Suse linux 10.1 but had trouble with sound and I hate KDE. GNOME functioned alot better so I want stick with that desktop environment. I have removed suse and want to try Ubuntu linux. I am a newbie to linux and not that knowlegedable about computers in general. So the situtation is this; I the hard drive partioned already 36GB with Win XP and the other with 56GB at the moment for saving data on. I would like to install on the 56GB part but would like to partion that so to allow data sharing between the two OS. Say 10GB and give Ubutun 46GB to run on. Can anyone tell how I can proceed with the installation. I would greatly appreciate any assistance. TAHNX

---

### Post by whizbaby on 2006-09-23
Format the sharing partition with fat32 so linux has no problems to write to it. You can have the rest (linux) auto-partitioned by the installer (leave as empty space).

---

### Post by K.Mandla on 2006-09-23
You can use something like Partition Magic to do that, or you can download the GPartEd live CD to do it. whizbaby is right: Partition off the "shared" area and leave the rest unpartitioned. That's the easiest way.

---

