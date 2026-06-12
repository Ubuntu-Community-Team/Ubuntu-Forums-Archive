---
title: "Installing Ubuntu"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by Jonneyc4444 on 2007-08-22
hii
I went to put ubuntu
on my computer so
i made a partition with GNOME partition mangager
but when i install the system it shows the
next screen
[[IMG]http://www.2send.us/uploads/96bffcde47.png[/IMG]]("http://www.2send.us/")
Or [http://www.2send.us/uploads/96bffcde47.png](http://www.2send.us/uploads/96bffcde47.png) if the link dosnt work
I need the answer in simple english beause im new in ubuntu and i dont have idea
Thnkes
Jonny

---

### Post by Seti on 2007-08-22
IIRC this happens of you are trying to install ubuntu and your root partition is XFS or some unsupported file-system. I think its something along those lines, but I could be wrong.  The installer does this because it cannot use grub to boot such a partition. If you make your / partition EXT3 or reiserfs, you shouldn't have this problem.

good luck

---

### Post by Jonneyc4444 on 2007-08-22
> **Seti said:**
> IIRC this happens of you are trying to install ubuntu and your root partition is XFS or some unsupported file-system. I think its something along those lines, but I could be wrong.  The installer does this because it cannot use grub to boot such a partition. If you make your / partition EXT3 or reiserfs, you shouldn't have this problem.

good luck

t didnt help
any ideas?

---

### Post by Outrunner on 2007-08-22
1. Did you check the md5sum [HOWTO]("https://help.ubuntu.com/community/HowToMD5SUM#head-cc4057205f46f3da4e36ee1974c50c51bd89ed24")
2. Did you burn the CD at the lowest speed?
and finally, did you check the CD for errors? (while booting from CD, there's an option to check the Cd for errors. use that)

---

