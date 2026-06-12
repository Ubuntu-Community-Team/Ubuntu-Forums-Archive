---
title: "Just recently installed 14.04, It won't connect for updates or adding apps"
date: 2014-06-22
forum: Installation &amp; Upgrades
---

### Post by steve_gesn on 2014-06-22
New to Ubantu but not Linux. Been a Linux user since 2001, just added Ubuntu. It won't do updates and it won't add new apps. So, what's the trick. I've used every program you have from "Intall Updates" to "Synaptic" I just keep getting an error message saying "Can't install updates. Check internet connection" My net is fine, I'm posting this, (On Ubuntu) right? Any suggestions?
Thanx in advance :confused:

---

### Post by philinux on 2014-06-22
Is this wired or wifi?

---

### Post by steve_gesn on 2014-06-22
wi fi, but I get Internet OK. No problem with anything else.

---

### Post by grahammechanical on 2014-06-22
Please run in a terminal and post back any error messsages.

```
sudo apt-get update
sudo apt-get upgrade
```

Regards.

---

### Post by steve_gesn on 2014-06-22
Nope, will not update, will not install new apps. I think this may be a repository issue--maybe? It doesn't seem to want to get it from the site. --Thoughts?

---

### Post by mörgæs on 2014-06-22
You were asked to 

> **grahammechanical said:**
> 
post back any error messsages.


If you want help please follow all instructions given.

---

### Post by philinux on 2014-06-23
+1 to the above and additionally post your sources list.

```
cat /etc/apt/sources.list
```

---

