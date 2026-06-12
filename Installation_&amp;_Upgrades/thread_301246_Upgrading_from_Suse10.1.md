---
title: "Upgrading from Suse10.1"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by Duwi on 2006-11-16
Hi,
I have Suse intalled on my T60 thinkpad and don't like it at all. i would like to install Ubuntu instead and was wondering whether I could keep the existing partitioning 9created during the suse install). I have different partitions for /boot,  /, /home etc and don't want to change their sizes nor locations nor their partition type (reiser, etc.)
Is their a way that during the install of Edgy I just tell the installer to use the excisting partitions as they are, just overwrite everything (maybe not /home) with Ubuntu stuff?

I would appreciate any help

thanks a lot

---

### Post by taurus on 2006-11-16
Yes, you can keep your existing partition table when you install Ubuntu.  I recommend you use the alternate CD since you have more control over what to do with it when you get to where you want to install it.  Make sure you format those partitions except the /home and don't forget to mount that partition to /home but skip the formatting.

---

### Post by Duwi on 2006-11-18
Thanks very, very much. the installation worked very smooth. I just had to deal with the graphics. I installed without touching the resolutions and then installed the ATI driver following the description on the Ubuntu Howto pages. (method 1) works nice.
Now I try to get the scroll button on My T60 to work.

Again Thanks a lot

---

