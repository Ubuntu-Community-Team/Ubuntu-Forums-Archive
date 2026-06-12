---
title: "export list of installed packages within apt-get ?"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by AndreasMeier on 2005-11-19
Hi there,

is it possible to export a list of all installed packages out of apt-get ?

I have a Kubuntu Hoary system with many packages installed and would to have the same packages installed on a new PC.
That would save me quit some work, if it is possible !!

Thanks in advance,
Regards,
Andreas

---

### Post by Arktis on 2005-11-19
Open up a terminal and use:
```
dpkg --get-selections > my-pkg-list
ls
```
Then, you should see a file called 'my-pkg-list' that has all your installed pakages in it.
```
gedit my-pkg-list
```
The problem with this is that in breezy, a lot of the packages will have different versions and therefore different names, so this isn't a catch all solution.

---

### Post by AndreasMeier on 2005-11-19
Ok, thanks for the quick answer.
I will try to get this done later the day.

Thanks,
Regards
Andreas

---

### Post by Arktis on 2005-11-19
Oho, I just re-read your post, and it seems like you're not upgrading to breezy as I thought you were.  So this should work fine.

---

