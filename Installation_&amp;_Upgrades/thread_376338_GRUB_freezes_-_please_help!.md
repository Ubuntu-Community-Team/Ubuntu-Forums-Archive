---
title: "GRUB freezes - please help!"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by rei_t_ex on 2007-03-04
First, I'd like to confess that I am very new to Linux - so if I say something stupid, or do not specify something that I should - please bear with me.

That caveat aside, my problem:

About a week ago, I decided to try Linux after years of being an exclusive apple user and got myself an Edgy LiveCD.  I installed Edgy as the sole operating system on my old (first generation) Macbook (2GHz Core Duo, 1GB, 80GB SATA).  The installation went perfectly, and I was very pleasantly surprised at how polished Ubuntu is.

Yesterday, I started looking for a way to change the usplash screen to something prettier (and hopefully with a correct resolution), but instead first stumbled on to this guide:

[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

describing how to replace GRUB with gfxboot.  I followed EXACTLY the instructions of the first post (uninstall old GRUB, install GRUB-gfxboot, edit menu.lst, setup GRUB from its terminal).  This did not cause any problems, but it did not change anything either.  Instead of giving up, I persevered and followed a suggestion in that thread to run:

```
sudo grub-install /dev/sda1
```

After a success message, I rebooted only to find that GRUB no longer works.  On boot, the computer now freezes at:

```
GRUB Loading stage1.5.

GRUB loading. please wait...
```

- exactly what I used to see right above the "Press escape to go to boot menu".  No error code is given.  It now also takes markedly longer (a second or two as opposed to instantaneous) for the second line (GRUB loading. please wait...) to appear after the first.

I posted my problem on that thread specifically (though it is not very active, which is why I am posting again here) and attempted to resolve it myself as follows:

I booted to the LiveCD, mounted my filesystem, restored the old menu.lst, and restored GRUB following the suggestions of this guide:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

All actions are successful, with no errors returned.  The device.map file also looks in order

```
(hd0)	/dev/sda
```

The problem still persists.

The only other thing I can think of is that it is a problem in the gfxboot package itself, and that maybe I should uninstall it and reinstall the proper version of GRUB.  But is there any way to do this from the LiveCD?  Synaptic and debpkg seem to only be able to affect the OS on the LiveCD, as far as I can tell...

Any help would be dearly, dearly, dearly appreciated.  I really do not want to be forced to reinstall the entire OS just over something that seems to be as if it should be a minor problem.

---

### Post by rei_t_ex on 2007-03-05
As another thought, does Feisty come with a new version of GRUB?  And if it does, is it possible to _upgrade_ (i.e. without losing data and settings) Edgy to Feisty using the Feisty LiveCD (or any other method that does not actually involve having to boot to my presently unbootable Edgy)?  Would Feisty's Migration-Assistant accomplish this?  Does it work in Herd5?

---

