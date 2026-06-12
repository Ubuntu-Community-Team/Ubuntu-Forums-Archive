---
title: "can I format HDD before installing Ubuntu?"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by ilyaz73 on 2011-02-24
I have an old Dell laptop that I inherited from someone. They had Win XP on it and I already replaced it with Ubuntu 10 from a bootable CD. However, I don't know whether it automatically formatted the entire drive before installing itself. I want to double check that neither I nor enyone else can recover any files of the previous owner fro this machine. Is there an option to format during install? I do not recall seeing one but maybe I missed it. If not, what's the best way to format the hard drive before (re)installing Ubuntu?

thanks much!

---

### Post by dino99 on 2011-02-24
welcome :)

and follow this little help:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

.... more info into the links below

---

### Post by sanderd17 on 2011-02-24
To be sure that nobody can recover information, you should overwrite every bit at least 7 times.

You can use shred for this.

```

shred -vfz -n 10 /dev/sda

```

will overwirte your primary hdd 10 times, the f option will force to overwrite all files, the z will overwrite even unused parts and the v will show you info.

Off coarse this has to be executed from a live CD or so.

use 
```

shred --help

```
to get info about shred.

---

### Post by smurphy_it on 2011-02-24
Anyone with some knowledge can recover files from a formatted drive.  If the files are that sensitive, then you should use a hard drive erasure program first to 'securely wipe your files'.

There are a slew of them out there, and dd can do it.  However, expect it to potentially take some time, as wipe standards are usually at least 3 times over-write.

It basically over-writes every bit on the drive with zero's.  Hence it takes some time.

I believe one such program is called "shred".  Just boot from a live USB stick, or LIVE CD first, and run it from there.

---

### Post by psusi on 2011-02-24
> **sanderd17 said:**
> To be sure that nobody can recover information, you should overwrite every bit at least 7 times.


Only if you think you are James Bond.  There is no basis in reality for this and that number is just pulled from thin air.  Everyone that suggests that has a different "minimum".  Simply writing zeros to the drive ONCE makes retrieval of the previous contents impossible short of dismantling the drive and examining it with an electron microscope.  If the CIA or whoever is really going to do that, who is to say how many times you have to overwrite it?

The drive's built in security erase feature that you can activate with hdparm will securely erase all of its contents, and a lot faster than shred.

---

### Post by smurphy_it on 2011-02-28
Last I heard the FBI standard was 10 times.  Also heard it is possible to recover if only writing zero's once to the drive.

---

