---
title: "Md5sum(s) wrong"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by totosplatz on 2007-04-23
I downloaded ubuntu-7.04-desktop-amd64.iso and ubuntu-7.04-desktop-i386.iso and got these md5sums -

    e0af27dc51b369b729d1a9d5706afa49  ubuntu-7.04-desktop-amd64.iso
    0b4c4a9e79817235c491de3b0db2ca20  ubuntu-7.04-desktop-i386.iso

-rw-rw-r--  1 jhowe jhowe 733171712 Apr 22 20:30 ubuntu-7.04-desktop-amd64.iso
-rw-rw-r--  1 jhowe jhowe 731797504 Apr 22 23:43 ubuntu-7.04-desktop-i386.iso

These md5sums don't match the proper codes - I have downloaded ubuntu-7.04-desktop-i386.iso
a second time and a 'diff' shows the second file is identical to the first.

The md5sum is NOT what is shown on the website:

    e296e3468358789904097fc8df29609a  ubuntu-7.04-desktop-i386.iso

Is the md5sum shown on <https://help.ubuntu.com/community/UbuntuHashes> 

My download was from the mirror in China at:

    <http://mirror.rootguide.org/ubuntu-releases/feisty/ubuntu-7.04-desktop-i386.iso>

In other words, the download was repeatable yet the md5sum is incorrect
according to the official values for this particular release. I will go ahead now
and make CDs with my two downloads but I wonder about the md5sum
values published.

Thanks.

---

### Post by Peacepunk on 2007-04-29
Downloaded today from Cambodia using Belgian server (skynet), overnight [64kbps! 14hours long :) ]
Thai servers where too slow, Japan & TW usually doesn't work either.

md5s as reported by k3b matches official as quoted in your post.

Cheers

---

### Post by amio on 2007-05-01
i have the same problem,
got an desktop-amd64 edition from rootguide.org with this md5sum:

e0af27dc51b369b729d1a9d5706afa49

What's wrong with it?

---

### Post by cookfromfrozen on 2007-05-01
If the MD5 sums do not match with those posted on the Ubuntu site then don't use that ISO, there's a chance one of the mirrors is holding a bad or even tampered with copy of the ISO.

Download from a different mirror.  Burning an ISO when you know the MD5sum is incorrect will only lead to trouble.

If every mirror is giving incorrect sums then you either have an unreliable internet connection that is corrupting downloads or a hardware problem.

---

### Post by flysurferrosa on 2007-05-03
I am having a similar problem; I downloaded the ISO twice and both times the sum check did not match with the ones on the ubuntu hash.  The sums for each ISO I downloaded were different too.  Should I keep trying different mirror sites until I find one that mathes?

---

### Post by tubeamp on 2007-05-07
I can confirm that I have downloaded ubuntu-7.04-desktop-i386.iso, and got the same md5sum as totosplatz:-
e296e3468358789904097fc8df29609a
First install failed at about 90%, it's installing again now. Will advise of outcome.

---

### Post by tubeamp on 2007-05-07
Second attempt at install finished with no reported errors. md5sum must be OK....

---

