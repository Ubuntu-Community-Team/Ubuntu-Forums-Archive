---
title: "gtksourceview 3.1x"
date: 2014-12-29
forum: Installation &amp; Upgrades
---

### Post by Edward_M_Varner on 2014-12-29
Greetings all,

Thank you for taking your time and helping me. 

I just installed this system last night and I am using Ubuntu 14.04 which I updated fully.

************
**ISSUE**
************
I have added a printer which does print color pages if I use the test page or Libreoffice. The issue is experienced when trying to print from gedit or other text editors. I tracked down the bug report [[FONT=sans-serif]Bug 1313283] [/FONT] which suggests a fix however, I'm not sure how to "force a gtksourceview upgrade" or review my current version for that matter. I did try searching, but had no luck.


Thanks,
Eddie

---

### Post by MAFoElffen on 2014-12-29
This will show you the specific packages that are installed for that:
```

dpkg --get-selections | grep gtksource

```
If you look at the output and insert the specific packageName into the following command, it will tell you the version of that package
```

dpkg -s <packageName> | grep -i Version

```
I think what you will find is that even the U+1 Dev Vivid (v15.04) repo's currently only go up to gtksourceview-3.0-1...

EDIT-- I see the source at Gnome and in test in very narrow focus to rhel branch, but not so far in test upstream in Debian or it's branches yet.

---

### Post by mc4man on 2014-12-29
The issue has been fixed with an upstream commit & probably in the 14.10/15.04 source & packages. It's quite likely that the commit will be applied to trusty's current gtksourceview source & released via an SRU though that may take a little while 
(- could be a week, could be a month or more..

One solution in that report was to install 14.10's packages, myself don't really like doing that..
Have tested the commit against the current 14.04 source, it fixes as seen in screen but haven't had a chance to look for any regressions yet 

If desired will point to a test ppa for 14.04

Edit: the good thing about working in preview is one can see if the highlighting prints out well on white paper. I use a non default color in gedit so lines displayed a yellow may not print well. So for printing would switch  gedit color(s), scr. 2

---

### Post by zhangdw on 2015-01-08
Hi, I wonder how you fix it. Can you please tell more details? Thank you. 

> **mc4man said:**
> The issue has been fixed with an upstream commit & probably in the 14.10/15.04 source & packages. It's quite likely that the commit will be applied to trusty's current gtksourceview source & released via an SRU though that may take a little while 
(- could be a week, could be a month or more..

One solution in that report was to install 14.10's packages, myself don't really like doing that..
Have tested the commit against the current 14.04 source, it fixes as seen in screen but haven't had a chance to look for any regressions yet 

If desired will point to a test ppa for 14.04

Edit: the good thing about working in preview is one can see if the highlighting prints out well on white paper. I use a non default color in gedit so lines displayed a yellow may not print well. So for printing would switch  gedit color(s), scr. 2

---

