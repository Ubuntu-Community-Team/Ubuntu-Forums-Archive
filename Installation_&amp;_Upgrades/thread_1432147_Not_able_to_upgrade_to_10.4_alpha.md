---
title: "Not able to upgrade to 10.4 alpha"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by harsh1kumar on 2010-03-17
I am running ubuntu 9.10 system. I want to upgrade it to ubuntu 10.4 alpha. But when I try the command "update-manager -d", I dont see the option indicating that a new release is available. Please tell me what to do??

---

### Post by mcooke1 on 2010-03-17
The  1st Beta of 10.04 is due today so upgrading to the alpha is not advisable at the moment.

---

### Post by phillw on 2010-03-17
> **harsh1kumar said:**
> I am running ubuntu 9.10 system. I want to upgrade it to ubuntu 10.4 alpha. But when I try the command "update-manager -d", I dont see the option indicating that a new release is available. Please tell me what to do??

Are you sure you know the risks of running a test system ?

[http://ubuntuforums.org/showthread.php?t=1431650](http://ubuntuforums.org/showthread.php?t=1431650)

In fact, I'd strongly advise you read all the stickies on that forum

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

and, if you are **sure** you have backups for if it breaks then..

```

sudo apt-get update
sudo apt-get dist-upgrade

```

It'll take a while, so be patient !!

/edit
Oh, if the above two commands don't get the test for 10.04, this will
```
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

```

(I did a clean install on a new partition, then rsync'd my 9.10 /home over, so that I kept 9.10 for when 10.04 testing broke)


Regards,

Phill.

---

### Post by harsh1kumar on 2010-03-18
Thanks for the reply. I am now trying this. I understand the risks of upgrading to a alpha release. I am just testing on one of my machines.

---

### Post by chill32 on 2010-04-01
do im downloading it becuase i cant wait for the official release

---

### Post by Mark Phelps on 2010-04-02
Please post any problems with 10.04 to the proper testing forum: Development & Programming, Lucid Lynx testing.

Please do not tack on more posts to this thread here.

---

