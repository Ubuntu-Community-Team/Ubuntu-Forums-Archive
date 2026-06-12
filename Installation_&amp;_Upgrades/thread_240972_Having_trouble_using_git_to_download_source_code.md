---
title: "Having trouble using git to download source code"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by shousonhill on 2006-08-21
this is my first
attempt using a version control system. I am working off the "Sugar
on Ubuntu Linux" guide on the OLPCWiki
[http://wiki.laptop.org/go/Sugar_on_Ubuntu_Linux](http://wiki.laptop.org/go/Sugar_on_Ubuntu_Linux)

I have loaded all of the prerequisite packages. When I run
sudo git clone git://dev.laptop.org/sugar-jhbuild

I get the following message "git is not called gitfm"
Press Return to run gitfm

I hit return and then I get

gitfm: fatal error: 'chdir' failed: permission denied

Atfirst I thought I might have an access problem on the remote site. I have since tried to creat a repository from scratch

when I run

sudo gitfm init-db

I get the same error. I figure there is something wrong w/ my git installation. Any ideas? thanks
Edit/Delete Message

---

### Post by shousonhill on 2006-08-21
Figured it out myself

sudo update-alternatives --config git
choose #2: git-scm

Ran this earlier but chose choice #1, whatever that was

---

### Post by exidez on 2007-04-29
thanks
that solved my problem too

---

### Post by Duxus on 2007-09-21
Yes. Helped me too.

---

