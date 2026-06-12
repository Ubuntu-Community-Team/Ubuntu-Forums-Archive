---
title: "HELP! Messed up with java-RHINO blocks mmy synaptic/terminal!"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by vickoxy on 2010-02-06
[SIZE="3"][SIZE="2"]Hi,
i messed up with java to integrate it in google-chrome. But i lost java support for firefox, then tried to remove all browser and java-and to reinstall them. But i can do anything now in Synaptic (i reinstalled firefox though, but java is not working)-having this message:

    ```
E: rhino: Unterprozess installiertes pre-removal-Skript gab den Fehlerwert 2 zurück
```


Can not remove rhino also.

So, if anyone knows what to do.

P.S. My wifi is also not working and can not install drivers.[/SIZE]
UPDATE: After few restarts, i have my wifi back, but rendomly i use it and need to reinstall hardware drivers for w-lan-process is always canceled because of error with rhino-but after restart i have wifi back.

Still, i have ubuntu-tweak installed and it shows me rhino packages as abundant-i should remove it. But that is impossible.

I use fluxbox and Karmic (Linux Mint)

---

### Post by lemming465 on 2010-02-07
The first thing I'd try, if you haven't already is an apt-get repair run:```
sudo -i
apt-get update
apt-get upgrade --fix-broken
```
If that runs afoul of the broken Rhino pre-remove script, then I'd try something lower level:```
sudo dpkg --remove --force-all rhino
```

I hope the English response is intelligable; my german isn't good enough to do tech support in it.

---

### Post by vickoxy on 2010-02-07
Thanks for answer-i should mark this thread solved, because i made new xubuntu 9.10 install.

:popcorn:

---

