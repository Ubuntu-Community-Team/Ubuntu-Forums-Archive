---
title: "Update-Manager stuck in the middle of 9.04 -&gt; 9.10 upgrade"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by CShadowRun on 2009-10-12
Hi, i decided to try out 9.10, so i ran update-manager -d, all was going well, it set my software channels, downloaded all the new packages...and now it's stuck at "Getting new packages, Fetching file 1842 of 1842". Been stuck for about 10 hours now, what do i do?

---

### Post by sdowney717 on 2009-10-12
restart, it has not installed anything yet

---

### Post by waspbr on 2009-10-12
considering the amount of new things in karmic, new grub and all, I would advise a fresh install.I always keep a separate /home partition anyway which makes it easy to bounce back from a  fresh install.

---

### Post by Lazy123 on 2009-10-12
> **waspbr said:**
> considering the amount of new things in karmic, new grub and all, I would advise a fresh install.I always keep a separate /home partition anyway which makes it easy to bounce back from a  fresh install.

Microsoft way of "upgrading" sucks. Upgrading from the previous version shouldn't be that hard when all the packages have come from official repositories. I hope that grub will be upgraded automatically in the next release, but otherwise upgrading went pretty well for me after I removed Openoffice (there was a conflict with openoffice.org-filter-binfilter package I hope they will fix before final release).

---

### Post by CShadowRun on 2009-10-12
> **waspbr said:**
> considering the amount of new things in karmic, new grub and all, I would advise a fresh install.I always keep a separate /home partition anyway which makes it easy to bounce back from a  fresh install.

Heh, I'm inclined to agree, my system is very messed up.

It over-wrote my keyboard layout file (fixed)
My cursor is a 24/7 waiting icon
All my icons in the applications menu are gone

And worst of all, nautilus won't start at all. (fixed, running nautilus as root, closing it, then running it normally, seems to "fix" it)

```

cshadowrun@mainpc:~$ nautilus

(nautilus:29477): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:29477): Unique-DBus-WARNING **: Error while sending message: Message did not receive a reply (timeout by message bus)
cshadowrun@mainpc:~$ 

```

:(

---

### Post by nanog on 2009-10-12
> there was a conflict with openoffice.org-filter-binfilter package I hope they will fix before final release

The bin-filter issue has been happening off and on since alpha4. 

```
killall soffice.bin ; sudo apt-get install -f
```

---

