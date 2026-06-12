---
title: "Enlarging swap partition without live gparted disk..."
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by orange2k on 2013-01-10
I would like to make my swap partition larger so I can enable hibernate on my computer...

Currently its only about 1 GB in size, and I would like to make it about 4 GB...

Do I really need to make use of Gparted live cd or is it possible without it?

---

### Post by Cheesemill on 2013-01-10
That depends on the partition layout of your drive.

Can you install [gparted]("apt://gparted") in your Ubuntu installation and then post a screenshot please.

---

### Post by orange2k on 2013-01-10
Here is the screenshot - "nepoznato" is the swap partition...

---

### Post by Cheesemill on 2013-01-10
You will need to boot from a Live CD to make any changes. This is because you need to resize your / partition (sda5) to make room for an enlarged swap. As partitions can only be resized when they're not mounted you will have to do this from outside your running Ubuntu installation.

Also I'm not sure what sda6 is, but it's currently not swap otherwise it would say so in the second column.

To check if you are using swap on your system you can use the command 'free -m'.

---

### Post by orange2k on 2013-01-10
free -m says the following:

```
orange@orange-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2518        966       1552          0         49        456
-/+ buffers/cache:        460       2058
Swap:          893          0        893

```

Does Ubuntu 12.04 live CD come with gparted or do I have to burn the gparted live cd?

---

### Post by Cheesemill on 2013-01-10
The Ubuntu Live CD has gparted installed on it.

---

### Post by Pjotr123 on 2013-01-10
Yes, you can use the Ubuntu 12.04 disk, because that contains Gparted as well. :)

However, be careful with hibernate and suspend:
[https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma)
(item 7, right column)

---

### Post by orange2k on 2013-01-10
> **Pjotr123 said:**
> Yes, you can use the Ubuntu 12.04 disk, because that contains Gparted as well. :)

However, be careful with hibernate and suspend:
[https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-always-work-well:-they-make-some-computers-malfunction-or-even-enter-a-coma)
(item 7, right column)

Oh, I see, so its probably better to stay away from hibernate...
Suspend works fine on my computer, so I'll just use that when I'm not at the computer...

thank you both Cheesemill and Pjotr123!

I'll mark this as solved...

---

