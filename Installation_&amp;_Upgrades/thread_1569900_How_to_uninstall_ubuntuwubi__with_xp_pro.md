---
title: "How to uninstall ubuntu/wubi  with xp pro"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by avdistribution on 2010-09-07
I installed ubuntu on an xp pro machine with wubi. I've read to uninstall I should be able to use Window's add/remove programs since wubi installed ubuntu as a program within Windows. 
But ubuntu is not in the list.
There is an ubuntu folder in "programs".
There's no separate partition for ubuntu and the wubi uninstaller does nothing.
I've read a few threads but none seem to mirror this exact problem.
So how do I get ubuntu uninstalled? 
I'm a complete linux novice, but reasonably experienced with Windows.

---

### Post by bcbc on 2010-09-07
> **avdistribution said:**
> I installed ubuntu on an xp pro machine with wubi. I've read to uninstall I should be able to use Window's add/remove programs since wubi installed ubuntu as a program within Windows. 
But ubuntu is not in the list.
There is an ubuntu folder in "programs".
There's no separate partition for ubuntu and the wubi uninstaller does nothing.
I've read a few threads but none seem to mirror this exact problem.
So how do I get ubuntu uninstalled? 
I'm a complete linux novice, but reasonably experienced with Windows.

usually there's an entry in add/remove programs. There's also a wubi-uninstall.exe in the *x*:\ubuntu directory. If you can't find either then likely you've got a partial uninstall and there's still an entry in boot.ini - so the windows boot manager prompts you every time. 
To remove this, back it up, turn off the read-only flag and remove the last line (containing wubildr).

The [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?") has detailed instructions for manually uninstalling.

---

### Post by avdistribution on 2010-09-08
Thankyou.
The wubi guide has this;
"In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line...."
But there is no wubi/ubuntu line in boot.ini. Just the XP default OS. I did try the wubi uninstaller so maybe that removed it? 
Since there's no sign of a separate partition and no boot.ini entry, is it safe to just delete the Ubuntu folder and reclaim that space?

---

### Post by bcbc on 2010-09-08
yes - you can delete that to reclaim the space

---

