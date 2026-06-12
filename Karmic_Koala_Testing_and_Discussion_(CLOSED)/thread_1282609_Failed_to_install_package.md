---
title: "Failed to install package"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Odisej on 2009-10-04
Hi all,

I am having the following issue ...  if I try to install a package using gdebi-gtk I get the error:

"dpkg: unable to read filedescriptor flags or <package status and progress file descriptor>: Bad file descriptor."

If I choose to use dpkg in terminal I do not encounter it. True, I am trying to install jaunty packages but I did not encounter it in the past, with previous versions.  

Any ideas?

Odisej

---

### Post by FuturePilot on 2009-10-04
Make sure you have all updates installed. This was recently fixed. 
[https://bugs.launchpad.net/ubuntu/+source/vte/+bug/438266]("https://bugs.launchpad.net/ubuntu/+source/vte/+bug/438266")

---

### Post by Odisej on 2009-10-04
Yes, it worked. Thanks.

---

