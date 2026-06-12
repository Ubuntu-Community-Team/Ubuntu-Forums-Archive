---
title: "Help installing programs for Ubuntu 7.10"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by Imperial_Onyx on 2008-07-07
I am totally new on Ubuntu.
Cans some teach or give me any tutorial how to install useful programs such as Open Office, VLC, and yahoo messenger.
I want to install these programs but i dont have any idea how to.

---

### Post by iaculallad on 2008-07-07
> **Imperial_Onyx said:**
> I am totally new on Ubuntu.
Cans some teach or give me any tutorial how to install useful programs such as Open Office, VLC, and yahoo messenger.
I want to install these programs but i dont have any idea how to.

NOTE: Issue the terminal commands below one-at-a-time

For OpenOffice:

```
 sudo apt-get install openoffice.org
```

For VLC:

```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install vlc

```
For Yahoo Messenger:

> Use the default application installed: PIDGIN

---

### Post by Partyboi2 on 2008-07-07
[[COLOR=Blue]Here[/COLOR]]("http://monkeyblog.org/ubuntu/installing/") is a small guide to installing programs.

---

### Post by abn91c on 2008-07-07
check all you menu's first before installing, open office is installed by default on ubuntu 8.04

---

### Post by H3lp3r on 2008-11-11
I can not find PIDGIN

---

### Post by Partyboi2 on 2008-11-12
> **H3lp3r said:**
> I can not find PIDGIN
If you are trying to install pidgin open a terminal (Applications>Accessories>Terminal) and type
```
sudo apt-get install pidgin
```

---

