---
title: "How to modify &amp; save sources.list"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by Harris2508 on 2008-06-29
I'm new to Linux and Ubuntu. I am trying to install Slim Devices Squeezecenter into my new install of Ubuntu Desktop 8.04. The install fails with the message that the source could not be found (error 404). I have entered the string "http://debian.slimdevices.com stable main (source code" Though it seems strange to me, in reading through the forum I see notations about modifying the etc/apt/sources.list with various strings. I've tried this but am not allowed to save the edited file. 

I've tried changing my permissions so that I have "administer system" checked in my listing in users and groups. Or, I guess I could logon as "root" (?), but I cannot figure out how to do that. 

I'd really appreciate any thoughts or ideas. Thank you very much.

--Bob Harris :)

---

### Post by Pumalite on 2008-06-29
Backup first:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
Edit:
gksudo gedit /etc/apt/sources.list

---

### Post by Wobblybob on 2008-06-29
and when you edit your source list with
sudo gedit /etc/apt/sources.list
to add the slindevices repo it should inc. the deb at the begining i.e. 
deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main
then enter 
apt-get update
followed by
apt-get install squeezecenter
good luck

---

### Post by Harris2508 on 2008-06-29
Thank you very much guys; I'll give that a spin. I really appreciate your help!

--Bob

---

### Post by Gainax on 2008-09-17
> **Wobblybob said:**
> 
apt-get update
followed by
apt-get install squeezecenter
good luck

If I have an exisiting SqueezeCenter running, will the above commands simply upgrade my current SqueezeCenter version?

I'm running 7.01 and want to upgrade to 7.2 as I'm wanting to fix some issues I've had with 7.01

Thanks

---

### Post by Partyboi2 on 2008-09-17
> **Gainax said:**
> If I have an exisiting SqueezeCenter running, will the above commands simply upgrade my current SqueezeCenter version?

I'm running 7.01 and want to upgrade to 7.2 as I'm wanting to fix some issues I've had with 7.01

Thanks
```
sudo apt-get upgrade
``` will upgrade a package, unless you compile the program from source.

---

