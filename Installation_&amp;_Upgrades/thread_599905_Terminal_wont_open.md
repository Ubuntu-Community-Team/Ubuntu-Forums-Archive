---
title: "Terminal wont open"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by Fire-EnigmaX on 2007-11-01
Hi guys,

I am a complete Newbie so please bear with me (i know your prob sick of hearing that but how else do you start!!)

I have just installed xubuntu 7.10 and used it fine onmy workcomputer so I am trying to get to grips with it...

My problem however is that I have installed it (the exact same methods) on my home pc and everything seems ok apart from the fact that if I try to open up terminal my computer seems to 'sort-o' reboot and brings up the normal login screen!!

I have tried re-installing already but this has still not fixed!!

Anyone any ideas on how to fix?
I know I can prob do most things using the gui but thats not the point of learnign to use linux is it!!

Thanks in advance.

---

### Post by taurus on 2007-11-01
Can you list the spec of your machine?  Are you running Gutsy or Feisty?  Is the x86 or x86_64 version?

---

### Post by Fire-EnigmaX on 2007-11-03
Hey, is there a command that I can run to give you all the info you need?

It is an old machine and I have not used it before to know the spec!, sorry!

---

### Post by arashiko28 on 2007-11-04
Hi, I have the same problem and started to surf the posts before opening a new one. It does the same effect that yo get when pressing ctrl+alt+backspace. It restart Xconf. I installed it today, I had Xubuntu 7.04 on the same desktop and didn't had this problem. This is a Celeron (coppermine) 700mHz, 256MB RAM, using xubuntu gusty. Although is pretty old, it manages heavy work, as beryl :). 

For checking your specs go to Applications, System, System Monitor and on the system lid (sorry forgot the name in english, it's not my main language). It'll show you something similar as the properties on my pc using windows.

---

### Post by The Grim MacKay on 2007-11-04
I'd like to bump this post and say I have the same issue. 
I'm trying to preserve an old Gateway Profile - it's a PIII (Coppermine) w/128MB of memory and a 20GB hard drive. I got an apparently successful install of Xubuntu 7.10 on it, but I've been having problems with a Trendnet PCMCIA Ethernet card. In trying to bring up terminal so I could use cardctl to see what it sees, I get the same re-boot-like effect described here. 

starting anac(h)ronistic cron anachron
starting deferred execution scheduler atd 
starting periodic command scheduler crond
checking battery state....
running local boot scripts (etc/rc.local)

and then I'm back at the login screen.

I note that this issue has been outstanding in the forums for a few days. As someone new to Ubuntu support protocols, is this something that is the norm - that it can take several days to get an answer to a question? I'm not being critical - I just want to have realistic expectations...

:-k The Grim MacKay

---

### Post by arashiko28 on 2007-11-05
[COLOR="Red"]** I SOLVED THE PROBLEM!!!**[/COLOR] It is quite simple.

On Applications, System, Add/Remove... look for terminal, there are a few terminal boxes unchecked, install them, I also installed Konsole, does the same work. After I did this, I could use Terminal normally.:guitar: Hope it does the same for you, guys.:popcorn:

---

