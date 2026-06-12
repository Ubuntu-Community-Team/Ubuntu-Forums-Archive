---
title: "Unity system requirements"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by abdulmajid on 2011-10-22
Hi all,

What are the system requirements for the new Ubuntu with the Unity desktop environment? I cannot get it run on my computer, yes my computer is like ancient...:ermm:

---

### Post by zvacet on 2011-10-22
Maybe [this]("https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements") can give you answer.

---

### Post by abdulmajid on 2011-10-22
Thank you, that really helped me.

---

### Post by Megaptera on 2011-10-22
For lower spec machines have a look at Lubuntu: [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

"A Pentium II or Celeron system with 128 MB of RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu. It should be possible to install and run Lubuntu with less memory, but the result will likely not be suitable for practical use."

---

### Post by abdulmajid on 2011-10-22
I have a Pentium 4 524, 1GB RAM...:/

---

### Post by Megaptera on 2011-10-22
That's plenty for Ubuntu 11.10
"The minimum memory requirement for Ubuntu 11.10 is 384 MB of memory for Ubuntu Desktop."

[https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#System_Requirements](https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#System_Requirements)

---

### Post by zvacet on 2011-10-22
AFAIK  you must have 3D acceleration to run Unity.From login window you can choose Unity2D,but as Megaptera said zouy can try Lubuntu if you want to.In terminal

```
sudo apt-get install lubuntu-desktop
```

From login window select Lubuntu session.

---

### Post by abdulmajid on 2012-03-12
What about Xfce? Which one would be better to use, XFCE of LXDE?

---

### Post by abdulmajid on 2012-03-15
I am using Ubuntu 11.10 64bit, Unity 2D. It's very slow. :(

---

### Post by mastablasta on 2012-03-15
> **abdulmajid said:**
> I am using Ubuntu 11.10 64bit, Unity 2D. It's very slow. :(
 
 
something else is wrong then. do you maybe have weak GPU and some other special effects turned on (transparency etc.)? special effects can slow it all down if you do not have propper graphics card to run them.
you can try Xubuntu and see how it goes. The computer is more than strong enough to run it.
 
Lubuntu is a bit more limited in configuraiton options than Xubuntu but still a good choice. however in my opinion and +buntu should work fine with your configuraiton.
 
what graphics chip do you have?

---

### Post by abdulmajid on 2012-03-15
Actually it's an ancient machine. Intel 865, in-built graphics controller with 96MB of memory. :p

I have tried Xubuntu 11.10 64 bit but it didn't recognize my Logitech webcam. :(

---

### Post by mastablasta on 2012-03-15
if Ubuntu recognised your cam then xubuntu will also do it. the difference between the two is only in default installed applicaitons and desktop. suggets you open a separate thread for logitech cam perhaps in hardware section.
 
the cause of slowness is as suspected the GPU. not only it's a poor chip it also doens't have good linux drivers.
 
if you could somehow get (even old) dedicated GPU it owuld solve your problems.
 
I assembled my wife's PC from old and some new parts and got cheapest (new) Celeron i could find, and added 5 or 6 year old 256 MB ATI graphics card, old ram (1.3GB DDR), old 60GB disk. it runs Kubuntu with most effects on and it is all quite fast. the only issue is Audio which i am hoping will be fixed when i upgrade to latest version or LTS. i also tried it live on an even older CPU with single core and 128MB GPU (about 9 years old). again very fast with effects on.
 
she also got an old notebook - 1.2Ghz Athlon, with only 224 MB ram, using a 32MB graphics chip and 20 Gb hard disk. well i stuck Chrunch bang with XFCE on it (basically debian 6 with some upgrades) and it is also running a bit slow but it is still usefull. can play video, youtube, work in office...
 
my point is don't give up hope and also your mashicne is not that old. there are also plenty other things out there you could try (different desktops environments etc.). 
 
but you would really really benefit from a dedicated graphics card even an old/used one.

---

