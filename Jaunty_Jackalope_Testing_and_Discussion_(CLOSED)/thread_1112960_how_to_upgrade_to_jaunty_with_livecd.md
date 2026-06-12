---
title: "how to upgrade to jaunty with livecd"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by SaiHayashi on 2009-04-01
hi all,
im not sure if someone has already asked, my poor google skills wouldnt find me the answers i wanted.

I have downloaded the jaunty's live cd BEFORE reading the "upgrade from 8.10" instructions.

Now the getting new packages process is taking quite some time to download the packages i believe is already on the livecd.

So may i just ask how to use the livecd to upgrade to jaunty without having to download the package all over again? (i also have another laptop to upgrade when final is released, so just wana prepare for it in the mean time.)

---

### Post by drs305 on 2009-04-01
You can use the livecd to accomplish a fresh install but not to upgrade a current version to the newer one. 

One thing you can do with the CD is select the option to keep your /home settings if /home is on a separate partition. You would select the /home partition during the install and instruct the install *not* to format the /home partition. This might minimally effect the install time but probably not by much.

---

### Post by skymera on 2009-04-01
System > Administration > Software Sources

Click "CD ROM" box.

Or in Synaptic in one of the menus is an option to add CD ROM, im sure either will work.

You can try a more/very risky option:

Replace your sources.list with Jaunty repos.

I did this from Ubuntu 7.04 to 7.10. It broke.

---

### Post by alphacrucis2 on 2009-04-01
> **SaiHayashi said:**
> hi all,
im not sure if someone has already asked, my poor google skills wouldnt find me the answers i wanted.

I have downloaded the jaunty's live cd BEFORE reading the "upgrade from 8.10" instructions.

Now the getting new packages process is taking quite some time to download the packages i believe is already on the livecd.

So may i just ask how to use the livecd to upgrade to jaunty without having to download the package all over again? (i also have another laptop to upgrade when final is released, so just wana prepare for it in the mean time.)

If I remember correctly you need to use the "alternate" CD.

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD")

---

### Post by theozzlives on 2009-04-01
you need the alternate to upgrade. If you want ext4 (like I did), you'll have to backup and wipe the drive.

---

### Post by SaiHayashi on 2009-04-01
> **skymera said:**
> System > Administration > Software Sources

Click "CD ROM" box.

Or in Synaptic in one of the menus is an option to add CD ROM, im sure either will work.

You can try a more/very risky option:

Replace your sources.list with Jaunty repos.

I did this from Ubuntu 7.04 to 7.10. It broke.
yes i was looking for that button. thx
but as alphacrucis2 and theozzlives pointed out, the upgrade paid no attention to the livecd.
looks like i will need to download alternate cd when final releases

thx all for helping ;-)

---

### Post by alphacrucis2 on 2009-04-01
> **theozzlives said:**
> you need the alternate to upgrade. If you want ext4 (like I did), you'll have to backup and wipe the drive.

Backup for sure. Wipe the drive no. tune2fs (with the appropriate parameters) followed by an efsck does a non destructive conversion from ext3 to ext4.

---

