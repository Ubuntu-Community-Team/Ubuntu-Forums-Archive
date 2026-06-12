---
title: "Removing Ubuntu and putting windows on."
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by mattnanokid on 2010-06-15
Hi, I've decided I don't like Ubuntu, so I would like to reinstall Windows. I have windows 2000, and have the CD to go with it, but the setup is not compatible with Ubuntu. I've tried booting from the CD, but it's not allowing me to do so. Is there ANY way to put windows back on my computer? By the way, if you are wondering why I'm using an old OS its because windows 2000 is very stable and I really like it.

---

### Post by DrMelon on 2010-06-15
It should boot from CD, and allow you to install it.
If problems persist, check your CD for scratches, etc. If worst comes to worst, use an operating system that is not ten years old.

---

### Post by TheStroj on 2010-06-15
By saying "but the setup is not compatible with Ubuntu" I suppose you mean the file system? (which really isn't compatible with windows). 

I was also wondering. If you can't boot CDs, how do you enter setup for installing windows?

Lets just say you can enter Windows 2k setup. Use Gparted live CD to format disk and create partitions, then simply run the setup again (don't forget to make the correct FS).

---

### Post by darkod on 2010-06-15
Another thought, depending how old/new your computer is.

I don't think 2000 includes SATA drivers if you have sata hdd. Even XP doesn't have them.

So unless you can set in your BIOS the SATA mode to be IDE or Native IDE, I don't think you can install 2000 no matter how much you like it.

Maybe that's the "incompatibility" you are seeing.

Lets not even ask what do you plan to do with 2000 and which recent software you plan to run on it.

PS. Maybe you could supply sata drivers on floppy if that is the problem.

---

