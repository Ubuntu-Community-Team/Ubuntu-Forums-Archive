---
title: "Install intrepid packages in hardy with apt like in Debian way"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by erlguta on 2008-08-19
Hello.
I am new user in Ubuntu but experienced in Debian.
I need to install some packages from intrepid of a new version of erlang package (is a programing language) in my hardy.
I was used to do this things really easy in my Debian installing it from Sid in testing, enabling the sid sources in my **sources.list**, making one **/etc/apt/apt.conf** file with:

```
APT::Default-Release "lenny";
```

And doing:

```
aptitude -t sid install package
```

My question is, can i do in the same way in Ubuntu?

Because i find that is a little annoying download packages and its dependencies one by one from [http://packages.ubuntu.com](http://packages.ubuntu.com)

Thank you in advance.

---

### Post by meindian523 on 2008-08-19
Enable backports in System>>Administration>>Software Sources.Then sudo apt-get update && sudo apt-get install erlang
provided erlang has been backported,of course.

---

### Post by erlguta on 2008-08-19
I don't see erlang in hardy-backports:
[http://packages.ubuntu.com/search?suite=hardy-backports&arch=i386&searchon=names&keywords=erlang](http://packages.ubuntu.com/search?suite=hardy-backports&arch=i386&searchon=names&keywords=erlang)

It is possible to enable intrepid sources like in debian?
and install it like:
```
aptitude -t intrepid install erlang
```
:confused:

---

### Post by kakao on 2008-08-26
I'm keen to know, too. Anyone?

P.S. Seams to be very limitedly supported in Ubuntu (Hardy). See [Idea #12564]("http://brainstorm.ubuntu.com/idea/12564/") and vote or extend it.

---

