---
title: "Major disaster upgrading to 7.04"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by anonymoususername on 2007-04-20
OK, here's my problem. I was updating from 6.10 to 7.04, amd everything was going smoothly, all the files had downloaded, and had almost finished installing, when my latop decides it's run out of power and switches itself off. Now, whenever I attempt to switch it on, it refuses to boot, it hangs straight after sitting at "Waiting for root filesystem". This happens on both 2.6.20-15 and 2.6.17-11. 2.6.17-10 gets as far as the Sign In screen, but then after I enter my username and password, just goes to a blank background. For reference, this is what I see if I press Ctrl+Alt+F1 (after removing "quiet"): [http://paste.ubuntu-nl.org/16607/](http://paste.ubuntu-nl.org/16607/)

Anyone know any way I can boot? I'd REALLY rather not lose all my files.

---

### Post by Nobber on 2007-04-20
File this under "/bin/sh: can't access tty; job control turned off" post #127942 today.

---

### Post by anonymoususername on 2007-04-20
> **Nobber said:**
> File this under "/bin/sh: can't access tty; job control turned off" post #127942 today.

Well, if the question has been asked so regularly, perhaps a link to the solution might be helpful? In any case, even if I can't boot 7.04, is there any way I can recover my previous installations of 6.10?

---

### Post by Nobber on 2007-04-20
Sorry, I wasn't trying to be unhelpful; I'm not aware of any solution to this problem.

I had my own (different) problem booting Feisty, and got around it by booting with the Edgy kernel instead. Hardly a long-term solution, though...

---

### Post by anonymoususername on 2007-04-20
> **Nobber said:**
> Sorry, I wasn't trying to be unhelpful; I'm not aware of any solution to this problem.

I had my own (different) problem booting Feisty, and got around it by booting with the Edgy kernel instead. Hardly a long-term solution, though...

Sorry for being hostile. Yeah, I've tried booting under an Edgy kernel, but I get the same error. Right now I'm attempting to download the alternate install CD and install over my current install, which will probably mean losing a lot of stuff.

---

### Post by gbesso on 2007-04-20
How about booting from a live cd, mounting your old root partition on /media/oldroot and doing: 
sudo chroot /media/oldroot
then sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get upgrade

and try sudo dpkg --configure -a

This probably won't work if it's the same issue other people are having, but since your laptop powered down in the middle of the upgrading process it might be a completely different issue to the one that was reported before.

---

### Post by anonymoususername on 2007-04-20
> **gbesso said:**
> How about booting from a live cd, mounting your old root partition on /media/oldroot and doing: 
sudo chroot /media/oldroot
then sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get upgrade

and try sudo dpkg --configure -a

This probably won't work if it's the same issue other people are having, but since your laptop powered down in the middle of the upgrading process it might be a completely different issue to the one that was reported before.

Thanks, I'll try that.

---

### Post by anonymoususername on 2007-04-20
Yeah, that seems to have worked. Thanks.

---

### Post by gstool on 2007-04-20
> **gbesso said:**
> How about booting from a live cd, mounting your old root partition on /media/oldroot and doing: 
sudo chroot /media/oldroot
then sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get upgrade

and try sudo dpkg --configure -a

This probably won't work if it's the same issue other people are having, but since your laptop powered down in the middle of the upgrading process it might be a completely different issue to the one that was reported before.

I had a different problem than that discussed here.  Reboot after install failed to start, File not Found.  Your fix above got me back on track.

Thanks a lot.

---

### Post by nibsa1242 on 2007-04-20
Thanks, I had a similar problem. [Hardlocked during install, don't even have the 2.6.20 kernel as an option], and this thread is at least leading me down a promising looking path.

---

### Post by sixlegs on 2007-04-20
I also experience a major crash when I did the upgrade.  It took 2 days and then came up with a display that was unreadable.  Now that I did a complete fdisk reinstall from my CD drive I no longer can see one of my USB drives unless I manually mount it.  Very irritating.

---

