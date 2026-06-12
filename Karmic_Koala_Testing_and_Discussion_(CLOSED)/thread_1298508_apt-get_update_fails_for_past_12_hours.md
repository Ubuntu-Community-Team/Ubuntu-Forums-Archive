---
title: "apt-get update fails for past 12 hours"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Tomy on 2009-10-22
I tried three other mirrors with same message.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

---

### Post by Nesaskewatch on 2009-10-22
Try removing bzip2, do the update, then reinstall?

Had a similar prob with filter/binfilter/openoffice.org.  Removed it, updated then reinstalled no probs.

Haven't tried it with bzip2 though...

---

### Post by Tomy on 2009-10-22
> **Nesaskewatch said:**
> Try removing bzip2, do the update, then reinstall?

Had a similar prob with filter/binfilter/openoffice.org.  Removed it, updated then reinstalled no probs.

Haven't tried it with bzip2 though...

I assume you mean to remove the package lists from /var/lib/apt/list. I tried this and got the same error message.

The universe list is the only probem.

This line in /etc/apt/sources.list works fine:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted multiverse

This line gives me the error:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted **universe** multiverse

The universe package list fails to download.

update: if I actually remove /bin/bzip2 gzip is used instead but the universe list still fails to download.

---

### Post by winotree on 2009-10-22
I just clicked your original link and got it -- maybe try again?  ;)

EDIT - added word *original*

---

### Post by Tomy on 2009-10-22
> **Tomy said:**
> I tried three other mirrors with same message.

W: Failed to fetch [us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2]("http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2")  Sub-process /bin/bzip2 returned an error code (2)

Okay, I can download the universe Packages.bz2 file and save it to my Desktop but when I right-click and "extract here" I get an error message "An error occured while extracting files".

If I do the same thing with multiverse Packages.bz2  "Extract here" does work.

Seems strange that no one else is having this problem.

---

### Post by Tomy on 2009-10-22
> **winotree said:**
> I just clicked your original link and got it -- maybe try again?  ;)

EDIT - added word *original*

Can you extract it??

---

### Post by winotree on 2009-10-22
Yes.  Although all I can see is a list.  [Sorry for the delay -- it was kitty-food-time].  :)

---

### Post by Tomy on 2009-10-22
> **winotree said:**
> Yes.  Although all I can see is a list.  [Sorry for the delay -- it was kitty-food-time].  :)

Thanks,
If you are referring to a long list of all the packages then it must be working for you.

I'm going to try the "main" server instead of the "us" server and see if that makes any difference.

---

### Post by winotree on 2009-10-22
Want me to PM a copy to you??

EDIT - on second thought -- that thing's huge!  Better not...

---

### Post by Tomy on 2009-10-23
Well, using the "main" server finally worked.

The first try I got an error on one of the other files and  the universe Packages.bz2 came through okay so I tried again and got all of them.

There must be a problem on my end (isp, router, nic ??) that is corrupting the files.

Thanks for the help.

---

### Post by winotree on 2009-10-23
Sure.  Anytime.  :D

---

### Post by Tomy on 2009-10-23
It was my router. I tried to "apt-get upgrade" and got an md5sum mismatch error because a file was corrupted. After swapping the router for an old Linksys I had on the shelf everything seems to work.

Thanks again

---

