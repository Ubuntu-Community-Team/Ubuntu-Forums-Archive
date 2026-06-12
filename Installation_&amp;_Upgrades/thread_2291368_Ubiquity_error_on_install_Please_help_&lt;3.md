---
title: "Ubiquity error on install? Please help &lt;3"
date: 2015-08-19
forum: Installation &amp; Upgrades
---

### Post by robhockey19 on 2015-08-19
I'm installing Ubuntu 14.04.3 onto my desktop using a CD that I burned the .iso onto. It boots fine and everything works, then when I get to the partitioning menu where you select your boot root, partion to install on, etc... it freezes and gives me this error. I've tried it with Ubuntu 15.04 as well. Any help is appreciated. Thanks a lot!

Here is the error:

[http://imgur.com/3z0xV5g](http://imgur.com/3z0xV5g)

[IMG]http://imgur.com/3z0xV5g[/IMG]

---

### Post by VMC on 2015-08-19
How were you selecting your partitions? [lvm, ext4 "/", "/home", etc]

---

### Post by robhockey19 on 2015-08-19
It didn't even let me select anything. I went to hit the + button and then it gave me the error. I redid it all and tried to hit the change button, same thing.

---

### Post by VMC on 2015-08-20
Looking again at your error. It references [launchpad bug 1064151]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1064151"). Go there and see if that's what you have.

---

### Post by robhockey19 on 2015-08-20
I did what the last person said and it worked! Thank you very much!

---

### Post by VMC on 2015-08-20
The authorities want you to mark this thread solved if your satisfied. Top under "Thread Tools".

---

