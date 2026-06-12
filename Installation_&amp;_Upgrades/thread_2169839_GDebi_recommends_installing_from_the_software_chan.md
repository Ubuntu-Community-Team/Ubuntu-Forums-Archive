---
title: "GDebi recommends installing from the software channel instead"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by Buntu Bunny on 2013-08-23
I'm working on a project in Scribus 1.4 and have had some issues. In researching for solutions, I learned that version 1.5 has what I need. This version is still in development (new territory for me). I downloaded it from [Launchpad]("https://launchpad.net/~scribus/+archive/ppa") and am trying to install it with GDebi. GDebi tells me

> Same version is available in a software channel
You are recommended to install the software from the channel instead. 

Could someone please explain to me what this means and where to find said channel?

---

### Post by ajgreeny on 2013-08-23
It is saying that the software channel (ie, the software-centre) is the recommended way to install a package.

For some reason you seem to not have the most up-to-date version available through the normal repos. Perhaps you have not run an update of them for some while?

---

### Post by Buntu Bunny on 2013-08-23
> **ajgreeny said:**
> It is saying that the software channel (ie, the software-centre) is the recommended way to install a package.

For some reason you seem to not have the most up-to-date version available through the normal repos. Perhaps you have not run an update of them for some while?

Thank you ajgreeny. You set me on the right path. I didn't find version 1.5 in Software Centre, but I did find it in Synaptic!

---

### Post by Dennis N on 2013-08-23
> **Buntu Bunny said:**
> I'm working on a project in Scribus 1.4 and have had some issues. In researching for solutions, I learned that version 1.5 has what I need. This version is still in development (new territory for me). I downloaded it from [Launchpad]("https://launchpad.net/~scribus/+archive/ppa") and am trying to install it with GDebi. GDebi tells me

 

Could someone please explain to me what this means and where to find said channel?

If you added that particular ppa to your software sources (software channels) with add-apt-repository, and then updated the sources list with apt-get update, the 1.50 version would become available for installation through the regular package manager. 

```
sudo add-apt-repository ppa:scribus/ppa
sudo apt-get update (or if using Synaptic, open it and Reload, and the 1.50 version should appear.)
sudo apt-get install scribus (or install from Synaptic)
```

---

### Post by Buntu Bunny on 2013-08-23
> **Dennis N said:**
> If you added that particular ppa to your software sources (software channels) with add-apt-repository, and then updated the sources list with apt-get update, the 1.50 version would become available for installation through the regular package manager. 


Dennis N, thank you! That was the explanation I was looking for. 

It's downloading now, so we'll see if it does what I hope it will.

---

### Post by Dennis N on 2013-08-23
Great! I love Scribus and use it quite a bit.

---

### Post by Buntu Bunny on 2013-08-23
I'm still learning it and find that even 1.4 has been quirky. Still, it's a good option for Linux DTP.

---

