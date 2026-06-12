---
title: "Howto re-install (or upgrade) Gnome *and* KDE"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by kline on 2006-08-20
In trying to copy an audio CD, I keep running into problems with Synaptic and lots of binaries over missing or non-seen or "unresolved" Gnome  andor KDE libraries.   apt-get is no better than the GUI front-ends.   

Is there some magic apt-get command to install what Synaptic refuses to handle?   Or is this stuff  just **broken**?  E.g., I  can't install k3b or other KDE desktop stuff.  Can apt-get reinstall stuff and if so, exactly how!



](*,)

---

### Post by nanotube on 2006-08-20
instead of apt-get, try using "aptitude". it is basically like apt-get, but more powerful, and is usually smarter about resolving dependency problems.

so you should try, for example
```
sudo aptitude update
sudo aptitude install k3b

```

and see what it says.

if "all else fails" (but not before :) ), you could also try 
```
sudo aptitude reinstall ubuntu-desktop
```
to reinstall gnome... but i think it's better to avoid such drastic measures.

---

### Post by aysiu on 2006-08-20
Dependency problems usually stem from conflicting repositories. I'd [get a fresh list](http://www.psychocats.net/ubuntu/sources) and then try again.

---

### Post by kline on 2006-08-20
> **nanotube said:**
> instead of apt-get, try using "aptitude". it is basically like apt-get, but more powerful, and is usually smarter about resolving dependency problems.

so you should try, for example
```
sudo aptitude update
sudo aptitude install k3b

```

and see what it says.

if "all else fails" (but not before :) ), you could also try 
```
sudo aptitude reinstall ubuntu-desktop
```
to reinstall gnome... but i think it's better to avoid such drastic measures.

The most aggressive things are for the last, I agree.  But altho, there was no trouble with the first command, aptitude doesn't know about

[INDENT]
root@localhost:/var/lib/dpkg# sudo aptitude install k3b
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "k3b"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
[/INDENT]

Maybe I should get a new sourse.list as Aysiu suggests.  Where/howto get this list?

---

### Post by mlind on 2006-08-21
These are URL's for (main mirror) Ubuntu repository. With all components enabled.
```

# Ubuntu (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu **dapper** *main restricted universe multiverse*
deb http://archive.ubuntu.com/ubuntu **dapper-updates** *main restricted universe multiverse*
deb http://security.ubuntu.com/ubuntu **dapper-security** *main restricted universe multiverse*

```

For better speed, you should choose closest mirror from here
[https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

(Don't forget to update package lists after editing sources.list).

---

### Post by kline on 2006-08-21
> **mlind said:**
> These are URL's for (main mirror) Ubuntu repository. With all components enabled.
```

# Ubuntu (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu **dapper** *main restricted universe multiverse*
deb http://archive.ubuntu.com/ubuntu **dapper-updates** *main restricted universe multiverse*
deb http://security.ubuntu.com/ubuntu **dapper-security** *main restricted universe multiverse*

```

For better speed, you should choose closest mirror from here
[https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

(Don't forget to update package lists after editing sources.list).



I've found a mirror in my locale, and the three directories  *multiverse, restricted,universe*.  But how to I use, say,    
[INDENT]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted[/INDENT]

(I've been a hacker for years but am new to the details of Debian)

---

### Post by kline on 2006-08-21
[FONT="Times New Roman"][SIZE="4"]**Sorrrrrrry**[/SIZE], gents! With a snipppnet from googling around, I looked in my sources file and figured it out. Things are    flowingin now, for the past several minutes.  Then I'll see if other things work, like "k3b".

gary kline

PS:   Altho some people might disagree, I'm reaaly *not* an imbicile....


[/FONT]

---

### Post by mlind on 2006-08-21
> **kline said:**
> I've found a mirror in my locale, and the three directories  *multiverse, restricted,universe*.  But how to I use, say,    
[INDENT]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted[/INDENT]

(I've been a hacker for years but am new to the details of Debian)

There's actually four components: *main*, *restricted*, *universe* and **multiverse**. The original problem is that you're currently missing universe and multiverse from your sources.list.
That's why package manager cannot find some of the required dependencies.

You can specify all of the components in one line like I did, or in separate lines like default sources.list seems to do.

---

### Post by kline on 2006-08-21
After poking around, I  can see why mising multiverse might cause havoc.  

/*
  In one sense, having an over-larded OS with lardy software would get past a lot of these dependency problems.  Still, to me, the unix paradigm is  just peachy.  &c.

  */

thanks for your help!

---

### Post by skeeterflea on 2006-09-02
I am having a similar problem, what was the fix for this?
Thanks

---

