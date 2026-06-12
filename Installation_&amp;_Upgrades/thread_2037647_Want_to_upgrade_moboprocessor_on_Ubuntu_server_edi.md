---
title: "Want to upgrade mobo/processor on Ubuntu server edition (Natty)"
date: 2012-08-05
forum: Installation &amp; Upgrades
---

### Post by packerac on 2012-08-05
I got some great advice last time I posted on Ubuntu forums, so I was hoping that you guys might be able to help me upgrade my computer!

Title says all - I bought a bunch of parts to upgrade my server computer, including a new motherboard, processor and more RAM, but I don't know where to start.

I'm assuming just replacing the parts and hooking my harddrive up is NOT the right thing to do.

It would be great if I could get some help or pointers to links explaining how to do it. Thanks!

PS:
Motherboard - Asus to Gigabyte (Z68AP-D3)
Processor - Athlon to Intel Xeon
RAM - 2 Crucial 4GB sticks, adding 2 more 4gb sticks (Kingston)
OS - Ubuntu server edition Natty

EDIT: It seems I *can* just upgrade and plop the old HDDs in (without any problems)??? [http://scottiestech.info/2010/03/17/upgrade-your-motherboard-without-reinstalling-your-os/](http://scottiestech.info/2010/03/17/upgrade-your-motherboard-without-reinstalling-your-os/)

---

### Post by packerac on 2012-08-05
1) I'm running the stock ubuntu server edition but I installed a GUI
2) The Athlon is a AMD Athlon II X4 630 Propus 2.8GHz
3) I tried to set them up in RAID but failed (when I first built the computer about half a year ago), so currently one HDD is completely unused (the OS+everything else is all on 1)

---

### Post by darkod on 2012-08-05
Yeah, you should be able to simly switch the hardware.

As for raid, don't try fakeraid in any case, if you want to use raid do it with software raid. Not sure where you failed last time but software raid is pretty simple to set up with the ubuntu server installation.

In fact, if the hardware switch goes OK and the server is booting fine, you can transform it into software raid1 without losing the data if that's what you wanted to do. There is a procedure for that.

---

