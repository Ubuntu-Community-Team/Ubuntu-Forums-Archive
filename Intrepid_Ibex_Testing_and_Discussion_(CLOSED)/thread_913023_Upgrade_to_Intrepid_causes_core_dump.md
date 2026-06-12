---
title: "Upgrade to Intrepid causes core dump"
date: 2008-09-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ubuntubrian on 2008-09-07
I upgraded my old Lombard to Intrepid. I couldn't use Update-Manager so I edited my sources.list and did and apt-get update, apt-get upgrade which ran fine.
I rebooted and everything seemed fine and there were a few funny kinks but they seemed to resolve. I logged out and in and again the desktop appeared and looked normal. However, almost all gnome apps crash with "illegal instruction (core dumped)". I can only see this if I run them in a KDE terminal as gnome-terminal crashes too. So no gedit, terminal, thunderbird, firefox, synaptic, update-manager. All the KDE apps run fine.
Any ideas of what to look for?

Thanks

---

### Post by entangled on 2008-09-07
I installed Intrepid Alpha5 yesterday, in a new partition, not an upgrade like you. I did have a gvfs crash almost immediately but I responded to the upgrade manager prompt for 105 package downloads (including several gvfs packages) and after this it seems stable. You may need to do the 105 downloads too?

---

### Post by ubuntubrian on 2008-09-07
I can't run update manager for the same reason. I ran apt-get and aptitude upgrades and a bunch of packages were removed and installed but I still get the same error if I try to start most gnome apps. I'll run dmesg and see what it shows.

---

### Post by cyberdork33 on 2008-09-07
did you also 'sudo apt-get dist-upgrade'?

---

### Post by ubuntubrian on 2008-09-07
Yes I did apt-get dist-upgrade. Also using aptitude update and upgrade and dist-upgrade. I can run kpackage and I ran smart upgrade. No luck with any of them. Thanks for the replies!

---

### Post by sh2008seo on 2008-09-08
[**world of warcraft cd key**](http://www.tgacn.com/wow-cd-key.php)[**buy wow gold**](http://www.tgacn.com/buy-wow-gold.php)[**world of warcraft gold**](http://www.tgacn.com/world-of-warcraft-gold.php)[**[color=white]Tcos [/color]**](http://www.tgacn.com/Tcos.php)[**[color=white]warhammer online[/color]**](http://www.tgacn.com/warhammer-online.php)Wants to get better equipment,Quicker way promotion, have more currency?I found a very very useful site to provides virtual currency, Item and power level service for players and sells Cd-key, game card for online RPG games. The lastest Recommended: EVE currency and wow cd key in store..The more info [www.tgacn.com](www.tgacn.com)    A very good place...

---

### Post by ubuntubrian on 2008-09-09
Any ideas? Help? Please?
Thanks

---

### Post by inportb on 2008-09-09
Hm... what you just did is generally considered dangerous. It's always been advised that upgraders use the upgrade manager...

---

### Post by cyberdork33 on 2008-09-09
> **inportb said:**
> Hm... what you just did is generally considered dangerous. It's always been advised that upgraders use the upgrade manager...

?
OK... It is really pretty much the same thing. There is no Upgrade Manager on Server and CLI installs... What are you supposed to do there?

ubuntubrian, since you are on PPC, Intrepid development for your Arch is probably lagging behind. This means it is likely not very stable at the moment. What you are describing really just sounds like very early alpha releases to me.

---

### Post by ubuntubrian on 2008-09-09
Well, I can live with that and wait. Would I just keep doing the updates and uprades until stable? It's an extra laptop so no pain. I do like what I see so far though of intrepid. 
Also, I had tried a clean install from the alternate cd but the install failed and as I said Update Manager wouldn't run the upgrade. I have upgraded before, though not recently, by editing my sources.list so that was my last choice.
Thanks for the replies!:popcorn:

---

### Post by cyberdork33 on 2008-09-09
> **ubuntubrian said:**
> Would I just keep doing the updates and uprades until stable?
That should work for the most part, though I have had my share of 'successful' upgrades that worked OK, but certain issues were not really issues for everyone else after awhile. I would continue with trying the releases every so often. Nothing to lose!

---

### Post by pxwpxw on 2008-09-10
Kernel is well behind for ppc binaries - on g5 here

 2.6.25-1-powerpc64-smp #1 SMP Fri May 30 16:31:36 UTC 2008 ppc64 GNU/Linux

ii  xubuntu-deskto 2.67           Xubuntu desktop system

admax@ice:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu intrepid (development branch)
Release:	8.10
Codename:	intrepid
admax@ice:~$ 

Had to kill thunar filemanager, but otherwise usable, using it now, occasional crashes. Not doing any updates for now.

Wait and see.

---

### Post by ubuntubrian on 2008-09-15
I get 

```
uname-r
2.6.24-19 powerpc
```
Pretty damn old kernel for intrepid! May be the source of my problem?

Just upgrading away.

---

### Post by cyberdork33 on 2008-09-15
> **ubuntubrian said:**
> I get 

```
uname-r
2.6.24-19 powerpc
```Pretty damn old kernel for intrepid! May be the source of my problem?

Just upgrading away.
yep. x86/x64 is on 2.6.27

---

