---
title: "2 linux Partitions?"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Kadrus on 2007-11-11
Euuh..I was wondering if I could install 2 Linux partitions..I want to install Gentoo Linux..and can I do so without having any problems or that sort of thing?I currently have Ubuntu 7.04 for further information..

---

### Post by rsambuca on 2007-11-11
You can actually install as many distro's as you want.  I just created one large extended partition for all of my linux distros.  Inside of the extended partition you can just create as many logical partitions as you want for each OS.  You only need one swap, as they can all share it.

I have included a screenshot of my partitioning scheme for your reference.  As you will notice I have one large extended partition containing 5 logical partitions and a common swap.  The large partition at the end is where I store all of the common media files that I can use from each distro.

---

### Post by rsambuca on 2007-11-11
Also, if you are going to install gentoo, I highly recommend installing it from a chroot environment in your existing Ubuntu.  That way, you have full access to your computer and internet while you are compiling gentoo.

---

### Post by Kadrus on 2007-11-11
> **rsambuca said:**
> You can actually install as many distro's as you want.  I just created one large extended partition for all of my linux distros.  Inside of the extended partition you can just create as many logical partitions as you want for each OS.  You only need one swap, as they can all share it.

I have included a screenshot of my partitioning scheme for your reference.  As you will notice I have one large extended partition containing 5 logical partitions and a common swap.  The large partition at the end is where I store all of the common media files that I can use from each distro.

Wow..thanks..i was just afraid that I don't run into some massive installation problems...where i have to reinstall everything..but now that I have a good proof..i have no doubts..thanks :)

---

### Post by Kadrus on 2007-11-11
> **rsambuca said:**
> Also, if you are going to install gentoo, I highly recommend installing it from a chroot environment in your existing Ubuntu.  That way, you have full access to your computer and internet while you are compiling gentoo.

Ok..will do that..thanks for the advice :)

---

### Post by rsambuca on 2007-11-11
Good Luck!

Here is a link to the instructions for a [gentoo installation from within another linux OS]("http://www.gentoo.org/doc/en/altinstall.xml#doc_chap5").

---

### Post by Kadrus on 2007-11-11
> **rsambuca said:**
> Good Luck!

Here is a link to the instructions for a [gentoo installation from within another linux OS]("http://www.gentoo.org/doc/en/altinstall.xml#doc_chap5").
Thanks for the all the help..although I was on the page which you directed me into this post..lol..what a coincidence!
:)

---

