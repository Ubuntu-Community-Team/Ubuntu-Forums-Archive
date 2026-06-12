---
title: "Why does my keyboard freeze after upgrading to Hardy"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by Olli on 2008-07-16
Dear sisters and brothers in Ubuntu,

We have an old s.c. grandchildrens' computer (Pentium III, 450 MHz; IBM keyboard, where the DIN connector connected to the computer via a DIN|PS/2 converter, double boot - Windows2000/Ubuntu 8.04.1 - wireless home net).

Ubuntu partition has functioned without problems, although slowly, until upgrading 7.10 to 8.04. The upgrading went through smoothly - until I tried to open the computer next time: I was not able to write the user login and password, in fact anything.

OK - a new attempt to install, this time from the scratch (except keeping the home partition). This time, as soon as I had chosen the keyboard and tried to check that I was able to write Finnish accented letters I found that I wasn't able to write anything.

The next attempt was to try Linux Mint 5, another Debian flavor, with the same unfortunate result.

Now I am in the situation that the keyboard is working with Knoppix (and Windows) only - but I hate KDE after getting accustomed with Gnome. I have been using different Linux flavours for more than 10 years in this computer, and this situation is very embarrasing, as whatever I try, I am not able to get to reconfigure xorg.config that I suspect being the culprit.

Has anyone encountered the same problem and found a solution? I would be most thankful for any hint.

Olli, the Greybeard

I checked yet the keyboard with Knoppix; no problem. It seemed that the "usual suspect", xorg.config, was not culprit; maybe by changing the [old but well-behaving] keyboard would help. I installed - once again - the newest version of Linux Mint. The keyboard worked all the time - until I defined the default language and rebooted. Fortunately the mouse was still working, so I was able to start in safe mode, ordered the next boot a normal one - and, lo and behold!, the keyboard hasn't made any trouble since then.

---

