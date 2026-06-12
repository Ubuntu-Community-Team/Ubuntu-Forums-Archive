---
title: "sun-java6-bin freeze"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by GolemdX on 2010-03-15
I was SSHing to my server, and installed sun-java6-bin, -jdk, and -jre. All was going fine, until it tried to install sun-java6-bin. It kinda just never progressed. I reset it, and do a 'sudo dpkg --configure -a' and it tries to configure it, and freezes completely once more. How can I get this to install without freezing the whole system?

```
golemdx@dobe-server:~$ sudo dpkg --configure -a
[sudo] password for golemdx:
Setting up sun-java6-bin (6-15-1) ...
```

That's as far as it gets.

---

