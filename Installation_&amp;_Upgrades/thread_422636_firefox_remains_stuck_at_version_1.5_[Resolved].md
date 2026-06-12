---
title: "firefox remains stuck at version 1.5 [Resolved]"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by hencq on 2007-04-25
Hi,

I've upgraded to Feisty, but for some reason my Firefox version remains stuck at version 1.5. The strange thing is though, that when I check in Synaptic, it says that version 2.0.0.3 is installed. Any idea how this is possible and how to fix it?

Thanks,
Hencq

---

### Post by bapoumba on 2007-04-25
> **hencq said:**
> Hi,

I've upgraded to Feisty, but for some reason my Firefox version remains stuck at version 1.5. The strange thing is though, that when I check in Synaptic, it says that version 2.0.0.3 is installed. Any idea how this is possible and how to fix it?

Thanks,
Hencq
Open a terminal (> Accessories > Terminal) and run:
```
aptitude show firefox
```
and paste the output in here. You will see which version is actually installed. How do you know you are running Fx 1.5 ?

```
~$ aptitude show firefox
Package: firefox
State: installed
Automatically installed: no
Version: 2.0.0.3+1-0ubuntu2
Priority: optional
Section: web

```

---

### Post by tp21 on 2007-05-19
hi,
i have the same problem.
i upgraded ubuntu sequentially from 6.06 to 6.10 and then 7.04. while having 6.06 i had firefox 1.5. and after the upgrade to 7.04 i found out that firefox is still 1.5 by checking Help -> Info. the funny thing is synaptic says that i have firefox 2.0.3.
i uninstalled firefox and reinstalled it again but it didn't help.

here is the results of aptitiude show firefox
Paket: firefox
Zustand: Installiert
Automatisch installiert: nein
Version: 2.0.0.3+1-0ubuntu2
Priorität: optional
Bereich: web

thanks

---

### Post by aysiu on 2007-05-19
Had you installed 1.5 using any kind of script? Can you post the output of these commands? ```
cd /opt
ls
```

---

### Post by tp21 on 2007-05-19
i installed firefox 1.5 using synaptic without any scripts.
here are the results:
firefox  google-earth

---

### Post by aysiu on 2007-05-19
If you have Firefox in your /opt directory, *something* other than Synaptic must have put it there. Either you put it manually there or a script of some kind put it there (Automatix, maybe?).

Try pasting (do not retype) these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
sudo rm -r /opt/firefox
```

---

### Post by tp21 on 2007-05-19
thanks alot aysiu. it worked out. now i have firefox 2.0.3
but what was wrong?

---

### Post by aysiu on 2007-05-19
Well, there are two kinds of Firefox:

1. The Ubuntu repositories one--that's the one you install with Synaptic Package Manager
2. The Mozilla one--that's the one from the Mozilla.org website

A lot of times people like to have the Mozilla one for whatever reason, and the instructions for installing it *and* all the scripts that install it put it in the /opt directory and then make the Firefox launcher point to the /opt/firefox Firefox instead of the Ubuntu one.

So the commands I gave you just made the launcher point back to the Ubuntu Firefox and then removed the /opt/firefox folder altogether.

---

