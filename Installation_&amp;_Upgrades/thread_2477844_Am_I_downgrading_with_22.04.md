---
title: "Am I downgrading with 22.04?"
date: 2022-08-08
forum: Installation &amp; Upgrades
---

### Post by libertyspike138 on 2022-08-08
So far I'm not too impressed... I moved my nVidia GTX 770 from an older Intel DH67CL board to a newer Gigabyte GA-B150M-DS3H board and installed 22.04 instead of 20.04. I have 2 1080P monitors, max resolution on xorg for mirror is 1360x768. Even worse in Wayland at 1024x768. I have the latest proprietary tested 470 driver installed for this card.

When trying to add new modes...

$ sudo xrandr --addmode DVI-I-0 "1680x1050_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  41
  Current serial number in output stream:  42

I can apply better modes in NVControlPanel but will not save...

Maybe even worse... My audio keeps skipping... I had it working for a bit but then my partition table got wiped and I had to start over. I performed the same fixes and it does not work. Also on the last install I had slightly better resolution...

Not sure if it is 22.04 or just this new board but this is a mess!

---

### Post by TheFu on 2022-08-08
Every new kernel has risks.  nVideo proprietary drivers stopped working for my fantastic 7200GS with the move off 16.04, so my choices were
* live with 720p resolution and the F/LOSS driver ... on a 1200p monitor which works perfectly at that resolution
* buy a new GPU, as cheep as possible.  This is what I did. I spent ~$70 for a 1030 GT and I wish I'd switched to AMD, since AMD wasn't/isn't so anti-Linux.

That was a few years ago.  I didn't want to be forced into a new GPU.  The hassles with the newer 1030 card have been going on since I got it.  They aren't continuous, but every patch and every new kernel is a risk for the proprietary nVidia drivers.  Most of the time, they work, but perhaps 10 times in the last 3 yrs, they do not.

Last fall, I replaced a 2015-ish  Intel Pentium with iGPU for a Ryzen 5600G w/ iGPU.  The 4.x kernel didn't come with that GPU supported, so there was tearing and poor performance, so I looked up the kernel version that was needed to gain support ... 5.10.x ... which isn't exactly what that system had by default - it is running the HWE for 18.04 - 5.4.x kernels.  Have to say, since moving to a non-standard kernel, just on that machine, everything related to the GPU has been fine. No issues.  Plus, last fall, a GPU like the nvideo GT 1030 I already have was $120, so extremely overpriced.  I barely use these GPUs. If the install was easy from a serial console port, I'd have been happy with that.  Should also say that the Ryzen 5600G iGPU is faster and more capable than the nvidia GT 1030 (DDR5) card.

Anyway, there are always people unhappy with new releases when they have old hardware that just doesn't work. OTOH, people with newer hardware don't care if our old stuff doesn't work at all.

To me, every Ubuntu release since 10.04 has been a downgrade.  10.04 had no surprises and behaved like I expected a Linux distro to behave.  Since then, every release screws up something, be it adding resolvconf (which is completely unneeded), swapping out initd (for systemd or upstart), pushing ugly, new¸ bloated, DEs, adding mandatory dependencies for things that I'll never use - cloud-init or bluetooth or mounting things under /media, forcing snap packages, netplan, and a few other things that should be optional, not mandatory.  Remember when they added amazon search for all local searches?  That was a huge mistake.  Most of those things took over a year after being added to the LTS before they were actually stable. Some aren't stable today 6 yrs after being forced onto user.  In my LUG, we fight with Pulse Audio still - almost every week.  That are introduced around 2004!  It will be retired before it "just works."  
I fear the same will apply to systemd stuff.  BTW, I'm a fan of journalctl - the system logging tool that came with systemd.  It is an improvement, though it isn't mandatory to use it in Ubuntu.

I really dislike the way that storage is setup on all new installs with a swap file and / partition that is larger than 40G, no separate /home, /var, /tmp, /boot partitions, at a minimum.  But everyone is a critic with different ideas.  Ubuntu has decided to make poor security choices in the partitioning to keep it simple. Confusing ignorant coming-from-MS-Windows users isn't a great idea either.  I really dislike the unwanted tracking in Ubuntu.

Canonical abuses the "default" just a little too much. They insert things as defaults which really need to be optional.  Support for CIFS, AD, google-logins, any social network connections, for example.  I'll never use any of those things. Don't want any of them.

But there are also the things that are done really well. Far too many to list.  Of my 20 complaints, there has to be 1000+ things that Canonical does better than any other distro.  Every distro has warts and it is impossible to please everyone, all the time.  Not you. Not me.  I just wish that LTS releases didn't have **any** non-working surprises.  Introduce surprises in the non-LTS releases, but leave the LTS alone, please.  No surprises.  Wayland has no good reason to be in any LTS yet. It isn't ready.

---

### Post by libertyspike138 on 2022-08-11
Ultimately I just ended up setting up another PC for my TV instead of running a mirror and can now run my main monitor at 1080P. Too bad that the mirroring options need some work and the nVidia Control Panel doesn't work well in 22.04 like it does in Windows.

---

### Post by QIII on 2022-08-11
> **libertyspike138 said:**
> Too bad that the mirroring options need some work and the nVidia Control Panel doesn't work well in 22.04 like it does in Windows.

That might be a good thing to bring up with nVidia.

---

