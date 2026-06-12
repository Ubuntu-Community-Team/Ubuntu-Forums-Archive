---
title: "[SOLVED] No wireless after kernel 2.6.24 upgrade"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by JunCTionS on 2008-10-15
Hello,
I have a Toshiba satellite_A135-S4677, and after the last update wireless stopped working (it seems to detect the card just fine but won't see any wireless networks). Ethernet works fine. And if I run the previous kernel (2.6.24-19) wireless works fine.

I've never compiled the kernel or have much of an idea on how it works, so any pointers would be nice.
Also I wanted to leave notice for other users that might encounter the same problem.

I got a clue that it might be the kernel by looking at the system log:

Process:kernel
Messages:
```
[ 5689.623947] WARNING: at /build/buildd/linux-backports-modules-2.6.24-2.6.24/debian/build/build-generic/compat-wireless-2.6/net/mac80211/rx.c:2127 lbm_cw___lbm_cw_ieee80211_rx()
[ 5689.623968] Pid: 5252, comm: Xorg Tainted: P        2.6.24-21-generic #1
[ 5689.624014]  [<f8bb7e09>] lbm_cw___lbm_cw_ieee80211_rx+0x1d9/0x650 [lbm_cw_mac80211]
[ 5689.624098]  [<f8b801a4>] ath5k_hw_get_tsf64+0x44/0x70 [ath5k]
[ 5689.624130]  [<f8b869bf>] ath5k_tasklet_rx+0x33f/0x5f0 [ath5k]
[ 5689.624162]  [<f8b866f7>] ath5k_tasklet_rx+0x77/0x5f0 [ath5k]
[ 5689.624231]  [tasklet_action+0x4d/0xc0] tasklet_action+0x4d/0xc0
[ 5689.624253]  [__do_softirq+0x82/0x110] __do_softirq+0x82/0x110
[ 5689.624280]  [do_softirq+0x55/0x60] do_softirq+0x55/0x60
[ 5689.624292]  [irq_exit+0x6d/0x80] irq_exit+0x6d/0x80
[ 5689.624299]  [do_IRQ+0x40/0x70] do_IRQ+0x40/0x70
[ 5689.624307]  [sys_read+0x41/0x70] sys_read+0x41/0x70
[ 5689.624335]  [common_interrupt+0x23/0x30] common_interrupt+0x23/0x30
```

any suggestions on how to fix it? (besides waiting for the next kernel to see if it's fixed). Where and how should I post this as a bug?

---

### Post by bluebook on 2008-10-15
I think I'm having the same problem. I'm on a thinkpad x200 in which the wireless didn't work right out of the box, so I reinstalled it and at least i got a wireless option. Then I tried to connect to my usual network, to no avail. After a reboot I've got nothing, not even the network. In fact my "network settings" are completely empty. 

Would appreciate help!

---

### Post by Dorrax on 2008-10-15
I'm using Ubuntu Hardy and my wireless stopped working after todays update as well. Anyone know why? How long does it take for a fix to get released? This is my first update problem...

---

### Post by JunCTionS on 2008-10-16
did you try with the old kernel?
kernel updates aren't so common... but from what I've seen it's not so hard to recompile a kernel to fix driver issues (I've never done it but I've heard some people do it almost on a daily basis ^_^).
Since my old kernel does work I simply changed the default boot option:
```

vim /boot/grub/menu.lst

```
then changed 0 to 2:
```

savedefault 2

```
saved and quit:
```

:w
:q

```
which changes it to the previous linux kernel

---

### Post by bluebook on 2008-10-16
I guess I'm not sure how to try with the old kernel. I was going to do what you did but I can't find a savedefault=2 (or anything like that, just safedefault=false) in my menu.lst and I'm afraid of adding that in ... 

Any help in reverting would be great, I'm lost without my wireless! [http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by steveneddy on 2008-10-16
While booting the PC, when the GRUB menu shows up, hit the ESC key and select the kernel with -19 at the end and NOT -21.

The -21 kernel upgrade is giving a lot of people fits.

---

### Post by bluebook on 2008-10-16
OMG that worked!!! THANK YOU!!


So is inserting savedefault=2 (or would it be 3, since it's 3rd on my GRUB menu list) the way to make that the default when rebooting?

Also - how do I make sure that in the next kernel update I get to keep THIS kernel that I know works? I just installed Ubuntu so I don't know how many old kernels it keeps ...

Thanks again!!

---

### Post by JunCTionS on 2008-10-16
You're welcome :) 
Well I'd suggest changing the option back to 0 for the next kernel update (thinking the issue will be resolved by then).
But yeah, you'll need to change this for the next time it upgrades since it'll probably start loading the -21 (faulty) kernel.
So another way to do it (so that it sticks with the -19 kernel) is changing the savedefault at the start for
```
 default saved 
```
and then at the end of the -19 lines put savedefault
This will make it the default entry each time you run it.
Also, I guess the correct way to do it (after reading the [manual]("http://www.gnu.org/software/grub/manual/html_node/savedefault.html#savedefault")) is also default 2 (or 3 in your case), and not necessarily savedefault #... but it works ;).

---

### Post by steveneddy on 2008-10-16
I'm sure that in the next few days the devs will put another update on the wire that will fix the mistake.

---

### Post by alexcckll on 2008-10-17
I trust therefore that the fix the devs may put up doesn't break things then fix them - but the package is withdrawn, fixed, then put back up - after full QA done.

Speaking as quite a new user, I've just disabled Recommended from Software Sources, and will only be pulling critical security updates until this is resolved.  One person made the comment that critical stuff like the kernel needs better QA and needs to be bulletproof before it goes out...

Just MHO - I wouldn't have the first clue on how to fix it..

---

### Post by JunCTionS on 2008-12-12
Oh well, it got fixed with Intrepid Ibex (or the kernel that came with it) so I guess this has been solved. (and I'll mark it as such)

---

