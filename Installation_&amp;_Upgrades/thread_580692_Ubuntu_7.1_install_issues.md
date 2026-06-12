---
title: "Ubuntu 7.1 install issues"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by varun_saa on 2007-10-19
I have downloaded Ubuntu 7.1 and tried to install.

Here is how it went.

I have Mandrive 2008 installed on a 80GB HDD.

I have about 40GB free.

I want install Ubuntu on about 20GB.

I start to install :

I have 2 choices :

1. guided install using largest free available space

2. manually ( I prefer ).

The 1st won't because work I want it use only
20GB of the free space. How to make it do ???

The 2nd I use and I create : root , swap & home.
So far good.

What I see is that the it partition manager does not allow you
to choose the swap partition. As when I proceed I see
that it has selected also my swap from mandriva2008
installation. So it wants to use 2 swap partition . Hmm

Is there a way out , I don't know ?

I don't want it use my mandriva2008 swap.

I always use seperate swap for each individual distro
and I have no such issues  with other distros.

The end results - I could not install.

Is there is way out or have I made any mistake, I don't
know?

Please guide me.

Thanks in advance

Varun

---

### Post by logos34 on 2007-10-19
There's a limit of 4 primary partitions per disk.  That may be why it won't let you make another swap/install fails.  I would suggest you use the mandriva swap, but if you must have a separate one for ubuntu then you'll have to make that 20 GB space an **extended** partition and put /, /home and /swap inside as **logical **partitions. 

[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-9.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-9.html)
[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-10.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-10.html)
[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-11.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-11.html)
[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by jespdj on 2007-10-19
Note: The version number is 7.10: seven point ten, which indicates October (month 10) of the year 2007. It's not "7.1".

---

