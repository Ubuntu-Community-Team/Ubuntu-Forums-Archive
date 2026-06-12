---
title: "2 SCSI Harddrives - anything I need to know..."
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by J77 on 2006-02-24
Hello,

I've been running Ubuntu on my FS7020 laptop for some time now...

I've just got a new desktop - FS Celsius R - with two SCSI harddrives.

Is there anything I need to know before installing ubuntu this time?

I presume the drives will act as separate 'home' partitions and I'll be able to access both at any one time.

Do I set them up as, eg. /home1 and /home2 ?????

Or... If I run programs on one can I write to the other? Or use one for swap, one for the programs running? Or mirror one for back-up?

And is so, how do I do any of the above?

Thanks, in advance, for your help.

---

### Post by gsdefender on 2006-02-24
The drives will act whatever you want them to do.
I suggest you installing Ubuntu on a single hard disk, keeping the second for additional storage, maybe as so:

```

mkdir -p /media/sd??/username/data
ln -s /media/sd??/username/data /home/username/additionalstorage

```

If you really need **more storage** for your home partition, it's easy to "stripe" it with a method like this.

As far as the drive is mounted and you have enough rights, every program is able to write wherever you teach him to.

Swapping is also easily done through the installer: you only need to create an additional swap partition - and it will get mounted alongside the one in the first disk.

Mirroring is a bit more complicated - and I don't actually think you need it.
You will need to investigate about Software RAID and Logical Volume Manager - I was not able to find info in the Ubuntu Wiki, and as I am not using it, I don't know what directions you should need. Hope this helps.

---

### Post by J77 on 2006-02-27
Thanks for the reply - hopefully the installation will run smoothly...

---

