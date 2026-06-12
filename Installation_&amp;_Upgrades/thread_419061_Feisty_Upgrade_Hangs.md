---
title: "Feisty Upgrade Hangs"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Mozork on 2007-04-22
Well, yesterday I tried to upgrade to feisty (from edgy) which maybe was not very wise, because I was not at home and my network connection was slow and not that stable.
But it went all well (I'm talking about the recommended upgraded through the update manager, here) until It came to a point where 114 of 115 Packages had been downloaded and then it just froze.
And so tried it with a better connection today, same problem. After that I ran it in the terminal and here's the output:

```
$ gksu "update-manager -c"
GTK Accessibility Module initialized
warning: could not initiate dbus
extracting '/tmp/tmpCHMbTe/feisty.tar.gz'
authenticate '/tmp/tmpCHMbTe/feisty.tar.gz' against '/tmp/tmpCHMbTe/feisty.tar.gz.gpg' 
GTK Accessibility Module initialized


```What's wrong, what can I do to fix it? And if I cant's do anything: are there other (safe) ways to upgrade?

---

### Post by Mozork on 2007-04-26
Solved.
It did not work because some extra repositories, I just had to uncomment them.

---

