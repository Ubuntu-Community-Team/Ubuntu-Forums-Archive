---
title: "Upgraded from 7.04 to 7.10, Now Can't Connect to Internet"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by confusedmatt on 2007-10-22
Hi all,

I've just upgraded from 7.04, where everything worked just fine, to 7.10 and now can't get on-line in either Firefox or Evloution Mail.

I am using a Linksys ADSL2MUE through the ethernet card, as I did on 7.04, which works on my XP machine.

The network manager can see the router because I can access it through 192.168.1.1, it network manager is showing that the connection is working.

I've tried the about:config stuff suggested in other threads, but no luck.

Please help.

Matt

---

### Post by G4HZA on 2007-10-22
I had this with one of my systems

Try the following command
sudo echo 0 > /proc/sys/net/ipv4/tcp_window_scaling


If it works add it to rc.local without the sudo.

Roger

---

### Post by confusedmatt on 2007-10-22
Hi Roger,

Tried this in the terminal, but got the message:

"Permission Denied"

Any suggestions as to why this may be?

Matt

---

### Post by confusedmatt on 2007-10-22
Hi all,

I've just tried restarting on an older kernel, and can now get on-line with firefox, but evolution mail still cannot connect!!!!

Any suggestions?

Matt

---

