---
title: "Sharing a /data partition between different Linux distributions"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by notessensei on 2008-09-23
Hi there,

I'm testing different Linux distributions: OpenSuse, Fedora, Ubuntu. So I partitioned my disk:

SDA1 /
SDA2 [for Suse]
SDA3 [for Fedora]
SDA4 Swap
SDA5 /Common

I installed Fedora first and pointed the folders in my home directory to /common/myFiles/Documents Music Pictures etc.

After installing Ubuntu the owner of common is stated as 500 (no name). I can switch to sudo and do a chown, but that will lead to the same access problem when booting Fedora later. What do I have to do to "sync" the user access to my /Common partition --- or is the only way to give read write to everybody (brrrr)
:-) stw

---

### Post by andrewc6l on 2008-09-23
The easiest way is probably to add a group in /etc/group in all your installations, and make sure the user you usually log in with is in that group. Give that group permission for /Common/.

(You'll need to go through /etc/group for all the platforms to make sure you don't accidentally use a group id that has the same number as one that already exists.)

Some more info is here:
[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)
[http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/](http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)
[http://ubuntuforums.org/showthread.php?t=462375](http://ubuntuforums.org/showthread.php?t=462375)

---

