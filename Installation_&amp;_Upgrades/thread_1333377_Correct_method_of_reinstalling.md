---
title: "Correct method of reinstalling"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by mjf on 2009-11-21
Hello,

I am trying to reinstall Ubuntu 8.10 after having various difficulties with 9.04 and 9.10.

To do this, I simply booted into the 8.10 CD and installed over my 9.10 partition. However, after doing this, my system is not quite back to normal (notably, sound doesn't work, which was my main issue with 9.10).

One thing I am suspicious about is the grub boot menu has about 12 entries such as 

```
Ubuntu 8.10, Linux kernel 2.6.31-14
Ubuntu 8.10, Linux kernel 2.6.31-14 (Safe boot)
Ubuntu 8.10, Linux kernel 2.6.28-16
Ubuntu 8.10, Linux kernel 2.6.28-16 (Safe boot)
...
```


But I think the 2.6.31-14 kernel is something that came with 9.10.  Is it possible 9.10 "residue" remains on the system and if so how can I ensure it is removed?

I believe my /boot directory is on the same partition as /. The only directory I have in a separate partition is /home.

What is the recommended process for completely reinstalling the system in a case like this? (I would like to preserve the data in /home, though)

---

### Post by darkod on 2009-11-21
If you didn't select Format box when reinstalling it would keep some old data. Usually you would always format / for a clean install and NOT format /home (when it's separate) so you can keep your files/settings.
If you are using the manual partitioning option when selecting the mount points using your old partition watch out for the format tick box.
Yes, the 2.6.31 kernel is from 9.10. If you are selecting that most probably you will keep having the old problems. Try the other kernel and see how it goes, and if you want do another clean install and this time format /.

---

### Post by mjf on 2009-11-21
> **darkod said:**
> If you didn't select Format box when reinstalling it would keep some old data. Usually you would always format / for a clean install and NOT format /home (when it's separate) so you can keep your files/settings.
If you are using the manual partitioning option when selecting the mount points using your old partition watch out for the format tick box.
Yes, the 2.6.31 kernel is from 9.10. If you are selecting that most probably you will keep having the old problems. Try the other kernel and see how it goes, and if you want do another clean install and this time format /.

Doh, can't believe I didn't realize that.  I saw the checkbox but assumed reformatting wasn't necessary for clearing all the old data for some reason.  Will try again, thanks.

---

