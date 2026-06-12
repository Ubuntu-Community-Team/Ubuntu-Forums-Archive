---
title: "wmd converter"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by Starcrunch on 2007-03-22
im having trouble playing my saved music and i need a converter so i can play it with the music player....so wmd to something

---

### Post by upbeat.linux on 2007-03-23
Two choices:

_1. Ubuntu option_:

  i. Open a terminal type:
          > sudo apt-get install rar unrar
  ii. Applications -> Accessories -> Archive Manager
  iii. Open your WMD files and extract the music you want

_2. Window$ option_: download and install WinRAR. You can associate the WMD files with WinRAR and then open them as a standard archive file. From their, extract the files you need.

Haven't tested the Ubuntu option, but its worth giving it a shot.  Let us know how you faired.

---

### Post by Starcrunch on 2007-03-25
this didnt work i got a message saying this  (Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate) 
do i need to dl a rar? im using 6.06 ubuntu

---

### Post by upbeat.linux on 2007-03-26
1. From the terminal 

```
sudo gedit /etc/apt/sources.list
```

2. Look for lines ending in 'universe' and add 'multiverse' after it. Uncomment the line if necessary.

3. Try the steps I suggested before.

If that doesn't work try downloading the Automatix package for 6.06:

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Installs a good deal of common apps including rar and unrar.

---

