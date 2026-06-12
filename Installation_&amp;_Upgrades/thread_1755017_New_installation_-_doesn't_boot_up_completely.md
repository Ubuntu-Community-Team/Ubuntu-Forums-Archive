---
title: "New installation - doesn't boot up completely"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by gilch on 2011-05-10
I installed Ubuntu 11.04 from a downloaded CD onto an old computer. It replaced the old Windows that was on it (that is what a wanted).  The machine is a AMD-64, I think the video is a Radeon.
When I reboot it only gives me
ubuntu login: 
I give the name, and then the password, and what I get is the following:

gilles@ubuntu:`$

How do I get my Ubuntu desktop?

Gilles

---

### Post by garvinrick4 on 2011-05-10
What does 
```
startx
```
give you

---

### Post by gilch on 2011-05-10
> **garvinrick4 said:**
> What does 
```
startx
```
give you
I tried that. It asked me to  install startx giving the instruction to use  (unfortunaely I didnt write that down). I installed it as requested: it ran screens and screens for several minutes. When I rebootede, nothing had changed.
 Thaks for the reply.


Gilles

---

### Post by garvinrick4 on 2011-05-10
You downloaded what? 32 bit 11.04 desktop ? Run these 3 to make sure you have a GUI
locate ubuntu-desktop
locate xorg
locate gdm

---

### Post by dFlyer on 2011-05-10
> **gilch said:**
> I installed Ubuntu 11.04 from a downloaded CD onto an old computer. It replaced the old Windows that was on it (that is what a wanted).  The machine is a AMD-64, I think the video is a Radeon.
When I reboot it only gives me
ubuntu login: 
I give the name, and then the password, and what I get is the following:

gilles@ubuntu:`$

How do I get my Ubuntu desktop?

Gilles

Is this the server version by chance?? When you boot the CD do you get to the try before you install screen?

---

### Post by gilch on 2011-05-10
> **dFlyer said:**
> Is this the server version by chance?? When you boot the CD do you get to the try before you install screen?

I didn<t know i had a choice. Yes it was the server version.
Gilles

---

### Post by gilch on 2011-05-10
> **garvinrick4 said:**
> You downloaded what? 32 bit 11.04 desktop ? Run these 3 to make sure you have a GUI
locate ubuntu-desktop
locate xorg
locate gdm

When I entered locate ubuntu-desktop, I got  the  following:
/usr/lib/taskse1/info/edubuntu-desktop.preinst
/usr/lib/taskse1/info/kubuntu-desktop.preinst
/usr/lib/taskse1/info/ubuntu-desktop.preinst
/usr/lib/taskse1/info/xubuntu-desktop.preinst

After I entered the other two (xorg and gdm), nothing happened.

What does that  mean?

Gilles

---

### Post by garvinrick4 on 2011-05-10
Download and Burn a new CD and install:
You have no grapic user interface with server edition:
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by gilch on 2011-05-10
> **garvinrick4 said:**
> Download and Burn a new CD and install:
You have no grapic user interface with server edition:
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

OK. I will try that. I had just used the first download file that showed up.

I"ll check more carefully this time.

THANKS

Gilles

---

### Post by dFlyer on 2011-05-11
> **dFlyer said:**
> Is this the server version by chance?? When you boot the CD do you get to the try before you install screen?

Download the desktop version and reinstall.

---

