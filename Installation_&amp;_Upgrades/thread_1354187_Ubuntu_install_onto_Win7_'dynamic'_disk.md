---
title: "Ubuntu install onto Win7 'dynamic' disk"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by warp_fo0 on 2009-12-13
My apologies if my search fu is weak and I didn't stumble onto the dozens of threads addressing this issue, but I just haven't found a direct reference. (Either here or google...)

I have a Gateway p-7811fx with two drives. While the laptop does have built in fakeraid, that option is not supported by Ubuntu 9.10.

My goal is to install both Ubuntu 9.10 as well as Win 7 as RAID0 stripes across both discs. I have one partition dedicated to Win 7 Ultimate. grub2 will boot the OS images.

The remainder of the drives will be Ubuntu and installed with the alternate installer. However, in order to RAID Win7, the drives must be converted to 'dynamic' volumes.

What I cannot seem to verify is whether or not converting the drives to dynamic will break grub.

I'd appreciate any input.

Thank you,

m

---

### Post by audiomick on 2009-12-13
Not much here, but I think it relates to your topic:
[http://ubuntuforums.org/showthread.php?t=1327910](http://ubuntuforums.org/showthread.php?t=1327910)

---

