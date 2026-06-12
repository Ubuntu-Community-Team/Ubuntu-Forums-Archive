---
title: "Problems installing ubuntu 7.10 alternate i386"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by Mykas0 on 2008-01-30
Usually, I would stick to my default Ubuntu installation, but a couple weeks ago I had a problem and I had to format that partition. Now, I'm trying to install version 7.10, and everything is going terribly wrong.

At first, I tried to install the "normal" version 7.10 (i.e. the one with the graphic installation), but I later found out that it didn't allow me to pick what components I wanted to install, during the initial setup - I want to install my OS with the minimum possible disk usage.

So, in the IRC support channel, I was told to try the "alternate" version of the system. So far so good, I went ahead and tried to do it, but after it formats the partitions and all that, it seems to hang around 18%, in the "Selecting and installing software" step.
Be aware that I'm trying to do this in a virtual machine (using VMWare 6.0.2), and I thought this could be a problem with the actual CD, since I burned it, and so I checked the actual CD it for errors - none found.
So, I decided to grab the actual ISO I've downloaded and tried to install it directly on the virtual machine - the result was exactly the same, i.e it hangs around 18% in the "Selecting and installing software" step.

Any clue on what may be wrong here, and how to fix it?

---

### Post by margori on 2008-01-30
Have you done MD5 verification of downloaded ISO and verificated if it matches with the online one?

Have tested CD integrity before install?

---

### Post by tenmoi on 2008-01-30
Well press F1 and enter this line to the "boot:" line: install hw-detect/start_pcmcia=false and press enter. This has solved my problem with getting stucked midway with the install.
If nothing helps you can try the expert mode and pick out the one that's causing you problems.

---

### Post by Mykas0 on 2008-01-30
Yes, I did all that before. However, I just tried to install it for the third time, and finally it worked, for reasons that I don't really understand. Unfortunately, unlike happened in past versions of this OS, I was never asked to pick what packages I wanted to install, and I really need to do it.

Before, there was a menu where I could pick what kind of utilities I wanted to install, like Programming ones, or Office ones, etc... how can I access such menu in this install, does anyone know?

---

### Post by tenmoi on 2008-01-30
happy you made it this time. However Ubuntu has no options as to what you want to install. You can add or remove packages later when you have got a working Ubuntu.

---

### Post by Mykas0 on 2008-02-02
That's one of those things which is easier said that done. A few years ago, when I first installed Linux, I know that I was asked about that kind of thing during the initial set-up, but when it comes to simply uninstalling the stuff I don't need, I'm just too afraid that I remove something important, something that may make it impossible for me to login in graphic mode... do you see what my problem is?

---

### Post by xiangcao on 2008-02-03
> **tenmoi said:**
> Well press F1 and enter this line to the "boot:" line: install hw-detect/start_pcmcia=false and press enter. This has solved my problem with getting stucked midway with the install.
If nothing helps you can try the expert mode and pick out the one that's causing you problems.
i got the same problem and looking for solve scheme now, i will try your way tomorrow, thank you~:)

---

