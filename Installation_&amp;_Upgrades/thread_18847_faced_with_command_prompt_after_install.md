---
title: "faced with command prompt after install"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by barneyl on 2005-03-09
hi folks,

i'm new to *nix, and have installed ubuntu on a spare desktop.

after installation, and logging in, i'm simply faced with a command prompt.

how do i fire up the gnome ui?  should this happen by default?

many thanks,

-b

---

### Post by krusbjorn on 2005-03-09
didnt happen by default to me.

try "startx"

---

### Post by barneyl on 2005-03-09
[QUOTE=krusbjorn]didnt happen by default to me.

try "startx"[/QUOTE]
 thanks - read this in an earlier post, so tried it, but comes back with startx : command not found?!

---

### Post by JaZzY JeF on 2005-03-09
What graphics card are you running?

---

### Post by barneyl on 2005-03-09
[QUOTE=JaZzY JeF]What graphics card are you running?[/QUOTE]
 couldn't tell you off hand - it's an old Dell OptiPlex - it did run the 'live cd' ok - i can have a look if it will help

---

### Post by JaZzY JeF on 2005-03-09
[QUOTE=barneyl]couldn't tell you off hand - it's an old Dell OptiPlex - it did run the 'live cd' ok - i can have a look if it will help[/QUOTE]

I'm running a Nvidia 6800 GT and had to type in:

sudo apt-get install nvidia-glx

sudo nvidia-glx-config enable

at the command prompt.

---

### Post by krusbjorn on 2005-03-09
[QUOTE=barneyl]couldn't tell you off hand - it's an old Dell OptiPlex - it did run the 'live cd' ok - i can have a look if it will help[/QUOTE]

im quite new to linux myself, but if this happened to me, i'd update the system and see if it gets better.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

---

### Post by barneyl on 2005-03-09
thanks guys.  i'll try this, as for several of the updates after install i had a connection timed out error.

i'll let you know if that helps.

-b

---

### Post by barneyl on 2005-03-09
success!! i'm replying from firefox within the lovely gnome UI!

to resolve the problem, i simply reinstalled saying 'no' to the automatic update option.

i was having real trouble with apt-get dropping the connection.

-b

---

### Post by satlurker on 2005-03-09
I'm having the same problem with a Dell Optiplex GX110 ...

I'm going to give this a try before I give up on Ubuntu ... one question though, if you do not do the package update right awawy, will there be problems when doing an update through synaptic etc.

I want to be able to keep the system up to date once it is installed.

Thanks for you help

T

---

### Post by krusbjorn on 2005-03-09
nah, there should be no problems.

---

