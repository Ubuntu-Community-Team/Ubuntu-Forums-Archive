---
title: "Pls help repair broken upgrade (8.04 -&gt; 10.04)"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by Skinner_au on 2011-06-28
Hi,

I've searched high and low on the tubes for a solution to my many problems arising from an upgrade between HARDY and LUCID (32bit). I've tried all of the *apt-get -f install *'s and liberal helpings of the *dpkg --configure -a *'s almost universally recommended. While I'm considerably closer than when I started, I'm not quite there yet.

To give a bit of (likely unimportant) background, this is a system that has been running for a little over 3 years, survived an upgrade from 7.10 to 8.04 and a conversion from physical to vmwware (currently running on ESXi4). There's alot (of junk) spread around the system and if I were to decommission it in favour of a clean install it would potentially take me a long time to get back to square one as it has accumulated so many small tasks over the years I'm not sure the effects would be immediately apparent to me. It's pretty much an indispensible part of my network and, suffice to say, I'd really rather resurrect it than wipe the slate.

The problem, like most good ones, began with my fault. Most crucially, I forgot to snapshot the VM prior to commencing the upgrade. At the root of the problem, a new version of python I installed quite along time ago (and forgot about) caused mass incompatibilities during the upgrade, and a significant number of packages failed.

After determining the cause and restoring the old python it took me a couple of days in the 7th circle of dependency hell coaxing all the packages back in to the system.

So I'm at the point now where APT thinks everything is hunky dory, but there are clearly some very crucial packages missing. GDM, for example, was not installed and after reinstalling that I have a login screen again, but no desktop will appear after logging in.

I'm a little embarrased to say that I've pretty much reached my knowledge limit of linux's engine room as I don't know what's missing to finish the installation. I also don't know how to ask the packaging system how to tell me what's missing (ie: a master list of packages for a desktop system) so I can compare and check that off. I'm not above doing that by hand if need be.

I'm reasonably certain there's something missing from the Xserver system, but I know too little about it to be sure, or how to determine it. Running the old *dpkg-reconfigure xserver-xorg* from the recovery shell results in no output. That is, it just drops to the next line.

If I try logging in under a X11VNC session I just get the old grey and white checker background with an X for a cursor, or just a black screen if I try it with an NX server login.

So even if the Xserver is part of the problem, I don't really know how to find out what else is missing and fix it. I'm sure the answers are out here on the net, I just don't know the correct questions to ask. I've also done an *apt-get install *for *ubuntu-desktop* which installed a heap more packages, but didn't fix everything.

Any help on my quest would be greatly appreciated.

Thanks

Sk

(PS: I can run synaptic over ssh from another machine if that helps)
(PPS: It's all on one partition, no separate /home or others)

---

