---
title: "crash during 10.04 install left system unbootable"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by bill_wad on 2010-06-06
my son kicked out power during the install phase of 10.04 (about half complete) and now the system is unbootable.  The boot process dies shortly after starting fsck with the error:

init: plymouth main process (382) killed by SEGV signal

So this looks bad (to me), segmentation violations are never good.

So does anyone have any suggestions for booting and completing the upgrade?

If I'm SOL on this OS image is there a way to image over the OS and save my data?  

The only option I see now is to buy a new disk, image onto it, mount my current disk and copy my data.  (takes money and time)

Thanks in advance

Bill

---

### Post by irongreatwall on 2010-06-06
Alright, I don't even know if members are allowed to help, but here is what I will do.

put the Ubuntu disc in the CD/DVD ROM (I would burn one if I haven't done that yet)

Make sure the CD/DVD ROM is set to be the 1st on the boot sequence (set in the BIOS).

Then power on / restart the computer

If the computer did indeed boot off of the CD/DVD you should see a familiar screen.

Then see if there is any options available to install the OS only w/o wiping anything out.



Hope this helps

---

### Post by bill_wad on 2010-06-06
I don't see an option to upgrade or repair the OS

---

### Post by irongreatwall on 2010-06-08
sorry, all out of ideas...

---

### Post by wilee-nilee on 2010-06-08
If this was a fresh install just pop the live cd in delete the partitions with gparted that were made or just install as before. It takes very little time to install and trying to fix one stopped in the middle is if done, may have problems later on.

---

### Post by bcbc on 2010-06-08
> **bill_wad said:**
> 
So does anyone have any suggestions for booting and completing the upgrade?

If I'm SOL on this OS image is there a way to image over the OS and save my data?  

The only option I see now is to buy a new disk, image onto it, mount my current disk and copy my data.  (takes money and time)


The way I see it, you need to buy a disk anyway - if you don't have a backup of your data, that's part of your problem. These days USB external drives are very cheap... you should be able to boot from live cd, mount your hard drive, plug in a USB and copy your data. If you need to you should even be able to save your entire /home directory and restore it later on a new install.

psychocats.net has some good tutorials [http://psychocats.net/ubuntu/backup](http://psychocats.net/ubuntu/backup) shows how to backup /home using rsync. Somewhere else on the site there is info on moving /home to a new partition which you could use to move your backed up /home to a fresh installation.

Finally, there may be a way to recover your broken upgrade, but I think - as long as you can recover your data first - reinstallation will be simpler.

---

