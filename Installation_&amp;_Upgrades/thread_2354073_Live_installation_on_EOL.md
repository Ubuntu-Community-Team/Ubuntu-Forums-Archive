---
title: "Live installation on EOL"
date: 2017-02-27
forum: Installation &amp; Upgrades
---

### Post by hennmann on 2017-02-27
Other than doing a clean install, I'm currently on 5.10 64 bit currently downloading 16.10 VIA bittorrent, and I'm wondering since 5.10 is EOL and an upgrade isn't? possible (or is it?) would it be possible to take the 16.10 ISO and install or upgrade "on the fly" while my 5.10 is running? As it is my dinosaur 5.10 is currently up to date, so the story goes, also is a network upgrade/installation possible as well since my network drivers etc. are installed and this is working?

---

### Post by oldos2er on 2017-02-27
You need to boot from a 16.10 (or 16.04 LTS) ISO that's been burned to DVD or USB; no upgrade is possible from such an old Ubuntu version.

---

### Post by Bucky Ball on 2017-02-27
> **oldos2er said:**
> You need to boot from a 16.10 (or 16.04 LTS) ISO that's been burned to DVD or USB; no upgrade is possible from such an old Ubuntu version.

^^^
This. And I strongly advise 16.04 LTS. You are digging another hole for yourself like the last one installing 16.10. It is not a long-term support release and dies in the middle of this year. 16.04 LTS is a long-term support release, supported until 2021 and LTS release will upgrade directly to the next LTS release (16.04 LTS> 18.04 LTS), leapfrogging the interim releases in between. By the looks of it, you want an LTS release. :)

Everything NOT ending in 'LTS' is an interim release and is supported for nine months (meaning you need to reinstall/upgrade everything six/nine months or so until you get to an LTS release; installing 16.10 = 16.10> 17.04> 17.10> 18.04 LTS). 

Good luck.

PS: Are you sure a new version of Ubuntu is going to run on your machine? If you've been at it since 5.10 that machine is a dozen years old at least so might be doubtful. You may need something lighter like Xubuntu or Lubuntu. More details of machine will help clarify ...

---

### Post by DuckHook on 2017-02-28
> **Bucky Ball said:**
> &#8230;Are you sure a new version of Ubuntu is going to run on your machine? If you've been at it since 5.10 that machine is a dozen years old at least so might be doubtful.+1

In fact, I believe that you are understating things in the interest of caution and diplomacy.

@OP

At the risk of overwhelming you with advice: your machine is highly unlikely to function well with Ubuntu. The HW of the 5.10 era was simply not made to run a modern heavyweight OS. A lightweight one might still be okay, but not something with Ubuntu's resource demands. While it is not possible to give precise advice without precise HW data, a few general observations are still valid.

[LIST=1]
[*]You need to stick to a 2-D desktop. This means that Ubuntu, Kubuntu and Ubuntu-Gnome are out, leaving you with Lubuntu, Xubuntu, Ubuntu-Mate and the new Ubuntu-Budgie.
[*]Of the four, Lubuntu and Xubuntu have been around the longest and are therefore presumably the most "stable". Certainly they would have more history of community-based solutions to their quirks and problems. This in itself is an important consideration for someone who is practically starting from scratch again.
[*]Lubuntu is the lightest of the two. Xubuntu is the prettier one. There aren't many cases where the HW restraints would dictate lightness before all else, but yours may be just such a case.
[*]Like Bucky Ball, I very much agree that 16.10 (or any non-LTS) is the wrong way to go. Stick only to LTS releases.
[/LIST]
A theme emerges: When it comes to old HW, the lighter, the simpler, the more stable, the better.

---

