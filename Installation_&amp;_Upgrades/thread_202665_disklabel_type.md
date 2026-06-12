---
title: "disklabel type"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-06-23
When using the Gparted utility on the Desktop CD installation is the disklabel parameter supposed to remain the default (MSDOS) or is it supposed to be one of the other parameters shown in the drop down ?

Thanks.

---

### Post by wpshooter on 2006-06-24
bump

---

### Post by wpshooter on 2006-06-24
Any thoughts on this ???  I can't be the only person that has ever run across this.

Thanks.

---

### Post by wpshooter on 2006-06-24
Here is listing of disklabel parameters that are given in Gparted.

default - msdos
              amiga
              bsd
              dvh
              gpt
              mac
              pc98
              sun
              loop

Is Gparted a Ubuntu/linux utility ?  If so, why would it assign a default disklabel of MSDOS ?

What are these other 8 disklabel types for ?

Thanks.

---

### Post by silhouette on 2006-07-04
I'm not familiar with GParted but I do know of a GNU utility called parted, so it sounds like GParted is just a front-end. In any case, I don't know the reason why there are so many disklabel types, but I do know that they all describe a partition table differently. The fdisk man page has some information on this - you can read it [here](http://www.die.net/doc/linux/man/man8/fdisk.8.html). I think the MSDOS disklabel is used by default because most people are familiar with it, and of course it's the only one Windows uses, so if you want a dual-boot setup, you don't really have to change anything.

---

### Post by wpshooter on 2006-07-06
[QUOTE=silhouette]I'm not familiar with GParted but I do know of a GNU utility called parted, so it sounds like GParted is just a front-end. In any case, I don't know the reason why there are so many disklabel types, but I do know that they all describe a partition table differently. The fdisk man page has some information on this - you can read it [here](http://www.die.net/doc/linux/man/man8/fdisk.8.html). I think the MSDOS disklabel is used by default because most people are familiar with it, and of course it's the only one Windows uses, so if you want a dual-boot setup, you don't really have to change anything.[/QUOTE]

Thanks. 

The link writeup provides only a passing reference to disklabel.

What disklabel(s) can be safefly used if dual booting is NOT going to be done (only want to use Ubuntu) ?  Is there one that would be preferred over the others ?

What about the one that is listed as **GPT** ?  Is this somehow a reference to the Gparted program ?

Thanks.

---

### Post by SoloSalsa on 2006-07-06
I have the same question.  Which label is best?  I have a 12GiB drive.
I do not want Windows at all either.
Thanks!

---

### Post by silhouette on 2006-07-07
Oh sorry, I didn't make that clear. The "MS" in an MSDOS disklabel doesn't mean it's incompatible with Linux (I would guess that it's merely a reference to the fact that Microsoft invented this particular format), so it's safe to use it even if just installing Ubuntu.

I'm not too sure what the other disklabels are for. The AMIGA, BSD, and MAC disklabels look like they're only compatible with those OS's. The SUN format is used more on UNIX-like systems, it seems. GPT stands for [GUID Partition Table](http://en.wikipedia.org/wiki/GUID_Partition_Table) and is a new-ish partition table format invented by Microsoft. Also it appears you only need to be concerned with using it if you're trying to make a 2TB (that's terabyte) or greater filesystem. I'm not sure what the LOOP label is for.

Anyway, the DOS label works just fine :)

---

