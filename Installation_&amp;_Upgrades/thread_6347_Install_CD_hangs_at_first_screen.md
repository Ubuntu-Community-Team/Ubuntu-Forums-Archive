---
title: "Install CD hangs at first screen"
date: 2004-11-27
forum: Installation &amp; Upgrades
---

### Post by slick_nick on 2004-11-27
So after perusing these forums and the wiki and finding nothing, I'm ready to post.   ](*,) 

I just got my sweet free Ubuntu cds in the mail today.  The Live CD boots and loads fine, and I can access my SATA hard drive just fine from within Ubuntu.

The Install CD boots to the very first Ubuntu screen, where it informs me that I can press F1 for help or Enter to boot. Unfortunately, nothing happens no matter what key I press - even Alt-F2 to bring up the console does nothing.

I've tried the Install CD with several different partition combos in the 2 gigs I've allocated it. No partitions, the full boot/swap/etc, just / and swap...nothing.

My computer:
Athlon 2800+ (well, 2600+)
MSI MS-7021 (VIA VT8377 / KT400) motherboard
2x512MB PC 3200
Seagate 80GB SATA drive
MSI Geforce FX 5600XT

Anybody? Thanks

---

### Post by steve1401 on 2004-11-28
Hi

I haven't used Ubuntu, or tried installing it. But if I am not mistaken, it is essentially Debian, which I do have installed.

A similar thing happens in Debian, and the way round it is to pass a parameter when you boot from the install CD. In Debian running kernel 2.6 it's;

linux26 noapci

Maybe Ubuntu allows for similar options, I don't know? From the install CD, if you press F2, F3 etc, do you get help options?

Steve

---

### Post by slick_nick on 2004-11-28
Thanks for the tip Steve; I just tried, but it doesn't work - the installer won't respond to any keystrokes as far as I can tell.

---

### Post by steve1401 on 2004-11-29
Ok, I have just downloaded the live CD and tried booting from that. I got the same hangs as you and had to keep resetting my machine to try again...

In the boot options at the bottom, I typed 'noscsi' (without the quotes) at the end of the boot options line. This worked for me. If you are doing a full install, do you get similar options? If not, try the live CD using 'noscsi' and if that works, at least you'll have an idea of what's at fault...

Steve

---

### Post by slick_nick on 2004-12-02
The funny thing is that my Live cd works just fine, which is fine to just play around, but I want to be able to load at the speed of SATA, not CD. 

How do you get to the boot options on the Install cd? If it's at the first screen, that's where my computer quits.

*bump*

---

