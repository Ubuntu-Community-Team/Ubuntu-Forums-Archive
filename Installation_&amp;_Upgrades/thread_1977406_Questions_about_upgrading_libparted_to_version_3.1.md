---
title: "Questions about upgrading libparted to version 3.1"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by Curious00 on 2012-05-10
I'm using Oneiric, and I need to be able to create more than 15 partitions on a big SATA disk which I'm using for backup purposes. 

I read [the release notes](http://sourceforge.net/projects/gparted/files/gparted/gparted-0.12.1/) for Gparted 0.12.1 and saw that this capability is now available.

So, I went about [installing 0.12.1 by using the special PPA](http://www.ubuntuupdates.org/package/getdeb_apps/oneiric/apps/getdeb/gparted). However, it still reports that it is using libparted 2.3. 

What's the best way to upgrade libparted to 3.1 on Ubuntu?

---

### Post by Curious00 on 2012-05-10
Ok... I've figured out a workaround. 

I downloaded [the latest source for parted](http://ftp.gnu.org/gnu/parted/) (3.1), and compiled it myself. Upon the advice built into the configuration routine, I found I needed to use two special options:


./configure --disable-device-mapper --without-readline
make


From then on, the process went smoothly, except that "make install" failed, and I needed to restore the original Ubuntu parted program with: 


apt-get remove parted
apt-get install parted


Happily, I was able to use the newly minted 3.1 parted binary in place. It had been created in the "parted/" folder within the unzipped archive. 

So, what I did was this: I had Gparted create each partition, one by one, and even though it errored out, I was able to check out the exact placement of the sector boundaries by using parted. I started the program: (sudo ./parted /dev/sda), and at the interactive prompt, typed this:

```
unit s
```

and then 

```
print
```

I noted the sector numbers of the boundaries of the slice, and then deleted the badly created partition with parted:

```
rm #
```

and created it again:

```
mkpart logical #######s ######s
```

Next, I was able to use either the regular command line tools such as (mkntfs and mke2fs) or even Gparted itself, to create the file systems within the disk slices.


It's a bit more work, but it seems to create reliable partitions that can be accessed by all the various operating systems which I use on my machine. Plus, I learned a lot, which is always cool! :p

---

### Post by Curious00 on 2012-06-04
**Subsequent discovery - cfdisk**

Some weeks later, I've discovered the glories of cfdisk. This is a much better partitioning tool than parted or fdisk or gparted, at least in my opinion. After learning a bit more, I thought it wise to redo the work I talked about above using cfdisk, so I could align the geometry properly according to the standard Microsoft geometry rules (255 heads, 63 sectors per track, and 63 hidden sectors before each logical slice, and before the initial primary partition).

The cfdisk version which comes with Ubuntu 11.10 works just fine, although the computer seems to need a reboot before you can format the new partition if it's one of the really high-numbered ones.

---

