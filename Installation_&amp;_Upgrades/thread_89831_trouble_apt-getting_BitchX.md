---
title: "trouble apt-getting BitchX"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by mil on 2005-11-13
im new to linux and i was getting some help installing things, apt-get i was told. when i try to use this command it tells me the following:

dan@ghost:~$ apt-get install BitchX
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package BitchX

it doesnt work for anything i try. anyone have any ideas? it works for other people apparently so i dont know whats wrong. please help. thank you.

---

### Post by transactionlogfiller on 2005-11-13
It's case sensitive. use apt-cache search BitchX to get the exact name and then install the right one.

---

### Post by mil on 2005-11-13
it doesnt work. i dont know whats wrong.

---

### Post by somas1 on 2005-11-13
sudo apt-get install bitchx worked for me.

---

### Post by mil on 2005-11-13
not me :(

---

### Post by somas1 on 2005-11-13
[QUOTE=mil]not me :([/QUOTE]
Did you try bitchx with all lowercase letters?

---

### Post by transactionlogfiller on 2005-11-28
Do we have the same repositories?

Here are mine.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Hoary Extras (because Breezy Extras are not curently available)
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by aysiu on 2005-11-28
[bitchx is in the universe repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=bitchx&searchon=names&subword=1&version=breezy&release=all). If you want to make sure you have them, see the first link in my sig.

---

### Post by Kyral on 2005-11-28
EDIT: Didn't see the rest of the thread LOL

---

