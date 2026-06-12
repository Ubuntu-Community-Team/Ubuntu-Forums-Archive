---
title: "Server install with 6 HDD in RAID onboard and SSD on PCIe add-in card - fails"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by Rebajas on 2011-10-15
HIya,

I'm hopping someone will know what the solution to my problem is:

I have a mainboard with RAID and 6 SATA ports. Into those I have 6 2Tb HDDs in RAID 1.

In addition to that I have a 2 port PCIe SATA card with a SSD attached.

When I install (11.10 server) I can't see my RAID array but I can see the SSD, so I continue with the install.

On reboot the machine hangs.

If I remove all the HHDs and connect the SSD to the mainboard I can install and run Ubuntu with no problems. If I then move the SSD back onto the PCIe card and reboot I can also log into Ubuntu. 

However, if I then readd the RAID array, everything dies again :(

So my questions are:

[B]How do I best go about using all the SATA on my mainboard for RAID with an SSD on a separate card for the system?

And why can I not see the RAID array when I do the install?[/B]

Thanks for any help you can offer on this one!


Tony.

---

