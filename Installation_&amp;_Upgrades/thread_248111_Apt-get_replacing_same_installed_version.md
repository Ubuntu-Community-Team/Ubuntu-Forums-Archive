---
title: "Apt-get replacing same installed version?"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by jkugler on 2006-08-31
[I looked and looked at the forum list, and this is the best topic under which to post this I could find.]

So, I'm doing some system tweaking (yes, sooooo unsupported, I'd probably sent most Ubunutu support peronnel running for their lives). :razz: 

In an effort to get PyQt3 and PyQt4 to co-exist on my Dapper system, I've compiled packages that replicate some others, or are just dummy packages to satisfy dependency chains.  And because some packages are locked to a certain version, I've named them the same as the ubuntu versions (Yes, I know, very non-kosher).  I may be able to get around the "same name" thing, but I had one odd thing pop up.  Now that the packages are installed, apt-get wants to "upgrade" them.  But to a new version?  No, to the *same* version as is already installed.  What am I not seeing here, or missing as to what apt-get is doing.  Output is below.

```
$ sudo apt-get upgrade -s
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  amarok amarok-xine
The following packages will be upgraded:
  python2.4-qt3 python2.4-qtext python2.4-sip4-qt3
3 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Inst python2.4-sip4-qt3 [4.3.2-0ubuntu2] (4.3.2-0ubuntu2 Ubuntu:6.06/dapper)
Inst python2.4-qt3 [3.15.1-0ubuntu3] (3.15.1-0ubuntu3 Ubuntu:6.06/dapper)
Inst python2.4-qtext [3.15.1-0ubuntu3] (3.15.1-0ubuntu3 Ubuntu:6.06/dapper)
Conf python2.4-sip4-qt3 (4.3.2-0ubuntu2 Ubuntu:6.06/dapper)
Conf python2.4-qt3 (3.15.1-0ubuntu3 Ubuntu:6.06/dapper)
Conf python2.4-qtext (3.15.1-0ubuntu3 Ubuntu:6.06/dapper)
```


Ideas? Comments? Clue sticks? :)

j

---

