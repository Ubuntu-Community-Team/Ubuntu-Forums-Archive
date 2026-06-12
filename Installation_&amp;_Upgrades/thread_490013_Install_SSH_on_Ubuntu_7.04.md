---
title: "Install SSH on Ubuntu 7.04"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by textguru on 2007-07-02
I am previously using Ubuntu 6.06 and now evaluating the new version. I am trying to install SSH thru this:
> sudo apt-get install ssh openssh-server

It seems its not working:

> Package ssh is not available.... E: Package ssh has no installation candidate

According to [http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server) , I need the following line:

> sudo apt-get install ssh
And got the same result. Any help?

---

### Post by oldmanstan on 2007-07-02
try this:
```
sudo apt-get install openssh-client openssh-server
```
unless you're having others connect to your machine you dont need the server part though...

---

### Post by VorDesigns on 2007-07-02
I believe it is 
```
sudo apt-get openssh
```

---

### Post by textguru on 2007-07-02
> **VorDesigns said:**
> I believe it is 
```
sudo apt-get openssh
```


probably you are pertaining to sudo apt-get install openssh? but it seems it didnt work also

---

### Post by textguru on 2007-07-02
> **oldmanstan said:**
> try this:
```
sudo apt-get install openssh-client openssh-server
```unless you're having others connect to your machine you dont need the server part though...

Same thing, no installation candidate for openssh-server and openssh-client is already installed.

---

### Post by oldmanstan on 2007-07-02
> **textguru said:**
> Same thing, no installation candidate for openssh-server and openssh-client is already installed.

what exactly are you attempting to do? because if you just need to connect to other computers then the client is all you need...

EDIT: in synaptic search for "openssh" and see if both client and server show up, server might be in a different repo that you don't have enabled... i'm not sure but that would possibly cause the error you're seeing...

---

### Post by textguru on 2007-07-02
> **oldmanstan said:**
> what exactly are you attempting to do? because if you just need to connect to other computers then the client is all you need...

EDIT: in synaptic search for "openssh" and see if both client and server show up, server might be in a different repo that you don't have enabled... i'm not sure but that would possibly cause the error you're seeing...
I want my computer to be accessed remotely. Actually I am building us a server that can be accessed thru ssh (which I am previously doing on ubuntu 6.06).

---

### Post by Bachstelze on 2007-07-02
*openssh-server* is what you need, then. *openssh-client* is installed by default.

---

### Post by textguru on 2007-07-02
> **HymnToLife said:**
> *openssh-server* is what you need, then. *openssh-client* is installed by default.
how? if I will run:

> sudo apt-get install openssh-server

It tells me that no installation candidate....

how to install openssh-server?

---

### Post by oldmanstan on 2007-07-02
what repositories do you have installed?

---

### Post by textguru on 2007-07-02
> **oldmanstan said:**
> what repositories do you have installed? I do not change the default repository list (sources.lst). is it not included on the cd?

---

### Post by oldmanstan on 2007-07-02
as i said before, go into synaptic (it can be your friend) and search for "openssh", if the server package comes up, try to install it from there, see what happens, if not then that tells you that you don't have the proper repository enabled, from what i can tell it should be there but check just to be sure...

---

### Post by bigken on 2007-07-02
[this]("http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html") might help

---

### Post by textguru on 2007-07-02
> sudo apt-get install ssh openssh-server

this works on Ubuntu Server 7.04! I will use this instead of the desktop edition. thanks guys! :KS

---

### Post by mtbosworth on 2007-07-13
I have this same problem as was originally stated on this thread.  There is no installation candidate.  Are you saying that you need to have ubuntu server edition to install ssh?  Shouldn't there be a way to install ssh server on the desktop edition?

---

### Post by Pumalite on 2007-07-13
Absolutely not. You can use ssh in Ubuntu Desktop. I do it all the time in my home LAN. If you have a firewall somewhere; open port 22

---

### Post by mtbosworth on 2007-07-13
I can work out the configuration and networking issues.  I just can't install the server.  Is there a source I can add to my repository list in order the apt-get install openssh-server command to work?

---

### Post by textguru on 2007-07-14
Problem just solve! try to update your repository list

> sudo apt-get update

and try to install ssh server again

> sudo apt-get install ssh openssh-server

It might work afterwards.

:KS

---

### Post by mtbosworth on 2007-07-14
Thanks.  That's all I needed to do.

---

### Post by textguru on 2007-07-15
> **mtbosworth said:**
> Thanks.  That's all I needed to do.
Im glad it helps you.

---

