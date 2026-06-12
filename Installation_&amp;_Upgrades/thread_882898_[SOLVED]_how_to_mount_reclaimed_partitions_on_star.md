---
title: "[SOLVED] how to mount reclaimed partitions on startup?"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by grikdog on 2008-08-07
I had Vista and Ubuntu in separate partitions, booting via Grub.  Vista choked, croaked and rotted, so I salvaged the Vista ntfs partition and for some reason, subdivided that into two ext3 partitions (I forget the history, it made sense at the time).

The problem is, I can *manually* mount those partitions, but I would rather do it on startup.  I understand I should edit fstab, but...  That file is intense, wherein partitions masquerade as UUID numbers that I have no idea where they came from.

How should I set up fstab to mount my salvaged /dev/sda1 and /dev/sda4 partitions? How do I know what UUID numbers to use?

---

### Post by grikdog on 2008-08-07
never mind - I found a discussion of vol_id elsewhere on the web, so figured out how to get UUID for partitions...

---

### Post by GreenN00b on 2008-08-07
You can also use the /dev/<partition> in fstab without problems ...

---

### Post by grikdog on 2008-08-07
> **GreenN00b said:**
> You can also use the /dev/<partition> in fstab without problems ...
Thanks, I'm using the UUID form, because the discussion I found has a pretty good rationale for using it (basically, it disambiguates hardware if you shuffle it during a move to another site, etc.)

It's nice to know that Ubuntu is sane under all the layers ;-)

---

### Post by jpaulb on 2008-08-07
> **grikdog said:**
> never mind - I found a discussion of vol_id elsewhere on the web, so figured out how to get UUID for partitions...

Please tell where.

---

### Post by grikdog on 2008-08-12
> **jpaulb said:**
> Please tell where.
Try Google.  That's how I found:

[http://coreythompson.com/2008/01/etcfstab-help-for-distro-hoppers/](http://coreythompson.com/2008/01/etcfstab-help-for-distro-hoppers/)

Might help.
d

---

