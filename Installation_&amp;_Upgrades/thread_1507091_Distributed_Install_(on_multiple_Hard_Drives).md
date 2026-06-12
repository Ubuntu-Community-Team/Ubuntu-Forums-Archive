---
title: "Distributed Install (on multiple Hard Drives)"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by paddy.melon on 2010-06-11
Here's Basic idea:
I've got a first-gen SSD with the problems so, I can't write very much or, could break it however, reading works 100% perfectly

So: 
Am I able to have some folders (important boot ones) on the SSD that don't ever get touched (except for maybe upgrading) but, are read frequently and the rest on my WD Raptor? How would I install this way...

Thanks so much for your help!

---

### Post by arrange on 2010-06-11
My 2 cents:
 * uninstall/disable everything you don't need - important
 * typically you don't need to write to any partitions on a regular basis except */var*, */home* and */tmp*. But on my 10.04 system I can see quite regular writes to */etc* as well. So place these 4 partitions on the HDD, and the rest you can keep on SSD IMO
 * edit your */etc/fstab* in a way that you mount your "SSD partitions" as **ro** (*read-only*). I would also recommend adding a **bootwait** option. If you want to upgrade etc you can always remount them as **rw** later. 

I say "my 2 cents" because I haven't done it myself.

---

### Post by srs5694 on 2010-06-11
You should ***never*** attempt to separate /etc from root (/)! Because /etc contains vital boot files, such as /etc/fstab, it *must* be accessible as part of the root (/) filesystem. Trying to do otherwise will produce an unbootable system. The same is true for /bin, /sbin, and /lib (or /lib32 and /lib64, if that's how your system configures it).

---

### Post by arrange on 2010-06-11
I'm sorry, you're right of course, to separate */etc* from **/** was a stupid idea, I don't know what I was thinking.

But he should be able to separate the other three I proposed - /var, /home and /tmp, shouldn't he?

---

### Post by srs5694 on 2010-06-11
Yes, /var, /home, and /tmp are all safe to put on separate partitions, and this is commonly done for all of them in certain environments.

---

### Post by paddy.melon on 2010-06-12
OK, sounds like an awesome idea: Put /var, /home and /temp... Off to do that now! Thanks guys!

---

### Post by JohnnyC35 on 2010-06-12
> **paddy.melon said:**
> OK, sounds like an awesome idea: Put /var, /home and /temp... Off to do that now! Thanks guys!

I don't suppose it would be possible to put /var /home and /tmp as tmpfs if you had the RAM available. Or would this cause massive breakage?

---

### Post by paddy.melon on 2010-06-12
> **JohnnyC35 said:**
> I don't suppose it would be possible to put /var /home and /tmp as tmpfs if you had the RAM available. Or would this cause massive breakage?

Why bother? Plus, this is for a MythBox so, the more RAM, the better, none to waste with these videos

---

### Post by JohnnyC35 on 2010-06-12
to reduce writes on the SSD if you only have that and not a hard drive

---

### Post by srs5694 on 2010-06-12
> **JohnnyC35 said:**
> I don't suppose it would be possible to put /var /home and /tmp as tmpfs if you had the RAM available. Or would this cause massive breakage?

I'm not an expert on tmpfs, but my understanding is that it's volatile -- that is, it disappears between boots. As such, putting /tmp in there might be OK, but putting either /var or /home there is asking for trouble, since files in both directories must be persistent across boots. /home, of course, holds your user data files. Even on a MythTV box, as mentioned in another post, these are important, since the frontend runs as a normal user and some frontend configuration files go there. /var holds various files that should be persistent, including log files and, depending on MythTV configuration, some MythTV database files. You wouldn't want your scheduling data to disappear whenever you reboot!

---

