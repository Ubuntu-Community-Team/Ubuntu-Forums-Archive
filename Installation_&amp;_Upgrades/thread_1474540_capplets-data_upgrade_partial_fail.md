---
title: "capplets-data upgrade partial fail"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by crossy on 2010-05-06
Doing a quick 'apt-get upgrade' this morning (*for some reason the update notification taskbarcon I had on 8.04LTS seems to be missing*) and saw the following:

> Setting up capplets-data (1:2.30.1-0ubuntu1) ...
Installing new version of config file /etc/xdg/autostart/gnome-at-session.desktop ...
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)

Setting up gnome-settings-daemon (2.30.1-0ubuntu1) ...

Anyone get the same, and should I be reporting this to someone? (I'm using Lucid-64bit on a Dell D620 laptop if that makes any difference)

---

### Post by youthzu on 2010-05-06
I got the same error.

---

### Post by Jimtheplanner on 2010-05-09
Same here.....

---

### Post by Wytze on 2010-05-09
Same error here. v10.04 LTS - Dutch.

---

### Post by eris23 on 2010-05-23
on maverick:

sudo dpkg-reconfigure gconf2
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)

---

### Post by ComputerJy on 2010-05-26
I think this has nothing to do with capplets. I guess it's trigerred everytime dpkg tries to read from gconf2

---

