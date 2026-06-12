---
title: "ubuntu corrupts partition table"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by dalyraptor on 2006-11-22
When I install ubuntu 6.10 from CD it corrupts the partition table so I cannot boot into windows. After much surfing the web loooking for answers ( which has been my experience with linux 100% of the time :( ) I was able to use PTDD Partition Table Doctor to recover the partition table.

  This app does not seem to be able to see the linux partition, showing it as free space, afterwards I have to re-install ubuntu. I re-installed ubuntu, but again, I cannot boot to windows, whatever the partition manager does messes up the partition table.

this sucks
Michael

---

### Post by deanlinkous on 2006-11-22
What kind of error do you get when you try to boot windows? Walk us thru the boot cycle and what happens please.

---

### Post by G-Shock on 2006-11-22
I have the same problem I think its because the grub installer overwrites the windows MBR it installs to hd(0) by default and I think it should be hd(0,1) or the wherever the bootable partition is. Maybe someone can clarify I dont know much about grub.

---

### Post by dalyraptor on 2006-11-22
ok, origionally i thought it was a ntfs resize problem but after being able to boot into windows i think the ntfs partitions are ok.

ok, when i choose XP from grub initially the system reboots, after this, i get the screen saying windows did not start properly last time, i can choose to start normally or in safe mode, all options make the computer reboot.

when i run the Partition Table Doctor from bootable cd as mentioned earlier, it says that the partition starts in a different place than what is written in the partition table. it then rebuilds the partition table, but leaves out the linux partitions :(

---

