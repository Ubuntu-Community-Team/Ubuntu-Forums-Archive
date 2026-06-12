---
title: "Is it safe to install NVIDIA drivers in Ubuntu 12.10 yet"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by proggy on 2012-10-26
I don`t want to install the drivers and have no Unity after reboot.
Was the bug fixed?

---

### Post by mikewhatever on 2012-10-26
Can you post a link to the bug report.

---

### Post by proggy on 2012-10-26
Wow no i can`t i just know there was a bug reports done just before the final release and it wasn;t fixed as lots of people still had issues.

---

### Post by cbennett926 on 2012-10-26
> **proggy said:**
> Wow no i can`t i just know there was a bug reports done just before the final release and it wasn;t fixed as lots of people still had issues.


Woooah there buddy, let's calm down here and try and take this with a mature stance. A lovely gentleman was trying to help you, you owe him and everyone else an apology. If your going to talk like that then you need to take your questions elsewhere. But to answer your question, yes you can install nVidia drivers, I currently am running them. I have used each of the drivers and they do work just fine. The bug you may have been referring to was this: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1070392](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1070392)

---

### Post by mc4man on 2012-10-26
Before installing proprietary drivers (nvidia or fglxr) first run this command to make sure it's installed
```
sudo apt-get install linux-headers-generic
```

---

### Post by proggy on 2012-10-26
> **cbennett926 said:**
> Woooah there buddy, let's calm down here and try and take this with a mature stance. A lovely gentleman was trying to help you, you owe him and everyone else an apology. If your going to talk like that then you need to take your questions elsewhere. But to answer your question, yes you can install nVidia drivers, I currently am running them. I have used each of the drivers and they do work just fine. The bug you may have been referring to was this: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1070392](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1070392)
woops i don`t think my reply came out as intended , it was not meant to be fresh or sarcastic as i really forgot the link where i saw the bug report and thank you fine sir for the link

---

### Post by proggy on 2012-10-26
> **mc4man said:**
> Before installing proprietary drivers (nvidia or fglxr) first run this command to make sure it's installed
```
sudo apt-get install linux-headers-generic
```
And thank you as they were not updated so let`s go for broke with installing the NVIDIA drivers

---

### Post by mikewhatever on 2012-10-26
> **proggy said:**
> woops i don`t think my reply came out as intended , it was not meant to be fresh or sarcastic as i really forgot the link where i saw the bug report and thank you fine sir for the link

No worries, I was just curious.

PS: Isn't linux-headers-generic installed by default on 64bit systems?

---

### Post by proggy on 2012-10-26
> **mikewhatever said:**
> No worries, I was just curious.

PS: Isn't linux-headers-generic not installed by default on 64bit systems?
Well i'm not sure i did an upgrade from 12.04 might;ve been something gone wrong while installing

---

### Post by proggy on 2012-10-26
Installed NVIDIA drivers ,rebooted ,Unity is there thank you all!!!

---

### Post by mc4man on 2012-10-26
> **mikewhatever said:**
> No worries, I was just curious.

PS: Isn't linux-headers-generic not installed by default on 64bit systems?
Something has changed in 12.10 so no they (the meta & actual packages) are no longer installed by default
This is causing all sorts of issues with sources that use dkms, the modules aren't being built
(and if users use the 'additional drivers' interface then they have no idea about this as it installs silently

The bug (one of many) directly on nvidia-* has been marked 'won't fix', on dpkg marked 'wishlist'
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341)

I've an additional one on ubiquity that's being ignored
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)

---

### Post by robtygart on 2012-10-27
> **cbennett926 said:**
> Woooah there buddy, let's calm down here and try and take this with a mature stance. A lovely gentleman was trying to help you, you owe him and everyone else an apology. If your going to talk like that then you need to take your questions elsewhere.

What? Thats an odd response, you must be joking hehe:confused:!     

It was a good statment, "If Ubuntu had control over the crappy nvidia drivers." I am had the same problem, I stayed with Kubuntu, even with Kubuntu I am having trouble, so far I had the best luck with The expermintal driver. 

I am sure you know if not 

Settings > Software sources > Additional Drivers


Edit: I see its been solved, but the above worked for me.

---

