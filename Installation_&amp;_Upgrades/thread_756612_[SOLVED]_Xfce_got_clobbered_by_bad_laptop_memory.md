---
title: "[SOLVED] Xfce got clobbered by bad laptop memory"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by benali72 on 2008-04-16
Hi,
I've been using 6.06 happily on my toshiba laptop for a good while.  Last night I added a new memory module, which turned out to be defective.  I took it out, but by then the damage was done -- my Xubuntu interface is now messed up.  For example:

-- program windows are not movable
-- new program windows open up at very top of screen
-- program windows don't have the 3 buttons in upper right corner (min/max/close)

My Kubuntu interface (which I wasn't using when the bad memory was installed) still works fine.

I tried using Kubuntu to reinstall the four Xubuntu packages via Synaptic Package Manager, but the problems persist in Xubuntu.

Does anybody have any ideas on how to fix the Xubuntu interface back to its defaults?

If not I'll have to do a full re-install (ugh!).  (I guess for this I would backup my Desktop and Firefox defaults and Home directory, then re-install Ubuntu, then re-install all the other programs I've installed on top of it, then restore my environment.) 

Thank you for any advice.

---

### Post by benali72 on 2008-04-16
Ok, here's what I did--

(1)  Went into working Kubuntu and removed entirely all Xubuntu packages using Synaptic
      Package Manager
(2)  Went into my home directory, found all desktop settings for Xubuntu--

     cd /home/my_userid
     find  .  -name  xfce*  -print  2>/dev/null
     /* go into each XFCE directory and delete everything */
     cd xfce4
     rm -R *
     /* .... etc for other XFCE directories and files ...  */
   
(3)  Re-install all Xubuntu packages using Synaptic

Now when I log into Xubuntu, everything works fine.  I had to re-build my Quick Launch bar was the only loss.  All the goofiness is gone, no full re-install necessary.

qed

---

