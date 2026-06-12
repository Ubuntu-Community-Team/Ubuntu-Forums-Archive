---
title: "Alpha 4 - Toshiba Satellite A30 won't boot"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gibbylinks on 2009-08-29
Hi,
I have a Toshiba Satellite A30 laptop with 2gb ram and 30gb hard drive.

I have been running Jaunty with no problems until last kernel update, which wouldn't boot, although I was able to revert to the previous kernel which booted fine.

I decided to try Koala and downloaded Alpha 4 iso, burnt a CD a booted from it. Everything works fine using the live CD. I have to use the ACPI=OFF option booting, which I also had to do with Jaunty. (I'm posting this using the CD now).

 I decided to install it, I formatted my root partition, and swap partions, kept my home partion (root and home formatted to ext4) and installed using the CD by clicking on the install icon. Everything appeared to go smoothly, but it won't boot.

I get an error 
"0.044001 ..MP-BIOS BUG: 8254 timer not connected to IO-APIC"
although it carries on beyond this point. It also hangs on keyboard until I press esc key and then it continues.

I have tried editing GRUB on booting and put the ACPI=OFF, NOLAPIC, NOAPIC options into the command line. I've done these command individually and combined with no joy. I can't get the machine to boot. Also tried recovery option from GRUB.

Does anyone have any ideas, pointers ?

Thanks :confused:

---

### Post by gibbylinks on 2009-08-31
Okay.

I want to boot from my live CD then mount the hard drive as system and read/write enabled so I can run apt to see if that fixes anything.

I can mount the hardrive but it's "read only" (ext4 format)

Can anyone help me do this ? :confused:

---

