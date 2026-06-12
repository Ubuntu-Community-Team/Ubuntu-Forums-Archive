---
title: "apache2 reinstall?"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by rizzchap on 2010-05-07
hello, I began by trying to change the sites-available/default file, and then because I got confused as to which was the backup and which was the working one, I removed the proper settings and ended up not having apache working.

so I followed some reinstall advice on a forum and ended up making things even worse.

so I've got an 8.10 server, but php files only try to 'open/save as'. This leads me to try to reinstall apache (which I've done once already. tried to, at least)

So I purged apache2, and apache2-common, then tried to reinstall. There may have been some dependencies that I just arbitrarilly said 'y' to, but I then ended up having to reinstall php5 and libapache2-mod-php5.

Is there somewhere that is a list of things I need, or better yet... have? Using apt-get is all fine and good but without the gui (it's a basic server), I can't see what I've got.

any help?

~rizz

---

