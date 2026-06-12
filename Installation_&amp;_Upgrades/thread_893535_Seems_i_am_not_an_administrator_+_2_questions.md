---
title: "Seems i am not an administrator + 2 questions"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by farmdve on 2008-08-18
It seems that i am not an admin as i cannot change the screen resolution to 1024x768
I should be as the name i typed in the installation screen is the same as now, yet i am not admin
Now for my question:
It seems that there is a problem when trying to use PPPOE
There is somekind of "Wired" connection that ubuntu tries to use but fails and cant let me choose to use the one i have made
Can u help me?
And why do i always need to press "Unlock" and enter pass to do some certain things?

---

### Post by conscious on 2008-08-18
> **farmdve said:**
> It seems that i am not an admin as i cannot change the screen resolution to 1024x768
I should be as the name i typed in the installation screen is the same as now, yet i am not admin
Check this out: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

> **farmdve said:**
> 
It seems that there is a problem when trying to use PPPOE
There is a (text-mode) program, pppoeconf, which can be used to configure PPPOE connections. It may be helpful for you.

---

### Post by farmdve on 2008-08-18
I read a bit of that and it said "You could type a command incorrectly and destroy the system"
Does this mean that if i type sudo displayconfig-gtk**K** i could do some damage even if the command is not valid?

---

### Post by aysiu on 2008-08-18
> **farmdve said:**
> I read a bit of that and it said "You could type a command incorrectly and destroy the system"
Does this mean that if i type sudo displayconfig-gtk**K** i could do some damage even if the command is not valid?
It should be ```
gksudo displayconfig-gtk
``` Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by farmdve on 2008-08-18
I know how to execute the command but will it be a problem if i were to mistype a command?
And is there some kind of soft that would make my connection(PPPOE) active like in bypassing the one that comes with ubuntu cause i cant set up that yet

---

