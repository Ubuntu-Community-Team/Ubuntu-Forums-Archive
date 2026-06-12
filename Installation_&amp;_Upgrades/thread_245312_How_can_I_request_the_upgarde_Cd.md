---
title: "How can I request the upgarde Cd ?"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by mesh2005 on 2006-08-27
ShipIt sent me the installation cd, I want to upgrade my installation (5.05) , how can I request the upgrade Cd ?

---

### Post by randell6564 on 2006-08-27
> **mesh2005 said:**
> ShipIt sent me the installation cd, I want to upgrade my installation (5.05) , how can I request the upgrade Cd ?

What is "5.05", breezy?  If you have breezy, then just install it, and go to system>Administration>Update Manager.

You should see a notification that there is an upgrade available.

OH, and you can just go to ubuntu.com and order the most current Ubuntu OS free.

---

### Post by Sef on 2006-08-27
> ShipIt sent me the installation cd, I want to upgrade my installation (5.05) , how can I request the upgrade Cd ?

There is no upgrade cd.  To upgrade your system, do the following:

1) Open the terminal (Applications > Accessories > Terminal)

2) sudo apt-get update

3) sudo apt-get dist-upgrade

---

### Post by randell6564 on 2006-08-27
> **Sef said:**
> There is no upgrade cd.  To upgrade your system, do the following:

1) Open the terminal (Applications > Accessories > Terminal)

2) sudo apt-get update

3) sudo apt-get dist-upgrade

OH yeah, Thats right!

---

### Post by lord_zerg on 2006-08-27
i find this question interesting.
the upgrade is a 600M download. i still use dial-up, yes i live in a third world country, but that aside. can't i use a 6.06 installation cd to upgrade my breezy box?
is there is a way to do this i'm interested on it, since i can gain access to the installation cd.

---

### Post by randell6564 on 2006-08-27
> **lord_zerg said:**
> i find this question interesting.
the upgrade is a 600M download. i still use dial-up, yes i live in a third world country, but that aside. can't i use a 6.06 installation cd to upgrade my breezy box?
is there is a way to do this i'm interested on it, since i can gain access to the installation cd.

YES, [www.ubuntu.com](www.ubuntu.com) can mail to you a copy of this cd.

---

### Post by lord_zerg on 2006-08-27
in fact, a friend of mine already ordered the cd. what i want to know is if i could upgrade from it, or if i would be force to reinstall everything, which include some software i downloaded from the repositories.

---

### Post by randell6564 on 2006-08-27
> **lord_zerg said:**
> in fact, a friend of mine already ordered the cd. what i want to know is if i could upgrade from it, or if i would be force to reinstall everything, which include some software i downloaded from the repositories.

You mean, put the 6.06 cd in, install it and be able to keep all your current settings, and software?  I never heard of doing it that way.

Your best bet, I think is to wait until it's bed time, and then do a 'sudo apt-get update'  and 'sudo apt-get dist-upgrade'

Sleep on it and you should have your upgrade by tomorrow I would assume!

I hope that things are not worse than THAT for you!

---

### Post by confused57 on 2006-08-27
Here's how I upgraded from Breezy to Dapper:
[http://psychocats.net/ubuntu/dapper](http://psychocats.net/ubuntu/dapper)

I think it was 620 Mb that had to be downloaded to complete the upgrade.

You have to have the Dapper alternate cd to dist-upgrade with a cd, you can't do it with the shipit cd(Desktop live cd).

Breezy will be supported with security updates through next April, so I wouldn't be in a hurry to upgrade...especially if Breezy is working well for you.

---

### Post by Anonii on 2006-08-27
> **randell6564 said:**
> You mean, put the 6.06 cd in, install it and be able to keep all your current settings, and software?  I never heard of doing it that way.

Your best bet, I think is to wait until it's bed time, and then do a 'sudo apt-get update'  and 'sudo apt-get dist-upgrade'

Sleep on it and you should have your upgrade by tomorrow I would assume!

I hope that things are not worse than THAT for you!


Well, also dial-up charges more for each minute you are online, so I guess he needs the cd for economical reasons too :)

---

### Post by az on 2006-08-27
The only cd that is shipped is the Desktop cd, from which you *cannot* upgrade.

And downloading 600 megs at 56k takes about a week.

---

### Post by randell6564 on 2006-08-27
> **azz said:**
> The only cd that is shipped is the Desktop cd, from which you *cannot* upgrade.

And downloading 600 megs at 56k takes about a week.

Yes but I believe that he said that he has version 5.05.  So by getting the cd, he will BE upgraded.

And, as far as dial-up, I've never had it so I did'nt have a clue that it takes that long.  DAMN! what a bummer!

---

### Post by lord_zerg on 2006-08-28
> **confused57 said:**
> Here's how I upgraded from Breezy to Dapper:
[http://psychocats.net/ubuntu/dapper](http://psychocats.net/ubuntu/dapper)

I think it was 620 Mb that had to be downloaded to complete the upgrade.

You have to have the Dapper alternate cd to dist-upgrade with a cd, you can't do it with the shipit cd(Desktop live cd).

Breezy will be supported with security updates through next April, so I wouldn't be in a hurry to upgrade...especially if Breezy is working well for you.

thx. that's what i wanted to know. i guess i'll have to get the alternate cd then.
btw, breezy works very well for me.

---

