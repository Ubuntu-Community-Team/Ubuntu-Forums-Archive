---
title: "Dapper and Firefox 2.0; when?"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by ermannobonifazi on 2006-11-05
Someone know if and when Firefox 2.0 will be avaiable to Dapper (Ubuntu 6.06) via automatic updates?

---

### Post by kerry_s on 2006-11-05
You can download the one from the firefox site and use that. Just unpack it and move it to /usr/lib, make sure you rename the old one to firefox.old before you copy the new one there. You also have to  copy the plugins folder inside firefox. It has to be done as root so do > gksu nautilus / <to be root.

---

### Post by ermannobonifazi on 2006-11-05
I know this. But I'd like not to mess manually my OS. I wonder why take so long to release the update for FF 2.0, since other Linux distro are already updated.

---

### Post by Buddha443556 on 2006-11-05
> I wonder why take so long to release the update for FF 2.0 ...

Read somewhere around here backports can take anywhere from 2 days to 2 weeks. I'm waiting too.

---

### Post by eeried on 2006-11-10
Never :evil: [http://www.ubuntuforums.org/showthread.php?p=1739815#post1739815](http://www.ubuntuforums.org/showthread.php?p=1739815#post1739815)
Unless backport can help us? I'm not sure of that.

cheers

---

### Post by aysiu on 2006-11-10
> **kerry_s said:**
> You can download the one from the firefox site and use that. Just unpack it and move it to /usr/lib, make sure you rename the old one to firefox.old before you copy the new one there. You also have to  copy the plugins folder inside firefox. It has to be done as root so do > gksu nautilus / <to be root.
Yikes! But why would you do that when a script can do it for you?
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by eeried on 2006-11-12
> Originally Posted by kerry_s  View Post
You can download the one from the firefox site and use that. Just unpack it and move it to /usr/lib, make sure you rename the old one to firefox.old before you copy the new one there. You also have to copy the plugins folder inside firefox. It has to be done as root so do > gksu nautilus / <to be root. 

Are you sure you only have to copy the content to /usr/lib. No other files that need editing?

Scripts are nice aysiu, but it's also nice to do things on your own, it's a good way of learning.

---

