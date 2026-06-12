---
title: "warning: Incorrect checksum in table [TAMG]"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by chuz41 on 2012-04-23
Hi, I have a problem with my computer,I have a GA-880GMA-USB3(rev. 3.1)motherboard and AMD FX-8150 processor.

When I try to install ubuntu, I was getting following message before the boot process would freeze: ACPI Warning: Incorrect Checksum in Table [TAMG] 0xD2, should be 0xD1 -(20110623/tbutils-314) .

I have the latest bios off the gigabyte website F4C and 8GB of corsair RAM.

I realy need get ubuntu in my system, I was try with ubuntu 10.04, ubuntu 10.10, ubuntu 11.04, ubuntu 12.04, scientific linux,  ubuntu 11.10, and ever got the same messege.
Any ideas why this might be happening?
Thanks

---

### Post by Paddy Landau on 2012-04-24
I wonder if your computer has UEFI? Is it a new computer with Windows? If so, it is possible that it uses the new UEFI security system that prevents installation of other operating systems and even drivers without a valid signature.

Can you find out from your manual or your manufacturer? If it is on, I think you'll have to turn it off via the BIOS settings.

If I'm wrong, then sorry, I don't know what to do next.

---

