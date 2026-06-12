---
title: "copy 1:1 a running system to an USB pendrive"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by cccc on 2012-03-22
hi

Howto copy 1:1 a running system to an USB or DVD and install it from the same media on other hardware?

---

### Post by cccc on 2012-04-18
Perhaps **[remastersys ]("http://www.geekconnection.org/remastersys/")**, I haven't tried yet, but will do.

[http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22](http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22)

---

### Post by sudodus on 2012-04-19
For me 'copy 1:1' means 'clone', and you can use ***Clonezilla*** to do that. Download the Clonezilla iso file, make a CD or USB boot drive and run Clonezilla. I would suggest that you make an ***image*** of your internal drive and put it on the removable media (DVD, USB pendrive or USB hard disk depending on size).

And finally move to the other computer and run Clonezilla to restore the image to the other drive. *Nota bene*: Everything on that drive will be wiped and replaced with the content from the image.

If you want the system to be truly portable, you should remove any proprietary drivers (for example drivers for graphics and wifi).
     -o-
But ***remastersys*** sounds like a good idea.

---

