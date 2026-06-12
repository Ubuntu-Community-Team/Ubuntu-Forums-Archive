---
title: "how to login to an hard disk install from live cd"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by planetLars on 2010-02-14
Hello,

I'm running x64 Ubuntu 9.10. I'm using the Live CD right now as grub didn't install as I'm on a RAID0. I'd like to login to the harddisk installation from the Live CD.

Is this possible so that if I run Synaptic gui from the desktops main menu I get the packages installed on my harddisk installation listed and can add packages to this? If yes, how?

Why? I want to check whether grub2 or grub was installed and install grub if possible. The instructions in [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445) didn't work. After chroot and doing all the mount stuff I wanted to remove grub2 but apt told me that grub2 wasn't installed but grub.

Thanks, Lars

---

### Post by darkod on 2010-02-14
You should have used the alternate install cd and grub would have installed ok. For raid and lvm the alternate install cd should be used.
You can add grub now to your existing install even with the desktop cd. No need to reinstall ubuntu. Look here and find the sections starting with:

**Live CD  Installation (Ubiquity graphical installer)**

 [IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/alert.png[/IMG] **MAKE SURE YOU BACK UP  ANYTHING OF IMPORTANCE!!!**
Read through the instructions and reinstall just grub. From what I can see Step 8 is the actual install that you have already done, so just do steps 1-7 to make the live cd see the raid, and continue with step 9 for grub installation.[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by planetLars on 2010-02-14
thanks. Ubuntu 9.10 comes with dmraid included thus the graphical installer worked and the alternate cd isn't needed anymore apparently.

The problem I have is that I followed the steps in the link given in my first post but I think the thread startet got it wrong when removing grub2: he listed grub2 when it was supposed to be grub-common. Perhaps the chroot mentioned there is enough and I can work from bash. I'm investigating. Also I discovered openroot. This is for people seeking an answer to the original question. I didn't try it. It might work.

Lars

---

### Post by darkod on 2010-02-14
> **planetLars said:**
> thanks. Ubuntu 9.10 comes with dmraid included thus the graphical installer worked and the alternate cd isn't needed anymore apparently.

The problem I have is that I followed the steps in the link given in my first post but I think the thread startet got it wrong when removing grub2: he listed grub2 when it was supposed to be grub-common. Perhaps the chroot mentioned there is enough and I can work from bash. I'm investigating. Also I discovered openroot. This is for people seeking an answer to the original question. I didn't try it. It might work.

Lars

You probably have more experience with raid than me, but just to point out that even for 9.10 on the ubuntu website the recommendation is still to use the alternate cd for RAID and/or LVM. There might be small differences that make grub install correctly, I don't know.
Anyway, that link for the Fakeraid HowTo has steps how to add grub to existing raid install.

---

### Post by planetLars on 2010-02-14
> **darkod said:**
> Anyway, that link for the Fakeraid HowTo has steps how to add grub to existing raid install.

Hello, those steps are identical to the ones I have except that dmraid is installed already in Ubuntu 9.10 (I just verified). (I guess it's also activated as I can access my RAID0 appropriately from nautilus and bash).

I followed the steps. My main problem: when starting grub --no-curses I get an "Unknown partition table signature" error. This prevents me from setting up grub at all. My dual boot is Windows 7. I haven't found any help regarding this particular problem on the web. If anyone can help... :KS

Lars

---

### Post by darkod on 2010-02-14
> **planetLars said:**
> Hello, those steps are identical to the ones I have except that dmraid is installed already in Ubuntu 9.10 (I just verified). (I guess it's also activated as I can access my RAID0 appropriately from nautilus and bash).

I followed the steps. My main problem: when starting grub --no-curses I get an "Unknown partition table signature" error. This prevents me from setting up grub at all. My dual boot is Windows 7. I haven't found any help regarding this particular problem on the web. If anyone can help... :KS

Lars

Sorry, I can't help with that error unfortunately. :( Maybe someone else will jump in. Also, maybe google might have some answers for that.

---

