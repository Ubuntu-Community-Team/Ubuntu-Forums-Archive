---
title: "Is ext4 the default?"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cjnkns on 2009-03-03
I just installed Jaunty last night, but I didn't see an option on ext4 vs ext3.

Is ext4 the default when installing?

---

### Post by linuxaz on 2009-03-03
I do not believe ext4 is the default.  It is however, available as an option.  I have it running here and it seems to work fine.

bertman

---

### Post by cjnkns on 2009-03-03
hmm darn - looks like I'l have to check what I am using and re-install :( if it's not ext4

---

### Post by nyarnon on 2009-03-03
Hmmm just saw that parted now recognizes ext4, now I'm really tempted to port my /home to ext4.

---

### Post by philinux on 2009-03-03
> **cjnkns said:**
> hmm darn - looks like I'l have to check what I am using and re-install :( if it's not ext4

Either reinstall or,
[http://www.kev009.com/wp/2008/12/how-to-upgrade-to-ext4-in-place/](http://www.kev009.com/wp/2008/12/how-to-upgrade-to-ext4-in-place/)
I'm sure there are other guides knocking about.

---

### Post by nyarnon on 2009-03-03
I read that and a few others, practically always the same text. What I don't grasp is the hint about /boot and grub as im running it on ext4. This text to old?

---

### Post by Kow on 2009-03-03
I think you have to choose manual partitioning in ubiquity to get the filesystem options. Guided/auto/whatever the hell its called will use ext3.

---

