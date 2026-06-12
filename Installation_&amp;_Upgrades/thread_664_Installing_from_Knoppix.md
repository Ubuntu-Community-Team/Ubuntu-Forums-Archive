---
title: "Installing from Knoppix"
date: 2004-10-14
forum: Installation &amp; Upgrades
---

### Post by bronson on 2004-10-14
The Ubuntu installer could not install onto my partition map so I decided to see if I could wedge things together from within Knoppix.  It took a bit of fiddling, but in the end I managed to get it to work.  Hopefully my experience will prove useful to other people.

[http://wiki.ubuntulinux.org/InstallFromKnoppixHowto](http://wiki.ubuntulinux.org/InstallFromKnoppixHowto)

Why go to all this effort?  I don't get to change the oddball partition map on my company's laptop with the windows partition on hda1 at the beginning of the disk, and the recovery partition on hda2 at the end of the disk.  I was trying to install Ubuntu onto hda3, with hda4 as a logical partition containing hda5=swap and hda6=/home.  Ubuntu's installer kept choking when it was to create the partitions.

---

### Post by Mighty Mik on 2004-10-22
This works for me till i get to the kernel part. apt-get can't find one.  :shock:

---

### Post by RandallC on 2006-07-20
When I try to make debootstrap, make gives an input/output error

---

### Post by sclough on 2006-08-17
Here's a little disclaimer:  I have not tried this!

But this link might help to anyone who's interested in this:

[http://blog.nanorails.com/articles/2006/07/01/remote-ubuntu-dapper-drake-install]("http://blog.nanorails.com/articles/2006/07/01/remote-ubuntu-dapper-drake-install")

---

