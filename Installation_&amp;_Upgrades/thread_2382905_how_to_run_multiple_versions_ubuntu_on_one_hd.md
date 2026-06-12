---
title: "how to run multiple versions ubuntu on one hd"
date: 2018-01-18
forum: Installation &amp; Upgrades
---

### Post by seekertom on 2018-01-18
I have a 1 tb hd with 93% free. One partition with working 17.04 installed.
I want to be able to install and run different versions of linux/ubuntu on that one hd.

How to set up new partitions and how to boot from each?
how to backup any/all partitions, possibly to a live cd?

thanks for your help!
st:confused:

---

### Post by cruzer001 on 2018-01-18
Running multiple flavors/versions of Ubuntu is fairly easy.  The same boot loader is used.  Running different linux distro's can get tricky.  Each distro you load will install its own boot loader.  Maybe compatible with everything, but maybe not.  I say make it easy on yourself and stick with the ubuntu flavors (Lubuntu, Xubuntu, Mate, KDE).  Get some experience first.  There is also the matter of removing them.  Once removed, nothing will boot and it will be necessary to repair this (grub).  Not that hard, but still got to know how.

I run multiple flavors/versions, but its all done in a virtual machine (virtualbox).  This is a excellent way to run anything I want without interfearing with my main install.  But again, there is a learning curve.

Lets discuss this first before getting into partitioning :)

And did you know 17.04 has reached end of life?

---

### Post by seekertom on 2018-02-01
Thanks, cruzer! To clarify, I will only be using the last 4 versions of ubuntu, 14, 16, 17.01, 17.10.1 at this time.
I had envisioned each on a different partition, and able to select which partition I boot into at startup time.
I had hoped to be able to copy each version from its source hd including everything, to one hd, separate partitions.

I suppose a lot of this is just an exercise which I'm sure will teach me a lot, and learning how to solve a definite issue is better than learning generalities from a turorial.

btw, I guess eol means no more upgrades, bug fixes etc, but does it mean I shouldn't continue to use it?

thanks!  seekertom

---

### Post by oldfred on 2018-02-01
Many recommend the virtual installs, but I have many Ubuntu installs on SSD & HDD system.
Some are now obsolete, some just to test one thing or another.
I also prefer to keep it somewhat simple and just use / (root) for each install, but then have all data in a /mnt/data partition which I mount in every install, so all the same data. But settings in /home may vary as I am testing each for something.

I use 25GB for each / (root) partition (including /home).
If not installing with Windows in BIOS boot mode, I recommend gpt as then every partition is equivalent to a primary partition. But if using BIOS to boot you need a bios_grub or if using UEFI you must have the ESP - efi system partition.
The last install will be the grub in control unless you use option not to install grub at all. But you can always boot into your main working install and reinstall its grub to be the grub in charge of booting system.

Some of the versions have changed. This is just an example. And now on HDD I have several more 25GB / partitions:
 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by Impavidus on 2018-02-02
Only 3 versions of Ubuntu are currently alive: 14.04, 16.04 and 17.10. You could leave a spare partition for 18.04. You could install 18.04 now, but it's still under development so don't expect it to be ready for use.

---

