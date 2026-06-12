---
title: "Python-Psyco for Bittorrent"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by Telarmago on 2007-01-08
I'm trying to install bit torrent on my 6.06 Dapper Drake Ubuntu installation. I opened the .deb, but it said I needed python-psyco. When I went to apt-get install python-psyco, it gave me this error:

telarmago@telarmago-desktop:~$ sudo apt-get install python-psyco
Reading package lists... Done
Building dependency tree... Done
Package python-psyco is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-psyco has no installation candidate
telarmago@telarmago-desktop:~$

Also, I uninstalled the bittorrent that came with the installation. It also removed ubuntu-desktop (I think), which is supposedly fine (from the description), and some GNOME Bittorrent GUI. Where can I re-install this GUI after I update Bittorrent (It was 3.x, the latest is 5.x)?

Help will be appreciated, and thank you!

---

### Post by Telarmago on 2007-01-08
Bump.

---

### Post by saivert on 2007-04-01
I also want to know how to install the python-psyco package. I downloaded it with apt-get source and tried building it but I get compilation errors when running "sudo python setup.py install".

Bram Cohen's Bit Torrent client require this and there must be other software which depends on psyco as well to get faster python code.

---

### Post by face00 on 2008-05-23
psyco will never work on 64 bit.   However, bittorent appears to work fine without psyco.

For example the following works on hardy 64bit:
```
wget http://download.bittorrent.com/dl/BitTorrent-5.2.0.tar.gz
tar xpfz BitTorrent-5.2.0.tar.gz
cd BitTorrent-5.2.0
```

Now edit debian/control and remove the dependency on python-psyco.   If you don't know how to use vi/vim, then use nano or editor of your choice:
```
vi debian/control   # and remove python-psyco,
sudo bash install_nix.sh  # ignore errors
cd dist
sudo dpkg -i bittorrent_5.2.0_python2.4.deb
```

hope this helps,
--
[http://myutil.com]("http://myutil.com")

---

