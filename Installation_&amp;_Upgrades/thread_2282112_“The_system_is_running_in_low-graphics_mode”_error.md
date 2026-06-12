---
title: "“The system is running in low-graphics mode” error but can run startx"
date: 2015-06-11
forum: Installation &amp; Upgrades
---

### Post by ilker3 on 2015-06-11
Hi, 
After an update my machine started to give "low-graphics mode" error. I followed the possible options but didn't help.
I am checking forums for the last couple of hours and tried almost all but nothing helped. 

However, if I first choose the option to start low-graphics mode,  X shuts down. After that if I run "startx" from tty terminal everything works perfect. 

The only error I could see in Xorg.0.log  is "No screen found" 
How can I detect the source of the problem ? Any help is appreciated. 
Thanks.

---

### Post by ilker3 on 2015-06-11
Hi again, 
I solved the problem but Ubuntu's behaviour is weird. The problem is not about the recent update but its because of a simple line I moved from .bashrc to /etc/profile while ago and never tested. The line was merely a script call 
. $ilkerScripts/bashRC
However ilkerScripts is defined in /etc/environment and I didn't know that it wouldn't be initialized when system runs /etc/profile. So system is trying to run a nonexistent file /bashRC. 

Now the weird thing is that Ubuntu is giving an unrelated error and crashing at low graphics mode. Does anyone have any explanation ?

---

