---
title: "Windows XP on extended partition... not recognized by GRUB"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by travist120 on 2008-07-22
I installed ubuntu over my windows Vista partition in a XP/Vista dual boot. After installing I was startled to see that grub didn't recognize my xp partition. I put the live cd back in to find that windows xp was under an extended partition along with my SWAP. So I tried reinstalling grub (sudo grub) from live cd and it still didn't work. I checked menu.lst to see if it may have been detected but commented out (I wanted to be thorough). but nothing. I tried google, but that's hard to put into a search box. So I ask, is there any way to 

A) Move my windows XP partition OUT of extended.
or 
B) Get GRUB to recognize it. 

here is the output of Fdisk - l

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4808    38620228+  83  Linux
/dev/sda2            4809        9729    39527932+   f  W95 Ext'd (LBA)
/dev/sda5            5021        9729    37825011    7  HPFS/NTFS
/dev/sda6            4809        5020     1702827   82  Linux swap / Solaris

```

---

### Post by fmartinez on 2008-07-22
I use a chainloader to boot multiple systems in grub. So try this: 
- In you menu.lst file look for the section where your Windows partition is listed. There you'll find a couple of lines starting with "Chainloader" and your Windows partion. 
- make a duplicate entry.
- alter the partitions to point to the partition other Windows install that's not showing up. 
- provided that you installed that particular OS's MBR on that partition the boot loader will pick up and allow you boot from it. 

or

if previously you had a 3rd party boot loader to boot from vista to xp when you loaded the chain loader it should of given you the same options as before.... 
It'll be interesting to see what happens when add that 2nd entry. Post the output of what happens.
hope this helps... good luck

---

### Post by logos34 on 2008-07-22
Question: when you had the xp/vista dual boot, you did install vista after xp, right?

But you'll have to make an image of xp and move it out of the extended (can't boot windows on a logical partition--boot files have to be located on a primary)...Delete the extended and swap, create a new swap at the end of the disk or right after sda1, then create a new primary ntfs partition out of the remaining space.  Restore the image.  But you'll have to edit boot.ini and fix your boot files, etc.  Lot of work.  

It would probably be easier to just back up whatever saved files you have on xp (assuming you can mount it in linux) and reinstall on a primary.  Then restore grub to mbr. (see my sig)

---

### Post by travist120 on 2008-07-22
Actually, it was the other way around. I had Vista first, then installed XP (I couldn't stand windows vista)

All right, I understand, make a new partition, then copy it over so that it is a primary. Just wish there was a drag 'n drop way of taking it out of the extended partition.

---

### Post by logos34 on 2008-07-23
If only you were moving it to a second disk, then you COULD use gparted dragndrop ('Copy/move' option)...

I've never dual-booted xp and vista, but I thought you had to use vista boot loader to boot xp (because xp NTLDR can't handle vista).  But if you installed xp last and it was working, then the boot files were likely on the vista (primary) partition--windows puts the boot files on the prexisting primary ('active') partition.  So maybe you deleted them along with vista.  In which case you have to copy them frm the xp cd and edit stuff like I said.

---

### Post by snkiz on 2008-07-23
This  may be a silly question, but have you tried booting the vista entry in grub? It could be that it points to the windows bootloader as you had it setup before. If not maybe you could restore it as a grub entry (Did that make any sense to anyone else?) I think that would be easier than a reinstall or replacing a partition.

---

### Post by travist120 on 2008-07-23
I would rather not re-install xp, it'd require a lot of driver finding and general pain, I was able to use it before when it was in an extended partition. Though I think I understand what's happening. Grub won't recognize windows XP because there is no bootloader anymore for it. When I deleted the windows vista partition, I erased the bootloader. So if it possible, I might be able to install a 3rd party bootloader for it. Maybe maybe not. But as long as I understand it I'm in better condition than what I once was.

I will look at google to see if I have any options for that.

Thanks!

---

### Post by travist120 on 2008-07-23
Quick search led me to this solution

Put windows XP installation disk back in and select the option "Recovery Console"

Followed by "fdisk /mbr" (without quotes)

Thanks for all the help, I will let you know if it works.

---

### Post by logos34 on 2008-07-23
> **travist120 said:**
> 
Put windows XP installation disk back in and select the option "Recovery Console"

Followed by "fdisk /mbr" (without quotes)


Don't do that--it will overwrite grub on the MBR and you won't be able to boot ubuntu.

It won't help anyway because you can't boot windows on a logical partitions and without the bootfiles (deleted along with vista).  Even if the latter were still there, the bootloader will look only for an active/bootable **primary** partition in the partition table.

see my sig to restore grub

---

