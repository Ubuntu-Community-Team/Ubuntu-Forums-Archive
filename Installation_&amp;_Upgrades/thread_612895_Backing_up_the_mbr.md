---
title: "Backing up the mbr"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by kofkof_00 on 2007-11-14
Hello,

I'm sure i'm just one step away from achieving this and it's something simple, but...

I found this info: [http://users.bigpond.net.au/hermanzone/p15.htm#How_to_back_up_and_restore_your_MBR](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_back_up_and_restore_your_MBR)

When I execute this in a shell I get:

lamb@lamb-desktop:~$ $dd if=/dev/hda of=MBR-backup bs=512 count=1
bash: if=/dev/hda: No such file or directory
lamb@lamb-desktop:~$

I also tried  sudo dd if=/dev/hda of=/home/herman/GRUBMBR.img bs=446 count=1

Where I replaced herman fo lamb.

My setup has 2 sata drives, one with various flavors of windows (used to have 2k :\ , then xp :(, and now Vista :(( ) 
I'm trying to backup my mbr because these os's keep crashing and need periodic refreshes. I'm tired of micro$haft eating my mbr & being all cheeky about it. "Oh, you had linux on here too?" I can fix it easy enough with other methods, but my goal here is ease of repair.

:confused:

---

### Post by kofkof_00 on 2007-11-14
Whooo hooo! I think I have it figured out!

sudo dd if=/dev/sda of=MBR-backup bs=512 count=1 

where "device.map" in /boot/grub said (hd0)	/dev/sda

I now have a backup of my mbr!


I'm going to go break it now so I can write a cool bash script to fix it!

---

