---
title: "saving repositories on a dvd"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by kjmdigitalwerx on 2008-02-25
First of all, I have left the darkseid forever..Thank you Linux !
Question, I have a friend whos laptop id wish to convert to Ubuntu 7.10.
Currently she has phone line service. Is there anyway that I can download all repositories and updates to a dvd(s), and load it onto her machine?
I`m sure it would take her forever using a phone line connection.
Whats a newbie to do?

Thank you in advance for your responses.
Kevin

P.S    Please include the steps for the downloading and installation from disc to her package manager.

---

### Post by logos34 on 2008-02-25
"all repositories"...that's quite a bit!  But a good start would be to get the gutsy install **dvd**--it has a lot more packages than the cd.  (unless of course she doesn't have a dvd drive)

As for the updates you could start by copying your own (assuming you run 7.10 also) to disc using **[AptOnCD]("http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html")**, then transferring it to her computer (stored in /var/cache/apt/archives).  For the rest, open synaptic on her machine, select remaining available updates and then File>Generate package download script.  Copy the file to your machine and use it to fetch the updates.

There may be an easier method, but that's one way at least.

---

### Post by zvacet on 2008-02-26
[nonetdebs](http://www.nonetdebs.homeip.net/)

---

### Post by mrpixels0 on 2008-02-26
Or you could do this in a shorter time :), just  follow the link there. 

[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=distrowatch]("http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=distrowatch")

takes about 48 hours and shipping is free only $29.00 and you can make a custom repo or copy them verbatim.

Just a thought.

MP0

---

### Post by kellemes on 2008-02-26
Another thought..
[APTonCD]("http://aptoncd.sourceforge.net/index.html")

---

### Post by zvacet on 2008-02-26
@ **mrpixels0**

No need to buy them.You can download repos from [here.](ftp://tuma.ui.edu/pub/ubuntu-repository/gutsy/)

---

### Post by logos34 on 2008-02-26
> **zvacet said:**
> [nonetdebs](http://www.nonetdebs.homeip.net/)

I thought I was forgetting something.  I came across that once before but apparently never bookmarked it.  

kjmdigitalwerx,

Try nonetdebs first.  That sounds like the easiest way.

---

