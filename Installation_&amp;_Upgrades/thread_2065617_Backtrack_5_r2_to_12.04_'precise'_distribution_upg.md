---
title: "Backtrack 5 r2 to 12.04 'precise' distribution upgrade"
date: 2012-10-02
forum: Installation &amp; Upgrades
---

### Post by Riddlebox87 on 2012-10-02
Hello, a few hours ago I had logged into Backtrack 5 r2 to check for updates and it said there was one for the distribution upgrade to 12.04 precise. Everything went well till after the reboot. I tried logging in and after that it gave me an error that it could not find the specified file. and sent me back to the command line. HELP!:confused:](*,)

---

### Post by dino99 on 2012-10-02
i dont know which kind of installation/upgrade you have done, but:

[PHP]BackTrack is a highly specialized distro[/PHP]

please read and understand: 

[HTML]http://www.backtrack-linux.org/wiki/index.php/Getting_Started[/HTML]

---

### Post by Cheesemill on 2012-10-02
Did you add any non-backtrack repositories to your system at any time (ie Ubuntu ones)?

BackTrack doesn't use the Ubuntu repositories so if you were using a default installation it wouldn't have offered you an upgrade, I've just checked on my installation and don't get offered an upgrade as there are none available.

What is the output of:
```
cat /etc/apt/sources.list
```

---

