---
title: "Trouble with Firefox 3.6 after using the beta/RC from mozilla daily ppa (9.10,64-bit)"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by forteller on 2010-01-23
I've been using the Fx 3.6 betas and RCs for a long time with very little problem. But after doing an update yesterday, after 3.6 was officially released, I've not been able to open Firefox/Namoroka. I've used Synaptic to remove it completely, restarted the computer (just in case), and installed it again, but I still get this error msg when trying to start Firefox from terminal:

```
/usr/lib/firefox-3.6.1pre/firefox: 59: dirname: Permission denied
/usr/lib/firefox-3.6.1pre/firefox: 88: /bin/pwd: Permission denied
/usr/lib/firefox-3.6.1pre/run-mozilla.sh: 39: dirname: Permission denied
/usr/lib/firefox-3.6.1pre/firefox-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory
```

Help? I really miss my Firefox! :)

---

### Post by mionescu on 2010-01-23
Try to install the new update of 3.6.1pre (which is already released or will be released in the following couple of days)

---

### Post by Tanker Bob on 2010-01-23
I've seen others with this problem. There's another thread somewhere here in General Help that said reloading the apparmor service solved the problem. OTOH, I installed 3.6.1pre from the daily ppa and it works fine with no complications.

---

