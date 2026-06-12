---
title: "Is jaunty to lucid possible?"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by stardustdk on 2010-03-22
Hey all.

I know people that is running Jaunty for now and is wondering if it is possible after the 29. April to upgrade directly to Lucid?

Ie with changes in sources.list.

If yes - how? 
I imaging the use of apitude.

Is it safe and/or wise?

Or do I have to upgrade the trational way? 
That is Jaunty->Karmic->Lucid?

Best regards

Stardustdk

---

### Post by phillw on 2010-03-22
> **stardustdk said:**
> Hey all.

I know people that is running Jaunty for now and is wondering if it is possible after the 29. April to upgrade directly to Lucid?

Ie with changes in sources.list.

If yes - how? 
I imaging the use of apitude.

Is it safe and/or wise?

Or do I have to upgrade the trational way? 
That is Jaunty->Karmic->Lucid?

Best regards

Stardustdk

Hi

you cannot go 9.04 --> 10.04 directly.

There are a few changes that have taken place in the releases, firstly grub has moved up a revision and ext4 is now the default filesystem. 

You can do 9.04 --> 9.10 --> 10.04, but I'd advise you make a separate home partition and then do a clean installation of 10.04.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Now, if you make /home as ext4 (the newer filesystem) you may well find that grub legacy cannot see it (this is NOT good). If you are going to do this, upgrade your grub-legacy to grub2, a nice HowTo is over here --> [https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)

BEFORE you make the new /home partition in ext4. (Grub2 will happily work on your existing 9.04 system)

Regards,

Phill.

---

### Post by ajgreeny on 2010-03-22
To be perfectly honest, unless you have lots of time to go through the two needed upgrades of distro, and the ability to troubleshoot the potential problems that occur each time, I would think it is much easier and quicker to backup everything and start afresh with a clean install of 10.04, either now to the beta, or in 4/5 weeks time, when the final will appear.

---

### Post by stardustdk on 2010-03-22
Thanks for the answers.

They were as expected. Hrm.... 

Will try to persuade the person to let me make a fresh 10.04 final install.

btw: / and /home are both ext3 partitions at the moment.

Best regards

Stardustdk

---

