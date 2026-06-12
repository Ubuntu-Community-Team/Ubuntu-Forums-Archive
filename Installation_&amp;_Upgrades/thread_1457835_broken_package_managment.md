---
title: "broken package managment"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by bobdobbs on 2010-04-19
Hi all.

I've have major problems installing cinelerra.
So, I tried to uninstall it.

I messed up at some point. Now, most apt operations result in errors.

At the moment, this is what I get when I try apt-get -f install:

```

(Reading database ... 522814 files and directories currently installed.)
Removing cinelerra ...
Description:	Ubuntu 9.10
en_NZ.iso885915
locale "ru_RU.KOI8-R" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerra (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Is there any way to fix this, or is my package managment permanently broken?

I just want to get to the point where apt isn't returning errors, because at some point I will want to upgrade to 10.04. This is just too risky with broken apt.

---

### Post by MelDJ on 2010-04-19
tried ```
sudo  dpkg --configure -a
```?

---

### Post by iponeverything on 2010-04-19
you might try the --reinstall flag for apt to reinstall cinelerra, and then remove it. You could also touch files that apt complains about not being able to delete, so that it has something to delete..

---

### Post by bobdobbs on 2010-04-19
> **MelDJ said:**
> tried ```
sudo  dpkg --configure -a
```?

Yeah - I'm not sure exactly what that does, but I did give it a shot. I found that command in an article about repairing broken package management.

This is particularly frustrating, because I've had package management break on me twice before. And the only remedy on both occaissions was to completely re-install the OS. 

I don't want to have to do that all over again.

---

