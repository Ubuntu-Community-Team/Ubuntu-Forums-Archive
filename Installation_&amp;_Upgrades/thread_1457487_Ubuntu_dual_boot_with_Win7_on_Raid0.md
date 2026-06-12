---
title: "Ubuntu dual boot with Win7 on Raid0"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by oogravyoo on 2010-04-18
New to Linux and am wanting to install ubuntu 9.10 or 10.04 on a single separate 80gb drive. I have Windows installed on 2 80gb drives in Raid0 (nvidia controller) 

I have installed 9.10 but Win7 will not load from the bootloader : gives me the error invalid signature. I've looked around and tried a few things to get it to load with no success.. 

is there something I needed to do during install that would have helped this situation? is the Raid0 the issue? 

If I try to install 10.04 it will hang and eventually errors out, I believe on the raid drive because it comes up with dev/mapper/nvidia_hhfbdccf1..

---

### Post by oldfred on 2010-04-18
Was the separate drive you were using once part of the raid set? grub2 has issues with some hidden raid settings on drives.


Another user, but he had grub legacy and it worked.
[http://ubuntuforums.org/showthread.php?t=1457222](http://ubuntuforums.org/showthread.php?t=1457222)

---

