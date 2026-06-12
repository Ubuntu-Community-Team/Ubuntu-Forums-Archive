---
title: "Is alternate install required to encrpt hd?"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by walter_j on 2010-02-10
I installed ubuntu 64 bit on a new laptop (Thinkpad X301 -Sweet!) but decided the entire disk should be encrypted. Do I have to reinstall using the alternate install cd to encrypt the disk? I already installed all updates, so hate to have to redo it all.

Walter

I bit the bullet and reinstalled. Tried to read the help files re encryption, but i didn't want to attempt anything in it. Looked way too hard.

---

### Post by bambii7 on 2010-02-11
Sorry to tack on to the bottom of your thread. But whats the alternate install for? I downloaded it and attempted to write it to disk twice and was wondering why it wouldn't boot.... LOL noob first attempts at linux

---

### Post by Sef on 2010-02-11
> Sorry to tack on to the bottom of your thread. But whats the alternate  install for? I downloaded it and attempted to write it to disk twice and  was wondering why it wouldn't boot.... LOL noob first attempts at linux

1) It is a way of installing without a live cd.

2) There are more packages on the disk since the gui (graphical user interface) - the click and point desktop - is not installed on the cd.

3) It would not boot most likely due to bad download (md5sum to check), burn to fast (burn at 4x or less) or a bad disk.   Instead of installing go down to 'check disk for errors' (or something similar.)

4) We have all had those noob attempts.

---

### Post by bambii7 on 2010-02-11
Thanks sef,
I torrent downloaded the alternate one. First attempt wrote the whole iso to disk. Second and third turned out the same, with all the folders sprawled out, but no icon or auto run action. I direct downloaded the desktop one, wrote image, and it works! Now my CD tray is stuffed on the laptop I intended to install it on hahahaha

---

### Post by bambii7 on 2010-02-11
Alright, just wanted to say thanks again. And go Unetboot, for an alternative to the bung CD drive (I think it just needs cleaning)

---

### Post by Richard1979 on 2010-02-11
> **bambii7 said:**
> Alright, just wanted to say thanks again. And go Unetboot, for an alternative to the bung CD drive (I think it just needs cleaning)

Try Truecrypt, it can encrypt the full disk even when running on the OS in question:
[http://www.truecrypt.org/](http://www.truecrypt.org/)

You can probably find it with apt-get.
EDIT: You can't, but they provide Ubuntu .deb installers. Yay. :)

---

