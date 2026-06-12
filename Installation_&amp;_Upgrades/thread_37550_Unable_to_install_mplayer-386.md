---
title: "Unable to install mplayer-386"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by franziski on 2005-05-27
I followed instructions that I found on ubuntuguide.org, but when I try to install mplayer-386 I got the following apt error:

```

frank@ubuntu:~$ sudo apt-get -t hoary install mplayer-386

I seguenti pacchetti hanno dipendenze non soddisfatte:
mplayer-386: Dipende: libavcodeccvs (>= 2:20050417-0.0) ma non sta per essere installato
Dipende: libc6 (>= 2.3.2.ds1-21) ma 2.3.2.ds1-20ubuntu13 sta per essere installato
Dipende: libfontconfig1 (>= 2.3.0) ma 2.2.3-4ubuntu7 sta per essere installato
Dipende: libpostproc0 (>= 2:20050417-0.0) ma non sta per essere installato
Dipende: libvorbis0a (>= 1.1.0) ma 1.0.1-1 sta per essere installato
Dipende: libxvidcore4 (>= 1:1.0.0-0.0) ma non sta per essere installato
Dipende: xmms (>= 1.2.10+cvs20050209) ma 1.2.10-2ubuntu1 sta per essere installato
E: Pacchetto non integro
```

Thanks!

---

### Post by netrattler on 2005-05-27
You need to add multiverse to your /etc/apt/sources.list file.
1. add this without the quotes "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse"

2.  sudo apt-get update
3. Then follow the instructions in the ubuntuguide and it should now install.

Joe

---

### Post by franziski on 2005-05-28
[QUOTE=netrattler]You need to add multiverse to your /etc/apt/sources.list file.
1. add this without the quotes "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse"

2.  sudo apt-get update
3. Then follow the instructions in the ubuntuguide and it should now install.

Joe[/QUOTE]



Please I would to learn more about these terms (universe, multiverse etc), what they means, how it works so where I can find more information about it?

Many Thanks!

---

### Post by franziski on 2005-05-28
[QUOTE=netrattler]
2.  sudo apt-get update
3. Then follow the instructions in the ubuntuguide and it should now install.
Joe[/QUOTE]

Still not Work  ](*,)

---

### Post by franziski on 2005-05-28
[QUOTE=franziski]Still not Work  ](*,)[/QUOTE]

I commented marillat repository in sources.list and all seems to work fine!!!!

---

### Post by franziski on 2005-05-28
[QUOTE=franziski]I commented marillat repository in sources.list and all seems to work fine!!!![/QUOTE]

...nope....nothing to do with firexof plugin  [-o<

---

### Post by netrattler on 2005-05-28
Here is a useful link on knowing what programs are included and where.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Joe

---

