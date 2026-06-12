---
title: "Atheros Wireless Problem"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by portxabia on 2009-12-14
I installed the Kernel update to 2.6.31-17 and checked out my AR2413 chipset Atheros wireless and it now worked ....for about 2 mins and then it ground to a virtual halt again, does not make any sense to me, still running on ath5k.

---

### Post by phillw on 2009-12-14
> **portxabia said:**
> I installed the Kernel update to 2.6.31-17 and checked out my AR2413 chipset Atheros wireless and it now worked ....for about 2 mins and then it ground to a virtual halt again, does not make any sense to me, still running on ath5k.

Hi,

honest - I'm not fobbing you off, but there is a sub forum for wireless stuff where that's what they do -->[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Head over to them, they don't bite ;-)

regards,

Phill.

---

### Post by coffeecat on 2009-12-14
> **portxabia said:**
> I installed the Kernel update to 2.6.31-17

What kernel update to 2.6.31-17? If you haven't got the proposed repository enabled, there won't be a 2.6.31-17 yet. At least not hereabouts. If you have the proposed repository enabled, disable it and use the 2.6.31-16 kernel until there is an official kernel upgrade.

**Edit:** yes, just checked and it's clear you do have the proposed repository enabled. Since the -17 kernel clearly has a faulty Atheros driver in it, **do not use it**. Boot into the 2.6.31-16 kernel. Once you've done that, read this:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

> Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.

---

### Post by portxabia on 2009-12-14
Thanks, but a couple of points I maybe didn't make clear, I was posting here because this is an upgrade problem, before the upgrade my system worked, after installing 9.10 it did not, and as my system is already broke I can't see any harm in downloading proposed Kernel updates. But I will follow your advice and stick to approved Kernels as I am certainly not an experienced Ubuntu user.

---

### Post by phillw on 2009-12-14
>  			 				enabling the proposed updates repository can break your system. It is not recommended for inexperienced users. 			 		

+1

---

### Post by coffeecat on 2009-12-14
> **portxabia said:**
> But I will follow your advice and stick to approved Kernels as I am certainly not an experienced Ubuntu user.

A wise choice. :wink:

A lot of people enable the proposed repository mistakenly - and then wonder why they get problems. I think they must think it gives them the latest and greatest, rather than simply patched updates which are put into proposed for experienced testers to quality assure them. And it's not just kernel updates - all (most?) updates are tested in proposed and most have the potential to break your system.

Good luck! :)

---

