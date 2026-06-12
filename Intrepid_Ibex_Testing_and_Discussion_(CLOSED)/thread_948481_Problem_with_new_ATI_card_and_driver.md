---
title: "Problem with new ATI card and driver"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bash on 2008-10-15
Today I finally got my new graphics card. It's a nice ATI 4850. Problem is now that I can't convince Ubuntu to use the ATI driver instead of Vesa. Before I used my onboard random Intel graphics. Now I plugged in the card and for some reason I can't manage to get Compiz to start. I know the fglrx driver isn't yet compatible with XServer 1.5, but then I should at least be able to use the open-source ATI driver which AFAIK should have Compiz support. And since Compiz doesn't work, I assume I got switched to VESA.

So how do I find out which driver I'm currently using and how the hell do I switch to another one. Back in the day "sudo dpkg-reconfigure xserver-xorg" used to do the trick, but that doesn't work anymore. So suggestions please.

---

### Post by bpl07 on 2008-10-15
If you want to use open-source, I believe you need to use radeonhd for your card.  Add this to the Device Section of /etc/X11/xorg.cong:

> Driver "radeonhd"

They don't have 3D acceleration for >R500 series, which includes your card.  Sorry, no compiz.  Some more details [here]("http://www.phoronix.com/forums/showthread.php?t=9951") (it's about hardy, but relevant to intrepid).

The proprietary driver was released last night.  If you upgrade your system, you should see the option to install it in System>Administration>Hardware Drivers.  For now, don't try to install it any other way (i.e. synaptic) unless you're absolutely sure you're installing the most recent version (8.543).  Once it's installed, change the Driver in xorg.conf to "fglrx" (it should automatically do this if installed with Hardware Drivers).

---

### Post by bash on 2008-10-15
My old laptop used to have an ATI card. Think it was a 9700M or something like that (Should be an R300). And there the open-source ATI/Radeon driver had AIGLX support. Will try it with the RadeonHD driver.

And new fglrx? Nice. Haven't read anything about it anywhere yet. Seems like the Ubuntu devs get a magic early release from somewhere ;)

The only problem is jockey still happily tells me that there is no driver available for my card.

**Update**

Seems like the CH mirror is slow to be updated again. Just now got the first new xorg packages. But half of them aren't even installable yet due to broken dependencies.

---

### Post by helliewm on 2008-10-15
See my post here: [http://ubuntuforums.org/showthread.php?t=948529]("http://ubuntuforums.org/showthread.php?t=948529") 

Last night Ubuntu released a new Beta ATI Catalyst Driver which fixes the problem. I have a ATI 4850 it now works beautifully in Ubuntu.

My post above tells you have installed the driver its very easy.

Helen

Edit: Remember to do sudo apt-get update and sudo apt-get upgrade before following my instructions. This is because the ATI driver has only just hit the Ubuntu repositories.

---

