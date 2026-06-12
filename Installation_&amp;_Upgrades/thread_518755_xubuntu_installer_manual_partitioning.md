---
title: "xubuntu installer manual partitioning"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by BuffaloX on 2007-08-06
Hi I'm trying to install xubuntu.
But I cannot figure out how to mark partitions for root, swap and home.
I choose manual partitioning, and all my partitions show up, but if I select edit, the installer thinks I want to resize too, which I don't, and I can only make the partition smaller than the original size.
If I delete the partitions, and attempt to recreate the same layout, the size I specify is ignored, and all available space is used instead.
Setting the format tag doesn't do the trick either.

I also tried guided, which resulted in not being asked about partitioning at all, weird???

---

### Post by wolfen69 on 2007-08-06
try gparted to partition ahead of time.

---

### Post by merlinus on 2007-08-06
Right-click on the partitions, and you should see a dropdown list of mount points.

-merlin

---

### Post by BuffaloX on 2007-08-06
@wolfen69
Problem is, the installer won't accept my pre-configured partitions.

@ merlinus
The right click offers only an edit option, which insist on also doing a resize.

I used alternate install instead, which worked OK.
Thanx anyway.

I actually just installed Xubuntu so I could install Gnome without some of the prepackaged stuff I don't want in ordinary Ubuntu. (When I try to remove those ex. Evolution, Synaptic wants to uninstall the entire desktop),

But X-Ubuntu is actually quite cool. in some aspects it's even better than Ubuntu gnome desktop. So I think I'll hang on to XFCE, and give it a proper shot. :)

---

### Post by merlinus on 2007-08-06
> 
I actually just installed Xubuntu so I could install Gnome without some of the prepackaged stuff I don't want in ordinary Ubuntu. (When I try to remove those ex. Evolution, Synaptic wants to uninstall the entire desktop),


This is not a problem.  Let it uninstall the desktop.  You will not lose anything useful.  I have gotten rid of lots of stuff from the regular ubuntu install.

-merlin

---

### Post by BuffaloX on 2007-08-06
> **merlinus said:**
> This is not a problem.  Let it uninstall the desktop.  You will not lose anything useful.  I have gotten rid of lots of stuff from the regular ubuntu install.

-merlin

I thought it would uninstall gnome entirely, I like gnome, and feel kind of lost without Gui.
Now I've tried XFCE, it turns out to be much better than I expected. I haven't really decided yet which one to use as default.

---

