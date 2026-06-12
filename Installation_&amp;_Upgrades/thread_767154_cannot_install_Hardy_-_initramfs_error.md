---
title: "cannot install Hardy - initramfs error"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by azurehi on 2008-04-25
I cannot install HH ubuntu 8.04 (not kubuntu 8.04) because of an initramfs error/problem.  I have downloaded images from several different mirrors, including the alternate version and burned each on new discs at the slowest speed and Always get the screen with BusyBox v1.1.3(Debian 1:1.1.3-5ubuntuiz) built-in shell (ash)
initramfs.  I have tried changing BIOS setting from IDE to RAID and at F6 adding pci-nomsi.  Nothing works.  

I have used ubuntu successfully since 6.06.  Could this be related to the kernel 2.6.24?  I am unable to install 8.04 - any suggestions will be much appreciated.

---

### Post by jedimasterk on 2008-04-25
Try inserting a floppy with some data on and see if the Live CD will continue on with the bootup process.

---

### Post by jedimasterk on 2008-04-25
Quote: Aliasbind's hint was right: I noticed the system trying to get a floppy. I inserted one, then ubuntu read the floppy for some time and finally continued to boot from CD. No error message or anything, just reading the floppy. While I'm writing this posting I still use ubuntu 8.04 in Live-CD mode.

And I have a ASUS P5B-Deluxe mainboard with this f****g JMicron controller stuck on it! This one gave me trouble eversince I bought the board some 18 months ago using Windows or different Linux distributions. Now it's definitly time to buy some SATA DVD-Writer and disable this controller. Perhaps it interferes here as well as some other users mention it as part of their system, too.

Try the floppy

---

### Post by tormod on 2008-04-25
Please report this in launchpad if it hasn't been already. File it on initramfs-tools if it happens both with the Desktop and Alternate CD.

---

### Post by oldnat on 2008-04-26
Alas, it does not work.
I inserted a floppy. It seeked it, but came to initramfs again. Then I write enabled the floppy. Then it seeked it not (just lit the LED), but came to initramfs again. I removed all USB card readers etc, disabled the serial and parallel ports etc - all the same. It stops at initramfs and I am not able to get it move on...

---

### Post by tormod on 2008-04-26
When the booting stops at the initramfs busybox prompt, it is generally because the "root=UUID=something" option in the grub kernel line is wrong. Type **cat /proc/cmdline** to see the value. Type **ls /dev/disk/by-uuid** to see what the possible values can be (of course only one of them is the correct root partition).

---

### Post by Solrac924 on 2008-04-26
wconstantine, was exactly was the error message (at the bottom) when you booted with no splash?

---

### Post by azurehi on 2008-04-27
Following the suggestion of Jong [http://ubuntuforums.org/showthread.php?t=765195&page=7](http://ubuntuforums.org/showthread.php?t=765195&page=7)  I booted the desktop live cd image, chose language, install, F6 and entered:

all_generic_ide floppy=off irqpoll

The image booted to live desktop and I was able to install HH without problem.  many thanks to Jong!!

---

### Post by stanley82 on 2008-04-28
I updated gutsy then upgraded to Hardy and get a white on black old fashioned DOS screen with all the initramfs stuff.  The above process normally upgrades me with only printer and firefox plugin problems.  Right now I'm dead in the water and do not have any floppies.  Im using ubuntu on an AMD64 system.  Regards Ian.

My fix
After a fair bit of digging using Google and getting lots of info I'm sure there is a problem with Hasty Heron.  I used my old RAF INIT and hit esc in grub tried Kernel 2.6.24.16 recovery and that sort of died.  Next boot I selected Kernel 2.6.22.14 generic and Ubuntu 8.04 came to life.  So I guess I'm using Ubuntu 8.04 with the 7.10 kernel.  At least it runs.  Thanks for your suggestions.  Strange things computers, once upon a time I fully understood them now I doubt anyone does.  Regards Ian.

---

### Post by Efaill on 2008-04-28
> **azurehi said:**
> Following the suggestion of Jong [http://ubuntuforums.org/showthread.php?t=765195&page=7](http://ubuntuforums.org/showthread.php?t=765195&page=7)  I booted the desktop live cd image, chose language, install, F6 and entered:

all_generic_ide floppy=off irqpoll

The image booted to live desktop and I was able to install HH without problem.  many thanks to Jong!!

Fantastic stuff did the job for me \\:D/

---

### Post by azurehi on 2008-04-28
Further note:  I found that at F6 adding only the "all_generic_ide" was all I needed to boot cd-rom and install HH.  I believe that this will also work in kubuntu 8.04 but have not tried it.  I'm glad to have learned of this and happy it seems to work.

---

### Post by bingobingo on 2008-04-28
I say do not do install 8.04, stick with 7.10. I did the upgrade and it is slowing my computer down bad, cpu is always loaded even with no apps running, do not know what is causing it, though all apps seam to run.

---

### Post by stanley82 on 2008-04-28
My fix
After a fair bit of digging using Google and getting lots of info I'm sure there is a problem with Hasty Heron.  I used my old RAF INIT and hit esc in grub tried Kernel 2.6.24.16 recovery and that sort of died.  Next boot I selected Kernel 2.6.22.14 generic and Ubuntu 8.04 came to life.  So I guess I'm using Ubuntu 8.04 with the 7.10 kernel.  At least it runs.  Thanks for your suggestions.  Strange things computers, once upon a time I fully understood them now I doubt anyone does.  Regards Ian.

---

### Post by GoldenNugget on 2008-04-29
I've tried using the all_generic_ide floppy=off irqpoll and it still doesn't boot.  I've tried various combinations as well.

I've also tried doing a fresh install with the alternate cd and that is also not working due to not being able to manually choose a cd module or something...  

God I'd like to try out HH but nothing seems to work...  And I want a fresh install since the last three times I've tried to upgrade my upgrade broke in some way.

---

### Post by vlgligor on 2008-04-29
Sorry, but the "all_generic_ide floppy=off irqpoll" options does not work for me, all the time I end up in the initramfs + busybox.

My configuration:
Intel C2Duo 6300
MB MSI P965 Platinum
HDD SATA
DVD-WR Primary IDE.

I could install it from the alternate CD, but after I boot in Hardy it ends up in the very same initramfs + busybox. The Gutsy was working from the beginning without any problems.

---

### Post by tormod on 2008-04-29
> **bingobingo said:**
> I say do not do install 8.04, stick with 7.10. I did the upgrade and it is slowing my computer down bad, cpu is always loaded even with no apps running, do not know what is causing it, though all apps seam to run.

What hardware do you have? Please file a bug so we can get this fixed in 8.04.

---

### Post by jedimasterk on 2008-04-29
> **tormod said:**
> What hardware do you have? Please file a bug so we can get this fixed in 8.04.


I got same error (initramfs)_. 
My hardware is
Asus K8VSE Deluxe (motherboard)(AMD 64 3200+)
eVGA 6800GT 256MB RAM
Seagate 500 GB SATA internal harddrive
2GB Corsair XMMS RAM
Pioneer IDE DVD+/-RW
Internal generic Comp USA IDE Floppy Drive.

---

### Post by tormod on 2008-04-29
The problem is that there are many different ways of something going wrong - each different bugs - that result in the (initramfs) prompt. In this thread there are so many different issues so it's quite difficult to get anything useful out of it.

This is also why (almost) no developers have time to look around in the forum, there's too much noise and misleading info. Therefore you have to file your own bugs and give precise, verbatim information if want to see your problems fixed. Developers read bug reports.

If you install Hardy from scratch (so upgrade and configuration issues can be ruled out) and your machine does not boot any longer or performs a lot worse than in other Ubuntu/Linux versions (so hardware problems can be ruled out), it is a bug that we would like to get fixed. Ubuntu should work well out-of-the-box on most common hardware.

---

### Post by bc90021 on 2008-05-02
Originally Posted by azurehi  View Post
Following the suggestion of Jong [http://ubuntuforums.org/showthread.php?t=765195&page=7](http://ubuntuforums.org/showthread.php?t=765195&page=7) I booted the desktop live cd image, chose language, install, F6 and entered:

all_generic_ide floppy=off irqpoll

The image booted to live desktop and I was able to install HH without problem. many thanks to Jong!!


This worked for me as well.  Unfortunately, it doesn't seem to recognise my bluetooth keyboard and mouse (though the BIOS does!) so I'm off to solve that problem.

---

### Post by Solrac924 on 2008-05-03
> **tormod said:**
> The problem is that there are many different ways of something going wrong - each different bugs - that result in the (initramfs) prompt. In this thread there are so many different issues so it's quite difficult to get anything useful out of it.

i totally agree on this. that's why i asked early on what was shown when the machine was booted (with no splash). the cause could be a misconfigured interrupt controller, or an interface being overlapped or with a direct memory access problem. i read where users are trying whatever remedy without truly understanding their hardware issue at hand. we should ask the person with any problems to do some reading before any posting. ;)

---

### Post by Shaman82 on 2008-05-03
Stanley82's workaround did the trick for me; I booted with the older kernel and all is well, so far. I've also seen on other threads that changing drive settings from SATA to RAID in the system BIOS is working for some. I've been using Linux for a while, but I am still a noob; take this post for whatever it's worth, if anything.

---

### Post by ProtocolOH on 2008-05-03
I've found a related bug.  I had previously tried installing Gibbon (7.10) on a new box I'd built, and really didn't have any issues with it.  But I didn't need the box immediately, so I let it sit idle.  Now that Heron is out, and it's a LTS release, I decided to have a go.

But even after diagnosing a bad Heron ISO burn (and then verifying that my second disc was 100% OK by booting it on another machine and checking it), my new box would always dump to the BusyBox/initramfs prompt.  I thought maybe it was the new RAID card (RocketRaid 3120) I'd put in.  I pulled all my expansion cards, but the problem persisted.

So I went into BIOS and reverted to "Optimized Defaults".  And whaddaya know, the system boots off the Heron CD and goes into the installer.  Huh.  So, on a hunch, I went back into BIOS to see what had reverted.  I made one change... to tell BIOS that I had no 1.44MB 3.5" floppy drive installed (I don't).  I rebooted, and got the BusyBox prompt.  Flipped the setting back (to saying I had a drive), and Heron boots.

If you think I should file a bug, please give this n00b a URL to point me to where I should do that.

Hardware:

Foxconn 6150BK8MC-KRSHN2 MiniATX mobo (nForce 430 / GeForce 6150)
  BIOS revision 012306 (58GW1P27, Jan 23 2006?)
AMD Athlon 64 3400+ (Socket 939, 2.2GHz)
2GB (2 x 1GB) Buffalo PC3200 DDR RAM (dual-channel)
Sun Quad Ethernet X1034A (PCI)
Adaptec AHA2940UW SCSI adapter (PCI)
HighPoint RocketRAID 3120 (PCI-E x1)
2x WD 200GB SATA drives (attached to RR3120 in RAID 1)
1x WD 80GB drive (attached to mainboard)
1x Samsung IDE CD/DVD burner

(Note: I'm seeing about upgrading the BIOS to 58GW1P34, but Foxconn only provides DOS-mode flash utilities... you realize what a pain in the *** it is to try and make a DOS boot disk without a floppy drive?)

EDIT: I managed to update my BIOS to version P34 (from version P27), and no change in this behavior.  I reverted to Optimized Defaults in the BIOS (which configures Floppy A as a 3.5" drive).  I booted the Heron CD, and started the disc self-check utility to verify that the utility was booting correctly.  Once it started doing the actual check, I rebooted, went into BIOS, and _only_ changed the floppy setting (to "no drive").  Saved, rebooted, started into the Heron disc-check utility, and after a few sweeps of the Cylon bar (what do you call that thing, anyway?), I got dumped into the BusyBox/initramfs prompt.  So there ya go... bug confirmed.  Please give me a URL if you want me to report a bug.

---

### Post by blueorder on 2008-05-04
Give this post a read. might be able to help.

[http://ubuntuforums.org/showpost.php?p=4576776&postcount=6](http://ubuntuforums.org/showpost.php?p=4576776&postcount=6)

---

### Post by tormod on 2008-05-04
> **ProtocolOH said:**
> Please give me a URL if you want me to report a bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

(see also the links in my signature)

---

### Post by ProtocolOH on 2008-05-04
> **tormod said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

(see also the links in my signature)
Danke.  I searched for related bugs, and there were a couple of close matches, but none seemed to involve the mechanic of changing BIOS settings and having that cause Hardy to fail to boot.  So I went ahead and filed a new one:

[https://bugs.launchpad.net/ubuntu/+bug/226519](https://bugs.launchpad.net/ubuntu/+bug/226519)

It may end up being a dupe of another bug, but whoever's in charge of the original bug should be able to figure it out pretty quickly.  Thanks.

---

### Post by stanley82 on 2008-05-05
I also had this initramfs on another system using Xubuntu install.  It was due to an error on my CD (guess a r/w is not as good as read only) so suggest choosing check CD before selecting install.  Regards Ian.

---

### Post by sharky517 on 2008-05-17
I also had the initramfs error, not to mention the installation process seemed to take longer than it should. After reading this post i simply added all_generic_ide to my boot options and everything went smoothly. I love when it's a one search solution!

---

### Post by uniontroublemaker on 2008-05-26
Inserting a floppy finally resolved this problem for me, after burning numerous CDs and DVDs thinking they were bad.  I even ordered a CD by mail.  I was finally able to do a clean re-install of Hardy to fix a corrupted online upgrade.

---

### Post by stanley82 on 2008-05-26
I am sure that you are right.  I overcame the issue by reverting to the Gutsy kernel and that is what I am still using on Hardy.  I am sure that most of these problems are due to a bad upgrade file or bad disk.  A corrupted file somewhere.  I was asked to cut a CD and retry.  I did that and selected check CD before doing anything else and once that checked out I ran the CD with out changing my HD settings.  That was fine.  So how do I get the Hardy kernel off the CD and into /boot....?  Regards Ian.

---

### Post by iqiszero on 2008-05-28
Folks,
I think I have a great news to fix this ****initramfs**** issue. Here is what I did.

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe ata_piix
modprobe ide_generic
exit

You will now boot into the LiveCD normally. 
Above worked successfully and I hope your case is working fine.

---

### Post by stanley82 on 2008-05-30
Did you arrow down and check the CD first?  My Hardy Kernel has an error after upgrade.  I cut a CD, checked it and booted the live CD without any F6 and it ran fine.  What I need to do is to get the kernel off the live CD and onto my Hard Drive.  I am sure that we all have different problems causing a boot fail.

---

### Post by RodGer GR on 2009-11-14
Hello. I have the same problem. I thought I found the solution using the alternate cd until I rebooted my desktop for the first time after the first login in my newly installed system.

I have the same message with BusyBox and Initramfs after choosing from the Grub menu and after seeing that orange bar loading for a while.

I tried to add the 'all_generic_ide' option in the menu.lst at the line where 'quiet' was and I got a message 'error 27 unrecognized command...'

Since I made it to install, I think there is a hope I can change something in my installed kernel (using a live cd) to make it functional again.

Any ideas what I should change?


More system information:
```
ubuntu                    
   [B] description: Desktop Computer
    product: POWERMATE_ML460_PRO
    vendor: NEC COMPUTERS SAS[/B]
    version: PM-F-ML460-PRO
    serial: 208268560001
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=E452A619-892E-DC11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: Q965T-NP
       vendor: ELITEGROUP COMPUTER SYSTEMS CO., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: NEC COMPUTERS SAS NOTE BIOS Version
          physical id: 0
          version: 965Q0190 (03/28/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU            2140  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.15.2
          serial: 0000-06F2-0000-0000-0000-0000
          slot: Socket 775
          size: 1200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 0x4D332037385436353533455A532D43453620
             vendor: 0xCE00000000000000
             physical id: 0
             serial: 0xF8102FFD
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.2
          serial: 0000-06F2-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82Q963/Q965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82Q963/Q965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:a000(size=4096) memory:fd700000-fd7fffff ioport:fd600000(size=1048576)
        *-display
             description: [B]VGA compatible controller
             product: 82Q963/Q965 Integrated Graphics Controller[/B]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:fda00000-fdafffff memory:d0000000-dfffffff(prefetchable) ioport:ff00(size=8)
        *-communication
             description: Communication controller
             product: 82Q963/Q965 HECI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=heci latency=0
             resources: irq:16 memory:fdfff000-fdfff00f
        *-ide:0 UNCLAIMED
             description: IDE interface
             product: 82Q963/Q965 PT IDER Controller
             vendor: Intel Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi cap_list
             configuration: latency=0
             resources: ioport:fe00(size=8) ioport:fd00(size=4) ioport:fc00(size=8) ioport:fb00(size=4) ioport:fa00(size=16)
        *-network
             description: Ethernet interface
             product: 82566DM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:16:ec:92:1a:ec
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.1-0 ip=192.168.178.29 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
             resources: irq:27 memory:fdfc0000-fdfdffff memory:fdffe000-fdffefff ioport:f900(size=32)
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:f800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:f700(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fdffd000-fdffd3ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:fdff4000-fdff7fff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:d000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:c000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
           *-storage
                description: SATA controller
                product: JMB361 AHCI/IDE
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:17 memory:fdcfe000-fdcfffff memory:fdb00000-fdb0ffff(prefetchable)
           *-ide
                description: IDE interface
                product: JMB361 AHCI/IDE
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: scsi4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0
                resources: irq:18 ioport:cf00(size=8) ioport:ce00(size=4) ioport:cd00(size=8) ioport:cc00(size=4) ioport:cb00(size=16)
              *-cdrom
                   description: DVD reader
                   product: UJDA770 DVD/CDRW
                   vendor: MATSHITA
                   physical id: 0.0.0
                   bus info: scsi@4:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   logical name: /cdrom
                   version: 1.02
                   capabilities: removable audio cd-r cd-rw dvd
                   configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/cdrom
                      logical name: /cdrom
                      configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:f600(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:f500(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:f400(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdffc000-fdffc3ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:b000(size=4096) memory:fd900000-fd9fffff ioport:fd800000(size=1048576)
        *-isa
             description: ISA bridge
             product: 82801HO (ICH8DO) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f300(size=8) ioport:f200(size=4) ioport:f100(size=8) ioport:f000(size=4) ioport:ef00(size=16) ioport:ee00(size=16)
           *-disk
                description: ATA Disk
                product: ST3160815AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9RA1L3HM
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2aff8c51
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: a0405a69-7bcd-d948-ab9a-0a16c99de2a6
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-11-11 20:27:46 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 131GiB
                   capacity: 131GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 14GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 112GiB
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 4094MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /media/d8d984b5-ab4b-4239-87a0-e65fe451cfbc
                   version: 1.0
                   serial: d8d984b5-ab4b-4239-87a0-e65fe451cfbc
                   size: 125MiB
                   capacity: 125MiB
                   capabilities: primary journaled extended_attributes recover ext3 ext2 initialized
                   configuration: created=2009-11-13 23:30:05 filesystem=ext3 modified=2009-11-14 01:18:55 mount.fstype=ext3 mount.options=rw,nosuid,nodev,relatime,errors=continue,data=writeback mounted=2009-11-14 01:18:55 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fdffb000-fdffb0ff ioport:500(size=32)

```

The problem seems to be solved with Karmic Koala but there are some other problems as I described [here]("http://ubuntuforums.org/showthread.php?t=1325892") and [here]("http://ubuntuforums.org/showthread.php?p=8314551#post8314551").

---

