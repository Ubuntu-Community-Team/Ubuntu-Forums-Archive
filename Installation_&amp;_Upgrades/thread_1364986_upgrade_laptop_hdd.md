---
title: "upgrade laptop hdd"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Post Monkeh on 2009-12-26
i have just ordered [this]("http://www.dabs.com/products/seagate-momentus-7200-4-500gb-sata-2-5in-7200rpm-16mb-68KD.html") to replace my current 120gb laptop hdd, which is very nearly full considering i have xp and ubuntu installed.


is there any way to clone my current disk when the new one arrives? i have ordered an external enclosure so i can use my current disk as an external drive once i swap it out.

bear in mind too that i do have xp installed on the current disk. i'm not an expert, but i do understand that this is likely to involve re-installing grub once i've cloned the drive, however i'm not really competent in the new grub that came with 9.10. i also expect i'll have to update the disk references in grub, but once again i've no idea how to do this.


is it even possible given that xp is installed too, or will it require me to reinstall?


even if it does require a reinstall of the 2 os's, if someone could give an easy way to clone the disk so my data at least is transfered (atm i have an xp partition, an xp data partition, a "/" partition, and a "home" partition.)

---

### Post by taurus on 2009-12-26
Maybe you want to have a look at Clonezilla, [http://www.clonezilla.org/](http://www.clonezilla.org/).

---

### Post by Post Monkeh on 2009-12-26
> **taurus said:**
> Maybe you want to have a look at Clonezilla, [http://www.clonezilla.org/](http://www.clonezilla.org/).

that looks promising. 120mb though, that leaves me about 250mb left :D

i still presume there'll be a bit to re-configure after cloning the old drive and installing the new one?

---

### Post by ajgreeny on 2009-12-26
Don't install it on your hard drive, but burn it to a CD and run from that.  At least that's the way I always thought clonezilla was used, but perhaps I'm wrong!

Don't forget, you will have to have another disk for the archived image, I think, as I don't think you can do it direct, though again, I could be wrong.

---

### Post by lukeiamyourfather on 2009-12-26
Clonezilla rocks for cloning disks. Or if you want to go back to basics use the dd command which will copy block for block from one device to another, but be sure to read all the man pages for it fist because it can do harm as well. Cheers!

---

### Post by Post Monkeh on 2009-12-27
> **ajgreeny said:**
> Don't install it on your hard drive, but burn it to a CD and run from that.  At least that's the way I always thought clonezilla was used, but perhaps I'm wrong!

Don't forget, you will have to have another disk for the archived image, I think, as I don't think you can do it direct, though again, I could be wrong.

yeah i noticed that when i downloaded.
at least i know that all my actual data will be transfered, but if anyone could give me a run through of the steps i need to take once i have everything cloned to the new disk, in order to get windows and ubuntu running again, that would be great.

i'm guessing (well hoping really) that i shouldn't really have to touch the windows side of it, but i am going to have to change both my grub setup (but i have no idea how to do that for grub 2) and i'd imagine i'll have to change my ubuntu setup (is it the fstab file?) to reflect the fact that there's a new disk there it needs to look for all my mount points on.

---

### Post by Post Monkeh on 2009-12-30
thought i would bump this.

i have seen a couple of tutorials for replacing a hard drive and getting grub up and running again, but none for grub2. [this]("http://encodable.com/tech/blog/2006/10/30/Ubuntu_Linux_Hard_Drive_Upgrade") is an old tutorial, but isn't it impossible to edit the menu file of the new grub?

or should i just be able to boot back up with my karmic cd and install grub2 from there?

i think i should be able to manage fixing the references in the fstab file, but with grub2 being fairly new i'd like to know what way it can be reinstalled when the hard drive is cloned.

---

### Post by Post Monkeh on 2009-12-31
well the hard drive's arrived, any info on what i need to do after cloning the disk and installing the new one would be very welcome as i'm going to be a saddo and install it tonight.

---

### Post by Post Monkeh on 2010-01-01
i see you all had more of a social life than me on new year's eve :P

for the record, clonezilla not only reinstalled grub for me, it also updated my fstab file entries, and only me messing around with my partitions after it was all complete actually caused me any problems (be careful when removing swap partitions in an ubuntu livecd people, it caused me some head scratching when my desktop loaded perfectly, meaning my home folder mounted ok, but every time i tried to do anything i was told that i had insufficient access rights)

all up and running now, and it only took a few hours to clone my 130gb disk.

---

