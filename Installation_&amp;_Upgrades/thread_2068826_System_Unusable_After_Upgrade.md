---
title: "System Unusable After Upgrade"
date: 2012-10-10
forum: Installation &amp; Upgrades
---

### Post by smokey_58au on 2012-10-10
HI,

I am a long time user (since Dapper) and big fan of Ubuntu but events of the past few days have me scratching my head.  I currently run 3 laptops and 4 virtual servers with Ubuntu and last week decided to upgrade my wife's laptop from 11.10 to 12.04.  It has been running successfully with no problems on 11.10 since I upgraded it from 11.04 a number of months ago and had no reason to suspect the oncoming shower of doom.  Her machine specs are:

Asus  R1e Laptop
Intel Core2 Duo CPU T7500 @ 2.2GHz
4Gb  RAM
160Gb Sata Drive (no other OS installed)
Intel GM965 Video Controller
Intel 82566MM Ethernet Controller
Intel PRO 4965 AG Wireless Controller

The laptop itself is about 5 years old, I have owned it since new and it has never let me down (probably because the first thing I did was remove Vista and install Ubuntu)!  ;)Anyhow, when I did an inline upgrade to 12.04 on it last week, on reboot after the upgrade it became extremely slow to the point of unusable.  The reboot took about 5 minutes and it was slow right from the outset, even getting to the login screen.  Once it had logged in and finished the startup it was still too slow to use - a wait of 30 seconds or more for a dropdown to appear or a window to load (System Monitor being a good example as I tried to look for the cause).  The hard drive light wasn't overworking and the drive itself didn't sound like it was thrashing but the cpu(s) use (when I could get the window to load) showed an extremely high level, 100% in most cases, and the culprit seemed to be System Monitor.  I could wear that particular application being the cause if it didn't display the slow performance during the whole boot process but it did and also when I had System Monitor not open it so I rejected that. Similarly, the only other application using system resources to any extent was Compiz which I highly suspected from the start after Googling the  problem and seeing so many slow performance issues related to it and Unity.  In it's defence however, it was only using about 20% of the system resources and even when I logged in using Unity 2D (one of the many suggestions I later tried) it made no dofference.  On top of that, I'm of the opinion that Compiz/Unity should only start to affect the performance much later on in the boot process, not while it was just starting but if I'm proven wrong then I'll be happy with that.

Over the course of the next few days I reinstalled (fresh from a CD) the OS a number of times, always reformatting the hard drive to ensure no crud was left from a previous installation.  I tried 12.10 beta2 64 bit, 12.04 64 bit, 11.10 64 and 32 bit, 11.04 64 and 32 bit and the behaviour on reboot immediately following installation was exactly the same in every case.  I finally regressed to 10.10 and lo and behold,  a perfect Ubuntu system (as I have come to expect).  So I then tried an inline upgrade from that to 11.04 and it went straight back to the poor performance as before.

Now the most frustrating thing in all this is that up until I tried the initial inline upgrade to 12.04 this laptop had been purring along on 11.10 as it had previously on 11.04, no slowness, no max cpu, no errors.  In my efforts to find the reason I must have Googled hundreds of pages and most pointed towards the culprit being either Compiz/Unity or the VGA Controller but as the problem is occurring before Compiz/Unity kicks in and the Controller works absolutely fine on 10.10 and during each of the CD installation processes then I don't think either of these are my problem.  For want of no other ideas, I am suspecting there is a later kernel version that is causing my problems but that is really out of my depth to investigate.  Has anyone else seen this behavior or have any idea what might be causing it?  I am stuck in a hard place with this now because 10.10 is no longer supported but I can't install anything newer and I don't want to have to go to Gnome or another flavour of Ubuntu if I can help it.

Help!  :(

---

### Post by 2F4U on 2012-10-10
You could try Xubuntu and see if it is better. What graphics card do you have and what graphics driver are you using?

---

### Post by smokey_58au on 2012-10-10
Thanks 2F4U.

Xubuntu is not a good option for me as it's my wife's laptop and she is not computer savvy at all.  To have to introduce her to a new look and way of doing things would be a major pain in the rear!  Aside from that, 11.04 and 11.10 have worked fine on this machine for more than a year so I would rather find what has suddenly caused this issue to occur.  To answer your question (from lspci -k):

VGA compatible controller:  Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
Subsystem:  ASUSTeK Computer Inc. Device 14e2
Kernel driver in use:  i915
Kernel modules:  i915

*edit:  I just realised that I can try Xubuntu as a fault finding exercise by cloning the drive with Clonezilla and then installing the latest Xubuntu.  I'll try that in the morning.  Cheers.*

---

### Post by smokey_58au on 2012-10-12
I have now tried the Xubuntu option and can confirm that the problem is not Compiz/Unity as the laptop displays exactly the same slow, unusable behavior in Xubuntu 12.04.  So now I'm thinking that it must be the kernel but I don't know enough to go about troubleshooting errors or conflicts caused by the kernel.  I really need to get this sorted because I can't upgrade from 10.10 and as it is no longer supported I can't get updates on anything.  Besides, my wife likes the Unity interface and I have to keep her happy, right?  ;)

Is anyone able to point me in the right direction of what logs to look at or terminal commands I can run to check?

---

