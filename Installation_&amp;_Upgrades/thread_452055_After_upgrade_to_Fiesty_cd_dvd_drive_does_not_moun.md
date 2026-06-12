---
title: "After upgrade to Fiesty: cd dvd drive does not mount"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by mpx on 2007-05-22
I've Pentium 4 PC. I just did an upgrade to Fiesty from Edgy using alternate install CD. Now after booting into gnome, the cd and dvd drives are not recognized. 

Please help.

Thanks,
mpx

---

### Post by magicfab on 2007-05-23
Can you post the content of the /etc/fstab file ? You should have a line with something similar to:
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by merlinus on 2007-05-23
Pardon me for jumping in, but I have had a similar problem from day one of installing Feisty.

My DVD-ROM drive is recognized, but NOT my Plextor cd-burner.

Here is the relevant fstab entry for the dvd-rom drive:

```


/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0


```

Nothing, however, for the burner, which continues to work perfectly in Win2000.

So far, no one has been able to offer any solution, not on the forums, launchpad, or anywhere else.

Many thanks!

-merlin

---

### Post by NutrOn on 2007-07-30
I added a bug report for this.
sudo: /dev/hdc: command not found
A similar problem was reported by a person who had a bad checksum for alt cd install.
If I query drives in Dev it says  cannot open dev/cdrom no application is known for this type of fie.
I cannot mount drive as user and cannot su to become user. It may be a missing portion of the base install, but how do I locate what packages are corrupt or missing?
--Nutr0n--

---

### Post by minhtrietle on 2007-08-02
I've tried so hard to deal with this problem too but this is what I ended up with.

:mad::mad::mad::mad:

---

