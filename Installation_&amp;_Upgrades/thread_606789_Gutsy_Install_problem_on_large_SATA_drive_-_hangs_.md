---
title: "Gutsy Install problem on large SATA drive - hangs at grub"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by hypatia on 2007-11-08
Hi ubuntuers,

I've just done a fresh install of 7.10 to a 500GB Seagate drive.  Everything goes fine until I reboot, at which point I get: 

Boot from CD-ROM...
Grub Loading stage 1.5:

and then nothing happens :(

My partition scheme is as follows:

/boot : 150mb, ext2, bootable
/ : around 20gb, ext3
swap : 4gb
/home : the rest, about 450gb, ext3

I've tried looking through my BIOS (DFI Lanparty K8M800-MLVF, VIA chipset) for a way to set LBA on my SATA drive but there doesn't seem to be one.  Does anyone have other ideas about how to get this working?  I've already tried reinstalling grub to the MBR, it says that it's worked but on reboot it still hangs.

---

### Post by bulldog on 2007-11-08
Make your hdd first boot device instead of the cd-rom.
Don't know if it makes a difference but who knows.

---

### Post by hypatia on 2007-11-08
Tried that too, only difference it makes is "Boot from CD-ROM..." doesn't show up :(

---

### Post by bulldog on 2007-11-08
If you have a live cd can you boot it and use the terminal to reinstall grub?
Specially look for errors please.
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr[b] but be carefull here,if the find command returned (hd1,?)
the setup should be (hd1) not (hd0)!! [/b]
```
setup (hd0)
```
Exit the grub shell
```
quit
```

---

### Post by hypatia on 2007-11-08
From my first post:

"I've already tried reinstalling grub to the MBR, it says that it's worked but on reboot it still hangs."

so yeah.  tried that too, no dice :(

---

### Post by nsindian on 2007-11-08
The install went fine but upon reboot I was having issues with "Nautilus error" and also something to do with not being able to contact the "bonobo server"? I tried different configurations for over a week but still some different issue kept creeping up on me after the install. I had two SATA drives, 1 was 160GB and the other 250GB, which were different make and model .... WD and Seagate I think. 
What I ended up doing was taking my EIDE drive, with XP on it, and I installing on that drive after freeing up some space. XP had to be repaired becasue it was a whole "new" computer for that drive. 
[FONT="Tahoma"][SIZE="3"][/SIZE][/FONT]

---

