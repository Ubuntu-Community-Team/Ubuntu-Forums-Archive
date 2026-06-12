---
title: "Installing Ubuntu Studio"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Murtagh on 2007-10-21
I just downloaded the iso images and installed them on my computer, but when i boot with ubuntu studio all i get is a command line. How do i get to the desktop.

I thought it could be a partitioning thing. Maybe its too small and didnt install the desktop environment... i dont know, im no expert.

heres an image of my partitions.

the first image shows my windows partition, a partition that i dont think is being used (hda2), the partition i think ubuntu studio is using (hda3) and two more i dont know what they are for. The other screenshot is just my ubuntu partition.

---

### Post by Pumalite on 2007-10-21
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by Murtagh on 2007-10-21
I did and it said it didnt have xserver-xorg package installed  so i did sudo apt-get install xserver-xorg and it installed it. 

Afterwards i did sudo dpkg-reconfigure xserver-xorg and i selected vesa as the driver and it took me to a series of screens to configure x. Once it finished and i typed startx and it came back with 

Fatal error: No valid FontPath could be found. 

Fatal error 104 (connection reset by peer) on x server ":0.0"

---

### Post by Pumalite on 2007-10-22
I'm afraid you have to reinstall.

---

