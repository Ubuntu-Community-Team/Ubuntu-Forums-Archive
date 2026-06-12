---
title: "Fiesty first boot error (failed to set xfermode)"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by lrose on 2007-04-21
After installing fiesty from a clean system the normal boot mode would hang forever. Booting in the recovery boot mode I found that the ATA system was giving me the following errors:

from /var/log/dmesg.0

```

...
[   30.354125] SCSI subsystem initialized
[   30.369485] libata version 2.20 loaded.
[   30.378007] ata_piix 0000:00:1f.1: version 2.10ac1
[   30.378057] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   30.378151] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   30.378268] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   30.378362] scsi0 : ata_piix
[   30.402227] usbcore: registered new interface driver usbfs
[   30.402330] usbcore: registered new interface driver hub
[   30.402423] usbcore: registered new device driver usb
[   30.405170] USB Universal Host Controller Interface driver v3.0
[   30.501267] Linux Tulip driver version 1.1.14 (December 15, 2004)
[   30.541781] ata1.00: ata_hpa_resize 1: sectors = 39851760, hpa_sectors = 39851760
[   30.541858] ata1.00: ATA-5: QUANTUM FIREBALLP AS20, A1Y.1500, max UDMA/100
[   30.541913] ata1.00: 39851760 sectors, multi 16: LBA
[   30.549801] ata1.00: ata_hpa_resize 1: sectors = 39851760, hpa_sectors = 39851760
[   30.549881] ata1.00: configured for UDMA/100
[   30.552270] scsi1 : ata_piix
[   30.670605] Floppy drive(s): fd0 is 1.44M
[   30.695472] FDC 0 is a post-1991 82077
[    4.580000] Time: acpi_pm clocksource has been installed.
[    5.064000] ata2.00: ATAPI, max MWDMA2
[    5.064000] ata2.01: ATAPI, max UDMA/33
[    5.228000] ata2.00: configured for MWDMA2
[   35.228000] ata2.01: qc timeout (cmd 0xef)
[   35.228000] ata2.01: failed to set xfermode (err_mask=0x4)
[   35.228000 ] ata2: failed to recover some devices, retrying in 5 secs
[   41.104000] ata2.00: configured for MWDMA2
[   71.104000] ata2.01: qc timeout (cmd 0xef)
[   71.104000] ata2.01: failed to set xfermode (err_mask=0x4)
[   71.104000] ata2.01: limiting speed to UDMA/33:PIO3
[   71.104000] ata2: failed to recover some devices, retrying in 5 secs
[   76.972000] ata2.00: configured for MWDMA2
[  106.972000] ata2.01: qc timeout (cmd 0xef)
[  106.972000] ata2.01: failed to set xfermode (err_mask=0x4)
[  106.972000] ata2.01: disabled
[  106.972000] ata2: failed to recover some devices, retrying in 5 secs
[  111.976000] ata2.00: failed to set xfermode (err_mask=0x40)
[  111.976000] ata2: failed to recover some devices, retrying in 5 secs
[  117.680000] ata2.00: configured for MWDMA2
[  117.680000] scsi 0:0:0:0: Direct-Access     ATA      QUANTUM FIREBALL A1Y. PQ: 0 ANSI: 5
[  117.680000] scsi 1:0:0:0: CD-ROM            SAMSUNG  DVD-ROM SD-612   0.4  PQ: 0 ANSI: 5
[  117.684000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 12
[  117.684000] PCI: setting IRQ 12 as level-triggered
[  117.684000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[  117.684000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
...

```

Like the error message implies, it is failing to set the transfer mode.  When you boot into Gnome it sees both optical drives but can only mount the DVD-ROM drive.  This issue is also present in the Fiesty Beta but not in previous releases.  Any help in resolving this so I don't have to boot the system in recovery mode all of the time would be appreciated.  I'm sure it is a bug but since searching launchpad for the this a bug was painful I started here. Note that the Memorex CD-RW is not listed, however this drive was used to boot using the LiveCD so this problem only exists after installation.

Here are the system details:
P3-1300
Intel 815i NorthBridge, ICH2 Southbridge
Quantum Fireball HD PATA
Samsung DVD-ROM PATA
Memorex CD- RW PATA
Geforce 3

---

### Post by vendejp on 2007-04-21
im experiencing the same problem after an upgrade to fiesty.  The splash screen hangs for a while and if i hit ctrl-alt-F1 to the shell screen it hangs 3 times saying "failed to set xfermode".

after that bootup is fine and all seems ok.  it just takes 2 min or so to startup.  Ill keep an eye on this.

---

### Post by lrose on 2007-04-22
I have found that removing the Memorex drive allows for a normal boot.  If I leave it in and wait for the boot to complete after all of the errors it is not able to mount it.  It is odd that the live cd has no issues but the installed version does.  I would think they would use the code/libraries.

---

### Post by kernelsandirs on 2007-04-22
I had the exact issue described.

 I found a post on the launchpad that said can't boot properly without adding irqpoll to the boot options, tried that and it fixed my issue right away

so in /boot/grub/menu.lst I added irqpoll to the kernel line

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash **irqpoll** 

now my lite on cdrw shows up and works properly.  I am not sure what performance hit this causes if any but it certainly fixed the issue.

---

### Post by honeydew on 2007-05-09
> **kernelsandirs said:**
> I had the exact issue described.

 I found a post on the launchpad that said can't boot properly without adding irqpoll to the boot options, tried that and it fixed my issue right away

so in /boot/grub/menu.lst I added irqpoll to the kernel line

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash **irqpoll** 

now my lite on cdrw shows up and works properly.  I am not sure what performance hit this causes if any but it certainly fixed the issue.

------- 

I was having the same issues and this seems to have fixed the problem.. do you know how could I test  a performance hit?

---

### Post by dom085 on 2007-05-12
I'm experiencing this "failed to set xfermode" problem as well, and I'm completely new to Linux... Would you please explain how I would follow those directions you gave? Or point me to a source that would?

---

### Post by honeydew on 2007-05-12
boot up the live cd.. when your at the boot screen the one that asks you if you want to install check the cd or boot from the first hard disk.. hit F6 then.. at the end of the line that pops up type 

irqpoll 

then hit enter.  from there you should boot up into the live cd.. 
best of luck.

---

### Post by JLarson on 2007-07-20
I have also experienced this problem under Ubuntu Feisty. Here is the solution I found for my setup.

In the BIOS under "IDE Configuration" set "Enhanced Mode Support On" to "P-ATA+S-ATA". When it is set to "S-ATA" (default) the computer will take nearly five minutes to boot, and the cdrom will not be detected properly. After combing google and these forums for hours and testing every possible setting in the BIOS, I stumbled across this one. The attachments posted are the output of lspci -vv and the relevant info from dmesg after changing this one setting. My motherboard is a Asus P4C800 flashed with a P4P800 BIOS to support CT-479 Pentium-M adapter.

On a side note, the lilo and kernel boot options tricks didn't work for my setup. I ended up with the exact same error and sluggish boot. 

Hope this helps...

Jason

---

### Post by aetherh4cker on 2007-07-20
> **kernelsandirs said:**
> I had the exact issue described.

 I found a post on the launchpad that said can't boot properly without adding irqpoll to the boot options, tried that and it fixed my issue right away

so in /boot/grub/menu.lst I added irqpoll to the kernel line

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=48c5a348-eb39-4171-8531-671a49fdb75b ro quiet splash **irqpoll** 

now my lite on cdrw shows up and works properly.  I am not sure what performance hit this causes if any but it certainly fixed the issue.

This seemingly worked for me too... but I worry about something I have no idea what it does.  Anyone know what this does?

---

### Post by tntwo on 2007-07-21
Hello!guys
     I found that  "irqpoll" makes my computer freezing after boot up more easily,especially when firefox is launched.Any idea to solve this problem?

---

### Post by siriusfox on 2007-08-04
I'm having the same problem as the original poster. I started with a default Compaq CD drive, then I upgraded to a TDK CD-RW (5200B), and suddenly I get all of these errors. I've had a few workarounds go ok, but I'd rather not have to configure this crazy thing every time I upgrade the Kernel.

What I am noticing, is almost everyone who specifies a ata device, talks about a CD-RW drive. I don't know if that could have something to do with it, but it is worth looking into.

---

