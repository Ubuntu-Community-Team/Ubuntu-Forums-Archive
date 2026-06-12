---
title: "Keepassx works strange in Ubuntu 8.10"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by birdySi on 2008-11-06
I'm using KeepassX for a while now. 

I've recently start using URL like this:

cmd://gnome-terminal -x ssh -X username@server

This works fine. But when I put in URL:

cmd://gnome-terminal --title "user (server)" -x ssh -X username@server

With this command the terminal doesn't open.

Furthermore, placeholders like {USERNAME} {TITLE} doesn't wokr either. For example if I have in Username field joe and in Title field noname.somwhere.com And than put in URL 

cmd://gnome-terminal -x ssh -X {USERNAME}@{TITLE}

It wont open terminal.

Reason beacuse I'm writing this post is that on my friends PC works KeepassX properly. But there is slight difference. He is using Ubuntu 7.10 & KeepassX 0.3.1. I'm using Ubuntu 8.10 & KeepasX 0.3.3. I have even installed KeepassX 0.3.1 and still nothing.

Does anybody have any idea how to solve this problem?

---

