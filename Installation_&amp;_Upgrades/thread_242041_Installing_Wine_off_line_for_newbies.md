---
title: "Installing Wine off line for newbies"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by rlreich on 2006-08-23
I'm trying to install Wine. My ISP requires an IE only web based sign on. It's a provider in China don't ask why I don't know. I can provide the IP address if anyone wants it. I can d/l on XP reboot and install if I knew what to do. So far I've tried all the tips I can find in the forums doing a "Wine" search. This is my first time using and Linux distro so I need some hand holding so to speak. I've copied the .deb files over and it says it's on there but I can't get it to start IE. I've even got the IE for Linux file but it won't run either. Can someone tell me how to 
1. Remove what I've got installed if needed 
2. How to properly install Wine OFFLINE and
3. Get IE installed so I can get online and do the updates needed.

It sucks being a newbie!

When I right click on the IExplorer icon I have the option to Open with "wine" but it won't open.

---

### Post by mlind on 2006-08-24
> **rlreich said:**
> I'm trying to install Wine. My ISP requires an IE only web based sign on. It's a provider in China don't ask why I don't know. I can provide the IP address if anyone wants it. I can d/l on XP reboot and install if I knew what to do. So far I've tried all the tips I can find in the forums doing a "Wine" search. This is my first time using and Linux distro so I need some hand holding so to speak. I've copied the .deb files over and it says it's on there but I can't get it to start IE. I've even got the IE for Linux file but it won't run either. Can someone tell me how to 
1. Remove what I've got installed if needed 
2. How to properly install Wine OFFLINE and
3. Get IE installed so I can get online and do the updates needed.

It sucks being a newbie!

When I right click on the IExplorer icon I have the option to Open with "wine" but it won't open.

1. Pick one of these
```

#removes package completely
sudo aptitude purge *package* 

#removes package, but leaves the configuration files
sudo aptitude remove *package*

#like the first remove, but allows you to 'break' dependencies. Handy when you need to remove a package for a moment, but not its dependencies.
sudo dpkg -P --force-depends *package*

```
or use synaptic.

2.
```

sudo dpkg -i *package.deb*

```

3. Try with [WineTools]("http://www.von-thadden.de/Joachim/WineTools/"). It contains script that should automatically install IE6 and required stuff for it.

---

### Post by bhdenterprises on 2006-08-24
hi, i want to also install wine in my ubuntu box so i can use Windows programs. but i my problem is: i have an ongoing Visual Basic project. Could it run in Wine? How about the DLLs that my project needs which usually are Windows native?

---

### Post by mlind on 2006-08-24
> **bhdenterprises said:**
> hi, i want to also install wine in my ubuntu box so i can use Windows programs. but i my problem is: i have an ongoing Visual Basic project. Could it run in Wine? How about the DLLs that my project needs which usually are Windows native?

I doubt it, but you should try it out at least. If you're about to compile windows native libraries, then I don't think it's going to work with wine.
But I guess you should post that one to Programming section. There's probably better alternatives than using wine for this.

---

### Post by rlreich on 2006-08-25
Thanks for your help. I got wine to install properly but I can't get IE6 to run. The wine browser window will open then sort of hang. I tried d/ling IE4linux but it wouldn't even try to start. I was able to get online through a p2p and download wine through Add/Remove Programs with no problem. Any suggestions would be very helpful.

---

### Post by Druidor on 2006-08-25
Have you tried the IE tab addon for Firefox.

[https://addons.mozilla.org/firefox/1419/](https://addons.mozilla.org/firefox/1419/)

---

### Post by rlreich on 2006-08-25
No I will try that also.

---

### Post by rlreich on 2006-08-25
The IE extension works on the XP side. I'm just hoping the extension will run when I reboot into Ubu. Thanks again for the tip!

UPDATE: The IE extensions won't run under linux distro. Great thought thanks again for the help.

---

### Post by Druidor on 2006-08-29
Another thought "IEs4Linux". Not tried it myself but others on the forum have quoted it as a possible for IE problems.

[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

---

### Post by rlreich on 2006-08-29
I finally got IEs4linux to work. I'm up and running now. Thanks!

---

