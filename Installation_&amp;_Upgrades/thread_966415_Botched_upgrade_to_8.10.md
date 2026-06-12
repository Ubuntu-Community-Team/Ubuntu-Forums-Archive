---
title: "Botched upgrade to 8.10"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Bulletbeast on 2008-11-01
[SIZE="-3"]Last night, I decided to upgrade from 8.04 to 8.10. The installer asked me for 600 or 900 MB, of which I had only 150 (when I was making my partitions, I had expected Ubuntu to fit comfortably in 7GB and to use my NTFS drives for most of my stuff, but packages quickly ate it all). I managed, reluctantly, to provide them, removing old kernel versions and documentation. Then, the updater asked me for twice that amount - about 1600 MB, which I also managed to free, somehow. It asked once again for varying amounts of space < 5M, and, in the end, I coaxed it to work and went to bed.

The next morning, my father had seen a message stating that the update had failed (he recalled nothing else), yet tried to log in to his account. When I woke up, the computer was in an infinite loop of rebooting. Booting without quiet and splash, I saw what seemed to be a long list of unsuccessful attempts to do something, culminating with **not being able to find libc.so.6**, which was also required to start a maintenance shell. I haven't got my install CDs so I ended up painstakingly repairing the XP installation that was rotting in one corner of what used to be called my C: drive, acutely realizing that the millions of dollars invested in Windows have been in vain, not making it any less lame, and I am writing to you from that now.[/SIZE]

Sorry for rambling. In short, I **failed to update to 8.10** last night, and the first of my troubles is that **libc.so.6 (version GLIBC_2.8) can't be found** at boot. I have this handy tool caller LinuxReader under Windows which says libc.so.6 is right there, in /lib and also in /lib32. Those files are only several bytes, though, which means they're symlinks. I have different "libc.so"'s and "libc.a"'s in /usr/lib and /usr/lib32 which seem to be the real deal, but knowing that doesn't boot my system any further. Any help?

I am able to get into ash through an 8.04 DVD that refuses to do anything else (my DVD drive's faulty), but I do not know how to mount my partitions. When I try to, it just says that the partition isn't in fstab.

---

### Post by Bulletbeast on 2008-11-02
Update:
another couple of messages that I saw said that mount points **/dev/shm** and **/dev/pts** do not exist, and a third one - that there is **no entry for the root filesystem in /etc/fstab.** They're both preceded and followed by the "can't find glibc" message.

---

### Post by Bulletbeast on 2008-11-02
I've found a program that lets me mount my ext3 partition from Windows, with rw access. Could anything be done from here?

---

### Post by Bulletbeast on 2008-11-02
Please, help.

---

### Post by Bulletbeast on 2008-11-03
I'm starting a nwe topic with a clearer title.

---

