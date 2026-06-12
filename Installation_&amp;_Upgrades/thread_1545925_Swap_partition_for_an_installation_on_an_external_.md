---
title: "Swap partition for an installation on an external HDD"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by Alcareru on 2010-08-04
Hi guys!

I was just wondering if some of you gurus could tell me if it's totally insane to make a swap partition on an external HDD. The connection is either with simple USB 2.0 (which is probably the usual case) or if possible double connection with Firewire and USB. Is it too slow to access the HD this way making swap partition utterly useless?

What I've done so far is installed ubuntu on an external HDD and during the process created a small swap partition too, but I was just thinking that should I just drop it and hope the ram is enough.

The idea is that now I have a full blown linux installation (with nice graphical interface!) which I can plug on to any computer, log in and do what ever I want, regardless of what is already installed on the computer. Mostly the idea is to enable easy creation/loading of backups and fixing broken installations, but it's a nice bonus that I can really do anything I could do with my regular desktop ubuntu computer. And most importantly it works the same so I don't need to bother learning to use another window manage or a mere terminal session.

---

### Post by dabl on 2010-08-04
> **Alcareru said:**
> Hi guys!

I was just wondering if some of you gurus could tell me if it's totally insane to make a swap partition on an external HDD. The connection is either with simple USB 2.0 (which is probably the usual case) or if possible double connection with Firewire and USB. Is it too slow to access the HD this way making swap partition utterly useless?



The question of whether a swap partition will be needed is not related to whether the installation drive is internal or external, it is related to the amount of memory available for programs and data to use.  "Better safe than sorry" would be the advice.

> 
The idea is that now I have a full blown linux installation (with nice graphical interface!) which I can plug on to any computer, log in and do what ever I want, regardless of what is already installed on the computer.

No.

Unless "any computer" is going to have identical hardware, in every respect, that's not going to work.  The drivers that get set up on your initial platform will be the wrong ones for other platforms.

Probably what you want is a "Live CD on USB stick" installation, which will give reasonably good performance on a maximum variety of hardware platforms. Forum search and Google will show you how.

---

### Post by snowpine on 2010-08-04
Your plan sounds realistic to me. Using a swap partition will allow you to run (slowly!) on computers that do not have enough RAM.

So long as you do not install any restricted hardware drivers, you should be able to boot your USB drive on a wide range of hardware. Ubuntu auto-detects hardware at each boot; an install is not specific to your hardware (unless as I mentioned you install restricted drivers).

---

### Post by Alcareru on 2010-08-04
Alright, thanks mates. I guess I'll just have to see how well my installation fares with different computers with different hardware. If not too well I might need to reconsider the choice of OS and/or the method of installation. I'll soon try it out on my desktop machine but right now my external HDD is busy creating backups of my new laptops original partitions.

---

### Post by Alcareru on 2010-08-05
Ok as is expected the X session fails intially as I plug the HDD on my desktop machine. Then again reconfiguring is a piece of cake. I just told it to do it and it did it all on its own. One click. Then I just retried to start X and wola here we go. Session starts and everything is working nicely, the bigger screen, Nvidia graphics drivers used instead of ATI, compiz rolling...woot, I'm more than happy with how this installation works. As of so far it's been a breez with the 2 machines I've tried it.

---

