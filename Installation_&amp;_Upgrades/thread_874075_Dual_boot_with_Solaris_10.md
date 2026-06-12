---
title: "Dual boot with Solaris 10"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by edwardswyco on 2008-07-29
I am new to Linux and Unix. A couple weeks ago, I decided to get rid of Windows and installed Ubuntu. I love it!

A friend recommended that I learn to play around with OpenSolaris 10 and I installed it...and then only Solaris would boot. Learning from blogs I have found, I reinstalled Ubuntu, took down the information from the menu.lst file:

title Linux
root (hd0,1)
kernel /vmlinuz root=/dev/hda2 ro

and then tried to install Solaris again. After the install, I opened Solaris’ menu.lst file and added my Ubuntu information. After restarting, it gave me the option for either OS, but when I chose Linux, it told me that it was an unknown file type and could not load. I tried fooling around with different things, but basically had the same result – Linux would not boot. I decided to just install Ubuntu on the drive, although I left about 20GB open in case I figured anything out.

I noticed that both times I installed Solaris, it erased my Linux swap drive. Always starting with four partitions, I would end up with only two. Upon further research, at Linux.com, an article said that Solaris and Linux do not like to exist on the same hard drive, so they suggest to install on separate hard drives.

If I were to slap on a slave drive and install Solaris on one, will this allow me to dual boot? I don’t want to lose my Linux stuff again (it’s backed up, but just an inconvenience). 

Thanks for any advice!!

---

### Post by DGortze380 on 2008-07-29
I know nothing about solaris, but maybe this will help. Seems like you're simply having issues with the boot loaders.

[http://max.berger.name/howto/solaris/Linux+Solaris.jsp#boot](http://max.berger.name/howto/solaris/Linux+Solaris.jsp#boot)

---

### Post by ladr0n on 2008-07-29
My suggestion (and what I plan to do in the computer I am building) is to install two hard drives.  Plug what will be the slave drive into the computer as the only hard drive, install Solaris on it, and let it get nice and comfortable.  Then plug in the soon-to-be master drive by itself, and install Linux.  Then plug in the two drives together, and set up an entry in the Linux grub's menu.lst to chainload the slave drive like so:
```
title OpenSolaris
rootnoverify (hd1,0)
makeactive
chainloader +1
```
You may have to tweak with it a little, but in theory that should work.

---

### Post by edwardswyco on 2008-08-01
I appreciate the help!!

I'll give it a try,
Jason

---

