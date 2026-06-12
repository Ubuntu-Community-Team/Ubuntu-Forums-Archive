---
title: "Upgrade to 14.04 from 10.04 mixed up user accounts"
date: 2015-11-30
forum: Installation &amp; Upgrades
---

### Post by cag1999 on 2015-11-30
I recently upgraded an older machine from 10.04 to 14.04.  I had 6 user accounts in 10.04 (Administrator, Adam, Alissa, and 3 others).  After the upgrade, I could log into all but 2 accounts, Adam and Alissa.  After a few painful hours of digging, this is what I came across.

Alissa (uid 1002) has a home folder titled adam.  The files under home/adam are all alissa ownership.  When she logs in, her desktop (and presumably shortcuts, etc) are all adam's from the 10.04 install.
conversely,
Adam (uid 1001) has a home folder titled alissa.  The files under home/alissa are all adam ownership.  When he logs in, his desktop (and presumably shortcuts, etc) are all alissa's from the 10.04 install.

One tweak I've made so far is to "sudo mv" the names of the home folders to the right owners (now alissa's home folder is home/alissa) and the sub folders all belong to her.  BUT, it's all adam's information from the 10.04 install.

To summarize:
Login     UID     Home Folder      Sub Folders       Information
alissa    1002    adam -> alissa   alissa                adam
adam     1001    alissa -> adam   adam                alissa

What is the easiest path to get these accounts corrected?  Any help is greatly appreciated.

-Adam

---

