---
title: "md5sum mismatch, ISOs on two different mirrors"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by Snowbat on 2007-02-07
```
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso (http://releases.ubuntu.com/6.10/MD5SUMS)
5e52369e420286389852acef8a934e23  ubuntu-6.10-desktop-i386.iso (South America/Brazil/Edugraf - INE - CTC - UFSC)
084296f4a4a6f5f5fd40e6521efee0d1  ubuntu-6.10-desktop-i386.iso (South America/Brazil/Ubuntu.c3sl.ufpr.br)
```

Both downloads show file size of 732293120 and mount without error using -o loop.  Have I got two bad downloads here or is it normal for Ubuntu images on the mirrors to have different md5sums?

---

### Post by lhtown on 2007-02-07
Are you giving us the md5sums from the mirror or from your download? It seems they should be identical on the mirror.

---

### Post by lhtown on 2007-02-07
If you have occasional trouble with your network or internet connection, you should use BitTorrent since it makes it easy to resume and verify a download.

Also, the md5sum is different after you burn it to a CD than just the raw download.

---

### Post by Snowbat on 2007-02-07
The md5sums I posted are of the ISO files I downloaded (apart from the first which is from the Ubuntu website).  I haven't noticed any problems with my DSL connection recently and I had no md5sum problems with the last few Mandriva releases I downloaded.

---

### Post by mikewhatever on 2007-02-07
Just a suggestion, but can it be, that different locations have different default languages for live CD sessions.

---

### Post by Snowbat on 2007-02-07
I guess that's a possibility.  Both mirrors are in Brazil and I'd expect localization to be either Brazilian Portuguese or English.  However, the md5sums of the files I downloaded neither match each other nor the published md5sum for this release so something seems to be amiss.

I'm investigating.  So far:
All filenames, directory names, and creation dates within each ISO match (mounted each ISO, ls -lR to a text file, diff textfile1 textfile2)

---

### Post by Snowbat on 2007-02-08
md5sum -c md5sum.txt has located a bad file within each downloaded ISO image.

ISO from UFPR:
./casper/filesystem.squashfs: FAILED
md5sum: WARNING: 1 of 412 computed checksums did NOT match

ISO from UFSC:
./bin/components/necko.dll: FAILED
md5sum: WARNING: 1 of 412 computed checksums did NOT match

---

### Post by ausgnome on 2007-02-08
I'm having the same problems 

  Tried all the asia pacific mirrors and two in the states 

  plus bittorrent all fail checksums 

   Even tried on a friends MAC on a different ISP 

   Theres definately something screwy somewhere

   If anyones got a copy of  Edgy i386 on a ftp server somewhere I'd like a link

---

### Post by maxamillion on 2007-02-08
rsync is your friend

---

### Post by ausgnome on 2007-02-08
rsync  probably would be if I new what I was doing with it

---

### Post by ausgnome on 2007-02-08
Well I tried rsync 

  and I get this 

  ubuntu-6.10-desktop-i386.iso
   732293120 100%    1.03MB/s    0:11:19 (xfer#1, to-check=0/1)
WARNING: ubuntu-6.10-desktop-i386.iso failed verification -- update discarded (will try again).
ubuntu-6.10-desktop-i386.iso
   170506912  23%    2.00MB/s    0:04:33


 rsync -Lvv --progress mirror.pacific.net.au::ubuntu-releases/edgy/ubuntu-6.10-desktop-i386.iso .

---

### Post by mikewhatever on 2007-02-08
Ever considered using bittorrent? Personally, I much prefer it over ftp.

---

