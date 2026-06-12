---
title: "First Time User - Ubuntu Hangs After Grub"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by code bunny on 2011-09-13
Rar! Hi. ^.^

Just installed 11.04 and I am having some problems! 

First:
- Black screen after grub; I put nomodeset instead of quiet splash like it said in the forums post on here.

Now:
- After Grub my system just hangs. It says:

Loading please wait...
Begin: Loading essential drivers ... done
Begin: Running /scripts/init-premounts ... done.
Begin: Mounting root file system ... Begin Running /scripts local-top ... done
Begin Running  /scripts/local-premount ... done
done.
Begin: Running /scripts/init-bottom ... done.

And then nothing! I just get a cursor. :confused:
Booting in recovery mode works fine.

Anyone have any ideas?
If it helps I am running 32-bit windows vista on the same machine, and have a GeForce 8800 GTS video card.

Don't make me go back to using vista :'x

---

### Post by lindajamison76 on 2011-09-13
Thank you, this is good news for new visitors.


__________________
[Watch Horrible Bosses Online Free](http://moviesonlinewatch.net/)

---

### Post by code bunny on 2011-09-16
Anyone? It seems like Nvidea graphics cards really cause issues with this.

---

### Post by MAFoElffen on 2011-09-16
> **code bunny said:**
> Anyone? It seems like Nvidea graphics cards really cause issues with this.
  - Was your install of 11.04 a fresh install or upgrade?
 - After your install of Ubuntu, did you install the NVidia drivers?
  -- If so were they from Ubuntu (Additional drivers) orstraight from Nvidia?

If you look at post 1 of this stcky:
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") 
Boot up in tty text mode with verbose kernel boot messaging turned on... and see if if reveals any errors. 

When booted via rescue mode, go to Administration > Additional drivers and check what driver is installed if any...

---

