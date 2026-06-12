---
title: "Error in making Gparted bootable USB drive with Startup Disk Creator"
date: 2014-08-05
forum: Installation &amp; Upgrades
---

### Post by Eric_Darsow on 2014-08-05
Hi. I'm trying to create a dual boot on my Lenovo T410. I downloaded the Gparted *.iso image so I can partition my drive. I downloaded Startup Disk Creator using the USC so I cna create a bootable drive from which I can run Gparted on my windows box. I specify the image file in SDC and the flash drive on which I would like Startup Disk Creator to create the bootable device. Durign the copying phase, the following error is returned:

   unorderable types: NoneType() <= str()

I tried erasing the flash drive and doing it again a few times. Same error.

The Gparted source image is called gparted-live-0.19.1-1-i486.iso

I'm running Ubuntu 14.04.1 LTS

Any thoughts?

---

### Post by yancek on 2014-08-05
> 
I'm running Ubuntu 14.04.1 LTS

You should still have the DVD/flash drive you used to install it, gparted is on it so you can use that.

---

### Post by oldfred on 2014-08-06
Is your system new enough to be UEFI. Then you would need the 64 bit version not the 32 bit version.
And if just about any computer that is not very old the 64 bit version may be better anyway.

You can also use the version of gparted that is on the live installer. I usually have both and and may use one or the other. The slight advantage of the gparted live version is that it usually is a bit newer version than the one in the Ubuntu distribution.

---

### Post by Eric_Darsow on 2014-08-06
Thanks for your replies. So I have two laptops: My old one is a 32-bit Xubuntu only box that I was trying to use to stage my partitioning for the new 64-bit install. I beleive based on searching that my 410 does use UEFI. So it sounds like I should try making my boot flash drive with the 64-bit iso for Xubuntu i have downloaded and try to use the gparted accessible in its install sequence? I'll give that a try. Thanks for your patience--I've only been a linux user for a few months now.

---

### Post by Eric_Darsow on 2014-08-06
We are all set with Ubuntu installed!

---

