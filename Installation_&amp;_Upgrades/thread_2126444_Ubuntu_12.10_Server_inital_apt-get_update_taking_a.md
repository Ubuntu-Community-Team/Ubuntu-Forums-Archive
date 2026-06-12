---
title: "Ubuntu 12.10 Server inital apt-get update taking a very long time"
date: 2013-03-17
forum: Installation &amp; Upgrades
---

### Post by amosjackson on 2013-03-17
I am using a clean install of Ubuntu 12.10 server and when I run the sudo apt-get update command, it gets stuck after a few get requests on this: ```
100% [waiting for headers] [waiting for headers]
```. I left it overnight and when I returned, it had finished but many of the packages had failed connections or 404s. I then changed the sources.list to this (thinking it might be a mirror problem):
```
###### Ubuntu Main Repos
deb http://uk.archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse 


###### Ubuntu Update Repos
deb http://uk.archive.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse 
deb http://uk.archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse 

```
When I updated, the exact same thing happened. I have tried using other mirrors as well but they all give similar results. Also, when I try to install using apt-get, it either says "unable to locate package (whatever the name is)" or "Package (whatever the name is) has no installation candidate"

---

### Post by sanderj on 2013-03-17
I think it would help if you would post the exact output of update command. 

And: "failed connections or 404s" looks like a plain connection problem. Might be remote (ie on the server), or on your local system. So: on what kind of LAN are you?

What's your output of:

```
time wget [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/)

time curl [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/)
```

HTH

---

### Post by amosjackson on 2013-03-17
I'm running Ubuntu server and because I can't update, I can't install an ssh server. How should I copy my outputs?

---

### Post by sanderj on 2013-03-17
> **amosjackson said:**
> I'm running Ubuntu server and because I can't update, I can't install an ssh server. How should I copy my outputs?

I can also give you different advices on that, but the shortest advice: use your phone or camera to make a picture of your screen, and post it ...

---

### Post by amosjackson on 2013-03-17
When I entered the commands, it got stuck both times: 

[IMG]http://i.imgur.com/GYIe3qm.jpg[/IMG]

AND

[IMG]http://i.imgur.com/4RwHDyV.jpg[/IMG]

---

### Post by amosjackson on 2013-03-17
I'm not sure if it matters but the server is behind two routers

---

### Post by sanderj on 2013-03-17
It looks like you have a network problem. I'll repeat my question: So: on what kind of LAN are you? Home-LAN? Corporate LAN?

Why are you behind two routers?

What is the output of

```

mtr -nrc2 8.8.8.8

time wget www.google.com

```

---

### Post by amosjackson on 2013-03-17
I'm on a home LAN. I'm behind two routers because the second router acts as an ethernet switch (also I need a second wifi network). But I tried it without the second router and it made no difference.
The results of those commands were:

[IMG]http://i.imgur.com/0c9n1MH.jpg[/IMG]

and

[IMG]http://i.imgur.com/NKiQUR7.jpg[/IMG]

---

### Post by sanderj on 2013-03-17
Your network looks OK. The uk.archive.ubuntu.com does connect, but you get no respsonse. Strange.

What is the output of:

```
time wget [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) 
time wget [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) 
time wget [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/)
```

---

### Post by amosjackson on 2013-03-17
All of those got stuck after "HTTP request sent, awaiting response..."

---

### Post by sanderj on 2013-03-17
> **amosjackson said:**
> All of those got stuck after "HTTP request sent, awaiting response..."

... and [www.google.com](www.google.com) went OK. Weird.

I'll now leave to you to narrow it down what is going between [www.google.com](www.google.com) versus the archive.ubuntu.com sites. Try different URLs, and see what happens. Remove one (or two?) of the routers. Connector your computer to another LAN and see if it works. In other words: explore & narrow it down. 

With that info, I can help you further

---

### Post by amosjackson on 2013-03-17
Something weird: mirrors that timeout on the server load perfectly fine on other computers on the same network (and router)

---

### Post by sanderj on 2013-03-17
> **amosjackson said:**
> Something weird: mirrors that timeout on the server load perfectly fine on other computers on the same network (and router)

And what if you live-boot Ubuntu from a CD/USB-stick in the server hardware?

---

### Post by amosjackson on 2013-03-17
I forgot to tell you that I also have a raspberry pi webserver on the same router as this one. The router forwards port 80 to it. Also, live-booting made no difference

---

### Post by amosjackson on 2013-03-17
Oh, and one more thing: I can ping 'uk.archive.ubuntu.com' perfectly well but curl and wget time out.

---

### Post by amosjackson on 2013-03-18
Everything finally works!!! All I had to do was reduce the mtu from 1500 to 1412. Thanks for all your help, anyway.

---

### Post by sanderj on 2013-03-18
> **amosjackson said:**
> Everything finally works!!! All I had to do was reduce the mtu from 1500 to 1412. Thanks for all your help, anyway.

MTU? Ouch! That was the one thing I wanted to mention but I didn't because I thought it was too unlikely and too difficult.

How can MTU be a problem? Do you use some kind of tunneling / VPN / ... ?

---

### Post by amosjackson on 2013-03-18
I really don't know. I just read on a forum somewhere that lowering your mtu might solve a problem. And no, I don't use any tunnelling.

---

### Post by sanderj on 2013-03-18
You can manually discover the MTU size with "ping -s":

```
ping -c4 -M do -s 900 nl.archive.ubuntu.com
ping -c4 -M do -s 1400 nl.archive.ubuntu.com
ping -c4 -M do -s 1500 nl.archive.ubuntu.com

```
Note: add 28 to that number to get the MTU size.

EDIT: one-liner to get the MTU:

```
$ ping -c1 -M do -s 10000 www.google.com | grep mtu | awk '{ print $NF }' | sed -e s/\)//
1500
```

HTH

---

