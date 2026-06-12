---
title: "Command to restore the original default sources.list in Gutsy"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by Kamallo on 2008-02-23
Hi everybody!

Does anyone know if there is a command (like dpkg-reconfigure or similar) to restore the original default /etc/apt/sources.list?

I've messed with it and now I would like to restore the original default (the one I had just after installation), I'm using Gustsy for AMD64.

It's ok if you post that file, but I'm quite curious about restoring it with a command, there must be somewhere this file in some package.
DPKG? APT? UBIQUITY? I tried to search but with no luck.

Thank you.

---

### Post by taurus on 2008-02-23
```

deb http://archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu gutsy universe
deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe

deb http://archive.ubuntu.com/ubuntu gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy partner 

```

p.s.  Next time, make a backup first before you start modifying anything.

---

### Post by Kamallo on 2008-02-23
Thank you for your answer.

> **taurus said:**
> 
p.s.  Next time, make a backup first before you start modifying anything.


Yes, you're right, I will do it.

Any idea about the command?

Bye :)

---

### Post by taurus on 2008-02-23
```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
```

---

### Post by Kamallo on 2008-02-23
Oh, sorry. I meant the command I was talking about in the first post...

---

### Post by wolfen69 on 2008-02-23
```
gksudo gedit /etc/apt/sources.list
```
then remove everything in the file and copy and paste the above sources list. then save and:
```
sudo apt-get update
```

---

### Post by tooferson5 on 2008-05-15
Is there a way I can use this for the Hardy repositories.  I want to restore mine to the original.  I am using Ubuntu Hardy AMD64.  Thanks.

---

