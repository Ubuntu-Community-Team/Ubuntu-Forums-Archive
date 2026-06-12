---
title: "gparted 2.1"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2006-08-19
This is what I did:

I DL GPARTED 2.1  because it has all of the needed NTFS fixes and then did:
```
apt-get build-dep gparted
```
and after all the dependencies were installed I untarred GPARTED 2.1, then did
```
./configure
```
after it finished OK without any dependency problems I did
```
make
```
and after that went ok I did
```
checkinstall
```

The GPARTED 2.1 starts up great. But I am curious how reliable is it since I manually compiled it?? Since there must be a reason that the newer version still isnt in the repos considering that all the dependencies are the same as with GPARTED 1.0.

Is it safe to use this compiled version to resize my NTFS partition?

---

### Post by zxee on 2006-08-19
I think hand compilied programs are as solid as things brought in by apt-it's my opinion though. I've never noticed in my own use or read anywhere that programs you compile, provided they install correctly, are any less stable than what the package manger installs. The package manager of course does all the dependency stuff we people don't want to fritter with.
There's also a live gparted cd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) I'm not sure what version of gparted is on that.

Of course the final question is a loaded one :) who can totally predict whether it will work? That's why you do backups right. 
I'm not being wise here BTW just reminding you that there is a certain unpredictability in using programs that alter drive media.

---

### Post by mlind on 2006-08-19
You should probably get newer gparted source package from Edgy or Debian unstable and compile it for your distribution instead.

Building from maintained source package has its benefits. Those often include fixes from package maintainers and are (usually) tested by numerous other people.

---

### Post by ashrack on 2006-08-19
Am interested in resizing the NTFS partition for 10GB to add another FAT32. Here's my current partition table:
[ATTACH]14554[/ATTACH]
And this is a preview of what happens when I resize the NTFS partition:
[ATTACH]14555[/ATTACH]

But now I dont know where to put it? As a logical or a primary partition! What do U suggest??

---

### Post by mlind on 2006-08-19
> **ashrack said:**
> 
But now I dont know where to put it? As a logical or a primary partition! What do U suggest??

It doesn't matter anymore I guess. There can be only 4 primary partitions, but numerous logical partitions.

---

### Post by ashrack on 2006-08-20
so I create the FAT32 partition as a logical partition of the NTFS one??

---

