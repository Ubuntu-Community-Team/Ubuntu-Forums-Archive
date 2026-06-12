---
title: "SATA Controller Card"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by msrk on 2011-02-28
I am considering buying a SYBA SY-VIA-150R PCI SATA / IDE Combo
RAID Controller Card.  I have a Dell Dimension 2400 that only has
an IDE controller.  I want to install Ubuntu 10.10 on an SATA
drive with the SYBA SY-VIA-150R card.  The SATA drive would be
the only drive and therefore it would be the boot drive.

Will the Ubuntu installer recognize that drive?

Thank you

---

### Post by Mark Phelps on 2011-02-28
I had the opposite problem -- new PC motherboard without extra IDE jacks, stuck in IDE controller.  Ubuntu installs could see the drives -- but could not boot from either drive connected to that controller card.

Thried three different controller cards -- same problem with all three.

Sorry, but don't have experience with the model controller card.

---

### Post by msrk on 2011-02-28
I received a response to an email inquiry I sent earlier to the manufacturer.  They explained that "Ubuntu will not recongize the driver because the current driver's for SY-VIA-150R may does not support Ubuntu 10.10."

Can someone recommend a fully compatable sata controller card for Ubuntu 10.10?

---

