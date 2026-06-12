---
title: "trouble installing to 64-bit powerpc lpar"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by jethrick on 2011-01-26
I attempted to install ubuntu-10.10-alternate-powerpc.iso to a 64-bit powerpc lpar (HMC controlled) by sharing the iso as a virtual optical device from the VIO server to the lpar of interest. The installer's inability to find a cdrom suggests the ibmvscsi driver is not included. A few questions:

1) Is that correct?
2) If so, might it be included in the future so Ubuntu can be installed in lpars in this fashion?  (I'm not sure, but it might imply including all drivers under linux-2.6/drivers/scsi/ibmvscsi).

I hoped an alternative strategy might be to install a "mini" image, and hope I could simply build and modprobe the needed vio drivers myself. The only available minimal cd image here [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) that I thought would be reasonable recent was the "Ubuntu 8.04 "Hardy Heron" Minimal CD"... but it doesn't boot. Indeed, although I've downloaded it numerous times, its MD5SUM never matches the stated value of 'ea27bc51724266831d8a025bc2648c49'. Instead, I always get '3f2f40fec2bf3e79442b919d19d9c557', so I'm of the opinion that the iso advertised on that webpage is corrupt.

So I have an additional question:

3) Will you be making a 10.10 minimal cd for 64-bit powerpc available? (I see it only for 32-bit).

---

