---
title: "Monitoring sous dosemu ?"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by olivier131313 on 2010-06-15
Hello,
I explain my situation.
I emulate an ERP software on dosemu, on a debian server and the emulation work well.
However, it's a critical network application, so i have to see often the use of processor and memory.
So, do you know if dosemu has natively an option of monitoring ?
Or if i have to install other packages to watch my server constants ?
I thank you beforehand !
Regards,
Olivier.

---

### Post by nerdzero on 2010-06-15
olivier,

What sort of monitoring did you have in mind?  Is the 'top' command not sufficient?

---

### Post by olivier131313 on 2010-06-15
Hello,
it's true i haven't been very specific ^^
I want an online monitoring, for example to manage my server remotly, to watch all time my server's use of proc, memory etc...
It's this type of monitoring i search, even if i think that it is not natively integrated to dosemu...
Thank you ^^ !

---

### Post by nerdzero on 2010-06-15
I've only ever used DOS emulators to play very old games :)  It does not seem to have any built-in reporting capabilities:  [http://dosemu.org/docs/README/1.4/](http://dosemu.org/docs/README/1.4/)

There are lots of tools available for linux though.  I have never used it but maybe 'monit' will do what you are looking for.

[http://mmonit.com/monit/](http://mmonit.com/monit/)

I just use ssh and 'top' or 'htop' though to check CPU and memory usage on my server.

---

### Post by olivier131313 on 2010-06-16
thanks for your answer,
i will check this tool ^^
++

---

