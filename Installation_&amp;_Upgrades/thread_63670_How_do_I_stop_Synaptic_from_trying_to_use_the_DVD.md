---
title: "How do I stop Synaptic from trying to use the DVD?"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by Blueshell on 2005-09-08
I've very recently installed Hoary, having used other Debians but not Ubuntu.  I did it by burning a combined live/install DVD and installing from that.

Unfortunately, now whenever I try to use Synaptic to install other packages, it often asks me to reinsert the DVD instead of just going to the net to grab the package.  While I understand that this can save bandwidth, it's a -major- irritation, because (a) now I need to keep the DVD (and not give it away!) or some random installation might wedge on me, and (b) if I happen to have done an installation and forget that I've left the DVD in there, a reboot will boot the installer again and not my installation!  (And since I'm on a fast connection, almost -any- request for media is far slower than hitting the net, since it involves finding a disk, getting to the physical machine, loading the media, etc etc.)

Surely there's some easy way of telling Synaptic to forget about the DVD sources of its packages, yes?  Or at least for those that haven't yet been installed?  If I'd known -this- would be the default behavior, I'd have installed from CD, which has many fewer packages on it, and thus had it ask for media far less often when installing new ones...

(I've tried searching for this info, but it's not at all obvious what search terms to use; the obvious ones find all sorts of irrelevant hits about installation in general; seems this should be prominently mentioned -somewhere-, like in the installation instructions or during installation or in a FAQ somewhere...)

Thanks!

---

### Post by wellery on 2005-09-08
put a comment at the start of the first line of the sources file.

Open up the terminal by going to

application->systemtools->Terminal

First type:

```
sudo vim /etc/apt/sources.list
``` 

Then put "#" at the start of the first line like this:

```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
``` 

and then type 

```
:wq
```  which means save (w) and (q) quit.

Then type:

```
sudo apt-get update
``` 

which will update all the packages with the new change that you made to the sources file (in other words it won't use the dvd/cd anymore).

---

### Post by Blueshell on 2005-09-08
Oh duh.  I'd already edited that file to enable universe & multiverse, but overlooked the very first line, repeatedly, 'cause it was separated from the rest and at first glance looked more like a version string.  But having actually -read- it this time...

Thanks!

---

### Post by manicka on 2005-09-08
or you could use gedit

sudo gedit /etc/apt/sources.list

comment out the line mentioned above.

Save and exit

sudo apt-get update

---

### Post by bob1082 on 2005-09-12
or you could go to synaptic

Settings>Repositories

and uncheck the CD 

but that would be the GUI way

---

