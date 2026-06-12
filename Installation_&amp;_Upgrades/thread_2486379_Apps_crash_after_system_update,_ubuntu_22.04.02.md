---
title: "Apps crash after system update, ubuntu 22.04.02"
date: 2023-04-27
forum: Installation &amp; Upgrades
---

### Post by ministar123 on 2023-04-27
I have just updated my ubuntu to 22.04.02 jammy. Problems are I can't open some applications, for example i can open Teams, Matlab, Firefox, but I can't open Google Chrome, Discord, Visual Studio Code. I uninstalled and installed discord again and it is working but for chrome is the same error as before:
 "[5002:5002:0427/222736.369724:FATAL:credentials.cc(127)] Check failed: . : Permission denied (13)
Trace/breakpoint trap (core dumped)".
That error was also for discord but reinstalling fixed it.
I tried reinstalling, resetting ownership, permissions, removing cache and configuration folders for chrome but nothing works.
Also other problem that happened with update is that it takes a lot of time from booting and entering my password to being able to use the system, in the meantime it is just a black screen.

Can someone help me with these problems? I'm pretty new to ubuntu and linux in general.

---

### Post by jarl-dk on 2023-04-28
I also just experienced this with chrome. On Ubuntu 22.04.2 that is.

I was just using a new kernel.

The only thing I got was
```

[11849:11849:0428/091628.955956:FATAL:credentials.cc(127)] Check failed: . : Permission denied (13)
Trace/breakpoint trap (core dumped)".

```

---

### Post by jarl-dk on 2023-04-28
I have filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-meta-nvidia-5.19/+bug/2017980](https://bugs.launchpad.net/ubuntu/+source/linux-meta-nvidia-5.19/+bug/2017980)

---

### Post by ministar123 on 2023-04-28
Yes i meant ubuntu 22.04.2, sorry.
Okay great.
But you don't have problems with other apps and slow start like I do?

---

### Post by jbrinkmann2 on 2023-05-30
Same here. A temporary workaround: start Chrome using the command line and add "--no-sandbox" as a parameter: 

google-chrome --no-sandbox

It is a potential security issue, though. Chrome warns you, when you do this. However, at least a way to access bookmarks, saved passwords and the like.

---

