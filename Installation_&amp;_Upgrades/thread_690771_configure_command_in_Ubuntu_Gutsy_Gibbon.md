---
title: "configure command in Ubuntu Gutsy Gibbon"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by rtrdom on 2008-02-07
Downloaded xpdf-3.02.tar.gz. Did tar<xpdf-3.02.tar.gz and it extracted as xpdf-3.02.
Moved both to /etc. Doing CD /etc/xpdf-3.02  puts me in the folder of /etc/xpdf-3.02.
Doing ls yields only /etc/xpdf-3.02.  OK...trying ./configure does nothing except tell me
there's no such command.  All tar balls I've tried to use yield same result.
How can I get tar balls to install in Ubuntu Gutsy Gibbon, please?

---

### Post by taurus on 2008-02-07
What's the output of this command from a terminal?

```
ls -la /etc/xpdf-3.02
```
Any reason you "want" to build xpdf from source since it is available from the repos?

```
sudo apt-get update
sudo apt-get install xpdf
```

---

### Post by rtrdom on 2008-02-07
Thanks for the response.  The output of that command shows that permissions
are authorized, if I read it right. As for the reason,,,I tried sudo aptitude update, then
if I remember correctly I tried sudo aptitude install xpdf-3.02.  I would really like to
learn the proper way to install from tar balls and I think I know...the problem I have
right now is it seems that everytime I try to configure, it won't.  here is the output
and again, thanks.
total 16
drwxr-xr-x   2 root root  4096 2008-02-06 22:58 .
drwxr-xr-x 118 root root 12288 2008-02-07 18:18 ..
jim@Bravo:~$

---

### Post by Partyboi2 on 2008-02-07
make sure you have build-essential and gcc installed
```
sudo apt-get install build-essential gcc
```when compiling make sure you are in the directory of what you are trying to install before executing commands like ./configure
Like taurus said you can install by apt-get (with universe repo enabled under Software Sources)

---

### Post by rtrdom on 2008-02-20
Thank you for the responses. I've checked, and build essetial and gcc are already
the newest versions. For some reason when I have used tar.....command, then
cd into the new folder and type ./configure, it does nothing.  Sometimes I can get
to the make, make install but not everytime.  I guess I'll just have to pay more
attention to using tar balls.
Thanks again for the responses.

---

