---
title: "How to make Ubuntu default in multi-boot?"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by Aurora on 2007-08-04
Hi,

I installed other distros after Feisty, and I would like to make Ubuntu back into the default in the GRUB menu.  How do I do that?  If there is a thread already, just point me to it---and maybe mention what you used as a search query.  I'm perplexed because I expected to be able to find threads already covering this; I searched for quite a while.

--Paul

---

### Post by taurus on 2007-08-04
You need to edit /boot/grub/menu.lst and change the _default_ value from whatever it is right now to the entry that Ubuntu is, starting from 0.  

The question is which other Linux distro did you install after you already installed Ubuntu?  And did you let that distro install GRUB to MBR?

---

### Post by Aurora on 2007-08-05
> **taurus said:**
> You need to edit /boot/grub/menu.lst and change the _default_ value from whatever it is right now to the entry that Ubuntu is, starting from 0.  

The question is which other Linux distro did you install after you already installed Ubuntu?  And did you let that distro install GRUB to MBR?

I did in fact let 64 Studio (and before that, Linux Audio Distribution) install GRUB to the MBR.  The file /boot/grub/menu.lst does not show any distros except Ubuntu Studio and its manifold kernel options.  On startup, it defaults to 64 Studio unless I select another kernel to boot.

Should I re-install GRUB from the Ubuntu install DVD, or is there some other way?

--Paul

---

### Post by Ozdemon on 2007-08-05
I find using the following GUI program to change the default OS boot order the easiest.
Download (click link): [SUM]("http://web.telia.com/~u88005282/sum/installation.html")

---

### Post by Aurora on 2007-08-06
> **Ozdemon said:**
> I find using the following GUI program to change the default OS boot order the easiest.

I installed it, but I couldn't make it work.  On your system, does this startup manager list the other OS's? It doesn't in mine. The other operating systems don't appear in the pull-down menu, Ubuntu is the only option, and it's selected by default. I also tried changing the colors and the time delay, but nothing changed. At boot-up, I still have 3 seconds to click the down arrow before 64 Studio boots.

:confused:I'm getting very perplexed.  What I thought would be a two-minute tweak is turning out to be another Linux roadblock.  This may not be worth too much more effort; it's easy enough to click the down arrow.

---

### Post by fredj on 2007-08-06
You need to find out which of your Linux distributions has the complete Menu.lst file. It will 
usually be the last one that you last installed. This will have rewritten the mbr to point to its grub
installation. When you have found the menu.lst that is being used at bootup you can edit it
so that the default entry points to Ubuntu.

---

