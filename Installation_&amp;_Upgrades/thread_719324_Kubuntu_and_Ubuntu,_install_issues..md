---
title: "Kubuntu and Ubuntu, install issues."
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by Zayne on 2008-03-09
So currently right now i'm using Ubuntu 7.10

I installed the Kubuntu desktop environment via Synpatic, and I like the feel of it but i'm having problems. Namely compiz isn't working, I can't get virtual desktops functioning properly nor a fair deal of the special effects. As well as all the programs from both, being practical duplicates with different names causing a fair deal of confusion and likely wasting a bit of drive space.

I'm wondering if a clean install to Kubuntu itself instead of installing packages through Ubuntu would help my issue. 

And if I install Kubuntu from the CD and remove Ubuntu will it wipe out all of my files? I have a lot of data that I don't particularly care to lose. Personal things like documents, images, music, that i'd like to save. 

Thanks in advance, all advice appreciated.

---

### Post by banewman on 2008-03-09
I can't help with the compiz/kubuntu issue but the best advice I've come across is to have a seperate /home partition - that way when I reinstall the os all the data in my /home/me is intact as I can mount that partition during the install.
:)

---

### Post by stefansmith on 2008-03-09
I suspect that a clean install of Kubuntu would be better, as I've tried but failed to tidily do what you are trying.

By a clean install I mean wiping the partition and redoing it from scratch -- which would wipe your files if they are on the same partition. I always put my files on a separate partition to the OS, plus backed up to an external hard drive or DVD-r. I suggest you do this, leaving you free to experiment with different OS installs.

---

### Post by Zayne on 2008-03-09
Normally, my files are on a separate partition. This has been the first time i've been in this predicament.

I just got a new system. Lovely. Shiny. One damn HD. It's also SATA, as opposed to all my old hard drives. Which are no longer even supported on my motherboard. So retreiving my data was a long arduous process using a 2GB flash drive and aMSN. I really don't want to repeat it. When I installed Ubuntu over Vista, I kinda...forgot..to create a storage partition.

Would it be possible to add a partition to my current drive on the 150GB that's still free without losing my current Ubuntu install, then install Kubuntu as a dual boot, and move my files over? Or should I 'bite the bullet' and burn my files to DVD's?


Also, this is a totally random question but while i'm on the problem train... would anyone know why aMSN is sending on a local network at no more than 6kbps? Normally, me and my boyfriend reach speeds of anywhere between 700kbps and 1500kbps, and that was between aMSN and Windows Live. Now that he's switched to Ubuntu..it's seemed to have killed our local speed.

---

### Post by stefansmith on 2008-03-09
I have a dual boot system (WinXp and Ubuntu) and have the following partitions on the one HDD (120GB):

1. The Windows OS (30 GB)
2. The Ubuntu OS (30 GB)
3. DATA (the rest of the free space, partitioned either a NTFS/FAT32, readable by both OSs).

I keep all my data on the DATA partition, meaning I can suffer an OS crash and not be worried at all. 

So yes, I would search on how to resize your ubuntu partition smaller and create a separate one for data, then you can move your files across. I'm sure there is a simple way of doing this -- gparted for example, although the advice here is still that you should backup, just in case.

---

