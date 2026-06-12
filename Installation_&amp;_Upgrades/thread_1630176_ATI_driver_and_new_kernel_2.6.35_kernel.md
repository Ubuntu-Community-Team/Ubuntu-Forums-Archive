---
title: "ATI driver and new kernel 2.6.35 kernel"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by bobyl573 on 2010-11-24
I'm not sure if anyone is having the same problem as me. With the recent upgrade kernel, my ATI driver can no longer work. After upgrading to the new kernel, upon reboot I would get stuck at the "checking battery status" and can't boot into kubuntu.

I'm running Kubuntu 10.10 64 on intel i5 with radeon hd 4870.

So I thought I messed something up since I was fooling around with conky script the day before. I did a clean install of kubuntu 10.10 64 and reset all my settings and my files. At this point, everything works smoothly and I can reboot multiple times without a problem.

I proceeded to install the Radeon catalyst driver following the documentation, which worked perfectly for me on the previous kernel. After rebooting, I can no longer get pass the "checking battery state" black screen. I had to boot into safe book, uninstall all fglrx and also delete xorg.conf to be able to boot back in normally.

Any ideas? I would really like my driver to be up and running.Please tell me what logs to post as well thanks.




update:

ok I have solved this problem. What worked was directing downloading the driver from ATI website and than directing running the install script. Before I was downloading the driver and building the debian packages and than installing according to the install documentation. I'm not sure why it made a difference, but thanks for those that helped!

---

### Post by SmileyChris on 2010-11-25
Yeah, think I'm experiencing the same bug (but on standard Ubuntu)

For now, I've been just booting into previous kernel. Had a very quick search and couldn't find a launchpad ticket. I guess we should open one...

---

### Post by Mauri72 on 2010-11-26
Same problem here: Vaio with Radeon HD5400 card. Boots fine with kernel 2.6.32 but not with 2.6.35

---

### Post by bobyl573 on 2010-11-27
anyone have any luck solving this one?

My problem was upgrading from kernel 2.6.35-22 to 2.6.35-23. I did another clean install of kubuntu 10.10 64 and the ati driver still doesn't work. I seem to see many different symptoms of the same thing around but not sure what the exact fix is.

I'm running xorg-server 1.9.0 if that makes any difference. it came with the downloaded kubuntu. 

The error I'm getting now seem to always be a Segmentation Fault in xorg.0.log. The only way to boot properly is to delete the xorg.conf file although than I wouldn't be running the fglrx driver but instead the radeon open source driver (i think?)

Any help would be appreciated!

---

### Post by omegamike on 2010-11-29
I am having the same issue...I don't have any insights to offer :(

---

### Post by pwzhangz on 2010-11-29
> **bobyl573 said:**
> 
update:

ok I have solved this problem. What worked was directing downloading the driver from ATI website and than directing running the install script. Before I was downloading the driver and building the debian packages and than installing according to the install documentation. I'm not sure why it made a difference, but thanks for those that helped!

Thanks for so timely updating your post and providing your own solution.  I had decided not to update my Vision-based laptop.

---

