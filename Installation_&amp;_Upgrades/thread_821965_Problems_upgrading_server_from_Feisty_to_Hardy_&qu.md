---
title: "Problems upgrading server from Feisty to Hardy: &quot; unmet dependencies &quot;"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by yintodo on 2008-06-07
I didn't install Gutsy and went from Festy to Hardy.

I have tried every solution that I have found on the net, but none has worked. Also, I don't know if this is the cause that Freenx doesn't start. 

----------------
```
root@-------:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  freenx: Depends: xfonts-base but it is not installed
  x-ttcidfont-conf: Depends: xfonts-encodings (>= 1:1.0.0-5.1) but it is not installed or
                             xfonts-base (< 1:1) but it is not installed
  x-window-system-core: Depends: xfonts-base but it is not installed
  xbase-clients: Depends: x11-apps but it is not installed
                 Depends: x11-session-utils but it is not installed
                 Depends: x11-utils but it is not installed
                 Depends: x11-xfs-utils but it is not installed
                 Depends: x11-xkb-utils but it is not installed
                 Depends: x11-xserver-utils but it is not installed
  xkeyboard-config: Depends: xkb-data (>= 1.1~cvs.20080104.1-1ubuntu6) but it is not installed
  xserver-xorg-core: Depends: x11-common (>= 1:7.0.0) but 7.0.0-0ubuntu45 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by avtolle on 2008-06-07
OK, to go direct from Feisty to Hardy, I suggest d/l the iso, burning a CD, and doing a fresh install. There is no direct upgrade for Feisty to Hardy, AFAIK, and I believe you are having the problems you post due to your attempt to do so.

---

### Post by yintodo on 2008-06-08
Many thanks for your response. 
As that server is not at hand, I haven't used the CD.

best
jj

---

