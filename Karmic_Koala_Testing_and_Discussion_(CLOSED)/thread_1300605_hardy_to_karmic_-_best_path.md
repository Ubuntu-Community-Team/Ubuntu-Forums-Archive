---
title: "hardy to karmic - best path?"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by aaronp on 2009-10-25
Hi all,

I've decided to upgrade from my current Hardy to Karmic when it is released this week. Not keen on following the upgrade path via Jaunty and Intrepid so it looks like I'll be doing a fresh install.

The good news is that I've got /home on a separate partition (same physical disk). I also have a couple of storage partitions, one on the same disk and then another one on an external usb drive.

Just wanted to find out the best method for safely doing this upgrade and, if possible, retaining all of the packages that I currently have installed as much as possible. (Including things that I may have added to my sources.lst over the past 12 months)

Can anyone advise the best approach and also which directories/files on the root parition I should backup etc.?

thanks
Aaron

---

### Post by zvacet on 2009-10-25
You will install Karmic on top of Hardy,**and you will not format any partition except root.**To save packages you installed in past use [APTonCD.]("http://aptoncd.sourceforge.net/") You will find it in synaptic.Other way is to type in terminal

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
```

E-mail that file to yourself and when you install Karmic then put that file in home directory and type

```
sudo xargs aptitude --schedule-only install < my-packages

sudo aptitude install
```

---

### Post by aaronp on 2009-10-25
> **zvacet said:**
> You will install Karmic on top of Hardy,**and you will not format any partition except root.**To save packages you installed in past use [APTonCD.]("http://aptoncd.sourceforge.net/") You will find it in synaptic.Other way is to type in terminal

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
```

E-mail that file to yourself and when you install Karmic then put that file in home directory and type

```
sudo xargs aptitude --schedule-only install < my-packages

sudo aptitude install
```

Thanks very much zvacet, great response.

Also, wondering whcih directories/files on my root partition I should back up before I start the upgrade. Anyone?

thanks
Aaron

---

### Post by zvacet on 2009-10-25
> Also, wondering whcih directories/files on my root partition I should back up before I start the upgrade.

All packages installed by synaptic,apt-get or aptitude are stored in var/cache/apt/archives.I believe you want to back up that.For that purpose use Aptoncd.

---

### Post by earthpigg on 2009-10-25
generally (assuming you are not running a server), there is no need back anything from your root partition up unless you have some software installed that is not in the repositories.

i disagree with the notion of backing up /var/cache/apt/archives unless you have dial up or unreliable internet - you will be backing up the 9.04 versions of software when you can just install the 9.10 versions via the method described above instead.

all of your personalized settings and whatnot are kept in /home.

even though you can indeed do what is described above to keep your /home in place during the fresh install, i *strongly suggest* you have a good backup anyways. you may misclick and format /home, your neighborhood may have a power failure mid-install, or the planets and moons may align in such a way that your install fails and you lose /home.

---

### Post by aaronp on 2009-10-25
> **zvacet said:**
> All packages installed by synaptic,apt-get or aptitude are stored in var/cache/apt/archives.I believe you want to back up that.For that purpose use Aptoncd.

Thanks again.
Sorry, I am referring to any configuration files or particular files that might be stored outside of my home directory that will get blown away when I format the root partition (e.g. cron jobs? etc.)

thanks
Aaron

---

### Post by oldfred on 2009-10-25
I have updated since 6.10 (I think) and have lots of stuff still installed. I also plan on a clean install if only to houseclean out a lot of the old. I was experimenting with the 64 bit version of 9.04 and exported a packages list and reimported it into the 64 bit verison. I ended up with a lot of old stuff again. I noticed python 2.4 and 2.5 since we are now on 2.6, I went back into synaptic and found a lot of residual config files also.
I also have installed some .debs and when I started housecleaning it wanted to delete these also. I am not sure there is a 100% good way.

Also on configs, I thought I might need them but then realized a lot of my current configs are what are causing so issues as they are old and the new versions are a lot different. There may be settings somewhere and I am sure I will want something, so I am backing up a lot of stuff that I hope I never need.

---

### Post by aaronp on 2009-10-26
thanks for your help guys

---

