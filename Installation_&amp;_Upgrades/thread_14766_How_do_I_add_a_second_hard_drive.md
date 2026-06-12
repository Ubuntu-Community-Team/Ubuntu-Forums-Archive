---
title: "How do I add a second hard drive?"
date: 2005-02-09
forum: Installation &amp; Upgrades
---

### Post by Locutus on 2005-02-09
I have working ubuntu system which is working wonderfully. I bought a second hard disk and have partitioned/formatted it with Qtpared as ext3 and labeled it /server. The hard drive is shown as /dev/hdb

How can add this to my system? I would like to call it /server. I am guessing that I have to mount it some how, perhaps in /etc/fstab?

Could anyone help a newbie? thanks for you help in advance.

Cheers,

Locutus

---

### Post by alastair on 2005-02-09
Edit the fstab file - if in doubt, copy the file to .bak beforehand.

Add a line like (replace X with your partition NUMBER!) :

/dev/hdbX    /server    ext3    defaults   0   2

Make sure /server exists. 

To mount - in a shell :

sudo mount /server

This is basic unix - plenty of books, guides, howto's etc. around.

---

### Post by Locutus on 2005-02-09
That worked perfectly! Thank you.

---

### Post by middlewordie on 2007-01-16
I have added a second hard drive (WD 160Gb) to add to my Edgy system but i think I need to partition it. How do i do this? Using the Live CD?

I would like to use it as a samba repository to two Windows XP machines, so I'm probably going to use Fat 32.

---

