---
title: "My first Linux upgrade, prep question"
date: 2021-01-20
forum: Installation &amp; Upgrades
---

### Post by mikeymikec on 2021-01-20
I'm using Lubuntu 18.04 LTS (I've been using it/Linux as my primary OS for about 2-3 years IIRC) and I'm receiving the message asking me if I want to upgrade to 20.04 LTS.  I've had a quick poke around with the new version with a VM so from that perspective I'm ok with going ahead with the upgrade, but I'd like to know what kind of prep people would recommend I do before telling it to do the upgrade.

I have a Intel Haswell system with an AMD R9 380X graphics card, UEFI enabled but secure boot off.  I didn't have any issues with 18.04 recognising the hardware.  Dual-booting with Win10 (just for gaming), operating systems are on different SSDs plus a data HDD formatted as NTFS, and grub handling the boot management.  I use Virtualbox for virtual machine usage, Wine for a single win32 app, Veracrypt, and other software that came with Lubuntu such as LibreOffice, Thunderbird, Firefox and Chromium.  I back up my personal data and will do so immediately before the upgrade.

Any suggestions for any other prep I should do first?  I'll wait for a day spare so if it goes titsup I have a bit of time to pick up the pieces.

---

### Post by ActionParsnip on 2021-01-20
Backup important files. Then test restore some data (if your data is disposable to you then you can skip this)

---

### Post by Dennis N on 2021-01-20
That particular upgrade from Lubuntu 18.04 to a later version wasn't recommended by the developers due to large changes in the environment from LXDE to LXQt. I believe it was first mentioned in the Lubuntu 18.10 release notes. They recommended a new install - that's why the new VM install you did worked well.

---

### Post by Impavidus on 2021-01-20
Normally that's about all the preparation you need, except for the live disk you need if things go wrong. However, the changes from Lubuntu 18.04 to 20.04 are so large that the Lubuntu team says this upgrade is not officially supported. I'm not sure why it's actually proposed, but maybe that's a part that Lubuntu has in common with Ubuntu and couldn't be switched off.

You could try the upgrade, but the probability of success isn't very high. Make sure you're ready to do a fresh install after all.

For other versions (like 20.04 to 20.10) or flavours (like Ubuntu or Xubuntu), release upgrades tend to work fine, but it depends a bit on how close your system is to a default system.

---

### Post by GhX6GZMB on 2021-01-20
Don't upgrade, do a new install. The leap from LXDE to LXQt is too large. Ask me how I know.

---

### Post by CelticWarrior on 2021-01-20
> **ml9104 said:**
> Don't upgrade, do a new install. The leap from LXDE to LXQt is too large. Ask me how I know.
+1
And the devs say it, you should listen.

---

### Post by guiverc on 2021-01-20
This has already stated, but I'll provide links & quotes

From the [Lubuntu 20.04.1 release notes]("https://lubuntu.me/focal-1-released/")

> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install.

Your base Ubuntu 18.04/bionic system sees the upgrade, so offers it.  The upgrade will work, but your desktop/GUI may have [*usually minor*] glitches as a result (eg. *menu items relating to the old LXDE options that go nowhere as programs don't exist anymore; ie. a less than ideal outcome*).

**Will upgrade work; yep**.  Can you have issues/problems; yep (*but many report it went well*).

Myself, I'd consider a re-install using "*Manual Partitioning*" and don't format your partition(s). 

 The Lubuntu team doesn't suggest this (it's backup data, clean install, restore that data you need), but in my own testing I like the ability to *upgrade via re-install* using the no-format options, but I'll suggest it (*as me*).  What I'm suggesting will

- note your installed packages (assuming no format)
- erase system directories
- install new system
- install your additional packages (if available in new release; ie. those you added yourself)
- won't touch user files (assuming no format)
- ask to reboot

The noting of additional packages you'd installed can cause some LXDE stuff to be re-installed (esp. if you'd have issues, and `apt install -reinstall` (*and thus flipped a package to being marked manually-installed*), but I've had great success with this method. I may scan what is re-installed (ie. apt logs) but only rarely.

I'm doing some QA-testing of issues now on a *system I use* testing for a bug, and I'm using the method I describe time & time again.. as I don't want my system to be returned to as it was and usable (*it's not on a test box!*) and I don't want to need to restore data.  I trust it.  (but note: it's easy to make a mistake, accidently leave a format checkbox ticked & have it clean install & all data destroyed; so of course backup first!)

---

