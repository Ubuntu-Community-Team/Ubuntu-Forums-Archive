---
title: "dapper install stops after booting from ISO cd"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by snitramc on 2007-05-02
I have a Dapper ISO CD I have used to install on an old (2004) Dell Latitude laptop. It worked fine. (My luddite 18 year old daughter is running it now, and its been 3 months and she hasn't blown up the install yet (like with winblows) and so I think we have a winner!)

Now I want to install Dapper on a new laptop I bought. I cold boot fine to the CD, and get the Install choice. When I choose Install, it loads all the stuff I expect to see - Booting the kernel, loading swap, starting X, all those first few things run fine off the CD. After it runs all that, it goes to a black screen with a white cursor in the ULC, and then a few seconds later, the CD stops spinning and the install just dies. Do I need a different kernel, this is a Duo Core Intel.

Everex 2052T Step Note Laptop
Proc=Intel 2050T Duo Core @ 1.60GHz
Mem=1GB
HDD=80GB (Partitioned into a 30GB partition for winblows vista and a 30GB ext2 for Ubuntu)

I'm willing to scratch the winblows partition entirely if you think it'll help, but I cannot see why that would be an issue. I partitioned the HDD using Paragon Partition Manager Personal Edition 8.5 (licensed) so I think I have real actual partitions. But I would like to have a dual boot machine when I am done so I can do some stuff @ work.

---

### Post by zvacet on 2007-05-03
Maybe is your graphic card.When you boot up you will see at the bottom F1......buttons.F1 is for help (if I remember correctly) and one of others is for graphic adjustment.Try with that option.That is all I can think of right now.

---

### Post by snitramc on 2007-05-04
I have tried running the live CD using 7.04, 6.10 and 6.06. I have tried running the live CD off the internal DVD drive and a USB attached drive. I have run it in safe graphics mode and not. It  sets up swap, locales, automatic login, hostname, keyboard, configures X, gnome-panel-data and screen saver, Preconfigures etc/modules and networking, and then the disc stops spinning and just sits there. Every time. I thought about downloading a 64nit version to try that, but all the links are broken. Anybody else have any ideas?:(

---

### Post by snitramc on 2007-05-08
Ok,  now I see it is the 8139too NIC drive causing problems. What a pain. I guess it's going to be many days before I get ubuntu running on this box.

---

