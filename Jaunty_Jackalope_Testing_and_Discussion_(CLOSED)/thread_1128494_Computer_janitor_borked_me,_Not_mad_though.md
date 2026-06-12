---
title: "Computer janitor borked me, Not mad though"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by BGFG on 2009-04-17
Like I said, we're still in RC so i hope it's sorted out. i just ran the CJ and it came up with a list of .deb files which i assumed were .DEB file to be **autocleaned**. As it would turn out it removed the actual programs, quite a long list, and now when i run 'aptitude update/upgrade' there is quite a long list of system libraries to be removed. My gnome theme is borked also :)

---

### Post by crjackson on 2009-04-17
> **BGFG said:**
> Like I said, we're still in RC so i hope it's sorted out. i just ran the CJ and it came up with a list of .deb files which i assumed were .DEB file to be **autocleaned**. As it would turn out it removed the actual programs, quite a long list, and now when i run 'aptitude update/upgrade' there is quite a long list of system libraries to be removed. My gnome theme is borked also :)

From what I can tell - Computer Janitor lists all packages installed externally. I consider it to be a tool un-installing external packages.

---

### Post by Darkshade on 2009-04-17
Am I the only one who finds Computer Janitor completely useless and a little dangerous for new non-experienced users? :S

---

### Post by crjackson on 2009-04-17
> **Darkshade said:**
> Am I the only one who finds Computer Janitor completely useless and a little dangerous for new non-experienced users? :S

No, I think so too. In fact I'm setting up a few rigs for some 1st time Ubuntu users, and I'm hiding Computer Janitor so they won't play with this.

---

### Post by BGFG on 2009-04-17
Then we need a better naming convention and a better explanation of the tools' purpose. 'cleaning up' alludes to removal of the unnecessary....needless to say, my machine exits sans CJ now.
Thanks for the point in the right direction :)

Edit: I'm not exactly fresh off the boat, but CJ lists the packages as debs, causing me to incorrectly assume that the intent of the tool was similar to apt-get autoclean. The should not be listed as debs, rather as installed packages.

---

### Post by Therion on 2009-04-17
Removed it ages ago.

---

### Post by crjackson on 2009-04-17
> **BGFG said:**
> Then we need a better naming convention and a better explanation of the tools' purpose. 'cleaning up' alludes to removal of the unnecessary....needless to say, my machine exits sans CJ now.
Thanks for the point in the right direction :)

For cleaning up duties, I suggest [BleachBit]("http://buck-nasty.blogspot.com/2009/01/bleachbit.html")

---

### Post by xebian on 2009-04-17
GIGO.

At least it managed not to remove itself. ;)

---

### Post by Reiger on 2009-04-17
> **Darkshade said:**
> Am I the only one who finds Computer Janitor completely useless and a little dangerous for new non-experienced users? :S

Yup. I mean most of its use can be replaced by a simple:
```

sudo aptitude search * | grep ^c

```
Which lists all conflicting packages, and 9.9 times out of 10 those are `cruft' Computer Janitor is supposed to remove...

---

### Post by BGFG on 2009-04-17
> **xebian said:**
> GIGO.

At least it managed not to remove itself. ;)

THAT, i would have appreciated ;)

---

