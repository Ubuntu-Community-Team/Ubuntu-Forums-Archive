---
title: "Wubi install on Windows 7?"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by Jeconti on 2010-01-07
Is there some special trick to a wubi install on a Windows 7 box? I just tried to do and got stuck in an infinte loop in trying to boot to Ubuntu. Whenever I tried it just kept dumping me back to the OS selection screen.

---

### Post by Mark Phelps on 2010-01-08
From what I've seen on other posts, the following combination simply doesn't work:  Win7 preinstalled (with two partitions), Wubi install of 9.10, GRUB2 install (default in 9.10).

Don't have any solutions for you if that is your combination because I haven't seen anyone posting them.

---

### Post by meierfra. on 2010-01-10
Lets check out your setup. Boot from the Ubuntu Live CD  and follow these [instruction]("http://ubuntuforums.org/showthread.php?t=1291280") to run the Boot Info Script and post the RESULTS.txt.  

Then boot   into a Window 7,  click on "Start" and type "cmd". Then press "CTRL+SHIFT+Enter".  This will open the commandline with administrative rights.  Type
```
bcdedit >C:\bcd.txt
```

Post the content of the file "C:\bcd.txt"

---

### Post by Mark Phelps on 2010-01-11
Just saw the link below:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

There are claims this fixes the problems...

---

### Post by meierfra. on 2010-01-11
> Just saw the link below:

[https://bugs.launchpad.net/ubuntu/+s...9/comments/210](https://bugs.launchpad.net/ubuntu/+s...9/comments/210)

There are claims this fixes the problems...

+1

I'm not sure that Jeconti has the same problem. The symptoms seem to be different.  But  anybody with Wubi should download the new "wubildr", otherwise one will be hit by that bug sooner or later.

---

### Post by Jeconti on 2010-01-13
When I finally came back to it, I just did a fresh Wubi install, this time running the program in Vista SP3 compatibility mode. Only issue has been incorrect screen resolution, but other than that, both systems boot just fine.

---

### Post by meierfra. on 2010-01-13
> both systems boot just fine.
Great. To avoid future problems, you should still follow  the instruction from the link in post 4.

---

