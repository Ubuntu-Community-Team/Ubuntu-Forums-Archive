---
title: "Suitable disc partioning"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by mistermax on 2007-04-26
I manually set my disc partitions up. I did this with the intention of keeping /home separate, as, from prior experience, every so often my 'tinkering' makes a mess of things.

Currently it looks like this

/dev/hda1 /boot is 486 MB
/dev/hda2 swap is 996 MB
/dev/hda3 /home is 139GB
/dev/hda4 / is 7.9GB

I've got 2GB of RAM and am wondering if I should have put more aside for swap? If so, how do I go about this exactly, now my system is live.

---

### Post by thingy on 2007-04-26
Why is /boot = 486mb?

/boot only contains the kernel image and some grub files. In normal systems this directory will never be greater than 64mb. Even a 32mb /boot is enough for people.

I recommend /boot to be 64mb max and no more. Why 64? well I like numbers that are a power of 2? heh! :-)

Swap of 512mb will prob. be enough as you have 2gb of ram.

A 8gb / is limiting only because your / will contain both app stuff in /usr and logs/cache stuff in /var. How about considering / to be at least 12gb and if possible make it 20gb to give yourself room to breathe.

---

### Post by mistermax on 2007-04-27
> **thingy said:**
> Why is /boot = 486mb?

/boot only contains the kernel image and some grub files. In normal systems this directory will never be greater than 64mb. Even a 32mb /boot is enough for people.

I recommend /boot to be 64mb max and no more. Why 64? well I like numbers that are a power of 2? heh! :-)

Swap of 512mb will prob. be enough as you have 2gb of ram.

A 8gb / is limiting only because your / will contain both app stuff in /usr and logs/cache stuff in /var. How about considering / to be at least 12gb and if possible make it 20gb to give yourself room to breathe.


That's cool - how do I go about resizing these then?

---

### Post by thingy on 2007-04-27
Depending on what file systems you have on these partitions i.e. ext2/ext3 etc. see if the [GParted Live CD]("http://gparted.sourceforge.net/features.php") can do what you want.
 
**Remember, _backup_ anything you do not want to loose _before_ you mess about with resizing partitions.**

---

### Post by mistermax on 2007-04-27
I'm not going to have to worry to much about backing anything up, given that I've just rebuilt a totalled system... :)

---

