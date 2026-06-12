---
title: "installing a program"
date: 2005-06-11
forum: Installation &amp; Upgrades
---

### Post by Dark Damo on 2005-06-11
i have a file

filenamehere.deb when i click on it to install it just opens? how would i install it?  :mad:

---

### Post by Xian on 2005-06-11
[QUOTE=Dark Damo]i have a file

filenamehere.deb when i click on it to install it just opens? how would i install it?  :mad:[/QUOTE]
Place it in your /home directory.
Open a terminal and enter this line:

```
$ sudo dpkg -i <filename.deb>
```

---

### Post by Dark Damo on 2005-06-11
[QUOTE=Xian]Place it in your /home directory.
Open a terminal and enter this line:

```
$ sudo dpkg -i <filename.deb>
```[/QUOTE]
 it gives me this

(Reading database ... 59347 files and directories currently installed.)
Unpacking opera (from .../opera_8.0-20050415.6-shared-qt_en_sarge_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3c102-mt (>= 3.3.1); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera

---

### Post by Xian on 2005-06-11
Do the following command and then you can install Opera:

```
$ sudo apt-get install libqt3c102-mt
```

---

### Post by Dark Damo on 2005-06-12
[QUOTE=Xian]Do the following command and then you can install Opera:

```
$ sudo apt-get install libqt3c102-mt
```[/QUOTE]
 ok i done that now when i put that file in root terminal i get


root@damo:/home/damo # /home/damo/opera_8.0-20050415.6-shared-qt_en_sarge_i386.d eb
/home/damo/opera_8.0-20050415.6-shared-qt_en_sarge_i386.deb: line 1: syntax erro r near unexpected token `newline'
/home/damo/opera_8.0-20050415.6-shared-qt_en_sarge_i386.deb: line 1: `!<arch>'

---

