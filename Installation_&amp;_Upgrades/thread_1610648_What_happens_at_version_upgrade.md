---
title: "What happens at version upgrade?"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by yc2 on 2010-10-31
Hello,

Every day when I start the computer the update manager downloads a list of packages availabe. If there are new versions of packages, I am offered to confirm that these should be installed. (This even includes kernel and bootloader.) This is the normal way of updating the system.

However. _What happens when the system is upgraded to a new version?_ (Happens every six months, of course.)

All packages are already updated at that time. Is there other software in Ubuntu apart from the packages that must be upgraded?

This is not just a theoretical question. To better manage the system and take care of the occasional problems that appear druing version upgrade, it is essential to know the process.

Thanks.

---

### Post by jrev on 2010-11-01
I never use the upgrade to a new version. This updating brings often problems.
I prefer to make a new clean install after backing up my data.:P

---

### Post by yc2 on 2010-11-01
I agree, I also make fresh installs and also stay with the LTS.

However, I hope someone can give information regarding the question in the thread:

What happens at upgrade to a new version?

---

### Post by coffeecat on 2010-11-01
If you stay with one version of Ubuntu, the 'updates' won't give you new versions of apps, the gnome desktop, the kernel, and so on. You get bugfixes and security patches mostly. You might get minor updates, but not the newer versions of gnome and open-office, for example.

If you do a dist-upgrade you get a newer version of the kernel, a newer version of gnome and whatever versions of all your apps that are appropriate to the Ubuntu version you are upgrading to.

Like jrev, I prefer to do a fresh install of each new version rather than a dist-upgrade. However, I believe the risks of a dist-upgrade are very much overstated. Any OS upgrade can be problematic - Windows and MacOS users have come to grief as well. But I wouldn't be surprised if a significant proportion of the upgrade disasters we hear about from threads posted to this forum were due to something the poster hasn't told us about, or has even forgotten. So-called "fixes" that involve editing system files, 3rd party software, general tinkering, that sort of thing.

---

### Post by yc2 on 2010-11-01
> If you do a dist-upgrade you get a newer version of the kernel, a newer version of gnome and whatever versions of all your apps that are appropriate to the Ubuntu version you are upgrading to.
Thank you coffeecat.

However, I don't think I have been able to ask my question clearly. I understand the *consequences *of a version upgrade. However, _I do not understand what happens during the minutes the upgrade process is taking place._

What would be the difference between the present Ubuntu and another (imaginary) Ubuntu where there were no version upgrades. Just continuous package upgrades.

---

### Post by coffeecat on 2010-11-01
> **yc2 said:**
> However, _I do not understand what happens during the minutes the upgrade process is taking place._

Have you ever done an update and  been prompted to  restart firefox? If you don't and continue to use firefox, things start to go wrong. There is a mismatch between the bits of firefox in memory and the executables and libraries now on the HD which have overwritten the old ones. Restart firefox and all the new stuff is reloaded into memory and the (newer) firefox works just fine.

A dist-upgrade is the same (if that's what you're asking) but writ larger. It's much safer not to use the system for anything else when doing a dist-upgrade because things can fall apart if you use them. The system will be stable enough to complete the dist-upgrade, but at the end it will be still running the old kernel, the old version of gnome and so on, but now has the new gnome libraries on the hard drive. Which is why you are prompted to reboot once the dist-upgrade is complete.

I used to run Gentoo, for which you compile everything. Twice I did a gnome upgrade in place, running gnome, but doing the upgrade compiles from a root terminal. It was an unnerving experience as bit-by-bit gnome fell to pieces in front of my eyes. Somewhat disconcerting was when nautilus failed and most of the desktop became unresponsive. I got there in the end. :|

> **yc2 said:**
> What would be the difference between the present Ubuntu and another (imaginary) Ubuntu where there were no version upgrades. Just continuous package upgrades.

I think your imaginary Ubuntu would be a rolling release distro such as Arch or Gentoo.

---

### Post by yc2 on 2010-11-01
I understand that for programs that are running, like the desktop, the kernel and many more, one must restart the program/system after the hard-disk files have been updated.

But that also happens with "normal" package upgrades, like f.ex. when a new kernel is installed. I assume the kernel is installed on the disk during the package upgrade and starts to run at next reboot.

So i still do not understand what is special with a dist-upgrade. Is it just some package updates and a restart? Just like any kernel update, for example?

---

### Post by coffeecat on 2010-11-01
> **yc2 said:**
> So i still do not understand what is special with a dist-upgrade. Is it just some package updates and a restart? Just like any kernel update, for example?

I really don't understand what you're asking. A dist-upgrade is an upgrade from one version of Ubuntu to another, Karmic to Lucid, Lucid to Maverick. It's akin to upgrading from Vista to Win7, or MacOS Leopard to Snow Leopard. Only with Ubuntu, the apps as well as the OS get upgraded.

If you're still puzzled I suggest you look up the feature lists for the recent versions of Ubuntu.

---

### Post by yc2 on 2010-11-01
I am trying to understand *how *a dist-upgrade works "technically".

The *consequences* (new features) of a dist-upgrade, I am aware of.

Is _all_ software in Ubuntu contained in packages visible in f.ex. Synaptic/dpkg? Does Ubuntu also consist of other software that is not visible in these programs?

Does a dist-upgrade consist of anything else than installing new packages and then making a restart?

Thanks for bearing with my questions :)

---

### Post by coffeecat on 2010-11-02
@yc2, my apologies, my brain got stuck when posting earlier. I was using the term dist-upgrade wrongly. I was meaning a version upgrade. Goodness why I used the term 'dist-upgrade', which doesn't involve a version upgrade.

Sorry about that.

---

### Post by ezsit on 2010-11-02
A version upgrade, say from Lucid to Maverick (10.04 to 10.10) merely involves replacing all the old packages with the versions that are contained in the new release, that is it. It is pretty darn simply, conceptually. In reality, it can be problematic. What are you not getting?

---

### Post by yc2 on 2010-11-02
Thanks for explaining coffecat, personally I often mix up words. Most important is that we discuss the same thing. I think we have done that in this thread.

I am just trying to understand the update process and what happens during version upgrade. I think the following is correct?

> Ubuntu software is contained in packages that can all be listed through Synaptic or dpkg. There is no software outside these packages. Ubuntu is updated regularly (about every few days or week) by upgrading these packages if new versions have become available.

Sometimes package upgrade includes restarting the system.

Some packages are tested in a development version. Every six months these packages are introduced into Ubuntu in a version upgrade, at the same time changing the version number from f.ex. 10.4 to 10.10.

Thanks for all input.

---

