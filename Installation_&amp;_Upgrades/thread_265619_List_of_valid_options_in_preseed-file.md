---
title: "List of valid options in preseed-file"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by martin_d on 2006-09-26
I intend to install Ubuntu Dapper on ~10 computers (and perhaps more) unsing a network-install and a preseed-file.

I found a lot of information about preseeding a debian install, but I found only a few about ubuntu.

So, is there a complete (!) list of options you can place in the preseed-file???

Thanks, Martin D.

---

### Post by bazzer on 2006-10-26
Hi Martin
I don't think there is a definitive list, but I'm watching to see if I'm wrong. Would be quite useful!
However, you can use any Debian stuff you find, it seems all interchangeable. If you're stuck, post what you're stuck on, I might have inadvertantly got the answer, having stumbled through this over the past 2 months!

---

### Post by grahamw on 2006-11-10
Here is the latest installer documentation from Debian.

[http://d-i.alioth.debian.org/manual/en.i386/install.en.txt](http://d-i.alioth.debian.org/manual/en.i386/install.en.txt)

All of the ones that I've tried from here have worked, even if they are not in the ubuntu installer documentation included on the CD.

Hope this helps.

---

### Post by paljas on 2007-03-23
I don't get the 

d-i passwd/make-user    boolean false

line to work. The installer still asks for a user account (6.10)

---

### Post by martin_d on 2007-03-23
I am currently using kickstart, but it might be similar:

You either need to set up the root account or a user account! With no accounts set up it does not work!

---

### Post by paljas on 2007-03-23
You 're right. This seems to work:

d-i passwd/root-login boolean true
d-i     passwd/make-user        boolean false
d-i     passwd/root-password-crypted    password        !

Now I have to find a way to connect it to my ldap server. That's why I don't use kickstart, the manual says kickstart can't do that. However, the debian installer docs also don't mention ldap.

---

