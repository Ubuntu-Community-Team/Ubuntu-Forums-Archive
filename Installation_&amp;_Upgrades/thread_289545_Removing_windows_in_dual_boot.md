---
title: "Removing windows in dual boot"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by jhaquo on 2006-10-31
Hi!

I have installed ubuntu on one of my laptops in dual boot with winxp, but now i would like to remove winxp and edit my main linux partition so it has the full size of my hd ( - swap partition of course).

How can i do that beside reinstalling everything please?

What are my options?




currently i have: 
windows parition: 80 gig
linux partition: 8 gig
swap partition: 2 gig

---

### Post by Kateikyoushi on 2006-10-31
You could boot the livecd and delete the windows partition.
Then you have two choices resize the linux partition and edit the grub and fstab. The easier is to make an ext partition in the free space and mount it in linux, it is easier because the partition number of the / linux partition won't change, results in less editing and you can even do it without booting live cd.

---

### Post by jhaquo on 2006-10-31
> **Kateikyoushi said:**
> You could boot the livecd and delete the windows partition.
Then you have two choices resize the linux partition and edit the grub and fstab. The easier is to make an ext partition in the free space and mount it in linux, it is easier because the partition number of the / linux partition won't change, results in less editing and you can even do it without booting live cd.

second options sounds good since i need the space for downloading purpose and stocking music/vids/pics/whatever i have to stock

how can i remove that windows partition, make it a usable linux partition and remove windows from grub please? im a total noob :s

---

### Post by gnarula on 2006-10-31
boot using the ubuntu live cd and go to GNOME partition editor. select the windows xp partition and right click it and select format. be sure to format it as ext3 to make it useful with ubuntu. for grub editing someone else will need to help.. srry

---

### Post by jhaquo on 2006-11-02
for grub, you have to edit the /boot/grub/menu.lst and remove the windows entries :)
thanks, i successfuly uninstalled windows \o/

---

