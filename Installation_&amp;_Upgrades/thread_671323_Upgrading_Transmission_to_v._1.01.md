---
title: "Upgrading Transmission to v. 1.01"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by orange2k on 2008-01-18
Today Ive noticed an upgrad for the Bittorrent program Transmission. I dowloaded the upgrade but when I looked in the about window it still says 0.93.
Then I looked it up in Synaptic package manager and when I clicked on "upgrade" it said it needed Transmission-common which is a non-installable dependency...

Does anybody use Transmission and has anybody got a clue what to do now, because I would really like to see if the new version (especially if its a 1.01 version) brings any improvement?

edit: I also use Deluge, which is great, but I like to have many many alternatives...

---

### Post by zvacet on 2008-01-18
Download source and compile it.It is very simple.You have instructions on Transmission site. If you don´t want to do that go [here](http://www.getdeb.net/search.php?keywords=transmission) and download deb.You can even put Getdeb as repo in your source list 

```
gsudo gedit /etc/apt/sources.list
```

add this

deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/

Save and close file.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by orange2k on 2008-01-19
Thanks...
I`m gonna try the "compile-it-yourself" way, because there is only a 32-bit .deb, and I want it 64-bit...:)

---

### Post by zvacet on 2008-01-19
I´m glad you decide to compile.Just want to tell you that you can find 32 and 64 versions on Getdeb.You missed line wich goes like this (now I will translate to english so be carefull):**You are browsing programs for Ubuntu Gutsy (32 bits),you can choose other version.**

---

### Post by orange2k on 2008-01-19
> **zvacet said:**
>  (now I will translate to english so be carefull)

I did it already and I must say its a nice feeling to have something compiled. Ive compiled the PS2 emulator before and it works perfectly. So does Transmission, but I still can`t tweak it to get the speed of Deluge...:(

The line in the bracket I like much very. BTW what is the original language? - you don`t have to automatically assume that people speak only english and FYI there is always babelfish...:)

---

### Post by zvacet on 2008-01-19
Sorry to hear that,because after trying many clients I find Transmission better than most.And it is Croatian (language I mean).

---

