---
title: "Ubuntu 9.10/64 on RAID 0 - Sony Vaio Z"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by asiandub on 2010-03-27
Hi all,

I got a new Sony Vario Z and try to install Ubuntu on it. The laptop has got two 64 GB SSDs setup as a RAID 0 array. 
([http://www.laptopsdirect.co.uk/Sony_VAIO_Z11X9E-B_Core_i5_Laptop_VPCZ11X9EB/version.asp?refsource=ldawin#top](http://www.laptopsdirect.co.uk/Sony_VAIO_Z11X9E-B_Core_i5_Laptop_VPCZ11X9EB/version.asp?refsource=ldawin#top))

As the configuration is done in the BIOS, I assume it's hardware RAID. 
([http://imageshare.web.id/images/ys1vdl4liu6ynt7udcll.jpg](http://imageshare.web.id/images/ys1vdl4liu6ynt7udcll.jpg))

The problem is that - no matter what I try - the installers are unable to write the GRUB loader on the hard disk. I tried both, standard and alternate installer (9.10 / 64 bit), and both failed at that point. Not a really error message, it just says "cannot write GRUB boot loader".

I also tried two different scenarios: 
- Ubuntu beside Windows (shrinked the partion for that)
- Ubuntu on the empty RAID

Same result for both.

Any ideas? Hints? 

Cheers,
Jan

---

### Post by asiandub on 2010-03-30
solved - had to kick to BIOS fakeRAID for a clean linux softRAID...

cheers,
Jan

---

### Post by kniklawski on 2010-04-08
I just got a vaio z as well.  I am having the same problem.  Would you mind elaborating on the solution?  I don't quite understand what you mean. 

**Thanks** in advance!

---

### Post by kniklawski on 2010-04-08
Please help!!  I can't find anyone else who has had the same problem, or has a solution.

It would be greatly appreciated!!

---

### Post by skitzandroid on 2011-01-25
I have the same problem.  Did anyone ever find a solution?

---

### Post by realzippy on 2011-01-25
Welcome to the forum!
[AFAIK]("http://linux-macbook-air-killers.blogspot.com/2010/03/fake-raid-in-linux-sony-vaio-z11-series.html") it is not possible to use this fakeraid-controller.
If not dualbooting you can set up a real software raid for ubuntu after disabling fakeraid in the BIOS.

For further problems (intel/nvidia graphics,microphone) on this laptop 
check out:
[https://launchpad.net/~sony-vaio-z-series](https://launchpad.net/~sony-vaio-z-series)

---

### Post by skitzandroid on 2011-01-26
Thanks realzippy.  That's not the answer I was looking for but you will save me a lot of searching for a non-fix.

Im gutted that this machine won't run Ubuntu.  Was blinded by the awesome hardware and never stopped to think that such specialised configs (quad-SSD, dual gfx cards etc) would not play nice without vendor support.

I'll go back to sobbing over my keyboard now ;)

---

### Post by realzippy on 2011-01-26
If you do not want a dualboot with windows,you can install a linux
software raid (which *might* be even faster...),or you can reinstall
windows and ubuntu without using the fakeraid-controller.

---

### Post by gyhor on 2012-01-03
it is possible to install ubuntu on the fakeraid.
Just use the alternate install cd or usb stick.

I installed ubuntu 11.04 on my Vaio VPC-Z21 without removing the raid 0 configuration. I have dual boot with windows.

---

