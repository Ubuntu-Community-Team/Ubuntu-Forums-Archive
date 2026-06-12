---
title: "kubuntu installation query"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by hellfried on 2006-08-25
i am trying to install kubuntu on my hd which has winxp, ubuntu 6.06, swap partitions already on it. i have earlier created an extra ext3 partition (sda5) using a livecd of gparted. i want to install kubuntu onto this free partition. 
winxp is sda1, ubuntu sda 3 and swap is sda 4
after booting into kde with the livecd of kubuntu, i proceed to install it.
i select to manually edit the partition table and then select sda5 in the 'prepare partition' menu. i am then faced with the 'prepare mount points' menu. what should i do here? it wants to reformat my sda4 and sda3 which is definitely bad news as that's where my ubuntu and swap resides.
i uncheck the reformat buttons and then check it for sda5. i choose '/' for sda5, media/sda3 for sda3 and 'swap' for sda4. i get an error message saying that mounting of sda3 failed. what should i select for each mount point?

---

### Post by orb9220 on 2006-08-25
You can install the kde desktop from gnome you don't install from the liveCD

That way you can logout and relogin into kde.
To install from gnome open a term and enter each command:
sudo aptitude
sudo aptitude update
sudo aptitude install kubuntu-desktop
or 
sudo aptitude install xubuntu-desktop
for xubuntu

---

### Post by hellfried on 2006-08-25
> **orb9220 said:**
> You can install the kde desktop from gnome you don't install from the liveCD

That way you can logout and relogin into kde.
To install from gnome open a term and enter each command:
sudo aptitude
sudo aptitude update
sudo aptitude install kubuntu-desktop
or 
sudo aptitude install xubuntu-desktop
for xubuntu

u mean i do not need to boot into kde with the livecd? did i just waste a lot of time downloading and burning the iso to cd?
when i am running on the livecd there is an icon on the desktop whereby i can click and install. i do not need to do that? will i again be faced with the mount points option again if i do it your way?

---

