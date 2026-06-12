---
title: "Firefox 2.0 in Dapper, help upgrading?"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by mattmagician on 2007-09-10
Okay, so i'm trying to get 2.0 again, (just reinstalled Dapper) and i'm getting
matt@Matt-Ubuntu:~$ sudo tar xzvf firefox-2.0.0.1.tar.gz -C /opt
tar: firefox-2.0.0.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
matt@Matt-Ubuntu:~$


when trying to put it into /opt...
any help? this is probably an easy fix..
I'm using [this]("https://help.ubuntu.com/community/FirefoxNewVersion") for reference.

---

### Post by eggdeng on 2007-09-10
You need to put the path to the tar.gz file, otherwise bash just looks in the current directory.
sudo tar xzvf /path_to_file/firefox-2.0.0.1.tar.gz -C /opt

---

### Post by mattmagician on 2007-09-10
Okay, still confused..(me not sleeping tonight is starting to show..)
> sudo tar xzvf /home/matt/Desktop/firefox-2.0.0.6.tar.gz/firefox-2.0.0.1.tar.gz -C /opt
would be it, no? because that'd ending up with:
> matt@Matt-Ubuntu:~$ sudo tar xzvf /home/matt/Desktop/firefox-2.0.0.6.tar.gz/firefox-2.0.0.1.tar.gz -C /opt
tar: /home/matt/Desktop/firefox-2.0.0.6.tar.gz/firefox-2.0.0.1.tar.gz: Cannot open: Not a directory
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error exit delayed from previous errors


---

### Post by mattmagician on 2007-09-10
update, i relized what was up, and got this:
any help?

> matt@Matt-Ubuntu:~$ sudo tar xzvf/home/matt/Desktop/firefox-2.0.0.1.tar.gz -C /opt
Password:
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
matt@Matt-Ubuntu:~$


---

### Post by eggdeng on 2007-09-10
You're missing a whitespace after the xzvf! Watch those typos, the shell is very sensitive to case and spaces.

---

