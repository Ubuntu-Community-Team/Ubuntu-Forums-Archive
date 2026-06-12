---
title: "No GUI, please help"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by visctrix on 2007-02-10
Accessing the internet through live cd only...

Since the last kernel update I get a message saying X is broken. What can I do to fix this? I've posted more details in [this long post]("http://www.ubuntuforums.org/showthread.php?t=357913"), but I'm desperate for some sort of answer please.

T.I.A.

visctrix

---

### Post by mikewhatever on 2007-02-10
If you haven't tried to reconfigure xserver yet, try choosing the old kernel from GRUB menu at boot. You should still be able to get to the desktop. If you have tried to reconfigure xserver, then look for a backup of xorg.conf. I am sorry not to have a permanent fix, but personally, I don't think I need such an update.

---

### Post by visctrix on 2007-02-10
1. How would I try to reconfigure xserver?

2. At first I managed to boot into the old kernel and tried to fix the problem, but since then I haven't been able to boot into any kernel, any version of Ubuntu, just the live cd.

---

### Post by mikewhatever on 2007-02-10
If you aren't able to boot at all, then it seems, there is no choice.
>  sudo dpkg-reconfigure xserver-xorg
You are supposed to use the command, when xserver fails to start, and you are left with the black screen with an option to login. 
Login first, then run the above command, and then, you'll be presented with a number of options to specify about your hardware. Chances are you'll not know the exact answers, but if at a loss, choose the default option. There is a good [xserver page on Herman's site]("http://users.bigpond.net.au/hermanzone/p7.html") to help you. Do not expect too much :) . In my case it didn't work at all.

---

