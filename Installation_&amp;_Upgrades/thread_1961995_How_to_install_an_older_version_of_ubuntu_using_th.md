---
title: "How to install an older version of ubuntu using the terminal (11.10 to 10.04)"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by species52 on 2012-04-20
Hello!

I have had a big problem since i upgraded to ubuntu 11.10, ubuntu wont startx or gnome, I go directly to the terminal. Apparently this is due to wrong Nvidia driver installed or an older kernel driver.
  
I have tried to reinstall nvidia drivers and the suggestions in:
 [http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal)

Now i have given up and wish to install ubuntu 10.04 witch i know works.

How do i do this in the terminal?

I'm really new to writing in the terminal so it pretty much have to be a instruction for a dummy :)

Thanks

---

### Post by mörgæs on 2012-04-20
Have you tried a fresh install of 11.10 where you use only open-source (=Nouveau) drivers?

---

### Post by tmaranets on 2012-04-20
Is your 11.10 a Wubi installation? If it is try deleting Ubuntu from your Windows side, and then install it again.

---

### Post by kc1di on 2012-04-20
do you know which nvidia video card you have?

in the terminal type the following command and post the out put here if your not sure which card you have.

```
$ lspci -v
```
you should be able to get 11.10 working :)

---

### Post by species52 on 2012-04-20
> **mörgæs said:**
> Have you tried a fresh install of 11.10 where you use only open-source (=Nouveau) drivers?

I installed/upgraded  it through the terminal so i don't know.


In addition to this I'm at work now so i cant do anything with the computer for another 4 hours

---

### Post by species52 on 2012-04-20
> **tmaranets said:**
> Is your 11.10 a Wubi installation? If it is try deleting Ubuntu from your Windows side, and then install it again.


I don't use windows at all.

---

### Post by species52 on 2012-04-20
I did it you guys!!

I found out that before when trying to install nvidia drivers it couldn't find or wasn't compatible with the kernel so somehow in desperation i managed to do it something like this (maybe not in this order):

sudo apt-get purge nvidia-current

sudo apt-get purge linux-headers-3.0.0-17-generic-pae

sudo apt-get install linux-headers-3.0.0-17-generic-pae

sudo apt-get install nvidia-current

There is a lot of people out there having troubles with their graphic card drivers. Someone should make a guide fore dummies who get stuck in terminal, it's very frustrating:)):P

---

### Post by mörgæs on 2012-04-20
Good, please mark the thread 'solved'.

---

