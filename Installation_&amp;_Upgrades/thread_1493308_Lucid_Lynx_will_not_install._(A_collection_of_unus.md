---
title: "Lucid Lynx will not install. (A collection of unusual problems)"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by Schmee on 2010-05-25
OK so I'm kind of a n00b to the forums but I'm not an entire n00b to linux or ubuntu in particular. I have had several issues regarding karmic and was wondering if anyone could explain to me why my system is cursed with absolute lucid fail?!

Let me begin by explaining my hardware:
AMD64 Athlon 6000+ (roughly 3ghz)
4gb ram
nvidia geforce 8800 gtx
two 320gb drives set up on a raid 0

Before trying to install Lucid I had a Dual boot with Windows 7 and Karmic(64bit) using grub as boot loader.

I originally tried to install lucid over my karmic partition which worked fine (It did have a hiccup before it installed and said that there was an error in installation and it had to go to live desktop mode. I had read online that it wasn't an issue and I should just install by 'trying w/o changes' instead of directly installing) until it got near the last 5% where it told me it couldn't install grub properly and asked me to install it somewhere else or to install manually. I figured it shouldn't be a problem since grub was already installed. This resulted in a broken grub. now I had no way of getting into either my windows partition or my lucid partition (which supposedly, minus the grub error, did install correctly). 

Ok so now I'm royally screwed because all my data is lost right? ok so I start off by reinstalling windows 7 because everyone knows that installing a dual boot without installing windows first is a pain in the you know what. Install works fine so I try to install lucid right after it. This time, however, when I try to install it side by side it tells me that it cannot install to that partition. In fact, it won't install to ANY partition. I thought it might have something to do with ext4 file system. I try just about every option to install except for overwriting the windows partition (which I need in order to get work done). I've tried several reinstalls including wiping the drives completely clean but still lucid will not install. Any help would be much appreciated as I would really like to start working with lucid for fun but perhaps this is just an omen that I should stick w/ karmic for now. Oh yeah I forgot to mention. After all the pain with trying to install lucid I tried to install karmic in the "partition that cannot be installed to" and it worked like a champ. no hiccups or anything.

thanks everyone,
~schmee

---

### Post by darkod on 2010-05-25
Your data was not lost, at least not until you decided to install again over it. Ubuntu is not installed on a RAID with the standard desktop (live) cd.

For a LVM or RAID setup, you need to use the alternate install cd. That's why grub installation failed but at that moment you could still only add grub.

For installing on fakeraid (mobo raid):
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

