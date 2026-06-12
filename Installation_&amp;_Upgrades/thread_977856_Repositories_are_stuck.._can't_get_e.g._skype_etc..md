---
title: "Repositories are stuck.. can't get e.g. skype etc. installed at all"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by arcticmagnolia on 2008-11-10
I previously had Ubuntustudio 7.04 & decided to install Ubuntustudio 8.1. The first problem I encountered was the network settings: Installation cd autoconfigured them & my Internet did not work because I live in a place where we have to use static ip (& other settings). So the FIRST problem was that I COULDN'T find anywhere in Ubuntu 8.1. to change those settings! Unbelievable.. :shock: Only place with any connection to network settings was System -> Administration -> Networking Tools but I couldn't get them changed there.

Well, I re-installed the whole thing and manually, during installation, put the ip-addresses etc. It worked. I got Firefox running & I was so relieved.
But...

**The Problem:**
I would like to install software like skype, xmms ... etc. but they won't get installed because my computer can't connect to repositories. If I apt-get skype all I get is something like this:
*Error -address of the repository- can't fetch the package: 80 (0.0.31.144). -connect (22 erranous argument) *
I must apologize I can't put the exact text here, 'cos my Ubuntu's language is set to Finnish. 

At first, with the installation of 8.1. I couldn't get Synaptic to load any web repositories but then I realized that I had to add a proxy (my Internet connection needs a proxy to work, this setting is actually already defined in system settings so I didn't realize that I had to set it again in Synaptic) to Synaptic Settings. Now I've got like one repository that works (don't know which -I have installed trillion repositories to my repositories-list) but it's of no help since I can get any software installed with it.

Can anyone help me? I'm getting desperate.](*,) I'm actually thinking seriously to move back to version 7.04 because at least a) it worked and b) you can change Internet settings with ease with it. Help!

---

### Post by arcticmagnolia on 2008-11-10
I got it figured out! The problem was with AptProxy.
This helped:
sudo gedit /etc/apt/apt.conf

and I changed this...
**Acquire::http::Proxy "address";**
to this:
**Acquire::Proxy "address";**
(and last thing I did: sudo apt-get update) 

So far so good... :)! Things seem to be working now!

---

