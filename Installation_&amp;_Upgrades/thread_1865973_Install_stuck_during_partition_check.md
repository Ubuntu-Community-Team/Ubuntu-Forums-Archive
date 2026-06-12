---
title: "Install stuck during partition check"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by skoinga on 2011-10-20
Hi,
I can't install Ubuntu on my PC (AMD 64bit processor, 2 GB RAM, 250 GB Hard Disk); during partition check, installer stucks.
Same behavior with: Ubuntu 9.10, 10.04, 10.10, 11.04, 11.10
I can only install Ubuntu 8.04 and make several upgrade.
I tried to pass "nodma", "noapic", "nolapic" parameters at boot but without solving my issue.
Any ideas?
Thankyou very much

---

### Post by MAFoElffen on 2011-10-20
> **skoinga said:**
> Hi,
I can't install Ubuntu on my PC (AMD 64bit processor, 2 GB RAM, 250 GB Hard Disk); during partition check, installer stucks.
Same behavior with: Ubuntu 9.10, 10.04, 10.10, 11.04, 11.10
I can only install Ubuntu 8.04 and make several upgrade.
I tried to pass "nodma", "noapic", "nolapic" parameters at boot but without solving my issue.
Any ideas?
Thankyou very much
Yes, but first...

What is your HDD type?  IDE, SATA2, SATA3, SCSI?

Reason I ask is that SATA3 is not supported by Linux yet, so you have to use the drive as SATA2. The other drives...

Well I have one of my test boxes, that during a development branch testing cylcle I averge one install a day on.  If I just boot on the LiveCD and install it hangs at the partition manager.  If I boot, enter the BIOS settings it will say "AUTO" on the drives.  If I look at the drives, it will display the drive info... If I exit the BIOS Settings, even without saving the settings, then when it boots on the LiveCD it goes to the partition manager successfully and see's the drives.

I could be wrong, but I think the Partition Manager looks at the BIOS/CMOS to check the drive types.  If things are different in the BIOS than is actually there, then it hangs.  At least on that test box...

Just something to try.

---

### Post by skoinga on 2011-10-21
> **MAFoElffen said:**
> Yes, but first...

What is your HDD type?  IDE, SATA2, SATA3, SCSI?


Hi,
it's a IDE hard disk. I'll try the bios way and let you known
Thankyou very much

---

### Post by MAFoElffen on 2011-10-21
> **skoinga said:**
> Hi,
it's a IDE hard disk. I'll try the bios way and let you known
Thankyou very much
I'll keep an eye on this and see how it works out for you...

---

### Post by skoinga on 2011-10-22
> **MAFoElffen said:**
> I'll keep an eye on this and see how it works out for you...

Still no luck.. I tried: CHS, LBA, Large in BIOS, but the problem still occurs.
I've also tried to completely delete the partition; the installer was fine a little more, but still hangs during "copy file" phase.

---

### Post by skoinga on 2011-10-27
> **skoinga said:**
> Still no luck.. I tried: CHS, LBA, Large in BIOS, but the problem still occurs.
I've also tried to completely delete the partition; the installer was fine a little more, but still hangs during "copy file" phase.

Problem solved with "acpi=off" at boot's live cd

---

