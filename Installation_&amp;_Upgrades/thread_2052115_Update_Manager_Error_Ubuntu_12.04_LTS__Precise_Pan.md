---
title: "Update Manager Error: Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by DenJento on 2012-09-02
Ubuntu 12.04, Shell Gnome 3, and dualbooting Windows 7. Installed via the live cd. Also this problem occurs with the default shell in Ubuntu 12.04. Also inserting the install cd doesn't work eather...

Allright so it seems I keep getting an error while trying to install any software using the terminal or trying to update my system using the Update Manager.
It is very frustrating, I can't seem to find any solutions online. The error that I get is while trying to update: 

CD/DVD 'Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)' is required
Please insert the above CD/DVD into the drive '/media/cdrom/' to install software packages from it.

Note that in Update Manager>Settings>Other Software the "Cdrom with Ubuntu 12.04 'Precise Pangolin' is unchecked.
___

This is the error I get while installing software in the Terminal:

Media change: please insert the disc labeled
 'Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)'
in the drive '/media/cdrom/' and press enter


Uggh it's so annoying, please give me an answer or else I'm forced to re-install Linux

PC:
-dualbooting Windows 7 & Linux
-Acer laptop
-Normal hdd
-Intel Pentium
-No graphic cards
-DVD-rewriteable

---

### Post by herbnerder on 2012-09-09
I had the same problem with a very similar laptop (if that even matters). Try going into your software sources and looking for an option to use the CD as a source. If that's enabled, disable it and re-open Software Center or update your packages, etc.

I'm not that familiar with 12.04 but it seems that maybe if you don't have an internet connection when you install, it uses the CD as a source. This is the first time I've tried installing without a net connection or at least recently, so I figured that must be it. Or, whatever the case, disabling CD as a source fixed my problem. Why it's failing after that, and in such a blocking way, even when you have the CD inserted is another issue.

---

### Post by jerrrys on 2012-09-09
You got it herbnerder; uncheck the CD option in software sources.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=software+sources&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=software+sources&as_qdr=all&sa=Google+Search&lang=en)

---

