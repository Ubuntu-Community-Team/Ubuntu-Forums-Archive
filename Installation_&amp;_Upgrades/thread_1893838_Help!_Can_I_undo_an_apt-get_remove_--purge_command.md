---
title: "Help! Can I undo an apt-get remove --purge command?"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by Hawkoon on 2011-12-11
I am sitting on an Ubuntu 11.10 desktop and something went horribly wrong here...  I wanted to uninstall gmpc and gmpc-plugins with ```
sudo apt-get remove --purge gmpc*
```but now see that a whole lot of other things got uninstalled/purged as well, incl. libre-office, xorg, ubuntu-desktop...

I haven't rebooted yet and I also still have the terminal with all the output from that apt-get command open. I wonder whether the programs and conf files are still in some cache so that I could restore everything I just removed/purged.

Or will it be less hassle to do a fresh install of my ubuntu?

Not so cheerful right now,

~H

---

### Post by 73ckn797 on 2011-12-11
Maybe you could reinstall ```
sudo apt-get -install gmpc*
``` before closing down terminal and restarting? I have never encountered this problem but have attempted removal of stuff only to find that the list of included items that would gut the system.

Search here for possible answers: [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by Hawkoon on 2011-12-11
Thanks 73ckn797,

I dry-run your suggestuion; it brings back some of the stuff, but not all like xorg and my desktop, and on top of all it would install a lot of new stuff I didn't have before...

I was hoping there is some kind of cached information that I can use to roll back all last changes.

~H

---

### Post by raja.genupula on 2011-12-11
do ```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by Hawkoon on 2011-12-11
Well, in the end I went for a manual roll-back, going backwards through the output from my apt-get remove mistake and installing package by package. I didn't get back my settings that way because I had actually issued apt-get remove --purge... but OK, it was still less hassle than going through a complete re-install.

I remember in 10.04, I used to use the synaptic gui and there was this history view thing where you could track what package got installed/removed at what point. But it doesn't seem you can tap into that information in order to have an easy way to undo previous changes.

~H

---

