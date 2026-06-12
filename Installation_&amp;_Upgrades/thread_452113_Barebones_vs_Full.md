---
title: "Barebones vs Full"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by Clay_Banger on 2007-05-23
What are the differences from; installing the [barebones system]("http://www.psychocats.net/ubuntu/minimal#barebones") then adding all of the things you need, gui, programs or just downloading the main desktop iso and installing that?

I'm aware that it will take a lot more time setting up with the barebones install, then using the main iso.
I'm guessing that boot times would be quicker and overall, ie programs load quicker etc.
Are these correct?

Also is there any advantages/disadvantages to using barebones over full install?

---

### Post by atoponce on 2007-05-23
If you install the server iso, then you will have Apache, MySQL and PHP installed.  2 of those being services that will slow down boot time.  However, you do have the precise control of what you want installed versus Ubuntu choosing for you.  Unless you are going to use fluxbox or evilwm over Gnome, or if your system resources are limited, I would recommend just installing the main desktop iso.

---

### Post by aysiu on 2007-05-23
Barebones is good for systems without a lot of resources (little RAM, small hard drive) because you'll have only the packages you need and only the services running that you want running. The disadvantage is that you have to add everything one by one, and you may not know what package you'll need to install to fulfill a need you have (say, automounting external media, for example).

The regular Desktop CD is good for systems with a lot of resources (at least 512 MB of RAM and 20 GB of hard drive space) because it includes all the major services and software that regular users expect. The disadvantage is that it won't run on low spec systems, and it may run more services than you want to have running.

---

### Post by Clay_Banger on 2007-05-23
> **atoponce said:**
> If you install the server iso, then you will have Apache, MySQL and PHP installed.  2 of those being services that will slow down boot time.  However, you do have the precise control of what you want installed versus Ubuntu choosing for you.  Unless you are going to use fluxbox or evilwm over Gnome, or if your system resources are limited, I would recommend just installing the main desktop iso.
I was referring to this: [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")
Not the server iso.

---

### Post by atoponce on 2007-05-23
I know what you were referring to.  The minimal iso just is 10MB versus 700MB.  When starting up, you still type 'server', which to the best of my knowledge, will install the Apache and MySQL daemons.  You can remove them later, if you wish, but they'll be installed by default.  Someone correct me if I'm wrong.

---

### Post by RedSquirrel on 2007-05-24
> **Clay_Banger said:**
> What are the differences from; installing the [barebones system]("http://www.psychocats.net/ubuntu/minimal#barebones") then adding all of the things you need, gui, programs or just downloading the main desktop iso and installing that?

I'm aware that it will take a lot more time setting up with the barebones install, then using the main iso.
I'm guessing that boot times would be quicker and overall, ie programs load quicker etc.
Are these correct?

Also is there any advantages/disadvantages to using barebones over full install?

With the barebones installation, you will get a very lean system that should boot in less time. Generally speaking, the only applications installed will be the ones you choose to install. You can choose lightweight applications that will indeed load much quicker.

You'll have a number of alternatives for applications, so you might have to do some research to figure out what applications to install for specific needs. This can be done by searching ubuntuforums.org or the web in general and of course asking questions if you didn't find what you were looking for.




> **atoponce said:**
> When starting up, you still type 'server', which to the best of my knowledge, will install the Apache and MySQL daemons.  You can remove them later, if you wish, but they'll be installed by default.  Someone correct me if I'm wrong.

Installing the LAMP tools is an *option* at install time, so I don't they're installed by default.

---

