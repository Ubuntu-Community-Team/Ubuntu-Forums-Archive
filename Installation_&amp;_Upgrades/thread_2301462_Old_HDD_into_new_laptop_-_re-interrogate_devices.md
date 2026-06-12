---
title: "Old HDD into new laptop - re-interrogate devices?"
date: 2015-11-02
forum: Installation &amp; Upgrades
---

### Post by Martyn12 on 2015-11-02
Wife is buying a new laptop because her current one is past it - problems with battery and mains power.  Long story short, she wants a new piece of hardware.  

I am hoping to swap out the HDD from her old laptop and put it in the new one (it was bought separately so is a larger capacity than the original anyway). 

Is there a way I can get Ubuntu to maintain the installation but re-interogate for the new hardware that will be present in the new laptop? 

Thanks for any advice.  

PS - I cannot remember if the Home directory is on a different partition or not.  I suspect it will be (it dual boots with Windows 7 but not bothered about that - it is just dead space).  All I want to do is ideally keep 14.04 installed and her Home directory intact.

---

### Post by Dennis N on 2015-11-02
The old drive in a new laptop will work provided the old drive has a SATA interface.  But, if the old drive dates to about 2006 or before, it may be a PATA interface drive (rather than SATA) which you can't physically plug into the new machine's drive bay. You can tell by the different connector, information on the label, or google the drive model to see. Also, older SATA drives (SATA 2) have a slower theoretical transfer rate than newer SATA 3, meaning somewhat slower performance. That may be a factor to consider.

SATA 2 = 3 GB per sec
SATA 3 = 6 GB per sec

As to the new hardware components, I can't really give you a answer to how completely it will reconfigure - I think you really need try it to see if any problems arise.

---

### Post by ajgreeny on 2015-11-02
Uninstall any proprietary graphics driver from the system before you stick it in the new computer and then you can install any different drivers needed after the first boot.

With the new motherboard you will also probably have to deal with UEFI and probably need to change to legacy BIOS/CSM or whatever it is called in your new machine as your old drive will presumably be formatted with the MBR partition table, not GPT.

---

### Post by oldfred on 2015-11-02
One user posted that he buys a new laptop regularly, removes hard drive and installs SSD so system is very fast.
Then when he sells system, he just puts original Windows drive back in which is just like new.

You may want to either use new drive or consider an SSD. Old drive will not be as fast.

---

### Post by Martyn12 on 2015-11-02
Thanks for both your replies.  

It is a modern-ish drive - probably less than 2 years old.  We got it for greater capacity.  Now the laptop itself is past it's best and she just wants a new one.  

I'll do as you suggest - uninstall any prop drivers then just go with the flow.  

Thanks again.

---

