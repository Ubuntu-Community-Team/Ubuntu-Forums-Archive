---
title: "Tried to upgade, but clean install definitely better!!"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by kendoori on 2010-01-01
My Lenovo X61 has the dreaded Intel GM965 chipset which made audio/video pretty broken under 9.04. I implemented the various fixes, but was quite ready to jump to 9.10, albeit not looking forward to migrating. Although many many experienced folks here absolutely recommend fresh install always, I was determined to see if I could make an upgrade work as I was quite satisfied with my various customizations.  To make a long story short, after several different types of attempts, I eventually bit the bullet and installed fresh and rebuilt my set up manually. In the end it didn't take that long, and I ended up with a known good state to start from.

Here are things I tried during upgrade process:
1-[Success] Checked system for compatibility by running 9.10 LiveCD. Audio and video worked properly with no tweaks.
2-[Success] Created separate home partition and successfully moved everything properly to this while still under 9.04. Since I was already using 2 NTFS partitions for my Windows dual boot (I may be ready to finally blow this away because of 4 partition limit), I had to kill my swap partition as part of this process and instead created a swap file within the home partition. Highly recommend [this]("https://help.ubuntu.com/community/SwapFaq") as background.
3-[Success] Bought a second identical hard drive which I cloned my install to using [Clonezilla]("http://clonezilla.org/"). Cloning worked like a charm and am glad that I could easily go back to where I previously was by just swapping drives at any point. Drives are so cheap that I highly recommend doing this. The interface is a bit rugged for now-Geeks, but I would say it's highly reliable and not really that hard to use (especially if you use the non-expert mode). It's a great comfort knowing that I can easily swap hard drives at any point.
4-[Failed] After creating home partition, tried in line upgrade. This looked like it was going to work, but the system choked big time upon reboot. In retrospect I believe the issue was that the Intel drivers didn't update properly, and had I dropped down to a command line and forced the process to completion on reboot, it might have worked.
5-[Failed] I was still determined to try to make this work, so I swapped the drives back, and tried again, this time burning an alternate CD. The results didn't turn out to be any different than in line upgrade. Again, I believe that this was X related and had to do with the Intel drives
6-[Failed] Tried and upgrade without blowing away home partition (as to preserve programs and settings). Used synaptics to mark my various packages prior to this, with the idea of restoring the programs I needed easily. This kind of worked, but various programs didn't act quite properly in the new environment, most notably Firefox 3.5 which had all kinds of issues with fonts. I ran into the issue where Firefox wouldn't display text on certain pages. Tried various remedies, only to give up in frustration (in spite of the fact that Chromium (and Chrome) worked OK. The more I played with the new install using the old configs, the more I became suspect that something was not quite right.
6-[Success] Copied home partition (my working data was already on a separate partition) to my network for select copying after totally fresh install. Created an old fashioned list in Tomboy of all the programs that I wanted in my new install. I resolved to do this all manually to ensure that I had the latest versions of the respect packages. 

So while it's true that many have successfully done inline upgrades, and others have also used their previous configurations stored in their separate home partitions, I spent lots of time trying to do this carefully with lots of back out options and now conclude that the inline upgrade process (and the various variations I attempted) wasted lots and lots of hours for me. In the end it was a good learning experience for me, and suspect that when 10.04 is released that I might try an inline upgrade again, but I have low expectations ;-)

---

### Post by phillw on 2010-01-01
Hi, yeah, for some the upgrade path was a pain - I'm glad you made a backup. Mine was smooth, except for messing up my grub-->grub2 conversion by pressing the wrong button !!
my ext3 --> ext4 transfer went similarly smoothly, i just had to 'tweak' one of the commands.

As a little point, if you make one of your partitions extended, you can put swap on there and make a /home partition there also. That'll make future updates easier for you.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)  is an excellent tutorial - the only change i made was to put my/home onto my extended partition also - as, like you, i dual boot & primary partitions were running a bit low (what with me popping on an area for 10.04 to 'play' on, as well)

Regards,

Phill.

---

