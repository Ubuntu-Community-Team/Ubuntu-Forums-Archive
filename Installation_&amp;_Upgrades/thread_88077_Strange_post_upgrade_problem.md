---
title: "Strange post upgrade problem"
date: 2005-11-09
forum: Installation &amp; Upgrades
---

### Post by IgorCastang on 2005-11-09
Hello all,

I'm facing a problem that seems related to the upgrade from 5.04 to 5.10, although it took me time to realise it, but any server running on my machine cannot be contacted any more...
here is an example

```

root@igorthinkpad:~# lsof -i 
COMMAND    PID     USER   FD   TYPE DEVICE SIZE NODE NAME
apache    3950     root   16u  IPv4  63383       TCP *:www (LISTEN)
apache    3951 www-data   16u  IPv4  63383       TCP *:www (LISTEN)
apache    3952 www-data   16u  IPv4  63383       TCP *:www (LISTEN)
apache    3953 www-data   16u  IPv4  63383       TCP *:www (LISTEN)
apache    3954 www-data   16u  IPv4  63383       TCP *:www (LISTEN)
apache    3955 www-data   16u  IPv4  63383       TCP *:www (LISTEN)
root@igorthinkpad:~# telnet 127.0.0.1 80
Trying 127.0.0.1...


```

the telnet NEVER connects and hangs there forever... It is the same for any daemon listening to incoming connexions (postfix, ftp, ...) it seems like some weird kind of filtering is occuring but i can't put my finger on it. Otherwise all network stuff is working ok. 
Any help would be greatly appreciated...

---

### Post by IgorCastang on 2005-11-10
Problem solved,

i had the iptables package installed, removing it did the trick...
I don't really need the iptables functionality so i removed rather than changig the settings...

---

