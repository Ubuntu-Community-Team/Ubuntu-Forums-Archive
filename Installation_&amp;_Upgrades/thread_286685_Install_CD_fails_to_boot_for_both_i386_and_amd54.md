---
title: "Install CD fails to boot for both i386 and amd54"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by Gorf on 2006-10-28
System Specs:#ubuntu
AMD64 3000
1G non-ECC DDR400
Seagate 100G SATA HD
ATI Radeon 9800 Pro
PS2 mouse and kb
Currently running Ubuntu 5.10 without any issue.

When I boot the system off of either the i386 or the AMD64 install CD, it gets to the boot options on the CD, I select to do an install (default and first option).  It unpacks the Linux kernel, initrd unpacks, then it switches to the Ubuntu logo with the scrolling bar underneath and proceeds to do something because the CDROM is fairly busy.  Then is switches to a dark screen.  On other 6.10 installs this is where X starts.  On this particular machine it clicks to black and never comes back.  CDROM activity stops and the machine will sit indefinately in that state.

Any ideas?  It seems there is quite a bit of problems similar to this.  Some posts in the forum have been suggesting that it is the Radeon card and I will certainly try swapping it out.  Any other suggestions?

---

### Post by Johnsie on 2006-10-28
I found that versions after breezy were very picky about what type of cd you use. I ended up only using traxdata, tesco and smartdata cd's rather than unbranded ones. It also depended on the cd drive i was using. Unfortunately there are a lot of other things that could be casuing this too. I hope you can find your answer.

---

### Post by Gorf on 2006-10-28
For the sake of archive here in the forum, here is what I discovered.

This issue was specifically relating to the video card.  Three attempts to install each with a different ATI card were all unsuccessful.  The 9800 Pro, the 9000, and a 9x00 something with all the TV bits.  All produced the exact same issue.  But when I installed a GeForce FX5200, bam booted first time.  

So for now I am chalking this up to some problem with the packaged ATI driver for the 9000 series radeon drivers.  I am going to try putting the card back post-install and see if the OS will pick up the change successfully.

---

