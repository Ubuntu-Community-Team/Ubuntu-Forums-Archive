---
title: "Lucid Lynx won't boot at all following NVidia drivers update"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by martinlittle on 2010-03-09
I was having problems with Lucid only booting to a shell after upgrading from 9.10, so I eventually followed these instructions to get my GeForce 7300 GT graphics card working: [http://ubuntuforums.org/showthread.php?t=1134426](http://ubuntuforums.org/showthread.php?t=1134426) .

Since I made those changes, my box won't boot.  GRUB comes up and I've tried all the options there with no luck, then I get a flashing cursor on the screen and nothing more happens.  I've removed the second disk drive, which had data only on it, to avoid any loss of data.

I've spent a few days reading forums and looking for solutions, but without any luck.  Removing the Nvidia card, and using the onboard video card hasn't changed anything.  Before I run a fresh install of Lucid, is there anything else I can try, please?

My computer is a Dell Dimension 5150 desktop, and Ubuntu is the only OS installed.  It's been running fine for years, as I've upgraded to alphas, betas and releases.

---

### Post by lidex on 2010-03-10
Have you tried booting into recovery mode and  then removing xorg.conf?

---

### Post by martinlittle on 2010-03-11
Hi lidex, I didn't try that unfortunately, and finally gave up, copied the last few files off the OS disk, physically disconnected the data disk, and re-installed Lucid.  All working OK now.

---

