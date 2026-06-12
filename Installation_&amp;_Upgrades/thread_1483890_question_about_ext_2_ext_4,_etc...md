---
title: "question about ext 2/ ext 4, etc.."
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by pdlethbridge on 2010-05-15
Why is there a difference and less problems when I download and install to ext 4 rather than ext 2?
Using ext 2 has been my normal since the 6.04, 6.10 days. But on this release it was a nightmare to install unless I used ext 4. Why is that?

---

### Post by pdlethbridge on 2010-05-20
bump

---

### Post by jlaki on 2010-05-20
Why are you avoiding ext4?

---

### Post by uRock on 2010-05-20
EXT4 is the default because it has more capabilities.

---

### Post by pdlethbridge on 2010-05-21
capabilities of what? I thought they were only different places to put things. How are they different?

---

### Post by Drenriza on 2010-05-21
[http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2)

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

The big difference for me (and the reason i use ext4 and not reiserFS) is that ext4 now has the ability of journaling. Something that in the beginning was not native to the Ext filesystem.

---

### Post by pdlethbridge on 2010-05-21
Ah, now I see, thanks. Now explain Unix Millennium Bug, Y2K38 in 50 words or less.:):):):):)

---

### Post by Drenriza on 2010-05-21
Unix 2038

As with all Unix and Unix-like operating systems, time and dates in FreeBSD are represented internally as the number of seconds since the 1st of January 1970 (the Unix "epoch"). Currently, that figure is stored as a 32 bit integer, and will run out part way through 2038. By then we should (hopefully) be using a counter of 64 bits (or greater) which should be good until the end of the universe.
[http://www.broadbandreports.com/forum/r19717856-Unix-Millennium-bug-in-2038](http://www.broadbandreports.com/forum/r19717856-Unix-Millennium-bug-in-2038)

Meaning that half way through 2038 the 32bit lenght will not be sufficient to store the time and dates in FreeBSD, in seconds from 1970 to 2038. And a new bit lenght will be needed to continue the counting.

---

### Post by pdlethbridge on 2010-05-21
Hey, I said 50 words or less. Also in binary, thats the day they all change to 1's.

---

### Post by John Bean on 2010-05-21
> **pdlethbridge said:**
> Using ext 2 has been my normal since the 6.04, 6.10 days.

6.04? Don't remember that one. Was it Breezy Drake or Dapper Badger? :-)

---

### Post by pdlethbridge on 2010-05-21
no, I think it was breezy dapper:p:p:p

---

### Post by uRock on 2010-05-21
01110101 00111001 11110101 01001111 11010010 00010001 11111101 01011001 01011101 01111001 10101010

---

### Post by pdlethbridge on 2010-05-21
looks like the ones won.

---

### Post by pdlethbridge on 2010-06-30
from what I read, the extensions are like the windows file systems, fat, fat32, ntfs. would I be right?

---

### Post by dabl on 2010-06-30
> **pdlethbridge said:**
> Ah, now I see, thanks. Now explain Unix Millennium Bug, Y2K38 in 50 words or less.:):):):):)

"Y2K, but 38 years later"   :lolflag:


Here's lots about Linux (and other) filesystems: [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by John Bean on 2010-07-01
> **pdlethbridge said:**
> from what I read, the extensions are like the windows file systems, fat, fat32, ntfs. would I be right?

NTFS has absolutely no connection with FAT, and in particular is not some sort of extension of it; in fact it's not a FAT ("File Allocation Table") based file system of any sort.

---

