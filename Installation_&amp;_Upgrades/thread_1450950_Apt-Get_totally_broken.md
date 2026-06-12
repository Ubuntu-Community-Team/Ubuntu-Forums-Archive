---
title: "Apt-Get totally broken"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by Piro24 on 2010-04-09
Hey all.

Today I tried updating my system, and was greeted with a rather annoying message. 

```
E: Problem parsing dependency Conflicts
E: Error occurred while processing openoffice.org-l10n-el (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

```

Any suggestions? Running apt-get install -f didn't help btw.

---

### Post by -humanaut- on 2010-04-09
you could try dpkg --configure -a 

or if all else fails It'd suggest running "sudo apt-get -f remove" instead of installing it.

---

### Post by Piro24 on 2010-04-09
Hi, Thanks for your reply.

Anyway, I tried dpkg --configure -a shortly after posting here, and that didn't help either.

I tried running sudo apt-get remove -f but got basically the same error message.

```

patrick@patrick-laptop:~$ sudo apt-get -f remove
Reading package lists... Error!
E: Problem parsing dependency Conflicts
E: Error occurred while processing openoffice.org-l10n-el (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

I was thinking about opening up that file and simply removing any entries that have anything to do with openoffice, but I'm not sure if that would work, and it's a lot of work on top of that.

---

### Post by drs305 on 2010-04-09
In Ubuntu you can often clear a "merge list" problem by refreshing the list. In synaptic (or the equivalent in other releases), untick all the repositories - remember which ones you disable. Refresh/reload the repository list, then reselect them and reload the repositories again.

---

### Post by -humanaut- on 2010-04-09
Wait that could be a bad idea. try this 

dpkg --clear-selections

---

### Post by Piro24 on 2010-04-09
Thanks for the suggestions guys. I couldn't actually get into a package manager, it would give me the error and then quit, so I'd have to use the terminal (which I generally prefer anyway).

Anyway, the problem went away seemingly by itself after an unrelated reboot (X crashed while I was playing AssaultCube).

Regardless, thanks for the suggestions!

---

