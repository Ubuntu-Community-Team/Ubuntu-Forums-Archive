---
title: "Backup &amp; Restore Question"
date: 2023-11-18
forum: Installation &amp; Upgrades
---

### Post by shaneabunting on 2023-11-18
Hi forum, I am currently trial running Ubuntu on an M1 MacBook Pro just finding the right software / trialing it with some data. If I back this up to a hard drive, and eventually buy a new machine, will I be able to restore it to the new machine as-is, or does this lead to issues? 

This is an ARM64 install (and sadly with that, I can't get some programmes running yet.  My concern is, with it being ARM64, am I asking for trouble to restore it to a new x86 machine?

---

### Post by TheFu on 2023-11-18
Yes for all binary, machine specific data. Most data formats are specified in a way to work across different CPU architectures.  You won't be copying compiled programs between any 2 different CPU architectures and expect them to work.   So videos, audio, office documents are all cross-platform.  ASCII text configs should migrate easily.  I don't know about gconf and dconf DBs.  I've never tried to migrate them between different architectures.

And nearly all scripted language programs will work cross-platform too, provided the dependencies can be met.

I would warn anyone coming from MacOS to avoid proprietary Apple file formats. Those often have problems since F/LOSS programs would need to reverse engineer access to the data files and reverse engineering isn't exactly a science for more complex data.

If you get specific with the exact data types and post to the Apple-user's sub-sub-forum here, you would target the crowd likely to have experience with similar stuff.

---

### Post by ian-weisser on 2023-11-18
Generally, I would recommend backing up only your Ubuntu data, which should be in your /home/$YOU directory.

Yes, you will encounter architecture problems. A wrong-arch restore of a whole-Ubuntu backup won't run. It won't even boot.

But clean installing is so easy: Make the Live USB. Use it to install. Reboot. Login. Use apt to install any extra applications. Then restore your data.
No magic. Each step is simple and verifiable. (Even easier if you keep some notes so you can reproduce your system reliably anytime)

Keep your backup as simple as you can. Simple enough that you understand it.

---

### Post by MAFoElffen on 2023-11-20
> **ian-weisser said:**
> Generally, I would recommend backing up only your Ubuntu data, which should be in your /home/$YOU directory.

LOL!!! @ --> "$YOU" <--

I know what you mean as a reference. Meaning $USER (variable for current logged in user) or UserName...

---

### Post by TheFu on 2023-11-20
I'd probably just use $HOME, but there are lots of ways to do things.  On some of my systems, home directories aren't under /home/.

---

### Post by ActionParsnip on 2023-11-20
Could also backup /etc too, many config files live in there also

---

### Post by TheFu on 2023-11-20
> **ActionParsnip said:**
> Could also backup /etc too, many config files live in there also

Here are the list of places I nominally backup, direct from a backup script:
```
        --include /usr/local \
        --include /var/snap/lxd/common/lxd/database \
        --include /var/snap/lxd/common/lxd/security \
        --include /etc \
        --include /home \
        --include /root \

```
I've posted simple backup scripts, using rdiff-backup, in these forums a few times. Also, I've posted my restore method. Getting the order of restored stuff correct matters.

---

