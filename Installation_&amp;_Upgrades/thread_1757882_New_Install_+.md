---
title: "New Install +"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by boysha on 2011-05-13
I hope this is not going to sound stupid or dumb...
I would like to install a new version of Ubuntu. I am thinking, if I was to keep the /home the same as it is right now, with all my files that are there now and just recreate / and SWAP, I should be able to install clean Ubuntu that has my old Home partition with all my files, right?
If not, please explain.
Thanks!

---

### Post by NormanFLinux on 2011-05-14
If you do a clean install, you'll erase your files. Are you going to do a back up of them first? You can save your files and settings only IF you upgrade within Ubuntu from an existing version to a new one.

Hope this helps.

---

### Post by boysha on 2011-05-14
Thanks. I was under the impression that if I was to leave my old Home and reformat/ create other partitions that I will be left with a new version and old Home.
Thank you.
Cheers!

---

### Post by Hedgehog1 on 2011-05-14
> **NormanFLinux said:**
> **If you do a clean install, you'll erase your files.** Are you going to do a back up of them first? You can save your files and settings only IF you upgrade within Ubuntu from an existing version to a new one.

**This is not correct**.  You can do a clean install and keep you data **if you have a seperate '/' and '/home' partition**.  I do this, and many of the forums power users do it as well. It gives you the best chance of a clean 'upgrade' by actually doing a clean install of '/' and leaving the '/home' partition untouched.


First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

p.p.s. Backing up your data 'just in case' a big install or upgrade is, however, always a good idea.

---

### Post by YesWeCan on 2011-05-14
BUT...you lose everything in /

So you would need to reinstall all applications you use.
You would need to reconfigure any global config files that you have changed (in /etc)
And maybe some other stuff.

So just be aware of this.

You can use 'dpkg --get-selections > beforefile' to list all your apps. into a file named beforefile. This may help when reinstalling. After the new install, run it again and then do a 'diff beforefile afterfile' to see what has changed.

Canonical recommend doing a upgrade rather than a clean install and I would recommend the same unless you have nothing important to lose.

---

### Post by Hedgehog1 on 2011-05-14
YesWeCan,

boysha wants to start with a clear '/' - and keep '/home':

> **boysha said:**
> 
I would like to install a new version of Ubuntu. I am thinking, if I was to keep the /home the same as it is right now, with all my files that are there now and just recreate / and SWAP, I should be able to install clean Ubuntu that has my old Home partition with all my files, right?

An upgrade is not going to get him that result.


***The Hedge***

:KS

---

