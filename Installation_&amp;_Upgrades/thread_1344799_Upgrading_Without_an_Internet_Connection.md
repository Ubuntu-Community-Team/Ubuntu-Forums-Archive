---
title: "Upgrading Without an Internet Connection"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by sufjanfan on 2009-12-03
Hello,
I have had Ubuntu 9.04 for a little while now on my Gateway laptop. However, I live out in the country and have dialup, so I have been unable to establish an internet connection. I would like to upgrade to 9.10, but I am unsure how to do so on the laptop itself. If there is way to download from a seperate computer and upgrade without losing what I have, I'd like to know how. I'm hoping this will fix many of the graphics bugs I am experiencing.

---

### Post by quixote on 2009-12-04
I haven't tried this myself, but the Ubuntu instructions are to download the *Alternate* server install CD, and then to upgrade using that.  I'm never quite clear on why they want you to use the server version in this case, so maybe I've misunderstood something, but that's what it says.  Instructions are [here]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD").  If it's hard for you to download that as well, then I think your situation is exactly the one for which the free CD shipping was invented. :D  [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)  or [https://shipit.kubuntu.com/](https://shipit.kubuntu.com/)

---

### Post by Bartender on 2009-12-04
It seems like the most reliable advice is to install clean rather than upgrade.
I know that's not what you wanted to hear but a lot of people are saying it.

---

### Post by quixote on 2009-12-04
Two things you could do to make a clean install a bit easier:

1) Make a CD of your currently installed programs using aptoncd. (It's in synaptic.)

2) Make a copy of your whole /home/*you* directory to external media or another partition or the like. (Obviously, not a partition involved in the new install!) Then, when you do your new install, **make a separate partition for /home**.  Once you have your new install, the aptoncd will get your specially installed programs back.  And copy your old /home/you over to replace the new /home/you (be sure the user name is the same!), and all your preferences etc will be right as they were.

---

