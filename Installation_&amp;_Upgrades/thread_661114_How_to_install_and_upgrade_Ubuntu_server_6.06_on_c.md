---
title: "How to install and upgrade Ubuntu server 6.06 on closed network"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by chip.ling on 2008-01-07
Dear all,

I have successfully installed Ubuntu 6.06 server version on my home pc. Then I update and upgrade it via apt-get.

And after that, I further install a couple of packages via the "apt-get install" command.

I noticed that when I issue the apt-get install command, the OS gets some of the packages through the internet.

Now I want to install the same thing to a pc in a closed environment (i.e. no internet access at all)

So how can I achieve that?

Rgds,
Chip

---

### Post by reckless2k2 on 2008-01-07
it's not going to work. the flip side is that if you're network is closed to the outside world you probably don't have to update. haha. without internet connection though, it's very hard to manage updates with a flash drive or such.

---

### Post by chip.ling on 2008-01-07
> **reckless2k2 said:**
> it's not going to work. the flip side is that if you're network is closed to the outside world you probably don't have to update. haha. 

It's true if you just use the LAMP out from the box. However, I need to install a little softwares to it.

> **reckless2k2 said:**
> without internet connection though, it's very hard to manage updates with a flash drive or such.

I agree that it is not easy but it should be do-able.

Rgds,
Chip

---

### Post by reckless2k2 on 2008-01-07
oh it is do-able but only through vast queries on ubuntu updates and then getting them all onto flash or external usb drives and then installing them on the box.

---

### Post by zvacet on 2008-01-07
Maybe you find [this](http://www.nonetdebs.homeip.net/) helpfull.

---

### Post by chip.ling on 2008-01-09
> **zvacet said:**
> Maybe you find [this](http://www.nonetdebs.homeip.net/) helpfull.

Thanks for the reply. I take a look at the link you provided. Not exactly what I want but thanks for the help anyway.

I don't want to go thru another web site since you don't know when the site is not accessable.

After some manual reading and testing, I think I find a solution. Will try it out tomorrow.

Thanks a lot.

Rgds,
Chip

---

