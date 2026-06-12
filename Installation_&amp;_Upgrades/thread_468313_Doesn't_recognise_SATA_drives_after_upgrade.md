---
title: "Doesn't recognise SATA drives after upgrade"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by pt123 on 2007-06-08
After upgrading from Edgy to Feisty on boot it  hangs up for a few minutes when detecting my non OS SATA drive and SATA DVD burner.

Looking at the dmesg output is seems to mistake the sata drive as an ide drive by refering to it as hde? shouldn't it be sda?

Here are the key lines from dmesg output:(full dmesg file attached)

```

[    7.654581] hde: max request size: 512KiB
[    8.507260] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000fea00003960e0]
[   37.597055] hde: lost interrupt
[   37.597079] hde: 781422768 sectors (400088 MB) w/16384KiB Cache, CHS=48641/255/63, UDMA(100)
[   67.537375] hde: lost interrupt
[   67.537398] hde: cache flushes supported
[   67.537442]  hde:<4>hde: dma_timer_expiry: dma status == 0x24
[   97.477697] hde: DMA interrupt recovery
[   97.477701] hde: lost interrupt
[   97.477734]  hde1 hde2 hde3 <<4>hde: dma_timer_expiry: dma status == 0x24
[  127.418018] hde: DMA interrupt recovery
[  127.418023] hde: lost interrupt
[  127.418046]  hde5<4>hde: dma_timer_expiry: dma status == 0x24
[  157.358339] hde: DMA interrupt recovery
[  157.358343] hde: lost interrupt

```
This mess goes keeps repeating till 512 (clock ticks, not sure of the time frame used in dmesg)

It is also calling the SATA burner as hdg

Here are the key lines from dmesg output:
```

[  254.165376] ide-cd: cmd 0x5a timed out
[  254.165383] hdg: lost interrupt
[  277.119628] hde: lost interrupt
[  307.063942] hde: lost interrupt
[  314.046019] ide-cd: cmd 0x5a timed out
[  314.046026] hdg: lost interrupt
[  314.046031] hdg: packet command error: status=0x51 { DriveReady SeekComplete Error }
[  314.046036] hdg: packet command error: error=0x50 { LastFailedSense=0x05 }
[  314.046040] ide: failed opcode was: unknown

```

When I physically remove these two drives it boots up fine, without any halts.

Before you say this mobo (Motherboard - Gigabyte Pentium 4 Titan Series GA-8IPE775 Series) is not supported by the Kernel, I had no problems do doing a fresh installation of Kubuntu 7.04. 
It recognised all the drives but named them sda,sdb & sdd.


Back to the upgrade - while upgrading it asked me do I want to replace the hdparm.conf file I said yes.

This was the changes it showed:
```

--
--- /etc/hdparm.conf 2006-11-04 18:10:24.000000000 +1100
+++ /etc/hdparm.conf.dpkg-new 2007-03-05 15:45:58.000000000 +1100
@@ -57,6 +57,8 @@
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
+# -s Turn on/off power on in standby mode
+#poweron_standby = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
@@ -124,28 +126,12 @@
# io32_support = 0
#}

-/dev/cdroms/cdrom0 {
- dma = on
-# interrupt_unmask = on
-# io32_support = 0
-}
-
-/dev/cdrom {
- dma = on
-}
-
#/dev/hda {
# mult_sect_io = 16
# write_cache = off
# dma = on
#}

-/dev/hdb {
-# mult_sect_io = 16
-# write_cache = off
- dma = on
-}
-
#command_line {
# hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

```


[b]
I am wondering is there anyway I can get Feisty to correctly identify my sata hard disk and burner. Is there .conf file which for some strange reason is picking it up as an IDE drive. Or do I have to use the naming convention of SDx for all the drives in Feisty and how would I go about this? 
[/b]

---

### Post by pt123 on 2007-06-08
[COLOR="DarkRed"][SIZE="4"]**Just an hour ago an Update to the Kernel arrived 2.6.20.16.29 that has fixed my problems with the SATA drives now all the drives are read as SDX. **[/SIZE][/COLOR]

I am so happy now, back in love with Ubuntu:D

---

