---
title: "Ubuntu Server Questions"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by nigel on 2006-06-05
Hi all

I am having trouble getting info on exactly what the 6.06 server install contains
eg version of php, mysql etc

also is there a specific forum i should visit for server related queries

Basically what I want is a server on my network that i am able to test a few sites on before putting them out in the real world, if i want to have more than one site, would i need more than one network card? as in one card per site?

Cheers

---

### Post by leetcharmer on 2006-06-05
no, you won't need more than one NIC.  All the websites will point to the same host (IP address) -- just, different locations on the server.

---

### Post by nigel on 2006-06-06
Ok thanks for that

Is there somewhere that lists the specs of the server though as i can't seem to find it anywhere

---

### Post by ubnoobie on 2006-06-06
[QUOTE=nigel]Ok thanks for that

Is there somewhere that lists the specs of the server though as i can't seem to find it anywhere[/QUOTE]

the "server edition" iso has two installation options, 'install' and 'install a lamp server'. the 'install' in this case is a bare (console) ubuntu-standard install; and lamp adds apache2 (2.0.55 prefork), php (5.1.2) and mysql (5.0.21). apache, php & mysql are basic installs with no extras. you also get a server-optimised kernel out-of-the-box. other server-oriented packages are on the cd, but not installed by default, including bind, exim4, php modules, postgre, mod-perl, mod-python, etc... (see [http://ubuntu.pastebin.com/763394](http://ubuntu.pastebin.com/763394) for server iso contents)

most server administrators would opt for the bare install and then installing the packages they require.

if you already have an 'alternate' iso, there's no real need to download the server iso as well: you can do a 'server' install off a x/k/ubuntu alternate iso to get a bare (console) installation (not to be confused with the server iso, as this method won't net you the server-optimised kernel); and then use aptitude to install the desired packages (including the server kernel, if desired).

---

### Post by nigel on 2006-06-06
Thanks that answers a pile of questions, i like the idea of the one click install, the last time i did a server install it took all day, and i managed to completelyscrew it up the next day

The other thing i meant to ask is

What are the hardware requirements, i am assuming they will be a heck of a lot less without all the desktop stuff, will this run OK on an old 300Mhz machine

Cheers

---

### Post by adamkane on 2006-06-07
It depends on the amount of traffic you experience. You are fine for a personal server, or if you only have a couple users at a time.

---

### Post by nigel on 2006-06-07
No this will just be a home based test machine (we have low speed Capped broadband here)

Thanks for all the help people

---

