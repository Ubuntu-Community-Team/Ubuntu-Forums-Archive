---
title: "Drive Does Not Boot"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by whitenerdy92 on 2007-11-27
I installed Ubuntu Gutsy on a 7-year-old(ish) Dell Dimension onto a 20GB drive as slave, the master being a 20GB drive with Windows ME. When moving this drive to another computer (a similar, but slightly newer, 6-year-old(ish) Dell Dimension), I set it to master, and it would not boot (only a flashing rectangle in the upper-left corner, like a command prompt). I believe that this should be fixed by either a)reinstalling Ubuntu on the first computer, with the drive set as master, or b)reinstalling Ubuntu on the second computer, with the drive as master.

My main questions are 1)which one, or both, will fix this problem, and 2)what caused this problem? Thank you for any help you can give!

---

### Post by BrianElliott0218 on 2007-11-27
From what you've said, you may need to boot with the driver update CD...  Let me know how that works for you as I'm trying to install on a Dell Laptop as well, and can't get it to load to the live CD boot.

It gives a lot of textual errors.

Let me know how you resolve it as I'm in the same boat right now.

Mine does come up to the option menu on startup of the CD.  Are you getting that far?

Thanks!

---

### Post by whitenerdy92 on 2007-11-27
Unfortunately, it's someone else's computer, and I can't access it right now, only the older computer is mine. The Live CD worked for Feisty, I have not tried it for Gutsy, but I do not think that this is the problem. The problem is that it cannot boot from the hard disk. I'm thinking that it had something to do with Grub or it's just confused about not being a slave drive anymore, and it doesn't know what to do?

---

### Post by torgrot on 2007-11-27
The problem is the grub geometry changed when you moved it from slave to master.  If you haven't spent to much time customizing it I would just re-install with the drive as master on the computer it is going to remain in.

torgrot

---

### Post by whitenerdy92 on 2007-11-28
ya thats what i thought had happened... im just gonna reinstall it, i didnt really do anything to it anyways.

---

### Post by whitenerdy92 on 2007-11-28
yes that appears to be the problem... i learned that the other computer refuses to boot from a cd, so i just installed as master on the older computer, and it worked :] thanks guys for all of your help!

---

