---
title: "How to install ATI graphics drivers (no additional drivers under software sources)?"
date: 2012-11-20
forum: Installation &amp; Upgrades
---

### Post by Mr.JJ on 2012-11-20
I am using ubuntu gnome remix 12.10 with ATI mobility radeon  HD 4300 graphics card. Software sources do not show any additional  drivers. How do I install the graphics drivers for my system?
  $ lspci | grep VGA 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4300 Series]

---

### Post by Bucky Ball on 2012-11-20
Have you done an update since install and checked again?

---

### Post by Mark Phelps on 2012-11-20
> **Mr.JJ said:**
> I am using ubuntu gnome remix 12.10 with ATI mobility radeon  HD 4300 graphics card. Software sources do not show any additional  drivers. How do I install the graphics drivers for my system?
  $ lspci | grep VGA 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4300 Series]

You DON'T.  

AMD dropped Linux driver support for the HD 2x/3x/4x series this summer.  Ubuntu 12.10 uses a newer version of the X-server than those drivers support, so now, you are limited to using the open-source Radeon driver -- which is installed by default.

---

### Post by QIII on 2012-11-20
Hey, Mark!  ATI again.  Grumble....grumble....

Mr.JJ -- you may see "solutions" to this, but they are not "solutions" at all.  They require you to downgrade X Server and use an older proprietary driver.

My first recommendation is to use the open source driver as Mark Phelps suggests.  In most cases it is absolutely fine.  It also will provide dependable and predictable support in the future.

But if you absolutely must use the proprietary driver, I would suggest using 12.04 LTS over breaking 12.10.

---

### Post by Mark Phelps on 2012-11-20
> **QIII said:**
> Hey, Mark!  ATI again.  Grumble....grumble...

You're right about that -- and it's not going to get better any time soon.

I think I saw something online about AMD firing the whole Linux support team -- so much for Linux drivers (if that is true)!

---

### Post by QIII on 2012-11-20
Haven't seen that in my Linux Foundation newsletters, but you never know...

---

### Post by Mr.JJ on 2012-11-21
Thank you all. I was of the impression that mobility radeon HD is different from the normal HD 4.xx series. AMD website shows the 12.6 driver version as the latest for my card and says "for Xorg 6.9 to Xserver 1.12 and Kernel version up to 3.4". 

In case I need to install that driver how do I go about it? Downgrade both X.org and kernel (I am using Xorg 1.13 and kernel 3.5.0.17) and install it from the site? Is it worth it?

> **Mark Phelps said:**
> I think I saw something online about AMD firing the whole Linux support team -- so much for Linux drivers (if that is true)!

Phoronix!

---

### Post by mastablasta on 2012-11-21
you mean this article?: [http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTU](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTU)
 
how you do it is that there is a PPA that will do that for you. doesn't work with all cards and some people had issues afterwards or after additional updates...:
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
 
more here (if something breaks): [http://askubuntu.com/questions/203232/radeon-hd-2000-3000-4000-on-12-10-quantal-fglrx-legacy-12-6-unsupported-wh](http://askubuntu.com/questions/203232/radeon-hd-2000-3000-4000-on-12-10-quantal-fglrx-legacy-12-6-unsupported-wh)
 
the funny thing is they are called legacy drivers yet some of these cards were still being sold in the shops just recently. they shouldn't do this if you ask me. but i guess they are tight with money. only this doens't help them. with more power users using their card there would also be more money. and let's not forget that linux people are often one of the opinion leaders.

---

### Post by bogan on 2012-11-21
Hi!, **Mark Phelp**s,

You Posted:>  you are limited to using the open-source Radeon driver -- which is installed by default.Is that what is shown as "radeon" by:```
 lspci -nnk | grep -iA3 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:9644]
    Subsystem: ASUSTeK Computer Inc. Device [1043:84c8]
    Kernel driver in use: radeon
    Kernel modules: radeon
```That data is not mine.
Would you please look at this thread:
[http://ubuntuforums.org/showthread.php?p=12365621#post12365621](http://ubuntuforums.org/showthread.php?p=12365621#post12365621) as I am not competent to advise the OP, beyond guesswork.

Chao!,** bogan.**

---

