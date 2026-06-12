---
title: "Partition with GParted, then install from Desktop CD?"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by JimNSB on 2007-06-23
My motherboard has problems with the Alternate CD (installation failed), but other owners report successful installs by switching to the Desktop CD.  Since that version has limited partitioning options, I'm wondering if its possible to create the partitions with GParted (using the LiveCD), but still install Ubuntu 7.04 from the Desktop CD.  All the guides & documentation I've found lead me to believe that only the Alternate CD can be used if I create my desired partition-scheme[COLOR="Blue"]*[/COLOR] with GParted.

I should add that this will be a single-boot Ubuntu system using a lone (empty) 320gb SATA HD.  Preferably, I'd like to set things up to simplify (as much as possible) adding another distro/OS down the road.


[COLOR="Blue"]*[/COLOR]/, /home, /usr, /opt, /tmp & /swap (and possibly /boot).

---

### Post by Pumalite on 2007-06-23
> **JimNSB said:**
> My motherboard has problems with the Alternate CD (installation failed), but other owners report successful installs by switching to the Desktop CD.  Since that version has limited partitioning options, I'm wondering if its possible to create the partitions with GParted (using the LiveCD), but still install Ubuntu 7.04 from the Desktop CD.  All the guides & documentation I've found lead me to believe that only the Alternate CD can be used if I create my desired partition-scheme[COLOR="Blue"]*[/COLOR] with GParted.

I should add that this will be a single-boot Ubuntu system using a lone (empty) 320gb SATA HD.  Preferably, I'd like to set things up to simplify (as much as possible) adding another distro/OS down the road.


[COLOR="Blue"]*[/COLOR]/, /home, /usr, /opt, /tmp & /swap (and possibly /boot).

Prepare the drive using Gparted and making one LARGE partition of the entire drive, formatted ext3. Then install. Choose 'Guided>Use Entire Disk'.

---

### Post by Bothered on 2007-06-23
I installed ubuntu most recently in exactly that way - partitioned with gparted using the live CD and then ran the installer, using custom partition options at the partitioning stage to set the mount points.

---

### Post by JimNSB on 2007-06-23
Great; thanks to both of you.

I also have a few questions about my partition plan; the sites/sources my research led me to either had no (clear) answer or contained what appeared to be 'conflicting' info/advice.

--right now, I'm only installing Ubuntu (new system; totally empty HD), but can forsee installing other distros (possibly even Windows) in a few months time.  I've read that some OS's prefer/require that the /boot partition occupy a specific location on the HD, and also that having a separate /boot partition has its advantages.  I figure including one now (in the optimal spot) would be much easier than '*squeezing one in*' later. So would it be a good idea to create a */boot* partition now, or wait until I add more distros/OS's?

--if the answer to including a /boot partition now is 'no', do I need to (or should I) flag the /(root) partition as *bootable*?

--since this won't be a server, is there any need (or advantage) to adding a /var partition?

TIA

---

### Post by JimNSB on 2007-06-23
After spending the afternoon researching this (and then downing a couple Advil!!), I have a new plan: 

/boot, /, /swap

...much easier <g>

---

### Post by merlinus on 2007-06-23
Don't forget /home!!!

-merlin

---

### Post by JimNSB on 2007-06-24
> **merlinus said:**
> Don't forget /home!!!

-merlin

Some of the dozens of opinions/views I read pointed out that on a single-user system (like mine), having a /home partition isn't as vital as on a multi-user box.  I understand there's many indisputable advantages to having separate partitions, but by letting the Desktop CD '*do its thing*' (create just a / and /swap) the installation occurred without a hiccup: I'm not gonna argue with success!

And now that I actually have my hands on a working Ubuntu system, I'm learning at a *much* greater pace than before.  Today I _know_ procedures that yesterday I had only 'read about'.  Soon (who knows ...maybe even later today!) I'll be able to backup, create additional partitions, etc., and be far beyond the point of '*planning*': I wish I had made this choice last weekend! <g>

Keep in mind this is a separate, new system; if things 'go south' I can just plug my old box's CAT5 back into the cable-modem and start again ...but I _won't_ be starting at *square-one*.

---

### Post by Bothered on 2007-06-24
It's easy to share a home between different OSs if it's on its own partition. However, I like to keep my OSs separate (each with its own documents folders) and so don't have a separate home partition.

IMO a boot partition is a good idea, even if you don't add any other OSs.

---

