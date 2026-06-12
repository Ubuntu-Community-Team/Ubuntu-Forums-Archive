---
title: "How do I manually install banshee 2.3.5"
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by ScottG89 on 2012-02-16
Hey guys, I have been using linux for over a year now, but I never had to install a tar file. I went to download banshee 2.3.5 today and it is a .tar.xf file. I was wondering if anyone could tell me the commands to install this file. Thank you in advance.

- Scott

---

### Post by winh8r on 2012-02-16
You can just open a terminal and type

```
sudo apt-get install banshee
```

and it will all be done for you.

Or do you want to do it manually?

---

### Post by ScottG89 on 2012-02-16
That only gets me version 2.2. This is version 2.3.5 on their site. I was trying to get that one, so I assume I have to do it manually

---

### Post by winh8r on 2012-02-16
Ok, this should work for you then.


manual method

move downloaded tar archive to home directory

open a terminal

```
tar -xf banshee-2.3.5.tar.xz
```

```
cd banshee-2.3.5
```

```
./configure
```

this will run a check to ensure that any dependencies are met
and prompt you to install or upgrade if anything is required.

```
make
```


```
make install
```

---

### Post by oldos2er on 2012-02-16
[http://banshee.fm/download/development/](http://banshee.fm/download/development/)

---

### Post by ScottG89 on 2012-02-17
I tried following the directions above but when I ran make or make install. I get make: *** No rule to make target `install'.  Stop.
or make: *** No targets specified and no makefile found.  Stop.

I went to the referred source and followed their directions, but when I got to the final step (make or make install or make run). I still get no target errors.

---

### Post by tomsn2 on 2012-02-17
I don't think it has released for Ubuntu.  Here is a link to the site for unstable beta releases.  

[https://launchpad.net/~banshee-team/+archive/banshee-unstable](https://launchpad.net/~banshee-team/+archive/banshee-unstable)

---

### Post by oldos2er on 2012-02-17
> **ScottG89 said:**
> I tried following the directions above but when I ran make or make install. I get make: *** No rule to make target `install'.  Stop.

"make" won't run unless ./configure completes successfully, so I'm assuming it hasn't. We'd need to see the terminal output from ./configure to know what's going on.

---

