---
title: "Is it safe to destroy &quot;undesired&quot; ZFS filesystems from a root on ZFS installation?"
date: 2020-04-21
forum: Installation &amp; Upgrades
---

### Post by 0n0w1c on 2020-04-21
Not knowing the underlying design of Zsys, I am not sure if it is safe to destroy undesired filesystems after installation.

Specifically, I would like to destroy the following:

/var/games
/var/snap (snap has been removed)
/var/www
/var/mail
/var/lib/AccountServices

All of these filesystems are currently unused, no files exist on them.

If I make another filesystem, /opt for example... will zsys snapshot it without changing the configuration? I am not even sure if/where to configure zsys if it is needed.

---

### Post by #&amp;thj^% on 2020-04-21
Why? I just have to ask. ****You must not modify any vol file in /var**.**
Because they are unused/empty= dose not mean they are undesired/useless, and some may be needed by the system.
Example To find your datasets, issue the command:
```
zfs list
```

For your reading pleasure: [https://thenewstack.io/how-to-create-and-destroy-zfs-snapshots-on-ubuntu-19-10/](https://thenewstack.io/how-to-create-and-destroy-zfs-snapshots-on-ubuntu-19-10/)

---

### Post by 0n0w1c on 2020-04-21
The statement "** You must not modify any vol file in /var **"... is that in the documentation?

It makes little sense to have a filesystem where one is not allowed to modify it.
Zsys has a create option, but no destroy option... but that is equally as important.

If I remove the filesystems, the mount points will still exist or I will make them if they do not.

---

### Post by #&amp;thj^% on 2020-04-21
> **0n0w1c said:**
> The statement "** You must not modify any vol file in /var **"... is that in the documentation?


Not that I officially found, as a tester I work with Devs from most Linux Distros, and one on one talks with them state that very wordage.
> When separating out /var and NOT using legacy mounts, journald writes to /var before zfs has initiated/mounted it. Hence, zfs will subsequently be unable to mount /var, as it now contains existing data. Note that I've not tested this very thoroughly, and it has been some years since I used zfs (so maybe I'm out in left field here....) but that sure looks to be what is happening.
However you are free to run your system anyway you want. :p And some applications may not be affected at all. (Just a roll of the Dice)
you asked if it was safe, and I replied wisely.

---

### Post by 0n0w1c on 2020-04-21
I thank you for your input, it is very much appreciated and your thoughts are under consideration.

This setup is headed for a production work environment, where /home is NFS mounted... so I mount over the /home/support filesystem. So far, Zsys has not choked or complained, which is a good sign.

If this was purely ZFS CLI, I would do it without much concern... however, Zsys may have other requirements that I am not aware of yet.

---

### Post by 0n0w1c on 2020-04-21
The snaphots need to be maintained and cleaned up as each filesystem has its own snapshots. Carrying unneeded filesystems means extra effort to clean... Zsys really needs a "purge" option (I miss the VAX VMS days).
Something like "zsysctl purge {zfs filesystem} --keep=4", which would remove all but the last 4 snapshots.
But I digress... undesired filesystems are simply something that can break and requires effort to maintain. When it comes to system administration, I like to keep to the KISS principle as much as possible.

---

### Post by #&amp;thj^% on 2020-04-21
Your Welcome and good luck with your set-up.
I do agree with the pure ZFS CLI idea, would be less troublesome working with /Root structures.
Indeed the KISS principle is a Golden Rule.:)

---

### Post by dad+sithlord on 2020-12-29
zsys does have a "purge" option - see here for details [https://didrocks.fr/2020/06/04/zfs-focus-on-ubuntu-20.04-lts-zsys-state-collection/](https://didrocks.fr/2020/06/04/zfs-focus-on-ubuntu-20.04-lts-zsys-state-collection/)
The other blogs in the set also explain more on how zsys was designed and put together.  See also [https://discourse.ubuntu.com/t/zfs-focus-on-ubuntu-20-04-lts-blog-posts/16355](https://discourse.ubuntu.com/t/zfs-focus-on-ubuntu-20-04-lts-blog-posts/16355)

---

