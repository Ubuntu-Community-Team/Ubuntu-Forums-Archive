---
title: "In trouble, right?"
date: 2005-08-30
forum: Installation &amp; Upgrades
---

### Post by handaxe on 2005-08-30
Fool that I am, I deleted my Ubuntu partition and then made a new one of larger size. (If you must know :|, I was trying to resize the partition using qtparted off a boot disk but the partition would not resize (others have seen this), despite there being 5 gigs free from a successfully shrunk NTFS partition).

I did not reformat. I did however reset the partition back to the original start / end parameters.

Now I have ext3 partition that is as empty as the SAHARA! Surely the files are recoverable as this is a partition problem and not overwriting, or did qtparted do that in remaking /dev/hda2?

Any help gratefully received.

(sigh!)

HA

---

### Post by az on 2005-08-30
Hmm..  Perhaps setting the start and end is not enough.  Parted has a rescue function

basically


parted
rescue
(start) 
(end)

ans see what happens

Also, if you can find another machine, install the parted-doc package.  Perhaps that documentation is available o the parted website.  There should be step-by-step instructions...

---

