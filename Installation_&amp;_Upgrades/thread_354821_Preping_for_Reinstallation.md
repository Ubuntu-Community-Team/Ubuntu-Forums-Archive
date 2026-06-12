---
title: "Preping for Reinstallation"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by Night on 2007-02-06
Hey so I have been using Ubuntu 6.10 64 for a while and have decided to downgrade to the 32 bit version so several applications I commonly use will work with less hassle. The problem is that I don't want to lose my setting for things like Firefox and such. So my question is what is the most efficent way of keeping my settings?

What I am think about doing is loading up a partition manager and splitting my harddrive them copying my home folder over to the new partition. Then when I reinstall just turn the new partition into my /home, will this work? Is there a better way to do this?

---

### Post by lhtown on 2007-02-06
You could email them to yourself or copy them to a disk or a usb stick. You don't need all of them anyway. It is probably better just to copy the ones you really want.

It seems to me that you should be able to do what you are talking about (I have never tried it), but you will want to back up any really important data first, which you should be doing anyway.

---

### Post by RandomJoe on 2007-02-07
I don't like trusting that things will work out when performing partitioning operations on the drive that holds my data!  Besides, it's always good to have backups.  My preferred way is to use rsync to back up to an external (USB/Firewire) hard drive or (what I do now) to another computer over the network.  Just run an occasional rsync again and it updates all the changes.

Whatever you do, be *sure* that when you copy/move your home directory, all the hidden "dot" files get copied too (since that's where a lot of the configuration info is).  There are a number of common copy methods that don't get them by default.

---

