---
title: "When I finish burning ubuntu to my CD and reset my computer..."
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by local444 on 2010-05-23
Hey i'm downloading ubuntu right now, and I have windows XP. So once it's downloaded and i burn it to my CD and reset the computer, will the OS on my computer always be ubuntu from then on? Or can I just put in the CD whenever I want to run Ubuntu,, and take it out when I want windows XP.

Thanks

---

### Post by darkod on 2010-05-23
You can run ubuntu from the cd, it's called live mode, but it won't be able to keep any changes like that. Anything you do will be lost.

Usually you would run it in live mode a bit, to see how you like it and whether it works fine on your computer. After that, you would install it on your hdd.

If XP is on the whole disk right now, you will have to shrink XP first to make space for ubuntu. It's best to do that using Gparted (System-Administration) in ubuntu live mode. After that boot XP few times to do its disk checks.

Then again boot with the ubuntu cd, start the installer and just use Use Largest Available Free space option. That will install ubuntu into the unallocated space you left.

Make a backup of your data before shrinking XP. Any resize operation has a level of risk to go wrong, so you should have a backup.

---

### Post by Tkdboy on 2010-05-23
If u setup ubuntu on Windows you can choose everytime which one u want to load.

---

### Post by darkod on 2010-05-23
> **Tkdboy said:**
> If u setup ubuntu on Windows you can choose everytime which one u want to load.

Yes, but installing inside windows (wubi) is not supposed to be used as long term install. Only as a quick try. And you can do the same by running the cd in live mode. So why bother with wubi?

In a proper dual boot you can also select which OS you want to boot on startup.

---

### Post by Tkdboy on 2010-05-23
I agree with you.
That it means he has to split the hard disk in 2 partitions...
Dont forget to install GRUB when u ll install ubuntu.

---

