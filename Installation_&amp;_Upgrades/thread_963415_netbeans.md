---
title: "netbeans"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Mcihi on 2008-10-30
hi,

i installed netbeans with
```
apt-get install netbeans
```

but when i try to start netbeans (either from the menu or the command line) nothing happens.

in syslog i just get those messages (i don't think it has something to do with netbeans):
```
Oct 30 13:04:49 pc init: tty1 main process (9253) terminated with status 1
Oct 30 13:04:49 pc init: tty1 main process ended, respawning
```

can anyone give me a hint?

---

### Post by fendres on 2008-10-30
Hello.
Try "strace -ff netbeans", possibly "strace -ff netbeans &> some_file" to get an idea of what the program does. See "man strace" for an explanation of the output.

---

