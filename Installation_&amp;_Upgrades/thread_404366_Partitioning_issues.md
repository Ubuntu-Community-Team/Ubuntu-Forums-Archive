---
title: "Partitioning issues"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by whistler404 on 2007-04-08
Hello,

I've been trying to install Ubuntu for about 2 days now - to be more specific, I can't resize my NTFS partition.
I currently have one 80GB windows installation NTFS partition, with 20% free space that I want to turn to an ext3 partition.

At first I tried the ubuntu installation program, and GParted gave me an error saying: "Extended record needed (1056 > 1024), not yet supported" or something like that - I tried to defrag (at first with the windows tool, later with Diskeeper), ran endless chkdsks, etc, but it just doesn't solve it. Upon googling I stumbled upon a forum thread of a guy with the same problem - and he claimed using the Mandriva installation used for him. Tried that too, no luck - unidentified error.

I'm kind of desperate. Two days of trying, countless defragmentations and chkdsks.. Anyone has an idea how can I resize this stubborn partition?

---

### Post by spin2cool on 2007-04-08
Try something like this:
[http://nishants.net/articles/ntfsresize.htm](http://nishants.net/articles/ntfsresize.htm)

---

