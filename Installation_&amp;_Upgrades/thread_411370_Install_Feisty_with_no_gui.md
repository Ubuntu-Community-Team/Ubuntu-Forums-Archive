---
title: "Install Feisty with no gui"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by tozebr on 2007-04-16
Hi, i'm braziliam so my english isn't nicer. but...

Well, i was used to use ubuntu 6.60, and 6.10 im my pc with windows xp . But i upgraded to Feisty a while ( i think i was 1 or 2 months ago) and i have experienced problems with. 
I was trying to undestrand a little more of linux and i downloaded Debian Etch stable ( last Week) and downloaded gentoo 2006.1 . I instaled debian with a clean install in my linux partition (actualy i've / and /home on separate partition ) and i 've noticed that debian is much, but much faster than ubuntu, even with  the same software. 
I was wondering if there is a way that i can install only the default/base system without a gui, and install only gnome-core whith not all those app, that i really don use, after with aptitude.

Is there a way ?

I'm downloading Feisty Fawn Alternate cd right now.

Thank you so much
Tozé

---

### Post by NeoLithium on 2007-04-16
I think the easiest way would be use the server edition which comes with no gui at all; and you can load that way after you've modified your sources.list.  I haven't tried with the alternate CD...perhaps someone else can answer that one.

---

### Post by tozebr on 2007-04-16
Can you tell me the difference beetwen the server and de desktop conf? i mean, i read somewhere that the kernel is sighly differ from desktop to server.

i will try to install server with only the base system and try to install xorg with gnome-core

thank you

---

### Post by kerry_s on 2007-04-16
Server install is the base system, it's just command-line,no gui. It's the best starting point to make a custom install.

net installer, this can install any supported ubuntu flavor-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

> Can you tell me the difference beetwen the server and de desktop conf? i mean, i read somewhere that the kernel is sighly differ from desktop to server.

the server is just the base system until you select server parts, which you can skip(tab and enter) when it comes to that part.
Everything is the same in ubuntu, kernels, packages, everything.

---

### Post by tozebr on 2007-04-16
and is there a gnome-base system
or just the ubuntu-dekstop metapackage that install all those million of apps ?

---

### Post by kerry_s on 2007-04-16
It's just like in debian.

do server install
login
sudo su
apt-get install xorg gdm gnome-core
reboot
select session and login

You don't have to stick with gnome though, you can install anything, custom means the choice is yours.

For example, i'm a fluxbox guy, i use->

apt-get install xorg gdm fluxbox synaptic geany emelfm

Just to start, after i log in to the gui i continue getting what i want, till i end up with my custom install->

---

### Post by tozebr on 2007-04-16
thank you so much

but i think i will stay with gnome ;D

or maybe enlightment 17

---

### Post by dbqp on 2007-04-18
I too was looking to install a GUI on my Ubuntu 6.10 server at home ( I want to install VM Ware Server for additional VM Servers...and VM Ware requires GUI for their VM Ware Server edition).

My question is what is the main differences between:

```
sudo aptitude install ubuntu-desktop
```

and

```
sudo apt-get install xorg gdm gnome-core
```

????

Would this still give me the Gnome Ubuntu log-in and GUI manageability as the desktop or what exactly would I get with the second command listed above? I am assuming this becomes a "minimal" GUI install, but that would just be a shot in the dark...

Thanks in advance!

---

### Post by dbqp on 2007-04-18
Nevermind! After using the terms from my previous post I found a lot more information than I probably needed to know.

For others:

[http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core](http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core)

[http://ubuntuforums.org/showthread.php?t=304330&highlight=xorg+gdm+gnome-core](http://ubuntuforums.org/showthread.php?t=304330&highlight=xorg+gdm+gnome-core)

These two links were a wealth of information...

dbqp

---

