---
title: "Unbootable: Best fstab approach?"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by RMOP on 2011-12-09
I made a single entry to my fstab on my nicely configured 11.04 machine...and now it doesn't boot into Ubuntu anymore. I was careful, only adding an auto-mount line for an NTFS Data drive, "knew what I was doing," but something went amiss.

I've never needed root access to an unbootable Ubuntu machine before.

I have three options, as I see it:

1) boot to Live CD and get root access to fstab and either edit it or replace it with a known-good backup copy. Never done that, but it seems to entail basic hand work via terminal.

2) boot to Windows and try ext2fsd to mount my Ubuntu partition w (supposedly) W/R access

[http://www.ext2fsd.com/?page_id=7](http://www.ext2fsd.com/?page_id=7)

3) boot to OSX and try mounting this drive on *that* system using a trial version of Paragon's extFS for MAC.

[http://www.paragon-software.com/home/extfs-mac/](http://www.paragon-software.com/home/extfs-mac/)

Nice to have options, I suppose, but having never used any of the above, I'd appreciate knowing which is likely to get me quickest and safest access to my fstab. Obviously, I need W/R access to fix things.

Thoughts, please? Many thanks.

---

### Post by nothingspecial on 2011-12-09
I'd do it from the live cd.

---

### Post by RMOP on 2011-12-09
> **nothingspecial said:**
> I'd do it from the live cd.

Did. The only painful part was wading through the awful Unity menu to find Terminal.

Thanks.

---

