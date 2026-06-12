---
title: "need help  installing wine"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by hawkeye-91 on 2008-07-06
Hey, I just installed ubuntu on my laptop, but i've been having problems installing wine. It says:

Error: Dependency is not satisfiable: wine

Please help!!!!
Thank You

---

### Post by Bakon Jarser on 2008-07-06
Try the instructions from the official wine site.  You'll get a better version of wine that way too.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by hawkeye-91 on 2008-07-06
Sorry, should have mentioned this earlier but i dont have computer access on that computer. I was wondering how to fix that problem without figuring out an internet connection for that one. 
Thanks.

---

### Post by issih on 2008-07-06
Not going to happen...at least not easily.

I guess you could download the wine .deb on one machine, then transfer that over to your other one and install it there, but you will almost certainly have unresolved dependencies.

Your best bet is going to be to find a network cable and jack that into the pc, its simply the easiest solution by miles and miles

---

### Post by Bakon Jarser on 2008-07-06
you need an internet connection to download things from synaptic or add/remove or apt get.  You could download it on another computer.  The .deb's for wine and it's dependencies will be saved in /var/cache/apt/archives

---

### Post by steveneddy on 2008-07-06
Get an internet connection, then in terminal

```
sudo apt-get install wine
```

---

### Post by hawkeye-91 on 2008-07-07
OK, so i have to download directly from the internet onto that computer? What if I download onto another computer and use a flash drive to move it over? Can it not install from the package?

Thanks!

---

### Post by Partyboi2 on 2008-07-07
> **hawkeye-91 said:**
>  What if I download onto another computer and use a flash drive to move it over? Can it not install from the package?

Thanks!
Yes you can do this but you may need to install other packages to be able to get that package installed.
If you do not have internet access on the ubuntu machine you can try [[COLOR=Blue]this[/COLOR]]("http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/") (but use the ubuntu live cd to download the packages) or you could also use [[COLOR=Blue]this [/COLOR]]("http://aptoncd.sourceforge.net/")
or manually install all the dependencies

---

