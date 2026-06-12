---
title: "Permanent settings on Live USB: TTYs and hosts  (10.04.2)"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by Peacepunk on 2011-06-02
This one has me not puzzled, but flabberugarnistablafed:

[COLOR="DarkRed"]
the impossibility to permanently change the settings of some config files in Live mode! i.e. the whole bunch of **/etc/init/tty*****.conf**. 

I don't like having 6 TTY's opened with no password asked... Plus, if I set up a new user, I'd have to give a password to shut down the machine since there are 6 'ubuntu' users logged!

Where are the source files that erase my mods at each boot? Or where is the script that reverts my changes?

If I add a comment, it stays; only if I change the TTY line back to **exec /sbin/getty 115200 TTY2** it gets changed back to the newer 'login -f' line at the next boot.

[SIZE="7"]??[/SIZE]
Working from **LTS 10.04.2** fresh torrent download, tried on _2 different flashdrives_ on _2 different machines_.

---

