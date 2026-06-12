---
title: "Upgrade Failure"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Tweaker420 on 2011-05-01
Hey all, 

    Having an issue upgrading to 11.04 from 10.04, a screen shot of the issue included.

---

### Post by Dutch70 on 2011-05-01
Hi and welcome to UF

You cannot upgrade from 10.04 to 11.04. You must go from one version to the next or from one LTS version to the next, such as from 8.04 LTS to 10.04 LTS. 

If you want to upgrade to 11.04, you will first have to upgrade to 10.10, then 11.04. *(not a good idea)*

I recommend doing a fresh install, it's much faster, simpler & more likely to be successful. 
Have a look at this thread.
[[COLOR="Red"]**I upgraded, and now I have this error...**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1580857")

.

---

### Post by Tweaker420 on 2011-05-01
Hello and Thank You, 

I guess i lied origonally there, unintentional of course. 

tweak@tweak-ubuntu:~$ cat /etc/issue
Ubuntu 10.10 \n \l

---

### Post by Dutch70 on 2011-05-01
I still recommend a fresh install. 

Did you read the link I posted? 

Upgrades are slow, complicated & not usually successful unless your system is very basic. So after all the trouble, there is a good chance you'll be doing a fresh install anyway. That is the very reason that most of us use a separate /home partition. So we can do a fresh install without losing any of our files or settings.

I've never done a successful upgrade, so if you still want to attempt it, maybe someone else will have more info for you.

---

### Post by khelben1979 on 2011-05-01
Have you tried with (?) : ```
sudo apt-get dist-upgrade
```

Does it report the same as Ubuntu Software Center?

---

### Post by Tweaker420 on 2011-05-01
As a matter of fact over the years ive never done a successful upgrade either. Always either broke my system or failed. Yes i checked the link thank you, and i think ill need to put /home on a seperate partition next time.

> **Dutch70 said:**
> I still recommend a fresh install. 

Did you read the link I posted? 

Upgrades are slow, complicated & not usually successful unless your system is very basic. So after all the trouble, there is a good chance you'll be doing a fresh install anyway. That is the very reason that most of us use a separate /home partition. So we can do a fresh install without losing any of our files or settings.

I've never done a successful upgrade, so if you still want to attempt it, maybe someone else will have more info for you.

---

### Post by Tweaker420 on 2011-05-01
> **khelben1979 said:**
> Have you tried with (?) : ```
sudo apt-get dist-upgrade
```Does it report the same as Ubuntu Software Center?

tweak@tweak-ubuntu:~$ sudo apt-get dist-upgrade
[sudo] password for tweak: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tweak@tweak-ubuntu:~$ 

And thanks for your reply~

---

### Post by Dutch70 on 2011-05-01
Wow, what do you get when you run...
```
cat /etc/issue
```

Also, you may find this link helpful very soon. 
[[COLOR="RoyalBlue"]http://www.psychocats.net/ubuntu/separatehome[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Tweaker420 on 2011-05-01
> **Dutch70 said:**
> Wow, what do you get when you run...
```
cat /etc/issue
```Also, you may find this link helpful very soon. 
[[COLOR=RoyalBlue]http://www.psychocats.net/ubuntu/separatehome[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

See thread comment #3 :) Ubuntu 10.10

---

### Post by Dutch70 on 2011-05-01
Well ...:confused:

I'm not sure why it's not upgrading & being that I've never been able to upgrade successfully myself, I really don't know what to tell you other than the obvious "fresh install".

---

### Post by Tweaker420 on 2011-05-06
Managed to get this solved, using the ppa-purge command on 2 repositories. x-updates and x-org edgers. after that the upgrade runs smooth. thans to those who replied:guitar:

---

