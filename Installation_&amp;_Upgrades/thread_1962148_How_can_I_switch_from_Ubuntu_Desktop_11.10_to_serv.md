---
title: "How can I switch from Ubuntu Desktop 11.10 to server of same"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by akshankumar on 2012-04-20
I want to upgrade ubuntu desktop 11.10 to server with same, what is the process without the cd method involvement

---

### Post by jadtech on 2012-04-20
could always down load the server(s) and parts you want to go with it from the software center..

---

### Post by mastablasta on 2012-04-20
just install the packages you want. what kind of server are you trying to make?

you can use tasksel to install various server packages.

---

### Post by dharmavir on 2012-04-22
Basically desktop version comes with pre-installed packages which can be useful as a desktop user and it is recommended to install server os as a clean install rather than installing required server packages if you're going to use it completely as a server.

If you just want to install some of server packages and you still want that system to be used as desktop machine for development you can try something like below to install your required server packages:

for e.g. to install wampserver do following:
```
  $ sudo tasksel install wamp-server 
```

---

