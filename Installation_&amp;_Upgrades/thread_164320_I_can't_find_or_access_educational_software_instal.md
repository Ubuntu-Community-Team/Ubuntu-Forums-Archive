---
title: "I can't find or access educational software installed through adept"
date: 2006-04-22
forum: Installation &amp; Upgrades
---

### Post by n7tzg on 2006-04-22
Hi all,

I installed software on my kubuntu laptop using the edubuntu desktop manager.  I opened adept and selected the educational files I wanted and committed the changes.  ubuntu went through the install, but when I looked for the files I couldn't find them.  They were not added to the applications menu, nor could I find them using locate.  any ideas would be very helpful.

Rob

---

### Post by tonyr on 2006-04-22
**locate** needs an updated db to be effective.  Did you```
sudo updatedb
```
before you used **locate**?

---

### Post by n7tzg on 2006-04-22
Yes I did.  I am somewhat familiar with linux as my company uses Fedora for their computer systems.  I develop firmware in that environment.  However, I am not very familiar with debian or its derivatives.  I tried sudo to locate the files, and found documentation in usr/share/doc, but that is about the extent of it.

---

