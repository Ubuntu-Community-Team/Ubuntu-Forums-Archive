---
title: "Ubuntu 10.04 will not install over Debian 502"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by Mark A Horn on 2010-06-19
I have Debian 502 installed on a Dell Petntium 4 (3.40Ghz).  It installed fine and works fine.  I have decided to try Ubuntu 10.04.   I was able to run Ubuntu 10.04 from the boot disk so I think the boot disk is fine.

Now I want to cleanly remove Debian and install 10.04.  I have not been able to do that.  I have tried several times over several days to do a fresh install from the Ubuntu 10.04 boot screen (it asked to run from CD or install Ubuntu.)  I take all the defaults and change only to Central time.  It eventually gets to a blank purple hue screen and that's it.

So, I think I want to just start over and completely wipe out Debian first.  I have nothing on Debian that I need.  Then I will install Ubuntu 10.04 after the machine is cleaned of Debian.  Could someone please give me the steps to do that?  (Please know I am new to Linux and Ubuntu and details would be greatly appreciated).

---

### Post by darkod on 2010-06-19
Does it go trough the partitioning process? Do you use Manual Partitioning so you can tell it to install into the existing debian partition?

---

### Post by Mark A Horn on 2010-06-19
I go through the 7 steps and click Install.  It asks if I want to run Debian side-by-side, or overwrite with Ubuntu (which I choose) or manual partition.  I do not know what it has done.  There are no informative screens that tell me any progress of the partition.  I eventually reach the purple screen and it is hung.  Like I said before, at this time I could care less about Debian - I just want to wipe the machine clean and start again with Ubuntu 10.04 on a clean box.

---

### Post by darkod on 2010-06-19
Well, it sounds like you are selecting the correct option, to use the whole disk for ubuntu and overwrite everything.
After clicking Install at the last step, there is no progress bar during the copying the files?

---

### Post by Mark A Horn on 2010-06-19
No, there is no progress bar.

---

### Post by Mark A Horn on 2010-06-23
Anybody got any ideas?  I am stuck.

---

### Post by oOarthurOo on 2010-06-23
It sounds like you're having a problem with the Ubuntu installer. I'd recommend downloading the alternate cd and using that, which does a non-gui style install. If you installed Debian, you'll have no trouble with it. And once Ubuntu is on there you can more easily trouble shoot the strange graphics problems which are causing a hung purple screen.

---

