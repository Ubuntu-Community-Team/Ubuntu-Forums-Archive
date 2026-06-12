---
title: "installed nvidia driver now black screen upon reboot"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by Stubbs3 on 2010-01-21
I have ubuntu 9.10 and a nvidia geforce 8600gt. 
 
I reciently installed the nvidia restricted driver 1.85. upon reboot of ubuntu it goes to just a black screen.
 
Im new to all of this (never typed a command before unitl a couple of days ago. 
 
Ive looked into a couple different posts and found a command to check/edit the driver (i think) and there is nothing in it to edit! I dont really know what im talking about.
 
I would really like to correct this and not just throw up my hands and give up.
 
Any help would be useful.
 
Thanks

---

### Post by presence1960 on 2010-01-21
I have a nvidia 8600 gt also. Try this to see if it solves your problem. Boot into recovery mode Ubuntu. let it do it's thing. Choose netroot. At the prompt type one at a time and press enter: 

```
install envyng-core
install envyng-qt
install envyng-gtk
```

Once all are installed run from the prompt ```
envyng -t
```

Follow the prompts now. First I would try to uninstall the Nvidia driver. Then choose to install nvidia driver. Reboot when completed. Boot into Ubuntu and see what happens.

---

### Post by Stubbs3 on 2010-01-21
It worked!
 
Here is what i found out though...
 
It was necessary for me to type the code this way though.
 
 
_______________________________________
apt-get install envyng-core
apt-get install envyng-qt
apt-get install envyng-gtk
envyng -t
 
_______________________________________
 
It was necessary to use the "apt-get" in front of everything. Otherwise it said something about a invalid command or something or other.
 
After trying to do them all like you said, when i ran the "envyng -t" it said to use the apt-get install envyng-core.
 
Im sure anyone else who types code all of the time would know to run the code that way, but being a nUbe I dont know enough.
 
Thanks very much for your help for pointing me in the right direction!

---

### Post by presence1960 on 2010-01-21
> **Stubbs3 said:**
> It worked!
 
Here is what i found out though...
 
It was necessary for me to type the code this way though.
 
 
_______________________________________
apt-get install envyng-core
apt-get install envyng-qt
apt-get install envyng-gtk
envyng -t
 
_______________________________________
 
It was necessary to use the "apt-get" in front of everything. Otherwise it said something about a invalid command or something or other.
 
After trying to do them all like you said, when i ran the "envyng -t" it said to use the apt-get install envyng-core.
 
Im sure anyone else who types code all of the time would know to run the code that way, but being a nUbe I dont know enough.
 
Thanks very much for your help for pointing me in the right direction!

Good catch, I have to blame that on not being alert in the morning. Glad you got it working. Enjoy ubuntu

---

