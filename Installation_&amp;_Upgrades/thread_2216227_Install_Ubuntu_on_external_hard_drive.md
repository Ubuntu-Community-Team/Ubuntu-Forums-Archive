---
title: "Install Ubuntu on external hard drive"
date: 2014-04-10
forum: Installation &amp; Upgrades
---

### Post by mollyman2 on 2014-04-10
Hi, 
First, sorry for my average English level, I'm French. Don't hesitate to ask me for more informations if I'm not clear. ;)

So, I have an Asus laptop with Windows 7 Familial 64bits.
For 1 year I had an so efficient dualboot between Ubuntu 13.04 and Win7(C: ) on internal drive(500Go) with a perfectly set exchanged data partition(D: ).
All was beautiful in a wonderful world but I would like to compile Android and that needs a lot of drive space that I don't have on my internal drive.
I have a 320Go external hard drive.

At begining, i made a dualboot with Win7 on internal drive and Ubuntu on external drive, it seemed to works ok but in fact, i had a grub error when I tried to switch on my laptop without external drive connected. I need to be able to use Win7 without external drive when I'm not home.
Next option is to set up BIOS to boot on external drive before the internal one by adding an boot option. But I don't have the "Add boot option" menu. It just appeared once; when I plugged another usb drive. So I had give up this option...
When I boot my laptop and I press "Escape key" I have the list of drives avaibles. I tried to launch live-cd and install Ubuntu and Grub on external drive and then boot on it. Here if I try to boot on my external drive by "Escape" menu, I got a black screen and that's all. Next I've rebooted on live-cd an set "boot" with Gparted on my external drive partition (maybe not clear sorry). It seems to works, I have Grub but when I choose Ubuntu, I have a black screen again.
Next try I've carried out is to install Ubuntu on external drive with disconnected internal drive, no progress, black screen as in previous try...
On Win7 I tried to "activate" my external drive with Diskpart but I gave up this solution because I don't understand the tutorials.

Today I'm really lost... #-o
I need your help to install Ubuntu on my external usb drive.
My wish list : I don't want to have an exchange partition. Only Win7 on internal drive and Ubuntu on my external usb drive. And I would like  to use Win7 on my laptop without external drive connected.



If you know what I have to do or just an idea, please tell me. :)
Thanks in advance !

---

### Post by pfeiffep on 2014-04-10
> So, I have an Asus laptop with Windows 7 Familial 64bits.
For 1 year I had an so efficient dualboot between Ubuntu 13.04 and  Win7(C: ) on internal drive(500Go) with a perfectly set exchanged data  partition(D: ).
All was beautiful in a wonderful world but I would like to compile  Android and that needs a lot of drive space that I don't have on my  internal drive.
I have a 320Go external hard drive.  At begining, i made a dualboot with Win7 on internal drive and Ubuntu on  external drive, it seemed to works ok but in fact, i had a grub error  when I tried to switch on my laptop without external drive connected. I  need to be able to use Win7 without external drive when I'm not home.

What happened to you Ubuntu 13.04 partitiion??   If you can still boot to the original Ubuntu  try ```
sudo update-grub
```

I have been successful booting 2 versions of Ubuntu - 1 on internal drive and the other on external drive. Once I had grub setup on internal I was able to select either Ubuntu, and if the usb drive wasn't connected laptop booted just fine to internal.

Couldn't you use the external drive as data for compiling while booting to internal Ubuntu?
Possible help[ here]("https://help.ubuntu.com/community/Boot-Repair")

Good luck

---

### Post by von Corax on 2014-04-10
I'm doing something similar, that is, I have Precise installed on a 1TB Seagate Expansion portable USB drive. When I started out with this, I was using a borrowed laptop which I didn't want to muck up, so I installed GrUB on the *external* drive. Now, when I pull up the BIOS startup drive menu, I select the Seagate and then I see the GrUB boot menu. If the Seagate isn't connected the host machine uses the normal Windows bootloader.

In other words, what you need to do is this:

1) reinstall the Windows bootloader on your internal HDD (apparently enough people have had this problem that there's a HOWTO around here somewhere, then
2) boot from your Live CD, reinstall Ubuntu (this step may not be necessary,) then when the installer asks you where to install GrUB, tell it to install on the *external* drive alongside Ubuntu.

I have used my external to run Ubuntu on *several different* Windows machines with no need to make any changes to the host machine.

Hope that helps.

---

### Post by oldfred on 2014-04-10
You want Windows boot loader on internal drive and grub2's boot loader on external drive.
Then set BIOS to boot external first and Windows internal drive 2nd. If external not connected it should just boot Windows.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

    
If you tick that second drive is external, Boot-Repair should configure it correctly, but post link if not.

---

### Post by mollyman2 on 2014-04-11
Thanks all for your answers ! ;)

@pfeiffep
I deleted my internal Ubutnu partition. I have only Win7 in internal drive now.
Yes, I already tried (many times) "sudo update-grub" and boot repair also but that don't solve my problem.
No I can't just put ubuntu data on the external drive, to compile Android, I need lot of space for Ubuntu system. It's not just some data, I have to install lot of softs. So I wish to put "all" Ubuntu in the external drive. :)

@pfeiffep & von Corax
I tried that. It works but not when I start up my laptop without the external drive. If I do that I obtain this error :
```
error: no such device: eeaebd51-d44f-426e-9127-509e0001edf9.
grub rescue> _
```
That is weird because in theory I don't intall Grub on the internal drive so no reason to have an error with Grub.
Sure I have search a long time on Google with this error text but I don't find the solution. If we find the solution to avoid this error my problem will be solved.

@pfeiffep & von Corax & oldfred

I can't set up my BIOS to boot on external drive before the internal one. The only solution is to use "Escape" key which shows a menu with the list of drives connected. But I don't know if this menu has the same function as BIOS boot order.
For me it's not boring to have to use "Escape" key to boot on external drive.

I'll make some new try to have the BootInfo report. Boot repair don't seems to works. It's strange because it ask me if my 320Go external drive is an removable drive so in theory it's good, in theory only...:mad:

Concerning UEFI I searched some informations about it but I don't understand nothing ! I just know that UEFI can replace BIOS but I don't understand nothing about how install it, start it and use it. :(

---

### Post by oldfred on 2014-04-11
Is this a new system?
If so then one system could be UEFI and the other BIOS. Then you only could boot from UEFI/BIOS or one time boot key as UEFI & BIOS are not really compatible and once you start booting in one mode you cannot change. Or you cannot use grub to dual boot.

BootInfo report will show us details.

---

### Post by mollyman2 on 2014-04-11
Okay,

There is 2 boot info links.
[http://paste.ubuntu.com/7236134/](http://paste.ubuntu.com/7236134/)
[http://paste.ubuntu.com/7236162/](http://paste.ubuntu.com/7236162/) Here, Windows boot good. If I choose external drive, Grub appear but if I launch Ubuntu, nothing happens. Just a purple screen.

I carried out 3 complete installations and 5 boot repair with recommended repair and some custom repair... always nothing.

---

### Post by oldfred on 2014-04-11
It looks like you have a Windows boot loader in sda & Ubuntu in sdb as that is what Boot-Repair did.

Part of issue is 13.04. You will not get any updates to fix things.
       EOL Notice: Raring (13.04) will be End of Life on January 27, 2014
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

If you just get blank screen after grub menu, then that is often a video issue. But it does look like you have installed the radeon driver.

---

### Post by mollyman2 on 2014-04-11
Yes Windows on sda and I want to install Ubuntu on sdb.
I don't think it's a video issue. In some case Ubuntu start up. But when Ubuntu start it's when I can't start up Windows without external drive.
I can't install Ubuntu 13.10 because it's not fully operational to compile Android. Only 13.04 or 12.04 should works. But in my opinion it's not a video problem due to the radeon driver.
Do you know what I have to do now ?
Installation of Grub in internal or internal drive don't solve my problem.

---

### Post by oldfred on 2014-04-11
With Windows boot loader in sda, you should not need external drive to boot Windows directly.

Grub menu will only appear with sdb boot. And it should then show both Ubuntu & Windows.

Your sda1 has an unusual start sector. Old XP use sector 63, and new systems use sector 2048. Yours is at sector 64, but not sure if that makes any difference? chkdsk from Windows may be required.

But you cannot update 13.04, so I do not think it would be a good choice. Perhaps 12.04.4?
If it boots sometimes that is a different issue and very difficult to debug.
Do logs show any errors after boot issue?
You may have log file viewer or look in dmesg.
 gksudo gedit /var/log/dmesg

---

### Post by mollyman2 on 2014-04-12
> With Windows boot loader in sda, you should not need external drive to boot Windows directly.
Grub menu will only appear with sdb boot. And it should then show both Ubuntu & Windows.
Yes I'm agree and it's what I have try lot of times.

Concerning boot sector, I have try to restore bootloader yesterday with Windows retore tools (by using F8 at the start of the laptop) but boot sector still present in 64 boot sector. I don't know how to change that. My laptop always have Win7 since purchase.
I don't know what kind of information I sould find with chkdsk.

Concerning Ubuntu 12.04.4 LTS yes I will install it instead of 13.04 it's a better choise. Lots of Android developpers use Ubuntu 12.04.
I tried to install Ubuntu 12.04 but not Grub at all.
I tried to install Ubuntu and Grub on sdb/Ubuntu on sdb and Grub on sda/Ubuntu on sdb and Grub on sda and sdb/Ubuntu and Grub on sdb with sda disconnected.
Ubuntu never start up ! ](*,) Grub never appear even when I've install Grub on sda.
Sure for all tries I tried some boot reparation but no result. Not even a purple screen. I don't know why Grub don't appear...

Concerning gksudo gedit /var/log/dmesg, there is no log on sdb. In live-cd I have just find this log :

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-15-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 (Ubuntu 3.11.0-15.25~precise1-generic 3.11.10)
[    0.000000] Command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009bbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009bc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000becf0fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000becf1000-0x00000000bed35fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bed36000-0x00000000bed46fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bed47000-0x00000000bed58fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bed59000-0x00000000bed61fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bed62000-0x00000000bed69fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bed6a000-0x00000000bed82fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bed83000-0x00000000bed83fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bed84000-0x00000000bed99fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bed9a000-0x00000000bed9cfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bed9d000-0x00000000bed9efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bed9f000-0x00000000bed9ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000beda0000-0x00000000beda3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000beda4000-0x00000000beda6fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000beda7000-0x00000000bedabfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bedac000-0x00000000bedb9fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bedba000-0x00000000bedcffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bedd0000-0x00000000bedd1fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bedd2000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffbfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001fbffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000001fc000000-0x00000001ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000200000000-0x000000023bffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: ASUSTeK Computer Inc. K52JT/K52JT, BIOS K52JT.206 01/25/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x23c000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 100000000 mask F00000000 write-back
[    0.000000]   3 base 200000000 mask FC0000000 write-back
[    0.000000]   4 base 23C000000 mask FFC000000 uncachable
[    0.000000]   5 base 1FC000000 mask FFC000000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 4GB, type WB
[    0.000000] reg 3, base: 8GB, range: 1GB, type WB
[    0.000000] reg 4, base: 9152MB, range: 64MB, type UC
[    0.000000] reg 5, base: 8128MB, range: 64MB, type UC
[    0.000000] total RAM covered: 8064M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 6      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 4GB, range: 4GB, type WB
[    0.000000] reg 3, base: 8128MB, range: 64MB, type UC
[    0.000000] reg 4, base: 8GB, range: 1GB, type WB
[    0.000000] reg 5, base: 9152MB, range: 64MB, type UC
[    0.000000] e820: update [mem 0xc0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: update [mem 0x1fc000000-0x1ffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbecf1 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcad0-0x000fcadf] mapped at [ffff8800000fcad0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000095000] 95000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd9000, 0x01fd9fff] PGTABLE
[    0.000000] BRK [0x01fda000, 0x01fdafff] PGTABLE
[    0.000000] BRK [0x01fdb000, 0x01fdbfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23be00000-0x23bffffff]
[    0.000000]  [mem 0x23be00000-0x23bffffff] page 2M
[    0.000000] BRK [0x01fdc000, 0x01fdcfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x238000000-0x23bdfffff]
[    0.000000]  [mem 0x238000000-0x23bdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x237ffffff]
[    0.000000]  [mem 0x200000000-0x237ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbecf0fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbebfffff] page 2M
[    0.000000]  [mem 0xbec00000-0xbecf0fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1fbffffff]
[    0.000000]  [mem 0x100000000-0x1fbffffff] page 2M
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] RAMDISK: [mem 0x7ee4c000-0x7fffffff]
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 00000000beda5e18 00064 (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000bed83c18 000F4 (v04 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20130517/tbfadt-395)
[    0.000000] ACPI BIOS Warning (bug): 32/64X FACS address mismatch in FADT - 0xBEDB7F40/0x00000000BEDD1D40, using 32 (20130517/tbfadt-522)
[    0.000000] ACPI: DSDT 00000000bed47018 117B9 (v01 _ASUS_ Notebook 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bedb7f40 00040
[    0.000000] ACPI: APIC 00000000beda4f18 0008C (v02 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: DBGP 00000000beda6f18 00034 (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
[    0.000000] ACPI: ECDT 00000000bedd1a18 000C1 (v01 _ASUS_ Notebook 06222004 AMI. 00000003)
[    0.000000] ACPI: SLIC 00000000bedb2c18 00176 (v01 _ASUS_ Notebook 06222004 ASUS 00000001)
[    0.000000] ACPI: MCFG 00000000bedd0d18 0003C (v01 _ASUS_ Notebook 06222004 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bedd0c98 00038 (v01 _ASUS_ Notebook 06222004 AMI. 00000003)
[    0.000000] ACPI: SSDT 00000000bed9f018 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023bffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x23bffffff]
[    0.000000]   NODE_DATA [mem 0x23bff6000-0x23bffafff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880233600000-ffff88023b5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23bffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009afff]
[    0.000000]   node   0: [mem 0x00100000-0xbecf0fff]
[    0.000000]   node   0: [mem 0x100000000-0x1fbffffff]
[    0.000000]   node   0: [mem 0x200000000-0x23bffffff]
[    0.000000] On node 0 totalpages: 2059403
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3994 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12148 pages used for memmap
[    0.000000]   DMA32 zone: 777457 pages, LIFO batch:31
[    0.000000]   Normal zone: 20224 pages used for memmap
[    0.000000]   Normal zone: 1277952 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009b000-0x0009bfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbecf1000-0xbed35fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbed36000-0xbed46fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbed47000-0xbed58fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbed59000-0xbed61fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbed62000-0xbed69fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbed6a000-0xbed82fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbed83000-0xbed83fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbed84000-0xbed99fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbed9a000-0xbed9cfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbed9d000-0xbed9efff]
[    0.000000] PM: Registered nosave memory: [mem 0xbed9f000-0xbed9ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbeda0000-0xbeda3fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbeda4000-0xbeda6fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbeda7000-0xbedabfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbedac000-0xbedb9fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbedba000-0xbedcffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbedd0000-0xbedd1fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbedd2000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffbfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffdfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x1fc000000-0x1ffffffff]
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88023bc00000 s86720 r8192 d23872 u262144
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2026946
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8004804K/8237612K available (7507K kernel code, 1079K rwdata, 4076K rodata, 1392K init, 1428K bss, 232808K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2659.896 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5319.79 BogoMIPS (lpj=10639584)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000027] Security Framework initialized
[    0.000045] AppArmor: AppArmor initialized
[    0.000047] Yama: becoming mindful.
[    0.000537] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002335] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003187] Mount-cache hash table entries: 256
[    0.003379] Initializing cgroup subsys memory
[    0.003389] Initializing cgroup subsys devices
[    0.003391] Initializing cgroup subsys freezer
[    0.003393] Initializing cgroup subsys blkio
[    0.003394] Initializing cgroup subsys perf_event
[    0.003397] Initializing cgroup subsys hugetlb
[    0.003416] CPU: Physical Processor ID: 0
[    0.003418] CPU: Processor Core ID: 0
[    0.003423] mce: CPU supports 9 MCE banks
[    0.003433] CPU0: Thermal monitoring enabled (TM1)
[    0.003443] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.003443] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.003443] tlb_flushall_shift: 6
[    0.003541] Freeing SMP alternatives memory: 28K (ffffffff81e6b000 - ffffffff81e72000)
[    0.005550] ACPI: Core revision 20130517
[    0.012850] ACPI: All ACPI Tables successfully acquired
[    0.038173] ftrace: allocating 31294 entries in 123 pages
[    0.053258] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.092947] smpboot: CPU0: Intel(R) Core(TM) i5 CPU       M 480  @ 2.67GHz (fam: 06, model: 25, stepping: 05)
[    0.198946] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.198952] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.198955] ... version:                3
[    0.198956] ... bit width:              48
[    0.198957] ... generic registers:      4
[    0.198958] ... value mask:             0000ffffffffffff
[    0.198959] ... max period:             000000007fffffff
[    0.198960] ... fixed-purpose events:   3
[    0.198960] ... event mask:             000000070000000f
[    0.213750] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.200488] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.240098] Brought up 4 CPUs
[    0.240103] smpboot: Total of 4 processors activated (21279.16 BogoMIPS)
[    0.242884] devtmpfs: initialized
[    0.244066] EVM: security.selinux
[    0.244068] EVM: security.SMACK64
[    0.244069] EVM: security.capability
[    0.244123] PM: Registering ACPI NVS region [mem 0xbecf1000-0xbed35fff] (282624 bytes)
[    0.244128] PM: Registering ACPI NVS region [mem 0xbed47000-0xbed58fff] (73728 bytes)
[    0.244130] PM: Registering ACPI NVS region [mem 0xbed62000-0xbed69fff] (32768 bytes)
[    0.244131] PM: Registering ACPI NVS region [mem 0xbed83000-0xbed83fff] (4096 bytes)
[    0.244132] PM: Registering ACPI NVS region [mem 0xbed9a000-0xbed9cfff] (12288 bytes)
[    0.244135] PM: Registering ACPI NVS region [mem 0xbed9f000-0xbed9ffff] (4096 bytes)
[    0.244136] PM: Registering ACPI NVS region [mem 0xbedac000-0xbedb9fff] (57344 bytes)
[    0.244137] PM: Registering ACPI NVS region [mem 0xbedd0000-0xbedd1fff] (8192 bytes)
[    0.245022] regulator-dummy: no parameters
[    0.245055] RTC time:  6:46:02, date: 04/12/14
[    0.245091] NET: Registered protocol family 16
[    0.245225] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.245227] ACPI: bus type PCI registered
[    0.245229] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.245295] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.245298] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.264512] PCI: Using configuration type 1 for base access
[    0.265375] bio: create slab <bio-0> at 0
[    0.265527] ACPI: Added _OSI(Module Device)
[    0.265529] ACPI: Added _OSI(Processor Device)
[    0.265531] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.265532] ACPI: Added _OSI(Processor Aggregator Device)
[    0.267584] ACPI: EC: EC description table is found, configuring boot EC
[    0.267589] ACPI: EC: Look up EC in DSDT
[    0.269747] ACPI: Executed 2 blocks of module-level executable AML code
[    0.281689] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.318719] ACPI: SSDT 00000000beda3a18 0047B (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.319232] ACPI: Dynamic OEM Table Load:
[    0.319235] ACPI: SSDT           (null) 0047B (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.319347] ACPI: SSDT 00000000beda1018 008A9 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.319841] ACPI: Dynamic OEM Table Load:
[    0.319843] ACPI: SSDT           (null) 008A9 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.329902] ACPI: SSDT 00000000beda2a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.330419] ACPI: Dynamic OEM Table Load:
[    0.330421] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.333791] ACPI: SSDT 00000000beda0d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.334281] ACPI: Dynamic OEM Table Load:
[    0.334283] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.338203] ACPI: Interpreter enabled
[    0.338210] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.338214] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.338227] ACPI: (supports S0 S3 S4 S5)
[    0.338229] ACPI: Using IOAPIC for interrupt routing
[    0.338256] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.338427] ACPI: No dock devices found.
[    0.355474] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.355584] acpi PNP0A08:00: Requesting ACPI _OSC control (0x1d)
[    0.355808] acpi PNP0A08:00: ACPI _OSC control (0x1d) granted
[    0.356341] PCI host bridge to bus 0000:00
[    0.356344] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.356346] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.356347] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.356349] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.356350] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.356352] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.356353] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.356355] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.356356] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfeafffff]
[    0.356365] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.356382] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.356455] pci 0000:00:01.0: [8086:0045] type 01 class 0x060400
[    0.356485] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.356588] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.356617] pci 0000:00:16.0: reg 0x10: [mem 0xd520a000-0xd520a00f 64bit]
[    0.356710] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.356808] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.356834] pci 0000:00:1a.0: reg 0x10: [mem 0xd5208000-0xd52083ff]
[    0.356940] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.357026] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.357065] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.357086] pci 0000:00:1b.0: reg 0x10: [mem 0xd5200000-0xd5203fff 64bit]
[    0.357181] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.357238] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.357270] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.357368] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.357428] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.357459] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.357557] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.357614] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.357646] pci 0000:00:1c.2: [8086:3b46] type 01 class 0x060400
[    0.357744] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.357801] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.357835] pci 0000:00:1c.5: [8086:3b4c] type 01 class 0x060400
[    0.357931] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.357989] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.358027] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.358052] pci 0000:00:1d.0: reg 0x10: [mem 0xd5207000-0xd52073ff]
[    0.358159] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.358242] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.358275] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.358388] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.358419] pci 0000:00:1f.0: [8086:3b09] type 00 class 0x060100
[    0.358599] pci 0000:00:1f.2: [8086:3b29] type 00 class 0x010601
[    0.358626] pci 0000:00:1f.2: reg 0x10: [io  0xe070-0xe077]
[    0.358636] pci 0000:00:1f.2: reg 0x14: [io  0xe060-0xe063]
[    0.358646] pci 0000:00:1f.2: reg 0x18: [io  0xe050-0xe057]
[    0.358657] pci 0000:00:1f.2: reg 0x1c: [io  0xe040-0xe043]
[    0.358667] pci 0000:00:1f.2: reg 0x20: [io  0xe020-0xe03f]
[    0.358678] pci 0000:00:1f.2: reg 0x24: [mem 0xd5206000-0xd52067ff]
[    0.358743] pci 0000:00:1f.2: PME# supported from D3hot
[    0.358821] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.358841] pci 0000:00:1f.3: reg 0x10: [mem 0xd5205000-0xd52050ff 64bit]
[    0.358870] pci 0000:00:1f.3: reg 0x20: [io  0xe000-0xe01f]
[    0.358975] pci 0000:00:1f.6: [8086:3b32] type 00 class 0x118000
[    0.359002] pci 0000:00:1f.6: reg 0x10: [mem 0xd5204000-0xd5204fff 64bit]
[    0.359194] pci 0000:01:00.0: [1002:68e4] type 00 class 0x030000
[    0.359207] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.359217] pci 0000:01:00.0: reg 0x18: [mem 0xd0020000-0xd003ffff 64bit]
[    0.359224] pci 0000:01:00.0: reg 0x20: [io  0xd000-0xd0ff]
[    0.359236] pci 0000:01:00.0: reg 0x30: [mem 0xd0000000-0xd001ffff pref]
[    0.359263] pci 0000:01:00.0: supports D1 D2
[    0.359300] pci 0000:01:00.1: [1002:aa68] type 00 class 0x040300
[    0.359313] pci 0000:01:00.1: reg 0x10: [mem 0xd0040000-0xd0043fff 64bit]
[    0.359363] pci 0000:01:00.1: supports D1 D2
[    0.359409] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.359412] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.359414] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd00fffff]
[    0.359481] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.359485] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.359490] pci 0000:00:1c.0:   bridge window [mem 0xd3e00000-0xd51fffff]
[    0.359586] pci 0000:03:00.0: [168c:002b] type 00 class 0x028000
[    0.359608] pci 0000:03:00.0: reg 0x10: [mem 0xd2a00000-0xd2a0ffff 64bit]
[    0.359710] pci 0000:03:00.0: supports D1
[    0.359712] pci 0000:03:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.359741] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.370930] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.370938] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.370946] pci 0000:00:1c.1:   bridge window [mem 0xd2a00000-0xd3dfffff]
[    0.371098] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.371103] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
[    0.371107] pci 0000:00:1c.2:   bridge window [mem 0xd1600000-0xd29fffff]
[    0.371231] pci 0000:05:00.0: [197b:2382] type 00 class 0x088000
[    0.371255] pci 0000:05:00.0: reg 0x10: [mem 0xd0207000-0xd02070ff]
[    0.371490] pci 0000:05:00.2: [197b:2381] type 00 class 0x080501
[    0.371514] pci 0000:05:00.2: reg 0x10: [mem 0xd0206000-0xd02060ff]
[    0.371745] pci 0000:05:00.3: [197b:2383] type 00 class 0x088000
[    0.371768] pci 0000:05:00.3: reg 0x10: [mem 0xd0205000-0xd02050ff]
[    0.371999] pci 0000:05:00.4: [197b:2384] type 00 class 0x088000
[    0.372022] pci 0000:05:00.4: reg 0x10: [mem 0xd0204000-0xd02040ff]
[    0.372250] pci 0000:05:00.5: [197b:0250] type 00 class 0x020000
[    0.372274] pci 0000:05:00.5: reg 0x10: [mem 0xd0200000-0xd0203fff]
[    0.372305] pci 0000:05:00.5: reg 0x18: [io  0x9100-0x917f]
[    0.372322] pci 0000:05:00.5: reg 0x1c: [io  0x9000-0x90ff]
[    0.372455] pci 0000:05:00.5: PME# supported from D0 D3hot D3cold
[    0.372495] pci 0000:05:00.5: System wakeup disabled by ACPI
[    0.382944] pci 0000:00:1c.5: PCI bridge to [bus 05]
[    0.382956] pci 0000:00:1c.5:   bridge window [io  0x9000-0x9fff]
[    0.382963] pci 0000:00:1c.5:   bridge window [mem 0xd0200000-0xd15fffff]
[    0.383081] pci 0000:00:1e.0: PCI bridge to [bus 06] (subtractive decode)
[    0.383093] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.383095] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.383096] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.383098] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.383099] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.383101] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.383102] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.383104] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)
[    0.383135] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.389815] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.389864] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.389911] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    0.389957] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.390006] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.390053] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.390100] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.390146] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.390186] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.390190] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.390191] acpi PNP0A03:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.390247] PCI host bridge to bus 0000:ff
[    0.390250] pci_bus 0000:ff: root bus resource [bus ff]
[    0.390254] pci 0000:ff:00.0: [8086:2c62] type 00 class 0x060000
[    0.390289] pci 0000:ff:00.1: [8086:2d01] type 00 class 0x060000
[    0.390325] pci 0000:ff:02.0: [8086:2d10] type 00 class 0x060000
[    0.390357] pci 0000:ff:02.1: [8086:2d11] type 00 class 0x060000
[    0.390389] pci 0000:ff:02.2: [8086:2d12] type 00 class 0x060000
[    0.390421] pci 0000:ff:02.3: [8086:2d13] type 00 class 0x060000
[    0.390708] ACPI: Enabled 3 GPEs in block 00 to 3F
[    0.390714] ACPI: \_SB_.PCI0: notify handler is installed
[    0.390765] ACPI: \_SB_.CPBG: notify handler is installed
[    0.390775] Found 2 acpi root devices
[    0.390831] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.390934] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.390936] vgaarb: loaded
[    0.390937] vgaarb: bridge control possible 0000:01:00.0
[    0.391092] SCSI subsystem initialized
[    0.391094] ACPI: bus type ATA registered
[    0.391160] libata version 3.00 loaded.
[    0.391188] ACPI: bus type USB registered
[    0.391203] usbcore: registered new interface driver usbfs
[    0.391211] usbcore: registered new interface driver hub
[    0.391238] usbcore: registered new device driver usb
[    0.391333] PCI: Using ACPI for IRQ routing
[    0.401045] PCI: pci_cache_line_size set to 64 bytes
[    0.401122] e820: reserve RAM buffer [mem 0x0009bc00-0x0009ffff]
[    0.401124] e820: reserve RAM buffer [mem 0xbecf1000-0xbfffffff]
[    0.401213] NetLabel: Initializing
[    0.401214] NetLabel:  domain hash size = 128
[    0.401215] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.401224] NetLabel:  unlabeled traffic allowed by default
[    0.401295] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.401300] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.403332] Switched to clocksource hpet
[    0.407747] AppArmor: AppArmor Filesystem Enabled
[    0.407783] pnp: PnP ACPI init
[    0.407798] ACPI: bus type PNP registered
[    0.407869] pnp 00:00: [dma 4]
[    0.407894] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.407913] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.408025] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.408057] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.408111] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.408114] system 00:04: [io  0xff00-0xff0f] has been reserved
[    0.408115] system 00:04: [io  0xffff] has been reserved
[    0.408117] system 00:04: [io  0xffff] has been reserved
[    0.408119] system 00:04: [io  0x0400-0x047f] could not be reserved
[    0.408121] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.408122] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.408125] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.408150] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.408185] system 00:06: [io  0x0240-0x0259] has been reserved
[    0.408187] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.408244] pnp 00:07: Plug and Play ACPI device, IDs ETD0001 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.408283] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.411655] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.411658] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.411660] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.411661] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.411663] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.411665] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.411667] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.411669] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.411671] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.411672] system 00:09: [mem 0xdffff000-0xdfffffff] has been reserved
[    0.411675] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.411799] pnp: PnP ACPI: found 10 devices
[    0.411800] ACPI: bus type PNP unregistered
[    0.418590] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.418601] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.418611] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000
[    0.418622] pci 0000:00:1c.5: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 05] add_size 200000
[    0.418637] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.418639] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.418641] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.418643] pci 0000:00:1c.5: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.418648] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd5300000-0xd54fffff 64bit pref]
[    0.418651] pci 0000:00:1c.1: BAR 15: assigned [mem 0xd5500000-0xd56fffff 64bit pref]
[    0.418654] pci 0000:00:1c.2: BAR 15: assigned [mem 0xd5700000-0xd58fffff 64bit pref]
[    0.418658] pci 0000:00:1c.5: BAR 15: assigned [mem 0xd5900000-0xd5afffff 64bit pref]
[    0.418661] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.418663] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.418666] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd00fffff]
[    0.418670] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.418673] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.418679] pci 0000:00:1c.0:   bridge window [mem 0xd3e00000-0xd51fffff]
[    0.418683] pci 0000:00:1c.0:   bridge window [mem 0xd5300000-0xd54fffff 64bit pref]
[    0.418690] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.418693] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.418699] pci 0000:00:1c.1:   bridge window [mem 0xd2a00000-0xd3dfffff]
[    0.418704] pci 0000:00:1c.1:   bridge window [mem 0xd5500000-0xd56fffff 64bit pref]
[    0.418711] pci 0000:00:1c.2: PCI bridge to [bus 04]
[    0.418714] pci 0000:00:1c.2:   bridge window [io  0xa000-0xafff]
[    0.418719] pci 0000:00:1c.2:   bridge window [mem 0xd1600000-0xd29fffff]
[    0.418724] pci 0000:00:1c.2:   bridge window [mem 0xd5700000-0xd58fffff 64bit pref]
[    0.418731] pci 0000:00:1c.5: PCI bridge to [bus 05]
[    0.418734] pci 0000:00:1c.5:   bridge window [io  0x9000-0x9fff]
[    0.418740] pci 0000:00:1c.5:   bridge window [mem 0xd0200000-0xd15fffff]
[    0.418744] pci 0000:00:1c.5:   bridge window [mem 0xd5900000-0xd5afffff 64bit pref]
[    0.418752] pci 0000:00:1e.0: PCI bridge to [bus 06]
[    0.419218] pci 0000:00:1e.0: setting latency timer to 64
[    0.419223] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.419225] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.419226] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.419228] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.419229] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.419231] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.419232] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.419234] pci_bus 0000:00: resource 11 [mem 0xc0000000-0xfeafffff]
[    0.419236] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.419237] pci_bus 0000:01: resource 1 [mem 0xc0000000-0xd00fffff]
[    0.419239] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.419241] pci_bus 0000:02: resource 1 [mem 0xd3e00000-0xd51fffff]
[    0.419242] pci_bus 0000:02: resource 2 [mem 0xd5300000-0xd54fffff 64bit pref]
[    0.419244] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.419246] pci_bus 0000:03: resource 1 [mem 0xd2a00000-0xd3dfffff]
[    0.419247] pci_bus 0000:03: resource 2 [mem 0xd5500000-0xd56fffff 64bit pref]
[    0.419249] pci_bus 0000:04: resource 0 [io  0xa000-0xafff]
[    0.419250] pci_bus 0000:04: resource 1 [mem 0xd1600000-0xd29fffff]
[    0.419252] pci_bus 0000:04: resource 2 [mem 0xd5700000-0xd58fffff 64bit pref]
[    0.419254] pci_bus 0000:05: resource 0 [io  0x9000-0x9fff]
[    0.419255] pci_bus 0000:05: resource 1 [mem 0xd0200000-0xd15fffff]
[    0.419257] pci_bus 0000:05: resource 2 [mem 0xd5900000-0xd5afffff 64bit pref]
[    0.419258] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.419260] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.419261] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.419263] pci_bus 0000:06: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.419264] pci_bus 0000:06: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.419266] pci_bus 0000:06: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.419267] pci_bus 0000:06: resource 10 [mem 0x000dc000-0x000dffff]
[    0.419269] pci_bus 0000:06: resource 11 [mem 0xc0000000-0xfeafffff]
[    0.419301] NET: Registered protocol family 2
[    0.419486] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.419742] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.419930] TCP: Hash tables configured (established 65536 bind 65536)
[    0.419964] TCP: reno registered
[    0.419976] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.420008] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.420099] NET: Registered protocol family 1
[    0.751556] pci 0000:01:00.0: Boot video device
[    0.751587] PCI: CLS 64 bytes, default 64
[    0.751636] Trying to unpack rootfs image as initramfs...
[    4.008030] Freeing initrd memory: 18128K (ffff88007ee4c000 - ffff880080000000)
[    4.008037] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    4.008039] software IO TLB [mem 0xbacf1000-0xbecf1000] (64MB) mapped at [ffff8800bacf1000-ffff8800becf0fff]
[    4.008250] Scanning for low memory corruption every 60 seconds
[    4.008554] Initialise module verification
[    4.008598] audit: initializing netlink socket (disabled)
[    4.008613] type=2000 audit(1397285165.852:1): initialized
[    4.032185] bounce pool size: 64 pages
[    4.032200] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    4.033384] zbud: loaded
[    4.033506] VFS: Disk quotas dquot_6.5.2
[    4.033541] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    4.033970] fuse init (API version 7.22)
[    4.034042] msgmni has been set to 15669
[    4.034595] Key type asymmetric registered
[    4.034598] Asymmetric key parser 'x509' registered
[    4.034629] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    4.034668] io scheduler noop registered
[    4.034670] io scheduler deadline registered (default)
[    4.034695] io scheduler cfq registered
[    4.034798] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    4.034866] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    4.034964] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    4.035059] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    4.035156] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    4.035246] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    4.035248] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    4.035250] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
[    4.035252] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    4.035270] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    4.035274] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    4.035292] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    4.035294] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    4.035298] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    4.035315] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    4.035320] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    4.035336] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    4.035338] pci 0000:05:00.0: Signaling PME through PCIe PME interrupt
[    4.035340] pci 0000:05:00.2: Signaling PME through PCIe PME interrupt
[    4.035341] pci 0000:05:00.3: Signaling PME through PCIe PME interrupt
[    4.035343] pci 0000:05:00.4: Signaling PME through PCIe PME interrupt
[    4.035344] pci 0000:05:00.5: Signaling PME through PCIe PME interrupt
[    4.035349] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
[    4.035358] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.035431] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 3b42 ss_vid 1043 ss_did 1c77
[    4.035470] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    4.035482] pciehp 0000:00:1c.1:pcie04: HPC vendor_id 8086 device_id 3b44 ss_vid 1043 ss_did 1c77
[    4.035513] pciehp 0000:00:1c.1:pcie04: service driver pciehp loaded
[    4.035525] pciehp 0000:00:1c.2:pcie04: HPC vendor_id 8086 device_id 3b46 ss_vid 1043 ss_did 1c77
[    4.035556] pciehp 0000:00:1c.2:pcie04: service driver pciehp loaded
[    4.035568] pciehp 0000:00:1c.5:pcie04: HPC vendor_id 8086 device_id 3b4c ss_vid 1043 ss_did 1c77
[    4.035597] pciehp 0000:00:1c.5:pcie04: service driver pciehp loaded
[    4.035601] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.035654] intel_idle: MWAIT substates: 0x1120
[    4.035655] intel_idle: v0.4 model 0x25
[    4.035656] intel_idle: lapic_timer_reliable_states 0xffffffff
[    4.035799] ACPI: AC Adapter [AC0] (on-line)
[    4.035881] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    4.036661] ACPI: Lid Switch [LID]
[    4.036697] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    4.036702] ACPI: Sleep Button [SLPB]
[    4.036727] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    4.036729] ACPI: Power Button [PWRF]
[    4.036789] ACPI: Requesting acpi_cpufreq
[    4.039245] thermal LNXTHERM:00: registered as thermal_zone0
[    4.039248] ACPI: Thermal Zone [THRM] (69 C)
[    4.039272] GHES: HEST is not enabled!
[    4.039356] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.041480] Linux agpgart interface v0.103
[    4.043200] brd: module loaded
[    4.044057] loop: module loaded
[    4.044129] megasas: 06.600.18.00-rc1 Wed. May. 15 17:00:00 PDT 2013
[    4.044447] libphy: Fixed MDIO Bus: probed
[    4.044545] tun: Universal TUN/TAP device driver, 1.6
[    4.044547] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.044603] PPP generic driver version 2.4.2
[    4.044663] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.044665] ehci-pci: EHCI PCI platform driver
[    4.044834] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    4.044871] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    4.044877] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    4.044901] ehci-pci 0000:00:1a.0: debug port 2
[    4.048888] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    4.048911] ehci-pci 0000:00:1a.0: irq 16, io mem 0xd5208000
[    4.058853] ACPI: Battery Slot [BAT0] (battery present)
[    4.059681] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    4.059703] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    4.059704] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.059706] usb usb1: Product: EHCI Host Controller
[    4.059707] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    4.059709] usb usb1: SerialNumber: 0000:00:1a.0
[    4.059809] hub 1-0:1.0: USB hub found
[    4.059814] hub 1-0:1.0: 2 ports detected
[    4.059983] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    4.059990] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    4.059994] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.060008] ehci-pci 0000:00:1d.0: debug port 2
[    4.063992] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    4.064007] ehci-pci 0000:00:1d.0: irq 23, io mem 0xd5207000
[    4.075681] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    4.075702] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    4.075704] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.075705] usb usb2: Product: EHCI Host Controller
[    4.075707] usb usb2: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    4.075708] usb usb2: SerialNumber: 0000:00:1d.0
[    4.075808] hub 2-0:1.0: USB hub found
[    4.075812] hub 2-0:1.0: 2 ports detected
[    4.075878] ehci-platform: EHCI generic platform driver
[    4.075884] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.075886] ohci-pci: OHCI PCI platform driver
[    4.075894] ohci-platform: OHCI generic platform driver
[    4.075899] uhci_hcd: USB Universal Host Controller Interface driver
[    4.075945] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    4.077608] i8042: Detected active multiplexing controller, rev 1.1
[    4.078445] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.078451] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    4.078470] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    4.078487] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    4.078501] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    4.078607] mousedev: PS/2 mouse device common for all mice
[    4.078771] rtc_cmos 00:05: RTC can wake from S4
[    4.078902] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    4.078933] rtc_cmos 00:05: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    4.078982] device-mapper: uevent: version 1.0.3
[    4.079039] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    4.079153] cpuidle: using governor ladder
[    4.079233] cpuidle: using governor menu
[    4.079242] ledtrig-cpu: registered to indicate activity on CPUs
[    4.079317] TCP: cubic registered
[    4.079393] NET: Registered protocol family 10
[    4.079561] NET: Registered protocol family 17
[    4.079570] Key type dns_resolver registered
[    4.079831] PM: Hibernation image not present or could not be loaded.
[    4.079835] Loading module verification certificates
[    4.080608] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: e20ade5b3af83aaa8563f0ef4119a030c4d3ffdb'
[    4.080621] registered taskstats version 1
[    4.083345] Key type trusted registered
[    4.086346] Key type encrypted registered
[    4.087801] AppArmor: AppArmor sha1 policy hashing enabled
[    4.088312]   Magic number: 10:757:771
[    4.088492] rtc_cmos 00:05: setting system clock to 2014-04-12 06:46:06 UTC (1397285166)
[    4.089400] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.089402] EDD information not available.
[    4.090763] Freeing unused kernel memory: 1392K (ffffffff81d0f000 - ffffffff81e6b000)
[    4.090765] Write protecting the kernel read-only data: 12288k
[    4.092296] Freeing unused kernel memory: 672K (ffff880001758000 - ffff880001800000)
[    4.092416] Freeing unused kernel memory: 20K (ffff880001bfb000 - ffff880001c00000)
[    4.111916] udevd[131]: starting version 175
[    4.123767] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.170788] sdhci: Secure Digital Host Controller Interface driver
[    4.170792] sdhci: Copyright(c) Pierre Ossman
[    4.179061] sdhci-pci 0000:05:00.0: SDHCI controller found [197b:2382] (rev 80)
[    4.179095] [drm] Initialized drm 1.1.0 20060810
[    4.179208] mmc0: no vqmmc regulator found
[    4.179211] mmc0: no vmmc regulator found
[    4.179347] mmc0: SDHCI controller on PCI [0000:05:00.0] using ADMA
[    4.179366] sdhci-pci 0000:05:00.2: SDHCI controller found [197b:2381] (rev 80)
[    4.179415] sdhci-pci 0000:05:00.2: Refusing to bind to secondary interface.
[    4.183972] ahci 0000:00:1f.2: version 3.0
[    4.184961] jme: JMicron JMC2XX ethernet driver version 1.0.8
[    4.184984] jme 0000:05:00.5: can't disable ASPM; OS doesn't have ASPM control
[    4.185978] jme 0000:05:00.5 eth0: JMC250 Gigabit Ethernet chiprev:23 pcirev:3 macaddr:f4:6d:04:86:87:ce
[    4.209565] [drm] radeon kernel modesetting enabled.
[    4.237531] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    4.237686] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    4.237690] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems sxs apst 
[    4.237697] ahci 0000:00:1f.2: setting latency timer to 64
[    4.237733] [drm] initializing kernel modesetting (CEDAR 0x1002:0x68E4 0x1043:0x1C92).
[    4.237804] [drm] register mmio base: 0xD0020000
[    4.237806] [drm] register mmio size: 131072
[    4.237873] ATOM BIOS: Asus
[    4.237946] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    4.237950] radeon 0000:01:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[    4.237953] [drm] Detected VRAM RAM=1024M, BAR=256M
[    4.237955] [drm] RAM width 64bits DDR
[    4.238038] [TTM] Zone  kernel: Available graphics memory: 4012522 kiB
[    4.238041] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    4.238042] [TTM] Initializing pool allocator
[    4.238047] [TTM] Initializing DMA pool allocator
[    4.238073] [drm] radeon: 1024M of VRAM memory ready
[    4.238075] [drm] radeon: 512M of GTT memory ready.
[    4.238389] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    4.240742] acpi device:04: registered as cooling_device4
[    4.240776] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    4.240834] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4
[    4.255494] [drm] Loading CEDAR Microcode
[    4.256197] [drm] PCIE GART of 512M enabled (table at 0x000000000025D000).
[    4.256351] radeon 0000:01:00.0: WB enabled
[    4.256354] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff88022d9f1c00
[    4.256356] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff88022d9f1c0c
[    4.257098] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c418 and cpu addr 0xffffc90010f9c418
[    4.257100] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    4.257101] [drm] Driver supports precise vblank timestamp query.
[    4.257126] radeon 0000:01:00.0: irq 46 for MSI/MSI-X
[    4.257138] radeon 0000:01:00.0: radeon: using MSI.
[    4.257163] [drm] radeon: irq initialized.
[    4.260351] scsi0 : ahci
[    4.260449] scsi1 : ahci
[    4.260530] scsi2 : ahci
[    4.260615] scsi3 : ahci
[    4.260693] scsi4 : ahci
[    4.260771] scsi5 : ahci
[    4.260883] ata1: SATA max UDMA/133 abar m2048@0xd5206000 port 0xd5206100 irq 45
[    4.260887] ata2: SATA max UDMA/133 abar m2048@0xd5206000 port 0xd5206180 irq 45
[    4.260888] ata3: DUMMY
[    4.260889] ata4: DUMMY
[    4.260892] ata5: SATA max UDMA/133 abar m2048@0xd5206000 port 0xd5206300 irq 45
[    4.260894] ata6: SATA max UDMA/133 abar m2048@0xd5206000 port 0xd5206380 irq 45
[    4.273821] [drm] ring test on 0 succeeded in 1 usecs
[    4.273880] [drm] ring test on 3 succeeded in 1 usecs
[    4.371719] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    4.504161] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    4.504164] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.504422] hub 1-1:1.0: USB hub found
[    4.504535] hub 1-1:1.0: 6 ports detected
[    4.579786] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.579820] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.580784] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    4.580996] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    4.581175] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    4.581182] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    4.581882] ata2.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    4.582257] ata2.00: ATAPI: SlimtypeDVD A  DS8A5SH, XAA2, max UDMA/100
[    4.583862] ata5: SATA link down (SStatus 0 SControl 300)
[    4.583889] ata6: SATA link down (SStatus 0 SControl 300)
[    4.584606] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    4.585322] ata2.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    4.585682] ata2.00: configured for UDMA/100
[    4.615759] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    4.748184] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    4.748187] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.748459] hub 2-1:1.0: USB hub found
[    4.748530] hub 2-1:1.0: 8 ports detected
[    4.819943] usb 1-1.2: new high-speed USB device number 3 using ehci-pci
[    4.882483] ata1.00: ATA-8: ST9500325AS, 0003SDM1, max UDMA/133
[    4.882486] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.884600] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    4.896804] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    4.897222] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    4.899136] ata1.00: configured for UDMA/133
[    4.899292] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      0003 PQ: 0 ANSI: 5
[    4.899477] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.899484] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    4.899532] sd 0:0:0:0: [sda] Write Protect is off
[    4.899535] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.899557] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.901402] scsi 1:0:0:0: CD-ROM            Slimtype DVD A  DS8A5SH   XAA2 PQ: 0 ANSI: 5
[    4.906108] sr0: scsi3-mmc drive: 31x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.906111] cdrom: Uniform CD-ROM driver Revision: 3.20
[    4.906223] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.906282] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.941199] usb 1-1.2: New USB device found, idVendor=04f2, idProduct=b1e5
[    4.941202] usb 1-1.2: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    4.941204] usb 1-1.2: Product: USB2.0 0.3M UVC WebCam
[    4.941206] usb 1-1.2: Manufacturer: Chicony Electronics Co., Ltd.
[    4.954393]  sda: sda1 sda2 < sda5 >
[    4.954761] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.007798] tsc: Refined TSC clocksource calibration: 2659.981 MHz
[    5.019955] usb 2-1.2: new full-speed USB device number 3 using ehci-pci
[    5.115329] usb 2-1.2: New USB device found, idVendor=046d, idProduct=c52f
[    5.115331] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.115334] usb 2-1.2: Product: USB Receiver
[    5.115335] usb 2-1.2: Manufacturer: Logitech
[    5.121703] hidraw: raw HID events driver (C) Jiri Kosina
[    5.127356] usbcore: registered new interface driver usbhid
[    5.127360] usbhid: USB HID core driver
[    5.129918] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
[    5.130057] hid-generic 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input0
[    5.131264] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input6
[    5.132741] hid-generic 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input1
[    5.441893] [drm:r600_uvd_init] *ERROR* UVD not responding, trying to reset the VCPU!!!
[    6.453969] [drm:r600_uvd_init] *ERROR* UVD not responding, trying to reset the VCPU!!!
[    7.466045] [drm:r600_uvd_init] *ERROR* UVD not responding, trying to reset the VCPU!!!
[    8.478117] [drm:r600_uvd_init] *ERROR* UVD not responding, trying to reset the VCPU!!!
[    9.490178] [drm:r600_uvd_init] *ERROR* UVD not responding, trying to reset the VCPU!!!
[   10.502261] [drm:r600_uvd_init] *ERROR* UVD not responding, trying to reset the VCPU!!!
[   11.514347] [drm:r600_uvd_init] *ERROR* UVD not responding, trying to reset the VCPU!!!
[   12.526410] [drm:r600_uvd_init] *ERROR* UVD not responding, trying to reset the VCPU!!!
[   13.538490] [drm:r600_uvd_init] *ERROR* UVD not responding, trying to reset the VCPU!!!
[   14.550550] [drm:r600_uvd_init] *ERROR* UVD not responding, trying to reset the VCPU!!!
[   14.570397] [drm:r600_uvd_init] *ERROR* UVD not responding, giving up!!!
[   14.570402] [drm:evergreen_startup] *ERROR* radeon: error initializing UVD (-1).
[   14.570448] Switched to clocksource tsc
[   14.570748] [drm] ib test on ring 0 succeeded in 0 usecs
[   14.570775] [drm] ib test on ring 3 succeeded in 0 usecs
[   14.571027] [drm] Radeon Display Connectors
[   14.571028] [drm] Connector 0:
[   14.571029] [drm]   LVDS-1
[   14.571031] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[   14.571032] [drm]   Encoders:
[   14.571033] [drm]     LCD1: INTERNAL_UNIPHY
[   14.571034] [drm] Connector 1:
[   14.571035] [drm]   HDMI-A-1
[   14.571036] [drm]   HPD1
[   14.571037] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[   14.571038] [drm]   Encoders:
[   14.571039] [drm]     DFP1: INTERNAL_UNIPHY1
[   14.571040] [drm] Connector 2:
[   14.571041] [drm]   VGA-1
[   14.571042] [drm]   DDC: 0x64d8 0x64d8 0x64dc 0x64dc 0x64e0 0x64e0 0x64e4 0x64e4
[   14.571043] [drm]   Encoders:
[   14.571044] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   14.571090] [drm] Internal thermal controller without fan control
[   14.571118] [drm] radeon: power management initialized
[   14.962834] [drm] fb mappable at 0xC035F000
[   14.962837] [drm] vram apper at 0xC0000000
[   14.962838] [drm] size 4325376
[   14.962839] [drm] fb depth is 24
[   14.962840] [drm]    pitch is 5632
[   14.963001] fbcon: radeondrmfb (fb0) is primary device
[   15.558954] Console: switching to colour frame buffer device 170x48
[   15.560988] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   15.560990] radeon 0000:01:00.0: registered panic notifier
[   15.561006] [drm] Initialized radeon 2.34.0 20080528 for 0000:01:00.0 on minor 0
[   15.701632] xor: measuring software checksum speed
[   15.740726]    prefetch64-sse: 12272.000 MB/sec
[   15.780726]    generic_sse: 10813.000 MB/sec
[   15.780728] xor: using function: prefetch64-sse (12272.000 MB/sec)
[   15.848742] raid6: sse2x1    6913 MB/s
[   15.916744] raid6: sse2x2    8216 MB/s
[   15.984778] raid6: sse2x4    9007 MB/s
[   15.984779] raid6: using algorithm sse2x4 (9007 MB/s)
[   15.984781] raid6: using ssse3x2 recovery algorithm
[   15.996288] bio: create slab <bio-1> at 1
[   15.996662] Btrfs loaded
[   16.005142] device-mapper: dm-raid45: initialized v0.2594b
[   18.840030] ISO 9660 Extensions: Microsoft Joliet Level 3
[   18.844269] ISO 9660 Extensions: RRIP_1991A
[   19.353297] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   60.714946] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   61.140821] udevd[1373]: starting version 175
[   64.009609] Bluetooth: Core ver 2.16
[   64.009637] NET: Registered protocol family 31
[   64.009640] Bluetooth: HCI device and connection manager initialized
[   64.009651] Bluetooth: HCI socket layer initialized
[   64.009654] Bluetooth: L2CAP socket layer initialized
[   64.009661] Bluetooth: SCO socket layer initialized
[   65.095516] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   65.095521] Bluetooth: BNEP filters: protocol multicast
[   65.095534] Bluetooth: BNEP socket layer initialized
[   65.199175] lp: driver loaded but no devices found
[   65.201550] Bluetooth: RFCOMM TTY layer initialized
[   65.201567] Bluetooth: RFCOMM socket layer initialized
[   65.201569] Bluetooth: RFCOMM ver 1.11
[   66.013264] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \GPIS 1 (20130517/utaddress-251)
[   66.014183] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 2 (20130517/utaddress-251)
[   66.014190] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   66.014195] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   66.014197] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   66.014198] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   66.014201] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   66.014202] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   66.014204] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   66.014205] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   66.170787] ppdev: user-space parallel port driver
[   66.748571] device-mapper: multipath: version 1.5.1 loaded
[   67.022046] psmouse serio4: elantech: assuming hardware version 2 (with firmware version 0x040102)
[   67.050428] psmouse serio4: elantech: Synaptics capabilities query result 0x78, 0x16, 0x0d.
[   67.088574] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   67.088769] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled until i915 loads
[   67.089582] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   67.158187] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input7
[   67.750448] asus_laptop: Asus Laptop Support version 0.42
[   67.751303] asus_laptop: BSTS called, 0xac00 returned
[   67.751318] asus_laptop:    model detected
[   67.751869] asus_laptop: Backlight controlled by ACPI video driver
[   67.751992] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input8
[   67.856539] init: failsafe main process (1602) killed by TERM signal
[   68.200130] mei_me 0000:00:16.0: setting latency timer to 64
[   68.200179] mei_me 0000:00:16.0: irq 47 for MSI/MSI-X
[   70.775087] cfg80211: Calling CRDA to update world regulatory domain
[   70.912294] Linux video capture interface: v2.00
[   71.518888] uvcvideo: Found UVC 1.00 device USB2.0 0.3M UVC WebCam (04f2:b1e5)
[   71.529712] input: USB2.0 0.3M UVC WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input9
[   71.529820] usbcore: registered new interface driver uvcvideo
[   71.529822] USB Video Class driver (1.1.1)
[   72.178670] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   73.081867] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   73.081872] hda-intel 0000:01:00.1: Using LPIB position fix
[   73.081987] snd_hda_intel 0000:01:00.1: irq 49 for MSI/MSI-X
[   73.085391] hda-intel 0000:01:00.1: Enable sync_write for stable communication
[   73.502603] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   76.517487] ath: EEPROM regdomain: 0x60
[   76.517492] ath: EEPROM indicates we should expect a direct regpair map
[   76.517495] ath: Country alpha2 being used: 00
[   76.517496] ath: Regpair used: 0x60
[   77.212552] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   77.213156] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900113c0000, irq=17
```

If you want boot info, I have a lot of them ! :lol:
That is some logs with Ubuntu 12.04.4 :
[http://paste.ubuntu.com/7237016/](http://paste.ubuntu.com/7237016/)
[http://paste.ubuntu.com/7237056/](http://paste.ubuntu.com/7237056/)

---

### Post by mollyman2 on 2014-04-12
Yeahh !! :D
I have solve the problem ! :P

I repared MBR with Windows tool (F8 when laptop start up).
Then, I used "EaseUS Partition Master", I rebuilded MBR of my sda (internal drive) in specifing that I want MBR for Windows 7 and not for XP. (As you have suggested 
oldfred ;) )
Then I rebuilded MBR of my sdb (external drive) for Win7 and not XP. After that I deleted all partitions on sdb.
And finally the installation of Ubuntu 12.04.4 ran without a hitch.

Just for information, I tell you what partitions I carried out.
In sdb : - 250Mo in ext4 mounted at /boot
           - 8Go of swap (I need a lot of swap to compile Android)
           - 312Go (the rest) in ext4 mounted in /
And Grub on sdb.

Without sdb Windows 7 startup without any trouble. To use Ubuntu I use the "Escape" key to choose the drive I want to boot.

Finally the problem is solved after 2 weeks and alot of hours spent by searching solution. I am very happy. Thank you to everyone and especially oldfred. ;)

---

### Post by mörgæs on 2014-04-12
Thanks for an attempt at marking the thread solved but please use Thread Tools.

---

### Post by mollyman2 on 2014-04-12
> **mörgæs said:**
> Thanks for an attempt at marking the thread solved but please use Thread Tools.

Yes sorry.
I'm moderator on a French forum that don't has this thread tools that's why I  forgot to use it. I corrected.  O:)

---

### Post by oldfred on 2014-04-12
Glad you got it working. :)

There also is a French forum. Not sure how active it is. 
 French Forums
 [www.ubuntu-fr.org](www.ubuntu-fr.org)

---

### Post by mollyman2 on 2014-04-12
;)
Yes I know the French forum but I thought it was a difficult problem and there is more English Ubuntu users than French ubuntu users.
And this is not bad, it makes me improve my English. :rolleyes:

---

