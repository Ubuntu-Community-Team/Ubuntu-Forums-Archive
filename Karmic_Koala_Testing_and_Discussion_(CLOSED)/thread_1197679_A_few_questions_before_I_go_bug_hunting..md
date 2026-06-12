---
title: "A few questions before I go bug hunting."
date: 2009-06-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by stuart.reinke on 2009-06-26
I've downloaded and burned the Alpha2 release of Karmic. I intend to install a dual boot with Hardy and search for bugs.  But first I need a couple of answers...

1.  I seem to remember seeing something about Grub 2 not working properly yet but can't find the thread again.  What do I need to do about it? (if anything)

2. I assume that the Karmic installation will be able to mount and access the files on the Hardy partition (ext3), but Hardy will not be able to access the Karmic partition (ext4). Is this correct?

Any other advice will be appreciated. I'm kind of excited to have the opportunity to help out. I hope I can do some good.

Stu

---

### Post by Rainstride on 2009-06-26
> **stuart.reinke said:**
> I've downloaded and burned the Alpha2 release of Karmic. I intend to install a dual boot with Hardy and search for bugs.  But first I need a couple of answers...

1.  I seem to remember seeing something about Grub 2 not working properly yet but can't find the thread again.  What do I need to do about it? (if anything)

2. I assume that the Karmic installation will be able to mount and access the files on the Hardy partition (ext3), but Hardy will not be able to access the Karmic partition (ext4). Is this correct?

Any other advice will be appreciated. I'm kind of excited to have the opportunity to help out. I hope I can do some good.

Stu
I'm testing A2 in a virtual machine and have had no problems with grub2. it will give a popup when you update that asks you to check the HD for grub. i just checked the main drive the file system was on, it worked fine.

yes on number 2, ext4 isn't in the hardy kernel so as far as i know it won't recognise it.

---

### Post by psyke83 on 2009-06-26
> **stuart.reinke said:**
> I've downloaded and burned the Alpha2 release of Karmic. I intend to install a dual boot with Hardy and search for bugs.  But first I need a couple of answers...

1.  I seem to remember seeing something about Grub 2 not working properly yet but can't find the thread again.  What do I need to do about it? (if anything)

2. I assume that the Karmic installation will be able to mount and access the files on the Hardy partition (ext3), but Hardy will not be able to access the Karmic partition (ext4). Is this correct?

Any other advice will be appreciated. I'm kind of excited to have the opportunity to help out. I hope I can do some good.

Stu

Make sure to read the release notes, it's especially important for Alpha 2. If you have a dual-boot configuration you may encounter GRUB2 errors - the issue is described in the notes and the bug reports are linked.

[http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2)

---

### Post by stuart.reinke on 2009-06-26
> **psyke83 said:**
> Make sure to read the release notes, it's especially important for Alpha 2. If you have a dual-boot configuration you may encounter GRUB2 errors - the issue is described in the notes and the bug reports are linked.

[http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2)

That's what I'm looking for. Just looking in the wrong place.

thanks.

Stu

---

