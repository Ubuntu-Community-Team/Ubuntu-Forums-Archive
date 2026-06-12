---
title: "I have a very old computer(12 years)..."
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by spi_ on 2011-11-26
hello,
  
I have a very old computer(12 years)...
My computer is:
AMD-K6-2(tm)   475 Mhz 3D processor
AT/AT COMPATIBLE
176Mb RAM
with cmov CPU...

I want to install in my HardDisk some version of (U,K,X,L,M,E,buntu), what version?
and I  have some other questions, how can I install Firefox, Google Chrome and Skype? I want it is "Persistence"?

I wait for your answer...
  
thanks a lot...

---

### Post by Lars Noodén on 2011-11-26
With the low amount of RAM and such you might try Lubuntu first.  Puppy Linux might also be a good choice.

---

### Post by IWantFroyo on 2011-11-26
Just to add a little:
Puppy Linux is a fork of Ubuntu 10.04, and really fast. You can still get many Ubuntu programs.

Also, if you want to try Arch Linux, that would probably be one of the fastest things you can run on it (providing you stick with the command line).

To install software, most Ubuntu derivatives have a GUI package manager. Something that will work on all is:
```
sudo apt-get install *application name here*
```

---

### Post by ajgreeny on 2011-11-26
You may have trouble with the installation process for Lubuntu, as there will possibly be insufficient ram to both run the GUI, and install the OS.   I think you may need the alternate-install-CD for Lubuntu from [http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/lubuntu-11.10-alternate-i386.iso](http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/lubuntu-11.10-alternate-i386.iso) which uses the older debian installation method, not so simple as the live CD, but still fairly easy to use.

Try the live CD first if you prefer that, and if that is not successful use the alternate-install-CD.

I have used puppy but never installed it; always ran it as a live CD/USB.  It runs entirely from ram so is fast, but it runs always as root, which might be dangerous if you have any banking etc to do online.

---

### Post by whatthefunk on 2011-11-26
Lubuntu will struggle on that I think.  Try Puppy.  Maybe Crunchbang?

---

### Post by snowpine on 2011-11-26
I recommend recycling or donating it and upgrading your hardware. There are some great after-Thanksgiving sales going on (if you live in the USA) and there are always great deals on Craiglist, Freecycle, etc.

Here's a helpful link:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by MAFoElffen on 2011-11-26
> **snowpine said:**
> I recommend recycling or donating it and upgrading your hardware. There are some great after-Thanksgiving sales going on (if you live in the USA) and there are always great deals on Craiglist, Freecycle, etc.

Here's a helpful link:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
LOL!  And I volunteer at one of those recyclers. Here's my 2 cents on Light-Linux under 128MB RAM.

If you go with Lubuntu or Xubuntu- Don't use the normal install disks/use the Minimal Install CD.  It us text based and will run in 64MB.

Xubuntu/XFCE- the XFCE desktop uses less memory that the Xubuntu desktop. Watch how many apps you have open at once.  With Xubuntu, it is slow, it swaps to disk at lot and when it hits that memory limits, it panics and things get weird. Stlll functional. You just have to be aware of what's running and be patient as there's a lagl etween when you ask something and how long it takes to respond. This runs better under 256MB-512MB

Lubuntu- Less overhead than Xubuntu. Runs faster that Xubuntu and XFCE.  Still panics when you bounce off the limited memory, but with more windows open. so less often. This runs bettter on 256MB+.

Puppy- Faster than Xubuntu and Lubuntu!!! There are 2 branches of Puppy. --> I use the branch based on Lynx.  Compared to Lubuntu and Xubuntu- a bit limited on functionality. They removed some things for the sake of lowering the overhead and speed. Very functional for what it is and it's purpose... 

Ubuntu CLI. Command Line. Runs under 64MB. Very fast. Full function. No GUI/only Command Line. Everything is there, but user has to know how to exist there (know commandline Linux). I have text based Browsers loaded, editors, etc.  Targeted user needs to know what they are doing.

Others?
[Light Linux Distributions - Hardware Testing (RAM)]("http://ubuntuforums.org/showthread.php?t=1582027&highlight=puppy+linux")

---

