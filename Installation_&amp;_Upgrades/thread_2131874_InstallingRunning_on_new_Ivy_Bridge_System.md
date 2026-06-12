---
title: "Installing/Running on new Ivy Bridge System"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by njparton on 2013-04-03
I'm having trouble installing 12.10 x64 on my new Ivy Bridge system (Z77/i7 3770) the longest I can get it to run for post-installation is 20-30 secs before it hangs. I'm not using the integrated graphics (660 ti instead) and the system either hangs at the login screen or 20 secs after logging in before I can run any upgrades. I can't ctrl-alt-f1 to a console either it just hangs. I've also tried 13.04 beta with similar results.

I run Win 7 x64 from a separate hdd which works fine (I can game or fold for hours) so I don't think this is a hardware problem. I've flashed the mb to the latest bios too.

Any ideas how I can either get the system running long enough to grab updates (a new kernel may help?) or any other bright ideas?

---

### Post by darkod on 2013-04-03
With nvidia you might need to boot with the nomodeset parameter once, to allow you to activate the driver in Additional Drivers. You have instructions here how to set the parameter for one boot only before you install and after (in your case focus on the instructions for after, of course).
[http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997](http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997)

---

### Post by njparton on 2013-04-03
Thanks but my graphics card isn't new, I had it in my previous system which worked with Ubuntu fine.

The only things that are new are the Z77 mb and CPU (even the memory has been carried over).

That said it isn't possible in the BIOS to switch off the Intel GPU per se, all you do is set the PCIE GPU to display first and this seems to do the trick (in windows at least as the intel GPU doesn't show up in device manager).

I'm just wondering if Ubuntu is having an issue with the Intel GPU as there are many a report of that on the web...

Otherwise I'm really struggling... :(

---

### Post by darkod on 2013-04-03
But if you are not using the integrated intel gpu, I don't see how that would freeze ubuntu. There are many reports, true, but when you are using the gpu I believe.

Doesn't matter much what was carried over and if it worked before (nvidia support changes with versions too). You said you are using a 660 which I believe is nvidia card (ATI guy myself :) ), and you also said "post-installation", which sounds like you made a new clean install.

From what I have seen on the forum, in 95% cases for nvidia you need nomodeset on first boot. That would be my first bet. It doesn't take much to give it a try.

---

### Post by njparton on 2013-04-03
OK I will give it a try.  It's just a bit strange that the same graphics card would now be a problem with the same version of ubuntu that's all I was struggling with...

---

