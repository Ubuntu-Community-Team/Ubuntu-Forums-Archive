---
title: "Ubuntu Edgy Install Fails, Linux Mint Works Like a Dream... What Gives?"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by swheatley on 2007-03-06
Hi everyone,

I'm not a newcomer to Linux. I've been using Linux off and on since 2000. I just tried installing Ubuntu 6.10 Edgy on my Dell Inspiron E1405. The installer failed when trying to start X and hung the machine. I tried to do the same thing with Linux Mint... not only did the installer work flawlessly, but both the live CD and installation picked up my wifi without a hitch, X picked up the proper resolution for my LCD (1440x900) and more.

I'd really like to use as close to "stock" Ubuntu as possible, so I'm wondering if anyone has any ideas why this might have happened, and how I can get Ubuntu to install.

---

### Post by teaker1s on 2007-03-06
have a look at your sources.list, as linux mint claims ubuntu compatibility then changing any sources to ubuntu should't break the system. you could then install the meta packages ```
ubuntu-desktop
``` and ```
ubuntu-base
``` to ubuntu it

you may also need usplash change

---

### Post by swheatley on 2007-03-06
Thanks teaker1s, I'll try that tonight and post how it goes.

---

### Post by swheatley on 2007-03-06
I tried installing ubuntu-desktop, but it tells me it will uninstall openoffice.org in the process. No problem, I'll just install it again later. However, when I try to mark everything for install, it gives me the following:

```

ubuntu-desktop:
 Depends: openoffice.org but it is not going to be installed
 Depends: openoffice.org-evolution but it is not going to be installed
 Depends: openoffice.org-gnome but it is not going to be installed

```

Any ideas?

---

### Post by teaker1s on 2007-03-07
I would suggest searching open office installed components and see if linux mint has any customised ones. further to this can you see any linux mint desktop related components that would block ubuntu-desktop?

Other than this you could install ubuntu related themes to change gnome:popcorn:

---

