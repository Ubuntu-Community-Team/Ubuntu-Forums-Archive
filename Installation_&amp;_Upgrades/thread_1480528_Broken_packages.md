---
title: "Broken packages?"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by luckymoonboy1 on 2010-05-11
ok, I have run into a problem upgrading from 9.10 to 10.04 on a system with NO internet using the alternet installer disk. I am NOT upgrading to a pre-release version. I am NOT upgrading from a pre-release version.this is what happens:

Image:
1) I run the upgrade with the command in Alt+F2.
2) I click NO, do not use the internet for the upgrade.
3) I click YES, I don't understand this, but I figured it might be normal since there is no network.
4) It tells me that I have held broken packages or that I am upgrading to or from a pre-release version. I am NOT.
5) I check the package manager for broken packages. There are NONE.

What do I do? It is not a dire nesecity that I upgrade, however I greatly wish to. Any help would be apriciated.

---

### Post by frantid on 2010-05-11
It might be the last bit, other software not on canonical support.  Do you have flash installed?  That has complicated a few upgrades lately.

edit: it will hold back on removing dependent packages, if an alternative is not found to upgrade.

---

### Post by luckymoonboy1 on 2010-05-11
No, as far as i know i don't have flash installed, however i do have a package that allows it to play Dvds. could that do it?

---

### Post by frantid on 2010-05-11
in synaptic, go to the origin button -- you can see where your stuff came from, it might be your graphics driver.

---

### Post by luckymoonboy1 on 2010-05-12
Is there a certain tab that it would be under? I have several tabs like 8.04 somthing /main and /restricted all the way up to 9.04 /main and /restricted and 9.10 only has a /main

---

### Post by frantid on 2010-05-12
the graphic drivers are usually in restricted.  I think the cd only contains main, so if a conflict with something outside of main exists you might have trouble without the internet connection.

---

### Post by luckymoonboy1 on 2010-05-12
So, the 10.4 alternet only contains the main drivers when the 9.10 contained both the main and restricted? How do I go about correcting this then? Do I need to locate an alternative driver?

---

### Post by frantid on 2010-05-12
I'm not sure where the list of contents are for the alternate.  The machine you're upgrading has never had internet access?

---

### Post by luckymoonboy1 on 2010-05-12
None. I live in a rural area and all we have is dial up available and I don't have a compatable Winmodem or and external modem.

---

### Post by frantid on 2010-05-12
here's a list
[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

what package is your graphics driver now?

I'll look for it faster for you on my broadband.

---

### Post by luckymoonboy1 on 2010-05-12
I have no idea. I'll look though, I'm headed home here in a few minutes. Will it just be listed somewhere under the 9.10 tab in the origin button?

---

### Post by frantid on 2010-05-12
search installed packages for your brand name, i.e. nvidia, intel  or ati

---

### Post by luckymoonboy1 on 2010-05-13
i found several but I'm not really sure what is what.

---

### Post by frantid on 2010-05-14
In the alternate cd there is a nvidia driver package.  So I am not sure what is causing the hold.  I would download the livecd and try to boot off of it.  Maybe at a library or someplace with wifi, if you have a laptop.  You could always try to uninstall your video drivers, it should fall back to the generic drivers.  I do see that one of your modaliases packages does not have the ubuntu symbol next to it.  Then try the update to see if it still stops you.

beyond that you could try looking for packages with problems:

```
sudo apt-get check

```
and any unconfigured packages

```
sudo dpkg --configure -a
```

---

### Post by luckymoonboy1 on 2010-05-17
I am very, very sorry, it seems i was wrong about my graphics card. it is an ATI Radon and not a NVIDA. I discovered this when i got home and looked in the case. I don't know if it makes any difference, but i looked up the ATI packages(in the picture below). I ran those commands that you suggested and i didn't get anything. i didn't know exactly which drivers to remove or how so i went looking around a bit more and followed the directory that was listed at the bottom of the original error message and found two .log files. I attached them below. one shows several errors that i don't understand(Main.log) and the other(apt1 and apt; starts at line 382) lists several broken packages towards the end. I'm not sure where the broken packages are, they aren't listed in synaptic, so i wondered if they might be on the CD, possibly some kind of corruption that the integrity check wouldn't find? I would post the errors but it is a long, long list. i am really sorry about the wrong information.

---

