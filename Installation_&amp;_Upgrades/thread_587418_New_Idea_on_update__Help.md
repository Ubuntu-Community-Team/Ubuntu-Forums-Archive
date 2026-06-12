---
title: "New Idea on update / Help?"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Ioky on 2007-10-22
As we all know Ubuntu update every 6 month. Great ideal as an OS, however, there are a problem bothers me a little bit. And it is software-package. For much people, include myself like to have a clean upload, but the problem is, each time we update our system. we need to reinstall all the software which takes forever, (It takes me 12 hours to install everything I need) I just wondering is there anyway to the system, have a copy list of all the software, and package I have, in a script or something, so the next time I update my system, I can just open the script, and the system automatic pick up all the software that list in the script, and install them automatically. I wonder is there anyway I can done it, or if not, would it be a good idea - cool feature for ubuntu to have?

---

### Post by kidders on 2007-10-24
Hi there,

How about **dpkg --get-selections**?

To make a list of actual practical use, I suppose it would be best to try to remove things that are dependencies of other packages in the list. As a little experiment, I gave this a shot, but it was surprisingly time-consuming...

```
[COLOR="DarkOrange"][Make a list of installed packages][/COLOR]
dpkg --get-selections | grep $'\t'"install" | cut -f1 > ~/list1
[COLOR="DarkOrange"][Make a list of top-level dependencies ... takes a little time][/COLOR]
for pkg in `cat ~/list1`; do dpkg-query -W -f '${Depends}\n' $pkg | sed 's/ \?[,|] /\n/g' | cut -d" " -f1; done > ~/list2
[COLOR="DarkOrange"][Use "list2" to remove redundant entries from "list1"][/COLOR]
cat ~/list1 ~/list2 | sort | uniq -u > ~/real_list
```

After a few levels of dependency calculations, the resulting list should be quite small, and ready to be turned into one gigantic "apt-get install ...". Anyhow, whatever you choose to do with the output it generates, **dpkg --get-selections** should at least put you on the right track.

I hope that helps.

---

