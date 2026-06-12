---
title: "MX6453 Bios Bug with Gibbon"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by AgentSmith15 on 2007-11-06
Hello,

I am trying to install Gutsy Gibbon on my Gateway MX6453 laptop. Right after the kernal gets loaded of the dvd/cd on the install cd I get a message like.
```
PCI: BIOS BUG #81[49435000] found
```

Then the screen goes black and the live cd never boots. 

AMD Turion 64x2  ( TL-52)
ATI Radeon Xpress 1100

I never had a problem with Feisty Fawn?

---

### Post by AgentSmith15 on 2007-11-07
I've googled the error and apparently there are many other people having this problem with Debian based systems. I would really love to be able to have linux running again, so if you have suggestions or questions feel free to ask. Please :)

---

### Post by Truefire on 2008-03-15
I have the same laptop, been using Ubuntu for awhile.

What you need to do is download the "Alternate Ubuntu Installer"
on the Ubuntu Download page, there's a Alternate checkbox.

It's not a liveCD, but still simple.
Don't freak with the 'old' look. It installs the same.
And when you want to upgrade, run

sudo update-manager -c

instead of a new disc install. 


If you don't know how to get Compiz (Fancy effects) running...
All you need to do is 

sudo apt-get install xserver-xgl

then restart.

Voila'.


:guitar: Rock on.

We have the same laptop, so if you have probs, PM me.

---

### Post by AK Dave on 2008-05-08
Same laptop. Gutsy and Hardy have no problems installing from the LiveCD, either 32bit or 64bit. Currently running Hardy64. Just last night I made a persistent LiveUSB of Hardy32 and the first platform I tested it on was the MX6453 laptop.

---

