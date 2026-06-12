---
title: "Odd ssh banner after 9.10 &gt; 10.04 &gt; 10.10 upgrade"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by cebesius on 2010-10-13
I just upgraded to 10.10 via 10.04 from 9.10, and now I'm getting an odd banner when logging in via ssh. I checked my /etc/sshd_config and it looks like Banner is disabled by default (commented out), and PrintMotd is set to no. It's really not a big deal, but I'm curious if anyone knows the cause of this.


```
myuser@mylocalbox:~$ ssh myremotebox
Linux myremotebox 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

```

---

### Post by aksoutherland on 2010-10-13
I don't know what caused it, but I had the same thing happen.
I cleared the contents of /etc/motd and /etc/motd.tail and everything cleared up.

---

### Post by luvshines on 2010-10-13
Yeah, /etc/motd should be having the content which you see when you ssh

You can put any message there to greet the people who ssh. Or maybe post warnings, rules to use your computer etc etc

motd (message of the day) ;)

---

### Post by Bee77 on 2010-10-23
> **aksoutherland said:**
> I don't know what caused it, but I had the same thing happen.
I cleared the contents of /etc/motd and /etc/motd.tail and everything cleared up.

Yeah, just clear/delete /etc/motd.tail and you're done. /etc/motd is automatically generated.

See here: [http://ubuntuforums.org/showthread.php?t=1593161](http://ubuntuforums.org/showthread.php?t=1593161)

(Thanks t[COLOR=Black]o [/COLOR]mörgæs[, ]("http://ubuntuforums.org/member.php?u=939075")[http://ubuntuforums.org/showpost.php?p=10013335&postcount=5](http://ubuntuforums.org/showpost.php?p=10013335&postcount=5))

---

