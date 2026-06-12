---
title: "Synaptic doesn't work anymore"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by michi21609 on 2008-10-19
Hi at all!

First of all: Please be aware of the fact that my mother tongue is German... So my English might be a bit strange...

To my problem:
I played a bit with installing/deinstalling Wine (several times, because I had the impression, that something didn't work...). Anyway, suddenly my synaptic didn't work anymore... the following message appeared: **E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.** So I tried **sudo dpkg --configure -a**

terminal printed the following message (a part is in german, i hope you understand it -> english translation in [] ):

```

Richte libc6 ein (2.7-10ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Segmentation fault
dpkg: Unterprozess[subprocess] post-installation script gab den[gave back] Fehlerwert[failurevalue] 139 zurück
```

ok, so I tried the following for more info: **sudo dpkg --debug=3773 --configure -a **

then the following was printed:

```

Richte libc6 ein (2.7-10ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Segmentation fault
dpkg: Unterprozess post-installation script gab den Fehlerwert 139 zurück
michael@michael:/usr/share/man$ 
michael@michael:/usr/share/man$ sudo dpkg --debug=3773 --configure -a
D000040: checking dependencies of libc6 (- <none>)
D000400:   checking group ...
D000400:     checking possibility  -> libgcc1
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000040: ok 2 msgs >><<
D000040:     checking Breaks
D000400:      checking virtbroken glibc-2.7-1
Richte libc6 ein (2.7-10ubuntu4) ...
D000002: fork/exec /var/lib/dpkg/info/libc6.postinst ( configure 2.7-10ubuntu4 )

Processing triggers for libc6 ...
D000002: fork/exec /var/lib/dpkg/info/libc6.postinst ( triggered ldconfig )
ldconfig deferred processing now taking place
Segmentation fault
dpkg: Unterprozess post-installation script gab den Fehlerwert 139 zurück
```

I have: ubuntu 8.04, Kernel Linux 2.6.24-21-generic

I also tried: **sudo apt-get -f install** -> didn't work!

Any sugesstions? What happened? Do I have to reinstall ubuntu?

Heeelp!

Thanks!
Michael[COLOR="black"]****[/COLOR]

---

