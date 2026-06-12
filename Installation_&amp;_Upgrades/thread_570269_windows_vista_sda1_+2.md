---
title: "windows vista sda1 +2 ?"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by michalski7777 on 2007-10-08
hello i currently have a dual boot vista and ubuntu 7.04 (cant wait for 7.10) and as i was looking at gparted i noticed that i had another volume named "toshiba system volume" along with a multitude of little open spaces on my hard drive. 

im scremballing to get as much space as possible of out my hard drive and just wanted to know if i could delete this and would it kill my windows/ubuntu as i am using grub

tech specs:in order of location
unallocated:     1mb
sda1:ntfs:     1.46gb: Toshiba System Volume
sda2:ntfs:     111.76gb ( soon to be severily shortend!): Windows partition 
unallocated:3.77mb
sda3:ext3:    27.94gb: ubuntu
sda4:ntfs:     7.88gb:  personal files

which ones can be deleted here without wreaking windows and ubuntu? and the personal files :P

where is grub located....where is the windows boot logger?

---

### Post by michalski7777 on 2007-10-12
that sunk realy fast to the bottom :S

---

### Post by celticbhoy on 2007-10-12
I would think that the Toshiba System Voume would contain drivers for a windows install.
Reading through other posts some folk have had problems if they have deleted these kind of partitions, and had to re-install windows.

---

### Post by michalski7777 on 2007-10-12
> **celticbhoy said:**
> I would think that the Toshiba System Voume would contain drivers for a windows install.
Reading through other posts some folk have had problems if they have deleted these kind of partitions, and had to re-install windows.

thank you very much you just saved me from making a big error

---

### Post by celticbhoy on 2007-10-13
Thats OK. That is what the forum's are here for - everyone helps eneryone else.

---

