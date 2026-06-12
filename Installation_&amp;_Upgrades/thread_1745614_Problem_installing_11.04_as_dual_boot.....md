---
title: "Problem installing 11.04 as dual boot...."
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Rodhill on 2011-05-01
My friend has Windows XP and I wanted to install Ubuntu 11.04 as a dual boot system. I loaded the install disk to boot from the cd drawer and when the install got to the part where the options where to install to showed, there was no option to install 'alongside XP' so I was stuck as I'm not sure where to go now:(
Should I have been given the choice to 'install alongside'?

---

### Post by groogrux on 2011-05-04
I ran into a similar problem setting up a dual-boot system on my friend's hp laptop (with Windows 7).  My guess would be that you already have 4 "primary" partitions.  Ubuntu can be installed on a logical partition, so if you can remove one of the partitions, it should give you that option to install alongside.  Be careful though, because the C: drive is among those 4 partitions.  Generally, if you see a partition labeled "HP tools" or "Dell Utilities", it isn't something that is typically crucial to the system.

---

### Post by Grichi on 2011-05-04
I have the same problem, but my ThinkPad -- an admittedly old but reliable R32 -- has no extra partitions at all.

---

