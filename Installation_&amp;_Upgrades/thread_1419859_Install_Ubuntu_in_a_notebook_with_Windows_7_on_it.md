---
title: "Install Ubuntu in a notebook with Windows 7 on it"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by davidsanchezvasquez on 2010-03-02
I just bought an HP notebook with Windows 7 installed. I would like to install Ubuntu so that I have both systems in the computer.

Id like to know whats the best way to install in this case (I have already a CD with Ubuntu 9.10 on it).

By the way, there is a single partition C with windows on it. Is there a way to create two new partitions while installing Ubuntu (one for Ubuntu and one for the data)?

Thanks

---

### Post by darkod on 2010-03-02
Just because windows shows only C: in Computer it doesn't mean there aren't any hidden recovery partitions or similar. Open Disk Management and check how many partitions it shows on the hdd.

If you can create at least one new partition (that means of you have maximum 3 partitions right now), you could create extended partition with one data logical partition, one ubuntu root logical partition, and one ubuntu swap logical partition.

It all depends on your layout right now, and how you want it to look after you install ubuntu.

---

### Post by RadLobster on 2010-03-02
When you boot from the CD and install Ubuntu you can choose how much space you want to give that partition. Also everything you have on your windows partition can be accessed through ubuntu .

---

### Post by wilee-nilee on 2010-03-02
darkod gives a good description, you also only want to use the disk manager in W7 to resize the windows partitions. You have at least 2 partitions on there now the recovery which is hidden and the main C.

On my acer aspire when I installed Ubuntu along side the XP install it showed that XP hidden recovery partition in grub and would reformat the main OS when chosen at boot. I am not sure if this is common.

---

### Post by darkod on 2010-03-02
> **wilee-nilee said:**
> darkod gives a good description, you also only want to use the disk manager in W7 to resize the windows partitions. You have at least 2 partitions on there now the recovery which is hidden and the main C.

On my acer aspire when I installed Ubuntu along side the XP install it showed that XP hidden recovery partition in grub and would reformat the main OS when chosen at boot. I am not sure if this is common.

It probably would be, for all those recovery partitions. They have boot files present too and grub will pick them up and create menu entry. To add to the confusion, win7 recovery partition can be reported as vista, the user says why do I have vista on the computer? Selects the entry in grub menu and just the beginning of the process can wipe the MBR before you can abort. :)

Instead of providing install dvd and save the user from that s**t... :(

---

### Post by Megaptera on 2010-03-02
In addition to the advice above, useful guide here:

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

On my Dell, I deleted the 20g Restore Partition as I have the Windows recovery discs from Dell and installed Ubuntu in that partition.

---

### Post by wilee-nilee on 2010-03-02
> **darkod said:**
> It probably would be, for all those recovery partitions. They have boot files present too and grub will pick them up and create menu entry. To add to the confusion, win7 recovery partition can be reported as vista, the user says why do I have vista on the computer? Selects the entry in grub menu and just the beginning of the process can wipe the MBR before you can abort. :)

Instead of providing install dvd and save the user from that s**t... :(

I started with Ubuntu so I run the newly acquired MS XP and W7 I now have like Linux no recovery just a install disc and everything backed up off the computer on a HD. 

A install medium is a important tool to have for any OS.

On the recovery showing up in the Ubuntu grub loader, on my setup it would reformat XP without touching the MBR. I wouldn't rely on my experience though I think your correct in being cautious with the possibility of this happening or at the least messing up the MS partition's. I have noticed though that the MS install programs seem to, like Linux have a back-out, before confirming changes most of the time.

---

### Post by Mark Phelps on 2010-03-03
> **RadLobster said:**
> When you boot from the CD and install Ubuntu you can choose how much space you want to give that partition...

Don't do this.  

Follow the other advice and use the Vista/Win7 Disk Management utility to shrink your MS Windows partition to make room  for Ubuntu.

Using the Ubuntu installer to do this in side-by-side mode risks corrupting the Vista/Win7 OS and rendering it unbootable.

---

