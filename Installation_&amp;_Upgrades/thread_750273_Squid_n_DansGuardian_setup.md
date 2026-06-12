---
title: "Squid n DansGuardian setup"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by links2u on 2008-04-09
Please help, I am a techie who works in a number of schools sorting windows pc problems and setting up networks etc. Having started to play with edubuntu I realise that this could be hugely beneficial to schools. 
I am currently trying to get Dans Guardian up and running to be used as a internet filter as the county filter is not very good. I understand that squid has to be installed and running fro this to happen. This is where my problems start. If I look in synaptics package manager it tells me both squid and dansguardian are installed.
From what I have read I now need to change a couple of lines in squid.conf .  I now start terminal and type " /etc/squid/squid.conf" and get command not found. 
I have tried lots of different things that I have found on the net and I can't seem to get off 1st base. Would I be better just to pay for a decent filter and install it on a windows machine?

---

### Post by Partyboi2 on 2008-04-10
[SIZE=1]You need to put gksudo gedit in front of/etc/squid/squid.conf to open the file.
gksudo is for admin privileges and gedit is a text editor.So in a terminal (Applications>Accessories>Terminal) you would type
```
gksudo gedit /etc/squid/squid.conf
```[/SIZE][SIZE=1]
Not sure what how-to you are using but [here]("https://help.ubuntu.com/community/SquidGuard") is one for using squid and [here]("https://help.ubuntu.com/community/Servers/DansGuardian") is another for setting DansGuardian up using tinyproxy instead of squid.
[/SIZE]

---

### Post by links2u on 2008-04-12
Thanks for taking the time to post. Its very much appreciated.

---

