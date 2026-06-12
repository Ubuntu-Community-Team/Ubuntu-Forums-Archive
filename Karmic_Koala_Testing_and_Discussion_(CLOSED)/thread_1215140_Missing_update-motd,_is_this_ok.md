---
title: "Missing update-motd, is this ok?"
date: 2009-07-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lachild on 2009-07-16
Hey everyone,

It appears that during one of my upgrades update-motd was removed and seems to be needed when upgrading update-manager.  I double checked and it seems that all the package lists (like ubuntu-desktop, ubuntu-standard, etc) are all still installed.  I was able to install the missing missing package manually, but if this is a required package by something apart of the standard desktop, shouldn't this package be a dependency of one of these package lists?  Not sure how important this is or if anyone else noticed, but should this be filed as a bug?

---------------------------------------------------------------------------
Setting up update-manager (1:0.124.4) ...

dpkg: error processing update-motd (--configure):
 no package named `update-motd' is installed, cannot configure
---------------------------------------------------------------------------

Thanks
LaChild

---

### Post by wayne_cat on 2009-07-16
keep an eye on this:

[https://bugs.launchpad.net/ubuntu/+source/update-motd/+bug/400462](https://bugs.launchpad.net/ubuntu/+source/update-motd/+bug/400462)

---

### Post by lachild on 2009-07-16
Thanks :D

---

### Post by autocrosser on 2009-07-16
I just got the error & tried reinstalling twice--second time it "took"--you might log out/in & try again.

---

### Post by wayne_cat on 2009-07-16
> **autocrosser said:**
> I just got the error & tried reinstalling twice--second time it "took"--you might log out/in & try again.

interesting .... I thought that update-motd is a new feature (at least for Karmic) ... I have checked my Karmic installation when I saw this thread ... not installed ... got the same error after running "apt-get dist-upgrade"... is your Karmic system an updated Jaunty?

---

### Post by autocrosser on 2009-07-16
Yes--this one is a "day-one" Karmic----I have not done a fresh install one yet--I normally wait until beta 4 or so for that.....So I would say that there is a lot of "cruft" from Jaunty...

---

### Post by ronacc on 2009-07-16
I've got a fresh install at A2 due to a self infilcted wound with my day-one install , on  update via synaptic update-motd errored , on the second try it completed .

---

### Post by wayne_cat on 2009-07-16
yet another "me too" bug report  :biggrin:

[https://bugs.launchpad.net/ubuntu/+source/update-motd/+bug/400462/+affectsmetoo](https://bugs.launchpad.net/ubuntu/+source/update-motd/+bug/400462/+affectsmetoo)

Hint:

"This bug affects me too" ... so useful

---

### Post by Slug71 on 2009-07-17
Synaptic says 'superseded by pam-motd...'?

---

### Post by pferraro on 2009-07-17
Correct me if I'm wrong, but the only package with a dependency on update-motd is ec2-init - so unless you've running cloud services, you can remove this package.

---

### Post by wayne_cat on 2009-07-17
[https://bugs.launchpad.net/ubuntu/+source/update-motd/+bug/400462](https://bugs.launchpad.net/ubuntu/+source/update-motd/+bug/400462)

```
Changed in update-motd (Ubuntu):
status:         Confirmed &#8594; Fix Released 
```

---

### Post by ranch hand on 2009-07-17
Could someone please tell me what this motd.sh does?  I have looked all over and can't find out what the devil it is for.

There is a reference that I ran into for a daemon and I have run every command I could think of but get nothing.  Man motd gets nothing.  Search engine gets package lists but no clue what they do.  It is starting to get on my thungas.

---

### Post by wayne_cat on 2009-07-17
> **ranch hand said:**
> Could someone please tell me what this motd.sh does?  I have looked all over and can't find out what the devil it is for.

There is a reference that I ran into for a daemon and I have run every command I could think of but get nothing.  Man motd gets nothing.  Search engine gets package lists but no clue what they do.  It is starting to get on my thungas.

Just a stupid "message of the day" tool

from:

[http://packages.ubuntu.com/de/karmic/update-motd](http://packages.ubuntu.com/de/karmic/update-motd)

```
This package installs a script in /etc/profile.d that dynamically generates a message-of-the-day by running scripts installed in /etc/update-motd.d, in lexical order.
```

---

### Post by ronacc on 2009-07-17
and who's great idea was it to make that part of a default install ????

---

### Post by pferraro on 2009-07-17
> **ronacc said:**
> and who's great idea was it to make that part of a default install ????

It's not part of the default install.

---

### Post by ronacc on 2009-07-18
then how the heck did I get it ? I didn't install it  and I don't have ec2-init (referenced above) installed.

---

### Post by ranch hand on 2009-07-18
> **wayne_cat said:**
> Just a stupid "message of the day" tool

from:

[http://packages.ubuntu.com/de/karmic/update-motd](http://packages.ubuntu.com/de/karmic/update-motd)

```
This package installs a script in /etc/profile.d that dynamically generates a message-of-the-day by running scripts installed in /etc/update-motd.d, in lexical order.
```
OH MY GOD.  I DON'T HAVE THAT!!!!!!!!

I think I could live without knowing that even existed.

Thanks, I really hate it when I can't figure out what I am missing.  I am not missing this.  I just don't have it.

---

