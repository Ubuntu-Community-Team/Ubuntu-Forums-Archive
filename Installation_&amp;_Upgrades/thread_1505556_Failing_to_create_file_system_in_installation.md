---
title: "Failing to create file system in installation"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by dawgie2009 on 2010-06-09
While installing Ubunto 10.0.4 configured to erase and format hard disk I'm getting an error saying the ext4 file system creation in partition 1 of serial ATA volume0 (Stripe) failed. 

Any idea how I can get around that? I want to format whatever existing on disk and install ubuntu. 

Thanks.

---

### Post by tommcd on 2010-06-09
> **dawgie2009 said:**
> While installing Ubunto 10.0.4 configured to erase and format hard disk I'm getting an error saying the ext4 file system creation in partition 1 of serial ATA volume0 (Stripe) failed. 

Are you trying to install Ubuntu using a RAID array?
Do you have RAID enabled in the computer's BIOS?
If so, then try disabling RAID in the computer's BIOS and then try installing Ubuntu.
That error you are getting is related to a RAID setup I think.

And welcome to the Ubuntu forums!

---

### Post by dawgie2009 on 2010-06-09
> **tommcd said:**
> Are you trying to install Ubuntu using a RAID array?
Do you have RAID enabled in the computer's BIOS?
If so, then try disabling RAID in the computer's BIOS and then try installing Ubuntu.
That error you are getting is related to a RAID setup I think.

And welcome to the Ubuntu forums!

Thanks! 

I tried all the possible combination in the bios with RAID but none of them worked :-(

---

### Post by tommcd on 2010-06-10
Make sure RAID is *disabled* in the BIOS if you have it enabled.
What happens if you try using manual partitioning?

---

