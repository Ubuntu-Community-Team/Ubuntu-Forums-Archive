---
title: "Upgrade problem - revisited"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by thereid on 2010-11-30
I posted this problem weeks ago, but I haven't got an answer that works yet...
This forum has SOOOO much information that I'm whelmed, and don't know where to look anymore.  Hope not to waste your time if I'm in the wrong place.

Running an IBM laptop with a P4 on a dual-boot partition with Win XP.

Ran 8.04 Hardy just fine for months.  Upgraded to 9.10 karmic with no problems.
Attempted to upgrade online to 10.10 maverick, and system now fails to boot.
I get the "circles" logo for a few seconds then a blank screen.

Would like to get back to ANY version of Ubuntu that runs; WITHOUT corrupting my XP partition.  I have my Hardy CD, and can boot to see (and modify?) files on the Linux partition.

Attached is my "Boot_info_script results.

Sorry to be such a noob that I need my hand held through this.  My next system will be 100% Ubuntu, and I won't fear experimenting.

---

### Post by zvacet on 2010-12-03
Upgrade failed because you are trying to skip version.You supose to upgrade to Lucid and then to Maverick.If you have any valuable files back them up and  do fresh install of Maverick.That will not harn your Windows,because every OS have their own partition.

---

### Post by sikander3786 on 2010-12-03
A clean install would be the best choice if you can backup all your important data from Ubuntu partition (use your Ubuntu Live CD to mount and extract data from Ubuntu partition).

If you decide to try and upgrade the existing one, press Esc as your computer gets past the Bios screen. From Grub menu, select Recovery Mode and Drop to Root Shell.

Try these commands,

```
dhclient eth0
```

Where eth0 is your network interface.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

If those return any errors,

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo shutdown -r now
```

If successful, you might be able to boot Ubuntu successfully.

Otherwise, if you decide to do a clean install, feel free to ask any help reagrding installation of new version. For that, we need the output of,

```
sudo fdisk -l
```

Good Luck!

---

