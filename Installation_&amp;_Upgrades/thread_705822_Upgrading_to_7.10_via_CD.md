---
title: "Upgrading to 7.10 via CD"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by madkid on 2008-02-23
Hello everyone. I'm a recent newbie to Ubuntu (although it seems to be a walk in the park now) and have just requested 7.10 on CD through the mail with shipit. I was wondering if an upgrade from the 7.04 I have installed currently will make my drivers incapable of running seems how there is a new kernel version in 7.10. Will my drivers need to be reinstalled or recompiled I should say if they were compiled in 7.04? Thanks for any feedback I receive from you guys. :)

---

### Post by Sam Lars on 2008-02-23
Do you have anything special done in 7.04 as far as drivers or modules go?  If not, it should all still work as it did, if not better.  If you happen across anything that stops working, it may be a bug...

---

### Post by madkid on 2008-02-23
Well I just have a few programs installed, some codecs to play my media and a martian driver for my linmodem. I'm sure that all my computers profiles will still be active even through the update and only added to if not touched at all. 

Edit: Also, if there are any problems with my computer after the upgrade, will there be a way to downgrade back to 7.04 without doing a fresh install?

---

### Post by Sam Lars on 2008-02-23
All that should be fine.  How is this linmodem driver installed?

---

### Post by madkid on 2008-02-23
I just had to compile it from source or something like that using the 'make' command in terminal and then use 'make install' to install it. After that it just worked, sort off. There's the minor problem of always needing to manually reactivating the driver every session. But that's beside the point.

---

### Post by Sam Lars on 2008-02-23
You might have to do that again... you might not.  You can try.
Is it a module you load via modprobe?

---

### Post by madkid on 2008-02-23
Nope. It's not a module loaded using modprobe. Here's the command that I use.

```
gksudo martian_modem
```

---

### Post by Sam Lars on 2008-02-23
You could add it to Sessions, or look up other ways to run it at boot...
So, yeah, you should be good on upgrade.  Let us know how that goes.

---

### Post by madkid on 2008-02-23
I'll let you know as soon as it arrives or, if I can't wait, I borrow a friend's CD from school. Thanks for the help and the fast post. I'm liking this community already.

---

### Post by zvacet on 2008-02-24
Do you have alternate CD,because that is only way to upgrade from disc.Do you have separate home partition?if you don´t make one before you go with upgrade.You have guide [here.](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Sam Lars on 2008-02-24
Are you sure?  I think that if you have a CD period you can add it to Synaptic and get packages from it... but like I said you'll have to get updates from the Internet anyway so you might as well just go from there in the first place.

---

### Post by zvacet on 2008-02-24
> Are you sure? 

Yes,I am.It is explained [here.](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by Sam Lars on 2008-02-24
Ah, I see, that makes sense (kind of).  Thanks.

---

### Post by madkid on 2008-02-24
If I install from the Live CD (a normal install) will it be able to keep my home folders from user accounts, the documents inside them, and the user settings of each account? Or is that only for Windows users?

---

### Post by zvacet on 2008-02-25
You will keep your home folder if it is on separate partition.That wa every time you upgrade or reinstall you will be do that on root partition,**and you will not format home partition.** If you don´t have separate home read [this](http://www.psychocats.net/ubuntu/separatehome) how to make one.

---

