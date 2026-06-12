---
title: "dvd+rw-tools"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2007-03-10
On update manager I am getting "**The following updates will be skipped**" - dvd+rw-tools.

What does this mean ?

Thanks.

---

### Post by sgenchev on 2007-03-10
It has broken dependencies. It declares that it depends on "genisoimage" package but there is no such package in repository. Package maintainers have to either remove this dependency or upload genisoimage.

---

### Post by wpshooter on 2007-03-10
> **sgenchev said:**
> It has broken dependencies. It declares that it depends on "genisoimage" package but there is no such package in repository. Package maintainers have to either remove this dependency or upload genisoimage.

So am I understanding correctly, that there is nothing I need to do about this but **WAIT** or am I supposed to attempt to fix broken dependencies ?

Thanks.

---

### Post by qamelian on 2007-03-10
Just sit tight and the problem will eventually be corrected. There are ways you can force this update to install, but you really are better off waiting for the dependency issue to be resolved. Otherwise you risk breaking things on your system.

---

### Post by tredegar on 2007-03-11
I have exactly this problem, but, interestingly, only on my laptop. Both laptop and desktop are running 6.06.2.

Anyway, I'll "just wait", as everything is still working beautifully!

---

### Post by DagMan on 2007-03-11
> **wpshooter said:**
> So am I understanding correctly, that there is nothing I need to do about this but **WAIT** or am I supposed to attempt to fix broken dependencies ?

Thanks.

If you already had it installed then it works, it just can't be upgraded at the moment.  I used it today.

---

