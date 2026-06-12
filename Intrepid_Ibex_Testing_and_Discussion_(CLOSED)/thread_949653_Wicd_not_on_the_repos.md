---
title: "Wicd not on the repos?"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eks on 2008-10-16
Hellos,

I recently installed Ibex Beta (Xubuntu version) on an Acer Aspire One (AAO). I actually installed it because I need Wicd, and could not succeed on installing Wicd on the broken Linpus that comes pre-installed on it.

Problem is, I cannot find Wicd anywhere on the repos. Event tried adding Wicd own repo, at *deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras *(AND hardy), but cannot find it.

What am I doing wrong? I don't want to install it manually because it asks for changes on the message dbus, etc...


eks

---

### Post by smartboyathome on 2008-10-16
After adding the repository, you need to refresh your repository cache (sudo apt-get update or reload in Synaptic). Then you should see it.

---

### Post by linomac on 2008-10-16
wicd at hardy repository works also for intrepid?
thanks

---

