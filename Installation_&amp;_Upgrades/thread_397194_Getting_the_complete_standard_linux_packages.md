---
title: "Getting the complete standard linux packages"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by ssiva on 2007-03-30
I have just installed the desktop release of Ubuntu and I feel like I am missing many things from a standard linux install.  This is not surprising as there was only one CD.  I see two tools available to remedy this; Synaptec Package Manager, and "Add / Remove Applications".  The problem is that I have no idea what all is needed to complete a standard install, and these tools don't seem to have a recommended list.  

Some of the tings I found missing were:
sshd
gcc
authconfig



Do I have to find these one by one and install these, or is there a way to select "all common packages" and have a big batch install done.

Thanks.

---

### Post by pradeepadapa on 2007-03-30
if u r looking for common softwares and such there is are softwares like Automatix and Easyubuntu, just install these softwares from synaptic manager or from the Add/Remove programs and then install them, open Automatix nd u can see some basic softwares which u might need,,,, and about 
ssh
gcc
authconfig

u can search in synaptic package manager nd then mark them to install them

u can also install the updates which are on the right hand corner of the desktop so that all the updated common packages will be installed.

hope this helps u

---

### Post by zvacet on 2007-03-31
If you installed you Ubuntu properly nothing is missing.packages you see that are not installed are one that you may need or not.So,if you need them you will install with synaptic.this one you will need so go to the terminal(programs>accessories>terminal) and type
```
sudo aptitude install build-essential
```

You can also instal** alien** with synaptic.

---

### Post by compiledkernel on 2007-03-31
Automatix is unsupported software by the community. These forums do not support it either. If you have difficulties with Automatix, you should refer back to their forums at [www.getautomatix.com](www.getautomatix.com) for further help.

Let me firmly reiterate that Automatix is just as it is --

"automatix is a script that tries to install some software, and often
fails and breaks systems. We don't provide support for it, and we strongly
discourage its use. Problems caused by Automatix are often hard to track
and solve, and it might sometimes be easier to !install a fresh copy of
Ubuntu."

That be said, result to other forms of documentation to find what you need. 

[http://wiki.ubuntu.com](http://wiki.ubuntu.com)
[http://doc.gwos.org](http://doc.gwos.org)

---

