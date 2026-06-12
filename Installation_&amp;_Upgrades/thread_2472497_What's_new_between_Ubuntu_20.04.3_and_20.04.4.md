---
title: "What's new between Ubuntu 20.04.3 and 20.04.4?"
date: 2022-02-28
forum: Installation &amp; Upgrades
---

### Post by username2758 on 2022-02-28
Hello everyone!

I have this Acer laptop model A515-45-R2A3 with relatively new AMD 5500u APU which only works flawlessly on Ubuntu 21.10, but I still don't know exactly why: first I tried Ubuntu 20.04.3 LTS with kernel 5.4 and then upgraded to version 5.13.0-28 which works fine on Mint 20.3, but for some reason I experienced lags and stuttering on Ubuntu 20.04.3 regardless of kernel versions (the entire system including mouse and keyboard completely freezes for a few seconds and then comes back to normal again).

What could be? Could it be that GNOME 40 on Ubuntu 21.10 solved hardware incompatibility issues with this recent AMD processor?

Does Ubuntu 20.04.04 also come with GNOME 40?

Thanks!

---

### Post by #&amp;thj^% on 2022-02-28
I only show this for careful consideration: [https://www.linuxcapable.com/how-to-install-gnome-40-desktop-on-ubuntu-20-04/](https://www.linuxcapable.com/how-to-install-gnome-40-desktop-on-ubuntu-20-04/)
[B
EDIT:[/B]
Another question is should you upgrade to this? Possibly the work is already started on GNOME 41, which is very unstable. Still, GNOME 40 from this PPA has matured and looks semi-stable, but make sure to have backups when working with any alternative desktop environment.

---

### Post by guiverc on 2022-02-28
> **username2758 said:**
> 

Does Ubuntu 20.04.04 also come with GNOME 40?

Thanks!

[Ubuntu 20.04.4 LTS]("https://fridge.ubuntu.com/2022/02/25/ubuntu-20-04-4-lts-released/") is a *re-spin* of Ubuntu 20.04 LTS media using later packages, and if you're using the HWE kernel stack (default for Desktop) it includes the kernel stack from Ubuntu 21.10.

From one of the [*announcements*]("http://The Ubuntu team is pleased to announce the release of Ubuntu 20.04.4 LTS (Long-Term Support) for its Desktop, Server, and Cloud products, as well as other flavours of Ubuntu with long-term support.  Like previous LTS series, 20.04.4 includes hardware enablement stacks for use on newer hardware. This support is offered on all architectures.  Ubuntu Server defaults to installing the GA kernel; however you may select the HWE kernel from the installer bootloader.  As usual, this point release includes many updates, and updated installation media has been provided so that fewer updates will need to be downloaded after installation. These include security updates and corrections for other high-impact bugs, with a focus on maintaining stability and compatibility with Ubuntu 20.04 LTS.") you'll read

> The Ubuntu team is pleased to announce the release of Ubuntu 20.04.4  LTS (Long-Term Support) for its Desktop, Server, and Cloud products, as  well as other flavours of Ubuntu with long-term support.


    Like previous LTS series, 20.04.4 includes hardware enablement stacks  for use on newer hardware. This support is offered on all  architectures.


    Ubuntu Server defaults to installing the GA kernel; however you may select the HWE kernel from the installer bootloader.


    **As usual, this point release includes many updates, and updated  installation media has been provided so that fewer updates will need to  be downloaded after installation. **These include security updates and  corrections for other high-impact bugs, with a focus on maintaining  stability and compatibility with Ubuntu 20.04 LTS.



I've added BOLD to the quote; but it's the same LTS software found on prior Ubuntu 20.04 LTS media with contains security fixes & other updates applied.

You can look at the [*manifest*]("https://releases.ubuntu.com/20.04/ubuntu-20.04.4-desktop-amd64.manifest") to see what's included if you prefer by package; downloading that & the prior .3 manifest will allowing easy package comparisons; but it's the later HWE kernel stack & security fixes applied only.

---

### Post by MAFoElffen on 2022-03-01
And to answer if you "should upgrade" to this? It is automatic in installed systems who apply updates.

guiverc answered that, but to reword it more simply:

Think of it as a point of time. These are the last updates before the freeze, before 22.04 gets released. If installed from an ISO, all the updates are already applied to this point of time. If you have been applying updates to your installed system, you are already there.
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsb_release -sd
Ubuntu 20.04.4 LTS



```

---

### Post by username2758 on 2022-03-01
Hey guys!

So I've decided to take the plunge and do a fresh installment of Ubuntu 20.04.4 on this laptop, and to my rather disappointment the lags and stuttering still persist but to a lesser degree. But then I did a little test by enabling Wayland instead of X11 and apparently all these issues disappeared. Why would that be?

I've also noticed between Ubuntu version 21.10 and 20.04.4 I am not getting the option to choose the power modes in the latter (Balanced Mode or Power Saving Mode). Also, there is a difference in the mouse gesture capabilities in Mozilla Firefox, the ability to pinch in and pinch out only available in Ubuntu 21.10. Can I also get that in Ubuntu 20.04.4?

---

### Post by ActionParsnip on 2022-03-01
Try Ubuntu 22.04 instead. It is the new LTS due out very soon and will be the latest version of Ubuntu

---

