---
title: "Installing 7.10 server help"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by jhyland87 on 2008-03-25
hey guys, so im taking this tutorial..
[http://howtoforge.com/perfect_server_ubuntu7.10_p4](http://howtoforge.com/perfect_server_ubuntu7.10_p4)

Im stuch on step 12 (**12 DNS Server**)

All is going well till I run "/etc/init.d/sysklogd restart"

it says "can not create /var/lib/named/dev/log, no such file or directory"

Obviously this is from the vi edit I did just prior to this.. However I try to create the folder..
(mkdir /var/lib/named/dev/log) and it says it exist...

Anyone had this happen? whats the correct step, or did I look over something?

---

### Post by jhyland87 on 2008-03-25
ok edit, I noticed the error changed once I made " /var/lib/named/dev/log", now it says:
cannot create  /var/lib/named/dev/log: address already in use

???

---

### Post by jhyland87 on 2008-03-25
ok so I tried to remove the log folder then restart, and I guess it did it, then I tried to start the log and it failed.. here is a picture (2 different computers, screenshots are a no no)

[IMG]http://i66.photobucket.com/albums/h247/farfromeinstein/203695129349.jpg[/IMG]

---

### Post by jhyland87 on 2008-03-25
Wait a sec!! In that tutorial you edit this vi..

vi /etc/default/syslogd

But execute this command?

/etc/init.d/sysklogd restart

whats with the k in the middle? typo

---

### Post by jhyland87 on 2008-03-25
Nope, Tried it.

[IMG]http://i66.photobucket.com/albums/h247/farfromeinstein/203695461765.jpg[/IMG]

---

### Post by jhyland87 on 2008-03-25
bump........?

---

