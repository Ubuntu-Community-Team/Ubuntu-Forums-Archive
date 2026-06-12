---
title: "alternative to raid0?"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by xero 1ne on 2007-05-09
Hellos...I've been trying to get 7.04 on my nforce 4 sata raid0 for a while, but gnome partition editor doesnt show the mapper device, and dmraid only shows 80gb when it should be ~160gb total

I want to have raid0, but idk if I'm able to do this, being such a linux newb.(i've tried every tutorial known to man)

Is there an alternative to raid0 to where i can have my two 80Gb drives as one partition for /?

(I'm going to put my swap on a spare 10Gb ide drive i have.)

I recently used Fedora for a little bit for the software raid, but it was uber-slow for me compared to ubuntu...

any help would be great :/

---

### Post by Wim Sturkenboom on 2007-05-09
I don't think that that's possible (although somebody else might know how to do it or can help you how to setup your raid). You can however mount your second HD so you can still access it (but it will not give you one 160GB partition).

---

### Post by dpecile on 2007-05-09
You need to see only 1 drive or need the speed of raid 0 ? if you need raid 0 only to see the 2 drives as one, you can use lvm, but this or raid 0 are the most dangerous configuration, because you have double chances to lost everithing if one drive fail...


Bye

Demian

---

### Post by xero 1ne on 2007-05-09
I understand fully the "risks" of raid0, but unless you are playing baseball with your hard drives, you should be fine. Hard drives are much more sturdy nowadays, and in all my life, i've only seen one hard drive die on its own.(the others were human error with the power cable:mad: ) 

Not too long ago, I was in a car wreck with my friend, the truck rolled ~5 times, his computer was totaled, mine was only a bit bent and dented in quite some places(steel <3) and all my computer booted just as normal right after that. (even his data was fine though)

Plus, I use Seagates <3

So if anyone can help me with the Mr. risky raid 0, please by all means do (lvm too)

Btw, I have a backup of all my data, because I HAVE done recoveries from a corrupt mft, re-partitioning, and accidental formats...not funn...but I just don't know how to get Ubuntu rolling with raid :/

The speed of raid0 would be awesome, but if i can't get that working, the convienience of only having to manage one 'drive' would be awesome as well

---

### Post by DJMatty on 2007-05-11
Hi

I got ubuntu going on my raid0 array (asus striker extreme 680i mobo), like you I had to read a lot of how-to's and tutorials and none of them worked...

Providing you get dmraid installed and seeing your volumes correctly (which it did first time on my system) I then installed feisty to a spare sata drive I had, then made the partitions I wanted on the raid array and manually copied the system across from the SATA to the raid partitions, then re-setup grub to use the raid drive, rebooted and all was good.

I have since reverted back to just using the install on the SATA drive as I had some other problems (gfx card related iirc) and had been re-installing a lot and couldn't be bothered with the hassle of the setup every time I re-installed, so just left the install on the sata drive.

HTH

Matt

---

