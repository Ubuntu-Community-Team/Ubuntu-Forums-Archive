---
title: "Edgy -&gt; Feisty has broken support for my ATI graphics card :/"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by AzraelUK on 2007-05-20
Hi,
I've recently upgraded from Edgy to Feisty. The installation wasn't exactly problem-free (the update manager crash halfway through, so I had to carry on from the console with dpkg), but now there's one main thing annoying me - my graphics card.

It's an ATI Radeon 9200, and it worked fine with the fglrx drivers before hand. When I rebooted after the installation it fell back to the terminal. Looking in xorg's logs, I've found it was because my card has 2 PCI addresses (one for VGA out, one for DVI out afaik) and fglrx didn't like that. It was moaning that there wasn't a Driver section each time for either PCI:1:0:0 or PCI:1:0:1, even though I made a Device section for them both manually.

So I switched from the fglrx drivers to the ati drivers, which didn't have any effect. I then tried the radeon drivers - Now, X starts. With no hardware acceleration.

Does anybody know how to fix this? I'll be fiddling more with dpkg-reconfigure xserver-xorg and /etc/X11/xorg.conf a bit more before I give up.

[INDENT][INDENT][INDENT]Cheers,
[INDENT]Peter[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by southernman on 2007-05-20
[Installing Ubuntu 7.04: ATI X**** Cards]("http://ubuntuforums.org/showthread.php?t=414194")

---

### Post by AzraelUK on 2007-05-20
No, it's not that... I don't have a X**** card, I've just got a **** card :). I've found [this thread]("http://ubuntuforums.org/showthread.php?t=446462") that seems to have the same problem. I think the only solution may be to downgrade from X.org 7.2 to 7.1 - any hints on doing that?

Peter Don't-Worry-I'll-Get-An-nVidia-Card-Soon Bunyan.

---

### Post by southernman on 2007-05-20
I thought X**** was meaning, any version of ATI card. My usual card of choice was the ole geforce mx440...  my bad.

Downgrading isn't something I could help you with... :(

Good luck

---

### Post by AzraelUK on 2007-05-22
OK - If anybody's interested, I've filed a bug report on Launchpad - it's at [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/116268]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/116268").

---

### Post by southernman on 2007-05-22
Thanks for the update > Peter Don't-Worry-I'll-Get-An-nVidia-Card-Soon Bunyan;)

Good luck!

---

### Post by myoungf1 on 2007-05-22
Ok for some information all proprietary drivers for any ATI cards are not built for Xorg 7.2 rather only for 7.1 and below.  I know there are ongoing discussions on getting the open source drivers updated for 2d and 3d acceleration but this is more an ATI problem than anything else with the proprietary drivers from the ATI/AMD site.

---

### Post by southernman on 2007-05-22
myyoungf1 - are you saying it doesn't matter what flavour of ATI card you have... they are all affected with the descrepencies stemming out of Xorg 7.2?

---

### Post by init6 on 2007-05-22
well ain't that a kick in the groceries.:(

---

### Post by myoungf1 on 2007-05-23
From what myself and my brother and several others in the forums have said in regards to Feisty and xorg 7.2 and ati cards the proprietary ati drivers don't work well period with Feisty.  There are people who are currently trying to get this as a bug in the next release but I am unsure where that is at the current moment.

---

### Post by AzraelUK on 2007-06-03
I've found out that it's just because my Radeon 9200 is too old to be supported by the latest version of fglrx. I've got the ATI drivers working with a small uncommenting in the source code (I found it in the wiki).

---

