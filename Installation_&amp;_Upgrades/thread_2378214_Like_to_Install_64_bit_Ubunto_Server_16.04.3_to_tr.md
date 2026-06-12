---
title: "Like to Install 64 bit Ubunto Server 16.04.3 to try it out without damaging Win7 sys"
date: 2017-11-21
forum: Installation &amp; Upgrades
---

### Post by rpasupul on 2017-11-21
What is the recommended direction to take. Are there any Virtual machines available to use ?

---

### Post by Tadaen_Sylvermane on 2017-11-22
Virtualbox. Best thing ever, I owe most of my linux education to it.

---

### Post by Bucky Ball on 2017-11-22
You are aware that the server version is just that; a server version. There is no desktop environment. Once installed, you will be looking at a CLI, like a giant terminal the full size of your monitor.

If this is not what you want, you don't want the server version. Are you wanting to do server-specific things or just curious or want a stripped back version of Ubuntu? If the latter, install [the minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD") and add a desktop environment to that and whatever else you want/need.

If you want to try out anything but the server version, then create an install disk, boot it and choose the option 'Try Ubuntu'. This takes you to a 'live' session without changing anything on the hard drive at all. You don't need to install Ubuntu, or use Virtualbox, to try it.

---

### Post by mastablasta on 2017-11-22
do it in virtualbox like this: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

if you need server that could be accessed from windows via browser you need to set bridged networking (in virtualbox network settings)

---

