---
title: "urgent help-dvd not being read in 64 bit ubuntu 8.04"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by neerajkumar on 2008-05-28
hello..
i had installed ubuntu very recently and am a brand new user.
when i tried o read dvd's in it,nothing seems to appear.
and the case is few dvd's are being read.
my mp3 dvd is read.but when i try to read a dvd wt divx movies it doesnt mount..nothing appears...
i am helpless without the cd rom.
can someone help me please?

---

### Post by zvacet on 2008-05-28
```
sudo apt-get install ubuntu-restricted-exstras
```

But maybe you allready have that installed.For playing DVD you need libdvdcss2 package.You will find it in medibuntu repository.To add that repo to your source list type this

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```

---

### Post by neerajkumar on 2008-05-28
hey..
but the thing is am able to playt some dvd's.
like an mp3 dvd.
but not a data dvd.
i can play divx files downloaded from de internet.
but here am not able to mount the data dvd on the first place.
is there any solution?
i hav the libdvdcss2 package installed.

i installed al that u told..but stil its not working...

---

### Post by zvacet on 2008-05-28
Do you have w64 codecs installed?If not in synaptic search box type w64 and you will find them.Install.

---

### Post by neerajkumar on 2008-05-28
> **zvacet said:**
> Do you have w64 codecs installed?If not in synaptic search box type w64 and you will find them.Install.

yes i do have that.
but still its not working.
something else i noticed was after installing the updates thru update manager i got an errror at the end.

it was like this.

"Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead."

does this have anything 2 do wit it?

---

### Post by zvacet on 2008-05-28
No it doesn´t.It simply say that your CD is not in drive and because of that system is not able to fatch updates from it.Go to the system>admin>software sources and there check/uncheck CD as repository.That will fix it.But that is not answer to your original question.

---

