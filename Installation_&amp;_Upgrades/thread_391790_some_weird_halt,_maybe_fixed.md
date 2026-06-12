---
title: "some weird halt, maybe fixed?"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by jon61484 on 2007-03-23
ok, so a while back when I first got into ubuntu and tried it out, I liked it. Loved it, wanted and thought it was the overall best (for me) but was saddened when I couldn't figure out some weird issue with my computer halting for no (apparent) reason. Here is what would happen.

I would be using various software, it seemed to not be specific to anything, just, if I was doing *anything* it would suddenly crash. If any audio was playing it would freeze playing just the last hertz signal sent to the audio driver. The hard drive light would be on.

So then I got back into ubuntu, after devling around in about a dozen other distributions of linux, having installed Ubuntu 6.06 LTS. So when I was using ubuntu before (ubuntu, xubuntu, kubuntu, I tried them all to see if it was because of the desktop environment differences) it seemed that the problem wouldn't go away. Of course I was using 6.10 of those. So, after hours of work in 6.06 LTS with added on the XFCE desktop environment (I still can boot to gnome too, I'm playing with both to determine which I like/need) no problems.

I upgraded from the 386 based linux kernel that was standard with the 6.06 LTS version I was using ("2.6.15.11-3 on 386" ) to the newest in the repository of 686 linux kernel ("2.6.15.12-28.1 on PPro/Celeron/PII/PIII/PIV."). Thinking, because it said something to the effect of "good for these systems..." and it mentioned PIII. Since I have gigabyte 6XBDU (dual PII motherboard with two PIII 500mhz katmai) I thought "let's see if this works."

So it would hang. and I was working on images, my html files... stuff in here, and I lost all that information like 5 times. lol. so I switched back to the older linux kernel in grub during boot and it seems to have fixed it. ;) my sadness is now happiness.

anybody know why specifically? if anybody else is experiencing this problem on an older system like mine maybe they should go to the linux kernel I am *now* using. Which appears to be... working just fine.

is there really any reason to try another linux kernel, maybe one that might work better for me on my older system? as is everything I use works fine and my system is pretty quick so I'm not complaining or seeing a need (that I know of) for much more performance from what I have. Nothing misbehaves... right now.

Oh, and fiesty won't even boot from liveCD on this system. Comes up with an error about tty1 and busybox. ? I wonder.

---

### Post by jon61484 on 2007-03-24
seems that for whatever reason it was the kernel issue. I suppose for whatever reason my processor(s)/overall system doesn't like 686 optimized kernels. :| oh well.
maybe if anybody else has this weird system hangup then they can try going to a 386 kernel as well. at least when I installed the new ram and had issues I was able to switch to another tty box out of the failed desktop to be able to see what the errors were.

---

