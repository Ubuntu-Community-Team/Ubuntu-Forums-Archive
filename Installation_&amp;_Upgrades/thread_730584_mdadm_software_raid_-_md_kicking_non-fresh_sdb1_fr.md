---
title: "mdadm: software raid - md: kicking non-fresh sdb1 from array?"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by thinking on 2008-03-21
hi@ll

i try to create a software raid for my 2 external usb hard drives

after adding both to /dev/md0, /proc/mdstat shows that it begins to sync
thats ok
12 hours later it finished
now i tried to mount /dev/md0, works too
did a reboot to show what happens, raid seems working
one day later (today) i booted the box again and dmesg showed the message
md: kicking non-fresh sdb1 from array!

i did nothing to the array than mounting it and rebooting 2 times
the question is: why did md kick sdb? what can cause it? since the disks are both only a week old i don't think its a hardware problem. are there any other possibilities?
to ask in a different way: how does md make sure that both disks are in sync during boot? checksum for 500GB? :lolflag:
OR do i have to disable the array somehow before rebooting?

thx@ll

> 
[   65.621967] sd 1:0:0:0: [sda] Spinning up disk...<6>ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   75.959677] .ready
[   75.963872] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   75.965470] sd 1:0:0:0: [sda] Write Protect is off
[   75.965476] sd 1:0:0:0: [sda] Mode Sense: 1c 00 00 00
[   75.965481] sd 1:0:0:0: [sda] Assuming drive cache: write through
[   75.967592] sd 1:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   75.969213] sd 1:0:0:0: [sda] Write Protect is off
[   75.969219] sd 1:0:0:0: [sda] Mode Sense: 1c 00 00 00
[   75.969222] sd 1:0:0:0: [sda] Assuming drive cache: write through
[   75.969287]  sda: sda1
[   76.002051] sd 1:0:0:0: [sda] Attached SCSI disk
[   76.008533] sd 0:0:0:0: [sdb] Spinning up disk....ready
[   86.481352] sd 0:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   86.482842] sd 0:0:0:0: [sdb] Write Protect is off
[   86.482848] sd 0:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[   86.482853] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[   86.484965] sd 0:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   86.486585] sd 0:0:0:0: [sdb] Write Protect is off
[   86.486590] sd 0:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[   86.486594] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[   86.486654]  sdb: sdb1
[   86.511939] sd 0:0:0:0: [sdb] Attached SCSI disk
[   86.547279] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   86.547326] sd 0:0:0:0: Attached scsi generic sg1 type 0
[   87.276763] md: bind<sdb1>
[   87.277529] md: bind<sda1>
[   87.277574] md: kicking non-fresh sdb1 from array!
[   87.277582] md: unbind<sdb1>
[   87.277590] md: export_rdev(sdb1)
[   87.375524] raid1: raid set md0 active with 1 out of 2 mirrors


---

