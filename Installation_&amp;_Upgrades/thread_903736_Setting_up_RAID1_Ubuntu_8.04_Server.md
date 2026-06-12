---
title: "Setting up RAID1 Ubuntu 8.04 Server"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by zalnn on 2008-08-28
I am looking at setting up a file/print server that will be running nfs, samba and a print server.
 
This machine will be setup with parts lying around, its going to be a P4, 2GHz, 256MB RAM and two PATA 40GB hard disks.

Setting up the RAID1 array.

I want to be able to eventually upgrade the hard disks to 120GB (or whatever is cheaply available) and have access to the full space.

My guess is that I need a combination of LVM2 and mdadm?

How do I setup RAID so that at a future date, I might be able to grow the RAID?

---

### Post by zalnn on 2008-08-28
My question re-phrased:

How do I setup bootable software RAID1 on 2 x 40GB now so that growing that same array to 2 x 120GB later will be as painless as possible?

---

### Post by Cheesemold on 2008-08-29
I'm trying to set up a RAID1 on my own computer at the moment and running into some difficulty...
But it seems like however you set it up it should grow fairly easily.

Using mdadm there are commands that let you remove and add drives to an array.  I don't have enough experience with the process myself, but I believe what you do is remove as many devices as you would need to without removing data from the array, and then add drives as you can.

If you have your 2x40GB drives in the array, you would remove one of them (if you needed to because of hardware limitaitons) and add the 120gb and reboot.
Following the page: [http://linux-raid.osdl.org/index.php/Growing](http://linux-raid.osdl.org/index.php/Growing)  you would type
mdadm --add /dev/md1 /dev/sdb3
mdadm --grow --raid-devices=4 /dev/md1


This would add the partition /dev/sdb3 as a spare device to the array, and the second command integrates the partition (if, in an indirect way) into the array.

You would add your drive into the array, allow it to sync, and then keep replacing the smaller devices untill you have removed the smallest drive, thereby increasing the potential storage space of your array.

Maybe it'd be simpler with LVM, but I'm really a linux noob and don't know much about it.

---

