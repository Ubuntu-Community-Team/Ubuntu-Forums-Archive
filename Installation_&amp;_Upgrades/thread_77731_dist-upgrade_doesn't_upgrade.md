---
title: "dist-upgrade doesn't upgrade"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by sixtwoten on 2005-10-17
i have ubuntu 5.04 installed and when i use sudo apt-get dist-upgrade it says 0 for upgraded, newly installed, to remove, and not upgraded. i thought with the release of 5.10, using dist-upgrade would upgrade my distribution. am i missing something?

---

### Post by adwait on 2005-10-17
You have to edit the /etc/apt/sources.list file and replace all the references to "hoary" to "breezy. You can open the file using
```
sudo gedit /etc/apt/sources.list
```

---

### Post by sixtwoten on 2005-10-17
at the top of the file, it has

deb cdrom:[Ubuntu 5.04 _Hoary Hedge_ - Release i386 (20050407)]/ hoary main restricted

how do i modify this to reflect breezy badger?

---

### Post by adwait on 2005-10-17
That is for the CD ROM, remove that line.

---

### Post by sixtwoten on 2005-10-17
if for any number of reasons i need to return to 5.04 hoary or even warty, can i do that after upgrading to 5.10 breezy? if yes, how?

---

### Post by ltmon on 2005-10-17
[QUOTE=sixtwoten]if for any number of reasons i need to return to 5.04 hoary or even warty, can i do that after upgrading to 5.10 breezy? if yes, how?[/QUOTE]

Not really... downgrading is not something supported.

The only way I know is to install with your "/" and "/home" in seperate partitions, and overwriting "/" with a fresh install of Hoary.

L.

---

