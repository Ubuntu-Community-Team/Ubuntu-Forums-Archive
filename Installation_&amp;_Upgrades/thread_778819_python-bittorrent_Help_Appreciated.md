---
title: "python-bittorrent Help Appreciated"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by Glaxed on 2008-05-02
I think I may have misconceptions about the python-bittorrent package.

I installed the latest version today, and for the life of me, I can't seem to find a source file or a man page anywhere! - Not to mention a complete lack of online documentation as well.

Isn't that package supposed to be used to help create torrent clients (like Deluge)?
i just wanted to play around with it because I like learning Python, but I can't *get *to it anywhere, Terminal Output:
```

q@QXD:~$ apt-cache search python | grep torrent
bittornado - bittorrent client with enhanced curses interface
python-bittorrent - Scatter-gather network file transfer
debtorrent - bittorrent proxy for downloading Debian packages
deluge-torrent - A Bittorrent client written in Python/PyGTK
deluge-torrent-common - A Bittorrent client written in Python/PyGTK - common files
deluge-torrent-dbgsym - debug symbols for package deluge-torrent
q@QXD:~$ up in python-bittorrent
[sudo] password for q:
Reading package lists... Done
Building dependency tree
Reading state information... Done
python-bittorrent is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
q@QXD:~$ locate python | grep torrent
q@QXD:~$ locate python | grep torrent | more
q@QXD:~$ echo "Crap."
Crap.

```Thanks guys.

---

