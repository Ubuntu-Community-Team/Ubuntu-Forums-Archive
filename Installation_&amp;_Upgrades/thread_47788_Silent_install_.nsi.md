---
title: "Silent install .nsi"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by xbilly on 2005-07-10
I want to install MakeTorrent for linux.

I downloaded the zip folder and unzipped it to /etc/maketorrent/

I got four .py files and an nsi file.

Now I am lost. How do I install the program? I gather i must some how use a "silent Install" method? Please help. I am new

---

### Post by llamakc on 2005-07-10
Please do not put stuff in /etc. If you want to play with compiling, do that in your home directory, /home/username, or in /usr/local or /opt, but not in /etc. Configuration and other important files go there.

If you have installed the "bittorrent" package, you already have the ability to create a torrent.

```

[ken:dload](06:45 AM)$ bt
btcompletedir				  btmakemetafile
btcompletedir.bittorrent	   btmakemetafile.bittorrent
btdownloadcurses			   btreannounce
btdownloadcurses.bittorrent	btreannounce.bittorrent
btdownloadheadless			 btrename
btdownloadheadless.bittorrent  btrename.bittorrent
btlaunchmany				   btshowmetainfo
btlaunchmany.bittorrent		btshowmetainfo.bittorrent
btlaunchmanycurses			 bttrack
btlaunchmanycurses.bittorrent  bttrack.bittorrent

```

Do you want a gui for creating the torrents?

FWIW, .nsi files are NullSoft (of WinAmp fame) installer templates for the NSIS installer & Windows.

Just make sure you have the wxWindows bindings for python installed, wxpython2.5.3, and you should be good to go.

---

