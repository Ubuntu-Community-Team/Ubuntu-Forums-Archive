---
title: "installation problem on AMD64"
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by mfleming on 2006-05-26
I'd really appreciate some help with the following.

I have just installed the Ubuntu 5.10 AMD64 image. This seemed to go OK, up to the point where I was instructed to remove the medium and reboot the computer. Then, the boot from HD failed to complete. I got the following message:

CLIENT MAC ADDR: (my mac address) GUID: FFFFFFFF-FFFF-FFFF-FFFF-FFFFFFFFFFFF
Configuring DHCP: (spinning image)

Eventually this timed out and I got a message from the NVIDIA boot agent complaining about the lack of a boot file.

Evidently the system hung trying to get DHCP working. Is there any way to debug this? I should mention that I gave my system a hostname of dp1, while there is already a dp1.dpath.mcw.edu on the subnet (the reason being that the new system will replace dp1.dpath.mcw.edu when it is configured). I can't imagine this should be a problem. Also, I should mention that I was able to load Ubuntu on this same machine from the AMD64 live CD without any problems, which would seem to eliminate hardware, compatibility, network issues etc as a cause of the problem.

Thanks much,

Matthew Fleming

---

### Post by Frank-Hamersley on 2006-05-28
Matt,

I have had problems (unresolved so far) in the area of the ATAPI CDROM which has caused bad packages to be loaded on to the HDD which then causes headaches later in the process.

I am using a HP dx5150.  All that said I had no problems with dhcp and have since moved the machine to a static address for other reasons.

Cheers, Frank

---

