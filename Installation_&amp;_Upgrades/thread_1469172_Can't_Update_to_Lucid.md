---
title: "Can't Update to Lucid"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by ahaider7 on 2010-05-02
Hi Guys,

I am using ubuntu 9.10 and now want to upgrade to 10.04. The standard way of updating mentioned at [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) is not working for me.

I started the Update Manager, installed all the available package updates but the distribution update button is not appearing as shown below.

[IMG]http://i44.tinypic.com/1zpobuu.png[/IMG]

meaning, there is no mention of new version.

Also, I have tried
```
sudo apt-get dist-upgrade
```but the resonse is:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```Please help

---

### Post by adiron on 2010-05-02
I'm having the same problem

---

### Post by utnubuuser on 2010-05-02
Alt+F2 or terminal:> sudo update-manager -d (y0u might have to have update-manger-core installed for this approach to work)
or 
check out this thread:> [http://ubuntuforums.org/showthread.php?t=1134044]("http://ubuntuforums.org/showthread.php?t=1134044")

Personally, I'll recommend a clean install over an update anytime.  - if you've already got a separate /home partition, upgrading via liveCD is so darn easy and a lot more likely to result in a happy computer/user than an update.

If you peruse the Forum, you'll notice that most problems that people encounter  with Lucid or any other release is whenever they update/upgrade instead of clean/fresh install from liveCD.

If you haven't already got a seperate /home partition, it's relatively easy to create one. - This should be standard for any installation, I'm surprised the Ubuntu installer isn't set up this way as the default installation configuration.

---

### Post by adiron on 2010-05-02
worked great. Thanks!

---

### Post by ahaider7 on 2010-05-02
Thanks [utnubuuser]("http://ubuntuforums.org/member.php?u=370166"), this command works.

sudo do-release-upgrade

---

