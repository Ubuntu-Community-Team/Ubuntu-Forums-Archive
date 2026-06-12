---
title: "My HH upgrade but only with 2.6.20-16-generic kernel"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Handssolow on 2008-04-28
I've just upgraded to HH but I'm still having to use kernel 2.6.20-16-generic. The background here is that after my unsuccessful kernel upgrade in February, instead of using 2.6.22-14-generic I had to drop back at boot up to choosing Grub's option of 2.6.20-16-generic kernel with FF. If I did otherwise I got a message indicating my OS was looking for a root file system and I'm dropped to a BusyBox initramfs line.

I've been waiting for the Hardy Heron upgrade which I downloaded today but despite having kernel 2.6.24-generic, I'm still getting the same error message. While I may have HH, yet again I have to drop back to use 2.6.20-16-generic to get my system to boot, why oh why?

For the HH upgrade this time I only had my IDE drive connected, having previously thought that having also my Sata drive connected was the cause of my failure with 2.6.22-14-generic. I noticed a few error messages during today's HH upgrade but none that appeared to point to the cause of my current problem.

What could be the explanation why I'm unable to use any kernel more modern than 2.6.20-16-generic with either FF and now Hardy Heron? Why am I still left waiting for a root file system if I select 2.6.24-16-generic?

---

### Post by Handssolow on 2008-04-28
At last I'm on the latest kernel (2.6.24-16-generic) with my IDE drive's 32 bit system thanks to Rocket2DMn. Adding noapic acpi=off to the end of the kernel line in Boot/Grub/menu.lst was the tweak that was required. Strange that this wasn't required with my 64 bit on a Sata.

[http://ubuntuforums.org/showthread.php?t=767668&highlight=noapic+acpi%3Doff](http://ubuntuforums.org/showthread.php?t=767668&highlight=noapic+acpi%3Doff)

---

### Post by Handssolow on 2008-04-29
Whilst I now can boot with 2.6.24-16-generic by adding noacpi acpi=off to the kernel line in Grub, I discovered that after I'd posted last night, my desktop didn't power down automatically.

Returning to it this morning, now the screen resolution isn't right but if I attempt a "sudo dpkg-reconfigure xserver-xorg" half way through I'm sent back to a Terminal message-

FATAL: Error inserting battery (/lib/modules/2.6.24-16-generic/kernel/drivers/acpi/battery.ko): no such device

I have a Asrock 939Dual-VSTA desktop motherboard, the only battery is CMOS battery! The bios does have an ACPI HPET Table which I can enable or disable but it seems to make no difference.

Any suggestions how I can sort out this acpi thing and reconfigure my xserver-xorg?

I'll check power down function next. Just checked again, no automated power down.

Added later: I'm booting having adding pci=noacpi to the kernel line rather than noacpi acpi=off
It boots normally, I've got a reasonable screen resolution with the Nvidia driver 1280x780 but I doubt shut down will be hands free and I haven't fully been able to customise the system sounds as I had with GG.

---

