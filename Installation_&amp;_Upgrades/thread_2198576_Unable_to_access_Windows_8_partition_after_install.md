---
title: "Unable to access Windows 8 partition after installing Ubuntu in Dell XPS"
date: 2014-01-09
forum: Installation &amp; Upgrades
---

### Post by ikanoviawaty on 2014-01-09
Hello everyone, 

I am new to Ubuntu and just partition my Dell XPS(Windows 8). The Ubuntu part works well but I am unable to acccess the Windows 8 partition at all. I need to switch back and forth since I need Windows 8 to connect to Citrix. 

Anybody has any idea how to do so?

Thanks!

---

### Post by jdeca57 on 2014-01-09
You give preciously little information about the way you upgraded. A upgrade guide is like this:
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
note that it is from last year in September and he talks about 13.04 but that's in general the same. (I assume we're talking about 13.10)
Normally the Windows partition is there and you can make it boot.

---

### Post by Mark Phelps on 2014-01-09
Two questions:
1) HOW did you do the partitioning to install Ubuntu? Did you shrink the Windows partition using the Win8 Disk Manager tool and then use the Something Else option to create the new partitions? Or did you allow the installer to shrink the Win8 partitions? IF you did the latter, you likely corrupted the Windows boot loader -- which is a common side effect of installing that way.
2) What happens when you try to access Win8?  Saying you can't access it doesn't give us any useful info.  We need to know how you're trying to access it and what happens when you try.

---

