---
title: "Windows Virtual PC Install"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by Danny159 on 2008-09-22
Hey,

I am trying to install Ubuntu Desktop and Server (two different PC's) and its not installing =(

I am installing it on Windows Virtual PC 2007 Running windows vista...
It boots into the .ISO and the CD and asks for my language..
Then it askes if I want to try or install ect... I have tryed Try and install...
When I do install this comes up...

[[IMG]http://img79.imageshack.us/img79/1120/linuxage1.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img79.imageshack.us/img79/linuxage1.jpg/1/w663.png[/IMG]](http://g.imageshack.us/img79/linuxage1.jpg/1/)

Then goes to...

[[IMG]http://img79.imageshack.us/img79/2295/linuxbew6.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img79.imageshack.us/img79/linuxbew6.jpg/1/w990.png[/IMG]](http://g.imageshack.us/img79/linuxbew6.jpg/1/)

Can anyone help?

Daniel

---

### Post by Danny159 on 2008-09-22
bump

---

### Post by Riax on 2008-09-22
You may not like this answer, but Microsoft has dropped support for running non-Windows-based guest operating systems in Microsoft Virtual PC; if you check their website for the list of supported operating systems, you won't see anything else. I don't know whether the behavior you described and depicted was intentional on their part, but I wouldn't put it past them.

On a Windows host, I've found VMWare Server ([http://vmware.com/download/server/]("http://vmware.com/download/server/")) to be an excellent virtualization solution. If you want scalability and power, VMWare Server is the way to go. However, if you're used to MS Virtual PC, you may also want to consider VirtualBox ([http://virtualbox.org/wiki/Downloads]("http://virtualbox.org/wiki/Downloads")). I've found it to be a bit simpler and more friendly than VMWare Server, and its interface is similar to that of Virtual PC.

I hope I've been able to help.

---

