---
title: "Installation problems with 9.10"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2010-10-02
I reinstalled 9.10 with CD. I can't find any of the programs I had previously, such as thunderbird. Why? What can I do?

---

### Post by garvinrick4 on 2010-10-02
> **Camilia said:**
> I reinstalled 9.10 with CD. I can't find any of the programs I had previously, such as thunderbird. Why? What can I do?
go to software sources in System/Applications and check to make sure all your repositorys are open. Then add partners and medibuntu (google and will give you a how to)Then add these two lines of code in a Terminal.
```
sudo apt-get install ubuntu-restricted-extras
```
```
sudo apt-get install thunderbird
```
The first line gives you all your flash,java.codecs and such. 
Below is the thunderbird package
```
rick@rick-laptop:~$ aptitude show thunderbird
Package: thunderbird
State: not installed
Version: 3.0.8+build2+nobinonly-0ubuntu0.10.04.1
Priority: optional
Section: mail
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Uncompressed Size: 33.9M
Depends: fontconfig, psmisc, debianutils (>= 1.16), libasound2 (> 1.0.22),
         libatk1.0-0 (>= 1.29.3), libc6 (>= 2.11), libcairo2 (>= 1.6.0),
         libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>=
         2.8.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>=
         2.23.5), libgtk2.0-0 (>= 2.18.0), libhunspell-1.2-0 (>= 1.2.8),
         libjpeg62, libnspr4-0d (>= 4.7.3-0ubuntu1~), libnss3-1d (>= 3.12.6),
         libpango1.0-0 (>= 1.14.0), libstartup-notification0 (>= 0.10),
         libstdc++6 (>= 4.1.1), libx11-6 (>= 0), libxrender1, libxt6, zlib1g (>=
         1:1.1.4)
Recommends: myspell-en-us | hunspell-dictionary | myspell-dictionary
Suggests: thunderbird-gnome-support (= 3.0.8+build2+nobinonly-0ubuntu0.10.04.1),
          latex-xft-fonts, libthai0
Conflicts: mozilla-thunderbird
Breaks: thunderbird-gnome-support (<= 3.0.4+nobinonly-0ubuntu3)
Replaces: mozilla-thunderbird, thunderbird-gnome-support (<=
          3.0.4+nobinonly-0ubuntu3)

```

---

### Post by Camilia on 2010-10-02
I reinstalled ubuntu and found that windows os was still on the computer. I previously had it to view netflix films. Since unable to get on Internet via windows, which was due to network program not getting installed, decided no more windows. Second installation of ubuntu erased windows. Thus able to download all previous programs.

---

