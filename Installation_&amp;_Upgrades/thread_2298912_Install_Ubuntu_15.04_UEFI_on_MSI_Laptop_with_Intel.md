---
title: "Install Ubuntu 15.04 UEFI on MSI Laptop with Intel Broadwell CPU"
date: 2015-10-14
forum: Installation &amp; Upgrades
---

### Post by Edward_Richards on 2015-10-14
Struggling to install Ubuntu on my new MSI Laptop. (PE70-2QE with an i7-5700HQ + dual grahpics, intel + nVidia 960m).

*If I try and run Ubuntu (or possibly anything - maybe completely unrelated issue) in Virtualbox, Windows itself actually bsods with "Machine check exception" which is apparently a common problem for the new intel CPUs (-5xxx series).*

I've made a UEFI bootable USB (with ISO image + Rufus). I set the following in BIOS:
[LIST]
[*]Intel SpeedStep --> off
[*]Intel Virtualisation stuff --> off
[*]Fast boot --> off
[*]Secure boot --> off
[*]Boot mode --> UEFI with CSM
[/LIST]
If I boot to the USB, it flashes up with "insecure mode" (or something like that), then I get 4 options: Try..., Install..., OEM..., Check disk...
I've tried both "Try" and "Install" and the results are the same for both.
If I boot without nomodeset, I get [this]("http://i.imgur.com/wh8oy01.jpg"). It then goes to the 5-dots Ubuntu loading screen, before rebooting of its own accord.
With nomodeset, I get [this]("http://i.imgur.com/ykzB7BI.jpg"). It then goes to the 5-dots Ubuntu loading screen, before hanging on 5 red dots.


TLDR - Can't install Ubuntu in UEFI mode on MSI Laptop with dual Intel/nVidia graphics, and Broadwell processor. Hangs before it even gets to the install screens. Nomodeset makes a difference, but doesn't fix it.

Thanks!

---

### Post by oldfred on 2015-10-14
Do you know if when booting if Intel or nVidia is default video? Can you set that in UEFI?
If nVidia nomodeset is correct, but in Intel you need a different parameter.
But you may also need other parameters.

You probably should be installing 15.10, even though still beta, just to have more of the updates from Intel & support software. It will be released by the end of the month, so close to final now.
       Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

    This is for the newest version of Intel but may work for you also?
 Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

---

### Post by Edward_Richards on 2015-10-21
Googling "Ubuntu 5700HQ" brings up so many threads, and most are unsolved.
I'm just going to wait for 15.10 tomorrow and see if I have better luck with that (I did try all your parameters - none worked unfortunately).
Most of the problems are either people with 5700HQs bluescreening in Windows on certain games and virtualbox, or people with a similar problem to me when trying to install Linux. Most seem to have MSI laptops as well...

---

### Post by jmarcfrappier on 2015-11-02
In the boot param, you need to add  "**libata.force=noncq**".
I have a GE72 6QD and i'm able to get to the actual login and work with it, just very medium graphics and no ext monitor.
Still trying to get either the intel or even better nvidia drivers to work and that's where i get into problems.:sad:
My ubuntu is on a second drive in a caddy replacing the dvd and both os boot fine.;)

---

