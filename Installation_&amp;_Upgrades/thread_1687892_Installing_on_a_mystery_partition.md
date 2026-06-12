---
title: "Installing on a mystery partition?"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by Tinfoilpain on 2011-02-14
Ok, I want to install and dual boot ubuntu and windows 7. Now when I go to see what my disc looks like so I can shrink some partitions I see one unnamed one that has no filesystem already there. (See Picture)
[IMG]http://i356.photobucket.com/albums/oo9/Tinfoilpain/mysterypartition.jpg[/IMG]
Now my laptop came like this, I never added the partitions, they were just there. So I was wondering weather or not I could install to that partition safely, as in I'm not overwriting some sort of important windows 7 thing. Thanks in advance.

---

### Post by Quackers on 2011-02-14
Your Data partition (D: ) appears to be within an extended partition. It also appears to have available space in it. You could shrink that D: partition (but not the extended partition it resides in). This will give you some free space within the extended partition in which Ubuntu can be installed.
I don't know what the 21GB partition is. Can you explore it?

---

### Post by Tinfoilpain on 2011-02-15
Sadly, No I can't explore the 21Gig partition, it doesn't show under my computer in windows and as you can see it shows no file system or anything on it.

---

