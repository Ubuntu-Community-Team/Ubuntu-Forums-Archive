---
title: "[SOLVED] Unable to install"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by birdkathe on 2008-08-04
I got to be an Ubuntu convert at my last job and thought I knew enough to install ubuntu easily (humble pie anyone?). So I ordered a computer without a pre-installed OS from PC's for Everyone. Here are the specs:
• Shuttle SP35P2 PRO Intel Socket 775 XPC
• Dual-Core Intel® Core™ 2 Duo E8500 3.16GHz 1333FSB 6MB Cache
• 4 x 2GB PC6400 800MHZ DDR2
• 1000GB Serial ATA 7200 RPM - Seagate Barracuda® 7200.11
• Samsung 20x DVD+/-RW Dual Layer SATA
• 19-in-1 3.5" Card Reader (Black)
• MSI nVidia GeForce 8400GS 512MB DDR2 PCI Express (1xDVI 1xVGA)

And here is an example of the error message I get when I try to check the CD for defects or install. This is a CD that I have checked the M5D hash's on and they looked ok.
---------------
ata3.0: revalidation failed (errno= -5)
ata3.0: revalidation failled (errno= -5)
ata3.0: (...)
ata3.01: exception Emask 0x0 Sact 0x0 SErr 0x0 action 0x2 frozen
ata3.01: cmd a0/00:00:00:24:00/00:00:00:00:00/b0 tag 0 pio 36 in
ata3.01: status: {DRDY}
(repeat last 3 lines idefinately)

The only thing I can come up with are some cryptic messages about SATA not working well with Ubuntu when I check out google. Thoughts?
-Kathe

---

### Post by Pumalite on 2008-08-04
What is the error message when you check CD integrity?
And if you can get to the install icon; then you are at the Desktop unless you are using the Alternate CD.
So; what is the error message when you try to install?
Are you using the Live CD cor the Alternate CD?

---

### Post by birdkathe on 2008-08-04
I get to the screen that gives the following options:
Try Ubuntu without any change to your computer
Install Ubuntu
Check CD for defects
Test memory
Boot from first hard disk

When I try either to "Install Ubuntu" or "Check CD for defects" I get the same error message in the BusyBox interface:
(initramfs) [   190.992806] ata3.0: revalidation failed (errno= -5)
(...] ata3.00: revalidation failed (errno= -5)
(...] ata3.01: failed to set xfermode (error_mask= 0x40)
(...] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
(...] ata3.01: cmd a0/00:00:00:24:00/00:00:00:00:00/b0 tag 0 pio 36 in
(...] ata3.01: status: {DRDY}
(...] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
(...] ata3.01: cmd a0/00:00:00:24:00/00:00:00:00:00/b0 tag 0 pio 36 in
(...] ata3.01: status: {DRDY}
(...] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
(...] ata3.01: cmd a0/00:00:00:24:00/00:00:00:00:00/b0 tag 0 pio 36 in
(...] ata3.01: status: {DRDY}
...

---

### Post by birdkathe on 2008-08-04
Just occured to me that I didn't answer all your questions:

> **Pumalite said:**
> What is the error message when you check CD integrity?
And if you can get to the install icon; then you are at the Desktop unless you are using the Alternate CD.
So; what is the error message when you try to install?
Are you using the Live CD cor the Alternate CD?

I do not get an error message when I check the m5d of the disk but it is an old blank CD so it's possible it was heat damaged.

I'm installing from a Live CD.

Thanks!
-Kathe

---

### Post by Pumalite on 2008-08-04
Burn a new CD in good quality CD-R. Burn at 4x or less. If you still have problems; report back
Clean the lens in your burner; just in case.

---

### Post by birdkathe on 2008-08-05
Same problem. I burned a new CD on a different computer at 4x. It seems to take a little longer to get to the error dump in BusyBox but that's the only difference I've noticed. I'm going to try to install from a flash drive and will report how that goes.

-Kathe

---

### Post by Pumalite on 2008-08-05
Try some boot parameters:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) 
Try the most common ones first:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off all_generic_ide vga=0x317 vga=771 vga=788 vga=789 vga=791
One by one or in different combinations.

---

### Post by birdkathe on 2008-08-05
In case I am being truly dense, here is the iso I'm trying to install from: ubuntu-8.04.1-desktop-amd64.iso

---

### Post by Pumalite on 2008-08-05
What is your specific question?

---

### Post by birdkathe on 2008-08-05
> **Pumalite said:**
> What is your specific question?

I hadn't seen your previous reply and wanted to post which version I was trying to install in case I had made a very basic mistake. I am researching the boot modifications you suggested right

Right now I'm trying the following:
Select "Check Cd for defects"
Press F6 to get "Boot Options"
Edit boot options to read: boot=casper integrity-check initrd=/casper/initrdgz [insert noapic/nolapic/etc] quiet splash --

Also do you have any suggestions on how to get BusyBox to just try to reboot as opposed to cutting the power?

Thanks for all your help.
-Kathe

---

### Post by Pumalite on 2008-08-05
With the appropriate boot parameters to boot your Live CD you shouldn't get to a Busy Box

---

### Post by birdkathe on 2008-08-05
> **Pumalite said:**
> Try some boot parameters:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) 
Try the most common ones first:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off all_generic_ide vga=0x317 vga=771 vga=788 vga=789 vga=791
One by one or in different combinations.

The key parameter seems to be "acpi=off" Check CD and Install ran fine with this added to the boot options. However when it restarted after the install it obviously did not change the acpi setting and we went back to the original error.

What exactly does acip do? (seems to have to do with power management and turning on/off fans from what google tells me) And how can I change the boot parameters?

Thanks!
-Kathe

---

### Post by Pumalite on 2008-08-05
[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)
You have to edit menu.lst and add it to the boot line permanently

---

### Post by birdkathe on 2008-08-05
Will setting apci=off adversely affect system performance?

---

### Post by Pumalite on 2008-08-05
Read the link I provided for you

---

### Post by birdkathe on 2008-08-05
Thank you very much for all your help!

-Kathe

---

### Post by Pumalite on 2008-08-05
You are welcome. Good luck!

---

