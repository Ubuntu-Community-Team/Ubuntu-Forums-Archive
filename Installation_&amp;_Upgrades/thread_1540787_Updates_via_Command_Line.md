---
title: "Updates via Command Line"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by Lyuokdea on 2010-07-28
Hi All,

I'll be working on my machine remotely for the next year -- and I want to update packages (like I would do with the update wizard if I were on the computer).

However, there are two things:

1.) I do not want to upgrade to new versions of ubuntu (I am currently running jaunty)

2.) There are two updates that I do not want (any update to mediawiki always crashes the system for me) - so i need to be able to pick what i don't want.

Can anybody help me with this?

Thanks,

~Lyuokdea

---

### Post by chopinhauer on 2010-07-28
There two main command line interfaces to the APT packaging system: [apt-get](https://help.ubuntu.com/10.04/serverguide/C/apt-get.html) and [aptitude](https://help.ubuntu.com/10.04/serverguide/C/aptitude.html).

Of the two Aptitude can mark some packages as 'held' (not to update) and has some other nifty features.

Regarding upgrades to new versions of Ubuntu, you won't be able to do it with just **apt-get** or **aptitude** so an:
```
apt-get upgrade
```
won't ever upgrade to a new Ubuntu version (unless you modified the source lists to make it happen).

---

### Post by snowpine on 2010-07-28
Support for Jaunty 9.04 ends in October 2010, so you will not be able to remotely update your system past that date unless you upgrade to Karmic (or newer).

---

### Post by chopinhauer on 2010-07-29
> **snowpine said:**
> Support for Jaunty 9.04 ends in October 2010, so you will not be able to remotely update your system past that date unless you upgrade to Karmic (or newer).

Newer is better: Lucid Lynx is a Long Time Support and will be supported till 2015 on servers.

---

