---
title: "Worst upgrade ever.. :S"
date: 2005-09-20
forum: Installation &amp; Upgrades
---

### Post by basttrax on 2005-09-20
Hey everyone.
So here's my little problem. 

I have a cd with Warty 4.10 on it. I wanted to upgrade to 5.04 and screwed everything up. 
I was thinking about doing another clean install of 4.10 and trying again.

Whats the best way to upgrade to 5.04 from 4.10?

Thanks alot
Basttrax

---

### Post by Xian on 2005-09-20
Is there any particular reason you don't just download the 5.04 ISO 
and install that instead of upgrading via 4.10?

---

### Post by basttrax on 2005-09-20
Normally thats what I would have done. 
My crappy "sony" dvd/cd burner crapped out on me a couple nights ago.
I still have my highspeed, and could download it, but not burn it.

basttrax

---

### Post by Gary Powers on 2005-09-20
[QUOTE=basttrax]Hey everyone.
So here's my little problem. 

I have a cd with Warty 4.10 on it. I wanted to upgrade to 5.04 and screwed everything up. 
I was thinking about doing another clean install of 4.10 and trying again.

Whats the best way to upgrade to 5.04 from 4.10?

Thanks alot
Basttrax[/QUOTE]

In Terminal, edit /etc/apt/sources.list using Gedit and change all the instances of "Warty" to "Hoary", then still in Terminal

sudo apt-get update
sudo apt-get dist-upgrade

That will get you to Hoary.

Gary

---

### Post by Xian on 2005-09-20
[QUOTE=basttrax]I wanted to upgrade to 5.04 and screwed everything up. [/QUOTE]
It might help to post the exact nature of your problem so as to try and
prevent it from occuring again.

---

### Post by basttrax on 2005-09-20
Should I somehow shut down the gui before doing the apt-get update?
So Gnome etc can update alright?

if so how do i shutdown the gui? i know to start it it's startx

thanks
basttrax

---

### Post by Xian on 2005-09-20
[QUOTE=basttrax]Should I somehow shut down the gui before doing the apt-get update?
So Gnome etc can update alright?[/QUOTE]
No, there is no need for this.
However, to shut down the GUI you hit Ctrl+Alt+F1.

---

### Post by wellery on 2005-09-20
[QUOTE=basttrax]Should I somehow shut down the gui before doing the apt-get update?
So Gnome etc can update alright?

if so how do i shutdown the gui? i know to start it it's startx

thanks
basttrax[/QUOTE]

no need. When you reboot every thing will be updated.

---

### Post by GOwin on 2005-09-20
if you want to stop the gui, from a terminal, do:

sudo /etc/init.d/gdm stop
< apt-get upgrade .... >
sudo /etc/init.d/gdm start

---

### Post by basttrax on 2005-09-20
Alrighty. It worked!

I'm now a proud user of Hoary 5.04 :)
Everything seems to be working great, did the reboot and woosh 5.04.
Thanks alot everyone,
I'll probably be back when everything falls apart later :0

Basttrax

---

