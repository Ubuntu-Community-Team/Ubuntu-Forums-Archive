---
title: "Automatic installing updates (aptitude)"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by EvilDoer on 2005-06-19
Hello,
yesterday after installation of UBUNTU 5.04 Hoary Hedgehod, 
i can't use synaptic or apt-get or aptitude... 

```
root@ubuntu:/ # apt-get install
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

So I started to find, what did it. And I find

```
root@ubuntu:/ # ps aux | grep aptitude
root      8192  0.2  1.0   9464  5408 pts/0    S+   08:13   0:07 aptitude --without-recommends -y install ~tubuntu-desktop

```

So... I was waiting,when it stoped downloading and updating, everything was ok! 
After this my synaptic showed that i must install 6 updates. So I did it.
But today, I can't use synaptic, apt-get... why? Because aptitude...  ](*,) 

Log aptitude:
```
Aptitude 0.2.15.8: log report
Sun Jun 19 01:32:37 2005

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
============================================
============================================
```

It seems that it does nothing now, but it blocks work with pkg.
How can I this "autoupdating" disable? It start everytime after booting... And nothing info about it...

Sorry for my english :) And Thnx for your help...

---

