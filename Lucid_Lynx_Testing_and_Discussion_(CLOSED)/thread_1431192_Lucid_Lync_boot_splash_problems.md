---
title: "Lucid Lync boot splash problems"
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Morimando on 2010-03-16
Hi there.

I upgraded to Lucid to see where we're headed and it's running fine, except for the splash stuff. It's really driving me crazy and I can't seem to find out how to fix it.
No here's the problem:
When booting, the screen stays mainly blank, with some graphic errors on top of the screen (mixed color "bar"). To see anything at all I have to disable the splash in Grub's starting line (removing splash silent).
Since I updated my netbook, too, I know that there should be a splash screen and I also know that GDM looks different now (which on my desktop PC also doesn't work, GDM still looks identical to Karmic here).
I already tried reinstalling grub-pc, grub-common, xsplash, plymouth, plymouth-x11, but nothing changed. With grub, I also completely removed it and reinstalled it afterwards (wasn't possible with the other packages, since they want to remove ubuntu-desktop &c. as well).
Am I missing something obvious?
I googled the net up and down, but don't seem to find out what's wrong, although there are some reports about plymouth not working well with the nvidia drivers (I'm using nvidia-185). Did anyone here experience the same problems and is able to help me?
Here are my specs (in parentheses are the specs of the netbook, where stuff works):

Lucid Lynx amd64 (i686)
Nvidia 8600GT (Intel Graphics)
6GB RAM (2GB RAM)
Nvidia-Drivers proprietary, 185 (Kernel Intel driver)
Vga=794 (Vga=792)
1650x1050 (netbook resolution, kind of forgot it atm)

Thanks in advance for any and all help

---

### Post by teh603 on 2010-03-16
Plymouth still doesn't work well, with any drivers. There's supposed to be a minor workaround for Beta 1 and a major fix for Beta 2.

---

### Post by howefield on 2010-03-16
Lucid isn't supported in the main forums till nearer release time.

Ask for your post to be moved to here 

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

where you will likely get more help.

---

### Post by ikt on 2010-03-16
> **Morimando said:**
> When booting, the screen stays mainly blank, with some graphic errors on top of the screen (mixed color "bar"). To see anything at all I have to disable the splash in Grub's starting line (removing splash silent).


There are quite a few bugs with plymouth at the moment similar to what you said,

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/531650](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/531650)

There is a mega patch incoming I think right before beta 1, so I'd give it another shot then.

---

### Post by mrbinitie on 2010-04-27
suffering the exact problem - its 2 days to the final release

---

### Post by jblackhall on 2010-04-27
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

---

