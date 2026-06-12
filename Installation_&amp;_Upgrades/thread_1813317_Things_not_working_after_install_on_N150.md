---
title: "Things not working after install on N150"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by fidelandche on 2011-07-27
Hi all,

I have just done a complete install of 11.04 on a Samsung N150 Plus. I installed via USB and completely removed windows 7. Now when I try and install chrome/gmail and ubuntu restricted extras nothing happens. For Chrome I downloaded the stable version from their website (34bit) and tried to install but nothing happened, the software center just opened and then froze. I also tried to install gnome gmail via the software center but again I can click on install but nothing happens and the same with Ubuntu restricted extras. I have done the following;

sudo rm /var/lib/apt/lists/* -vf
and

sudo apt-get update
and

sudo apt-get upgrade


but still no joy, so I am now a bit stuck on where to go next.

Cheers

Andy

---

### Post by fidelandche on 2011-07-27
I have retried to install chrome, downloaded again and when I go to install the software center opens then appears to freeze before a page opens which states that chrome is installed but it is nowhere to be found!!! So I typed into terminal the following sudo apt-get remove google-chrome-stable that then runs then I get the message in terminal google chrome needs to be reinstalled but I cannot find a archive for it.

Now I am totally confused because when I click on the package for chrome and the software center opens it is still saying that it is installed!! very confused at this time.

---

