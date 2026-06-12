---
title: "Slightly corrupted panel after install Radeon 5450 + FGLRX driver"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by XEtedBear on 2012-01-19
I installed a Radeon HD 5450 card in my Fujitsu Scaleo EV desktop (running 11.10) by merely replacing the un-identified custom graphics hardware with the ATi card. The system booted without problem (with a dramatic increase in performance), but I assumed that Oneiric would need to use a specific driver for this hardware. I searched for alternative drivers; the output told me that the proprietary driver installe was not activated. Activation failed with a message in jockey.log which was unintelligable to me.

I then followed a thread in the forums for installing the AMD/ATi proprietary driver. This worked without problem and the system started just fine after a reboot - except that the  top panel (I'm using Gnome 3 desktop) is corrupted by narrow bands of colour and the text is almost impossible to read. There is a similar problem with corrupted text that is displayed in the right-hand navigation column when browsing the list of all applications. That corruption looks like the wrong resolution is being used to drive my LCD - but all other text (for example the titles for the applications) appears fine,

I took a snapshot of the corrupted panel, it is attached. (I can't figure out how to use Snapshot when browsing  the list of appplications.)

Any advice on how to overcome these small problems?

---

### Post by BlinkinCat on 2012-01-19
Hi,

This may be related to this Bug - 

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577)

I have this problem and as a result use Open source driver

---

### Post by XEtedBear on 2012-01-20
Yes, thanks for telling me about this. As far as I can understand the tech-speak in this bug report, it does seem to describe the symptoms I am experiencing.  I am correct in reaching the bottom line that the problem is stil not solved?

I switched to Unity and find that things work fine (as far as I have tested). I again looked at 'additional drivers' and was again told that 'post-release updates' are available. Again the attempt to instal the update failed. Is this another bug?

So I still have the 'release' (i.e. not post-release) proprietary driver installed, and not the open source driver. I would make the switch but for 2 concerns:

1. What do I lose (performance ?) and what do I gain (stability ?)
2. I have read so much about people getting to the point of having no GUI after switching drivers, and read so much advice on installing display drivers which turns out to be wrong (or inappropriare) that I now have no idea how to make this driver change safely, Where is the 'How To' for this process that has been verified by some group with authority to give/withold such endorsement?

---

### Post by coffeecat on 2012-01-20
I'm posting from my main desktop running Ubuntu 11.10 and fitted with a Radeon HD5450 card. I'm using the default open source driver and I get perfectly good compiz/Unity. If you are not a gamer needing the extra 3d acceleration capability of the proprietary driver, I suggest you uninstall it and enjoy the trouble-free experience of the open source driver.

---

### Post by XEtedBear on 2012-01-20
> **coffeecat said:**
>  If you are not a gamer needing the extra 3d acceleration capability of the proprietary driver, I suggest you uninstall it and enjoy the trouble-free experience of the open source driver.

I'm certainly not  a gamer (about 2 orders of magnitude too slow and too old); so, pray, what is the secret Linux incantation I have to learn to make a smooth, error free transformation to the open source driver AND still have a working system afterwards?

---

### Post by coffeecat on 2012-01-20
With 11.10, if you installed the fglrx driver with the Additional Drivers utility, then you simply open Additional Drivers, disable the proprietary driver, wait for AD to do its stuff and then reboot. However, you mention following a thread on the forum, which might have involved downloading the driver from the AMD site and running an installation script. If you did, then there *should* be a uninstall script, but I have no experience of installing the fglrx driver from the AMD site.

More here, and also how to purge fglrx and reinstall the OS driver if Additional Drivers fails for whatever reason:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Post back if you have any problems.

---

### Post by XEtedBear on 2012-01-20
Thanks for the guidance. 

In my previous post I tried to give a hint that I have found so many guides in the community that turn out to not work as described on the box - for whatever reason. I also have (had) this nagging doubt that changing a display driver in Ubuntu never properly works, especially if it's for an ATi device. 

Well, I don't have any doubts now - about both topics. My nice desktop Ubuntu system is sitting there with a beautiful black screen (so I can't see the dead pixels now), going nowhere. The URL guidance sadly makes the assumption that there is some way to type in the set of mysterious and 'fuzzy' incantations (my CRT, which I am using now to access the forum, combines pathologically with the default Ubuntu font set to make it almost not exactly impossible (but very close) to distinguish between 1,i and l. Given the power of these arcane incantations, I'm sure this will make a difference - when I have deduced how/ where to type them into a dead system. I also have doubts about the reference to fglrx-modaliases. I read in the bug report above that this package is no longer required.

Ah! Computing. Never a dull moment.... (Which is why I run at least 3 Ubuntu systems concurrently:2 are always certain to have shot themselves in the (same) foot somehow)

---

### Post by coffeecat on 2012-01-20
Fear not. All is not yet lost. It sounds as though the proprietary driver has (temporarily) broken the GUI. If so, there are two things to try.

The first is to boot into recovery mode, making sure you are connected to the network with a wired connection, not wireless. At the recovery mode menu choose "drop to root shell with networking", or words to that effect. You will be presented with a '#' root prompt. Hereafter, double-check everything you type - you have full root privileges. Have a look at the wiki link I posted and try the commands for "Problem: Need to fully remove -fglrx and reinstall -ati from scratch". You'll have to decide whether you need the first "fglrx-uninstall.sh" command because you didn't confirm whether or not you ran a script downloaded from the AMD site. I rather suspect you may have done, because the proprietary driver installed from Additional Drivers should not have given you the problem you are experiencing.

When you run those commands, leave out the sudo that prepends each line - you don't need it. Also, I suggest you run this last. You may not need it, but it won't do any harm to get you back to the open-source driver:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

(That's X11 = capital-X, eleven.)

If all those commands run without incident, try rebooting.

If that doesn't work, or you can't boot into recovery mode, the other thing to try is chrooting into your Ubuntu installation from a live CD. I can tell you how, but let's see if recovery mode works first.

---

