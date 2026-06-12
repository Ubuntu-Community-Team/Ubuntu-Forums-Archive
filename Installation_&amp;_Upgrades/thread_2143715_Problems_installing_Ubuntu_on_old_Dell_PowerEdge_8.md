---
title: "Problems installing Ubuntu on old Dell PowerEdge 800"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by agentjwall on 2013-05-09
Hello,
I'm trying to install Ubuntu (64-bit) on an old Dell PowerEdge 800 Server and I'm running into problems. The server only has a CD-Drive (Not DVD) and doesn't seem to support USB-Booting (As far as I can tell). Ubuntu 64-bit is too large to fit onto a normal CD so I'm struggling to find a way to install it.

Any ideas?

Thanks in advance,
Wallace

---

### Post by snowpine on 2013-05-09
Hi Wallace,

Give the Ubuntu Minimal CD a try; it's tiny! :)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by ibjsb4 on 2013-05-09
Ubuntu 12.04 will fit on a cd and its supported till 2017.  And at boot (login) choose Ubuntu 2D by clicking on the icon.  Your server is not going to support 3D.

You can also install the classic desktop if that one is not to your liking and again choose at login.

[In terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal"), enter:
```
sudo apt-get install gnome-session-fallback
```

---

### Post by snowpine on 2013-05-09
Presumably OP is installing Ubuntu Server on his/her server, so 2D/3D is a moot point, no? :D

agentjwall, I am not sure your hardware supports 64-bit? Might want to try 32-bit.

---

### Post by ibjsb4 on 2013-05-09
Im thinking 64 bit server is 701M and a cd can hold 703M.  At any rate, better to hear it from the OP :)

---

### Post by agentjwall on 2013-05-09
Bear with me I'm new to Ubuntu...

I am intending to use it as a server still but what's the difference between Ubuntu Server and Regular? My server has 8 gigs of RAM so doesn't it require 64-bit?  Also what's the difference between 2D and 3D?

---

### Post by snowpine on 2013-05-09
Ubuntu Server is designed for this: [http://en.wikipedia.org/wiki/Server_%28computing%29](http://en.wikipedia.org/wiki/Server_%28computing%29)

Ubuntu Desktop is designed for this: [http://en.wikipedia.org/wiki/Desktop_computer](http://en.wikipedia.org/wiki/Desktop_computer)

Whether you want 32 bit or 64 bit is entirely dependant on the CPU. What is the CPU?

---

### Post by agentjwall on 2013-05-09
Intel Pentium(R) 4 CPU 2.8 GHz x2

---

### Post by ibjsb4 on 2013-05-10
If you wish to use your Dell as a server, then install the "Server Edition".  If you want to use it as a desktop computer (with a GUI) then install the standard Ubuntu.  Just because your Dell is a server does not mean you have to install the server edition, it can also run a standard desktop.

The info Im finding online indicates that [your processor]("http://ark.intel.com/products/27447/Intel-Pentium-4-Processor-2_80-GHz-512K-Cache-533-MHz-FSB") is single core, no [hyperthreading]("http://en.wikipedia.org/wiki/Hyper-threading") and no [SMP.]("http://en.wikipedia.org/wiki/Symmetric_multiprocessing")

Ubuntu 12.04 (Unity desktop) was the last release to fit on a CD.  There is also [Lubuntu]("http://lubuntu.net/") and [Xubuntu]("http://xubuntu.org/") which may run faster on your processor.

So I guess the question is what do you intend to use it for.

---

### Post by agentjwall on 2013-05-10
I'm mostly using it as a hobby; setting it up for random odds and ends like cloud-storage and whatnot.

I think I have enough information to go from here. Thank you both for all of your help!

---

### Post by beatgr on 2013-06-14
[QUOTE=agentjwall]I'm trying to install Ubuntu (64-bit) on an old Dell PowerEdge 800 Server and I'm running into problems. The server only has a CD-Drive (Not DVD) and doesn't seem to support USB-Booting (As far as I can tell). Ubuntu 64-bit is too large to fit onto a normal CD so I'm struggling to find a way to install it.[/QUOTE]
Wallace -

The DVD-ROM drives have been so cheap past few years (surplus pulls), 
I swapped out the CD-ROM for a DVD-ROM in my old PowerEdge 1400 server -- and never looked back!

---

