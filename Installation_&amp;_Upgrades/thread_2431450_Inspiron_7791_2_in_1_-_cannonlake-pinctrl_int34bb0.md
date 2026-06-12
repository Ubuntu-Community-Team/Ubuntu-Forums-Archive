---
title: "Inspiron 7791 2 in 1 - cannonlake-pinctrl int34bb:00: request() failed for pin 180"
date: 2019-11-16
forum: Installation &amp; Upgrades
---

### Post by jeff-kane1 on 2019-11-16
I have a new 2 in 1 Dell Inspiron 17" 7791.  The newest version.  It has an Intel i7-10510u CPU.  16GB ram.  512GB SSD.

I shrunk the Windows partition and have 400GB for Ubuntu now.  I created a bootable USB with the Ubuntu install ISO. 

I am trying to install Ubuntu.  I tried 19.10 first.  I get these 2 lines on the screen and then it hangs.

[FONT=Calibri]cannonlake-pinctrlint34bb:00: request() failed for pin 180[/FONT]
[FONT=Calibri] [/FONT]
[FONT=Calibri]cannonlake-pinctrlpin-180 (int34bb:00:431) status -16[/FONT]
[FONT=Calibri] [/FONT]
I tried 18.04 LTS next.  It gets as far as the purple splash screen and counts up the first 3 dots.  Then it hangs with the last 2 dots still greyed out.

Any hints on where to look for a next step?

---

### Post by mörgæs on 2019-11-17
Hi, welcome to the fora.

In a live boot please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and post lshw.txt in CODE tags. It will tell us all about the hardware (though you have already posted some information).

---

### Post by jeff-kane1 on 2019-11-17
It won't live boot.  It only makes it that far while trying to boot.  Is there some trick to force it to a command prompt?

I did install in a VirtualBox.  That works with windows as the host.

---

### Post by mörgæs on 2019-11-17
Can you boot the [daily live]("http://cdimage.ubuntu.com/daily-live/") ISO?

---

### Post by jeff-kane1 on 2019-11-17
That says it is AMD and not Intel.  I tried it anyhow.  Result is attached, if attaching worked.  The result was the same except that it has an initramfs unpacking failed: Decoding failed error also.

---

### Post by jeff-kane1 on 2019-11-17
Would a windows hardware or component export help?  I tired to paste here, but get a security token error.

---

### Post by wildmanne39 on 2019-11-17
> **jeff-kane1 said:**
> Would a windows hardware or component export help?  I tired to paste here, but get a security token error.
That is because the text is to large to post here, you can post it on pastebin:

[https://pastebin.com/](https://pastebin.com/)

Then paste the link back here.

---

### Post by jeff-kane1 on 2019-11-17
Hardware: [https://pastebin.com/qAYtTMiL](https://pastebin.com/qAYtTMiL)

Component: [https://pastebin.com/DfRtFznp](https://pastebin.com/DfRtFznp)

---

### Post by jeff-kane1 on 2019-11-18
May have made some progress.  There is a bios update from 1.1.0 to 1.2.0 that came out yesterday.  I applied it.  Now Windows won't boot!  Grrr.  I am in the process of doing a factory restore of Windows.  However, before I started that. I booted to the current live Ubuntu, because the USB dongle was already plugged in and I was curious.  It booted successfully!  :-)

Give me a bit of time to do finish recovering Windows and then I will try live again.  If that works, I will try installing Ubuntu 19.10 in a new partition again.  I will report my results here when I am done.

---

### Post by oldfred on 2019-11-18
Generally with Dell you do have to do the UEFI update, but that should not break Windows.
Also if SSD, you may need SSD firmware update.
And only use Windows to shrink the NTFS partition & reboot, so it can run chkdsk.
Then make sure Windows fast start up is off. Note Windows updates often turn fast start up back on and then grub will not boot Windows. But you still boot Windows from UEFI to turn off fast start up again.

You have a nVidia card/chip. That will need nomodeset to boot live installer. And first boot or until you install nVidia proprietary driver. Ubuntu's newest version offers to install nVidia driver during install.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Issues are common across many Dell models. But you have very newest, so may need very newest Ubuntu or extra boot parameters or drivers.
Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options)

DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)

---

### Post by jeff-kane1 on 2019-11-18
So ... looks like making sure the bios is at 1.2.0 is a major part.  I can boot to a live session.  Extremely slow though.  I would say so slow that it is not usable.

I went ahead and shrunk the windows partition again.  Left 350 Gig for Ubuntu.  Booted in 19.10 live to see if it would work.  Same as the current live was.  It ran, but clicking anything made it scream to a halt for a couple of minutes.

I am in process of doing an install.  It is hung after asking for Updates and other software.  Not sure what the next step is, but it has not asked where to install to yet, so I am concerned that this is not the right place to take a long time.  It's been about 20 minutes with a blue disk spinning.  <sigh>

I guess I will give it a bit more time and then give up until tomorrow.  I made progress today, but am about out of patience.  ;-)

As for this thread, make sure the bios is updated to 1.2.0 from the install of 1.1.0.  That was the key to getting past the boot errors.

---

### Post by jeff-kane1 on 2019-11-18
I gave up.  Even opening a terminal and running the lshw command is too slow.  Been staring at it for 5 minutes and nothing.  Anything else I do is the same way.  Too slow to be worth it!

---

### Post by jeff-kane1 on 2019-11-18
I am up and running ... Kind of!  Windows is hosed again!

So, I had to use safe video mode.  That made the install run so much faster.  

Then I had to turn off Secure Boot in the BIOS.  That pissed off Windows.  Had to do a bitlocker recovery.  Luckily I had use my M$ Live account to login originally, so it synced that up and I was easily able to find it.

But, Ubuntu only booted to a grub prompt.  

More reading and I found that the BIOS also needed System Configuration SATA set to AHCI even though I am using the SSD and not a SATA drive.  

I did another install run and it worked this time.  Runs pretty fast too.

However, Windows hates AHCI instead of RAID On.  It keeps going into recovery mode.  I can go to the BIOS and set it back to Raid On and it will boot again, but then Ubuntu beeps and goes into a memory test.

A lot of progress for one day!  I am going to try to take a break again ... but who knows.  Sometimes I just can't walk away.  ;-)

I will add another comment with the lshw output in case it will help someone else.

Next step is to install Virtualbox and see if I can get Windows to run in it.  If so, I don't care about the dual boot mess with having to press F2 and change the Hard Disk setting each time.

---

### Post by jeff-kane1 on 2019-11-18
lshw output ...

```
computer
    description: Convertible
    product: Inspiron 7791 2n1 (0951)
    vendor: Dell Inc.
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.2.0 dmi-3.2.0 smp vsyscall32
    configuration: boot=normal chassis=convertible family=Inspiron sku=0951 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0NNGJG
       vendor: Dell Inc.
       physical id: 0
       version: A00
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: 1.2.0
          date: 08/08/2019
          size: 1MiB
          capacity: 32MiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-10510U CPU @ 1.80GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-10510U CPU @ 1.80GHz
          serial: [REMOVED]
          slot: CPU 1
          size: 4115MHz
          capacity: 4900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 700
             slot: L1 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 701
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 702
             slot: L3 Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 2667 MHz (0.4 ns)
             product: HMA81GS6JJR8N-VK
             vendor: SK Hynix
             physical id: 0
             serial: [REMOVED]
             slot: DIMM A
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR4 Synchronous 2667 MHz (0.4 ns)
             product: HMA81GS6JJR8N-VK
             vendor: SK Hynix
             physical id: 1
             serial: [REMOVED]
             slot: DIMM B
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             logical name: /dev/fb0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
             configuration: depth=32 driver=i915 latency=0 mode=1920x1080 visual=truecolor xres=1920 yres=1080
             resources: iomemory:600-5ff iomemory:400-3ff irq:195 memory:6022000000-6022ffffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: iomemory:600-5ff irq:16 memory:6023110000-6023117fff
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: latency=0
             resources: iomemory:600-5ff memory:602312b000-602312bfff
        *-generic:2 UNCLAIMED
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: latency=0
             resources: iomemory:600-5ff memory:602312a000-602312afff
        *-communication:0
             description: Serial controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm 8250 bus_master cap_list
             configuration: driver=intel_ish_ipc latency=0
             resources: iomemory:600-5ff irq:20 memory:6023122000-6023123fff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: iomemory:600-5ff irq:129 memory:6023100000-602310ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.3.0-23-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.03
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0 UNCLAIMED
                   description: Generic USB device
                   product: FingerPrint
                   vendor: Goodix
                   physical id: 5
                   bus info: usb@1:5
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: Video
                   product: Integrated_Webcam_HD
                   vendor: CN0HK46K8LG00982BFVSA00
                   physical id: 6
                   bus info: usb@1:6
                   version: 86.14
                   serial: [REMOVED]
                   capabilities: usb-2.01
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: a
                   bus info: usb@1:a
                   version: 0.02
                   capabilities: bluetooth usb-2.01
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.3.0-23-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.03
                capabilities: usb-3.10
                configuration: driver=hub slots=6 speed=10000Mbit/s
        *-memory UNCLAIMED
             description: RAM memory
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz (30.3ns)
             capabilities: pm cap_list
             configuration: latency=0
             resources: iomemory:600-5ff iomemory:600-5ff memory:6023120000-6023121fff memory:6023129000-6023129fff
        *-network
             description: Wireless interface
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             logical name: wlp0s20f3
             version: 00
             serial: [REMOVED]
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-23-generic firmware=48.4fa0041f.0 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
             resources: iomemory:600-5ff irq:16 memory:602311c000-602311ffff
        *-generic:3
             description: SD Host controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=0
             resources: iomemory:600-5ff irq:19 memory:6023128000-6023128fff
        *-serial:0
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:16 memory:4010000000-4010000fff
        *-serial:1
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:17 memory:4010001000-4010001fff
        *-communication:1
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: iomemory:600-5ff irq:166 memory:6023125000-6023125fff
        *-sata
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: sata msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:131 memory:bc200000-bc201fff memory:bc204000-bc2040ff ioport:4080(size=8) ioport:4088(size=4) ioport:4060(size=32) memory:bc203000-bc2037ff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:5000(size=8192) memory:a4000000-ba0fffff ioport:6000000000(size=570425344)
           *-pci
                description: PCI bridge
                product: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 06
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:16 ioport:5000(size=4096) memory:a4000000-ba0fffff ioport:6000000000(size=570425344)
              *-pci:0
                   description: PCI bridge
                   product: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018]
                   vendor: Intel Corporation
                   physical id: 0
                   bus info: pci@0000:02:00.0
                   version: 06
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:126 memory:ba000000-ba0fffff
                 *-generic
                      description: System peripheral
                      product: JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018]
                      vendor: Intel Corporation
                      physical id: 0
                      bus info: pci@0000:03:00.0
                      version: 06
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress msix bus_master cap_list
                      configuration: driver=thunderbolt latency=0
                      resources: irq:16 memory:ba000000-ba03ffff memory:ba040000-ba040fff
              *-pci:1
                   description: PCI bridge
                   product: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018]
                   vendor: Intel Corporation
                   physical id: 1
                   bus info: pci@0000:02:01.0
                   version: 06
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:127 ioport:5000(size=4096) memory:a4100000-b9ffffff ioport:6000000000(size=570425344)
              *-pci:2
                   description: PCI bridge
                   product: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018]
                   vendor: Intel Corporation
                   physical id: 2
                   bus info: pci@0000:02:02.0
                   version: 06
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:128 memory:a4000000-a40fffff
                 *-usb
                      description: USB controller
                      product: JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018]
                      vendor: Intel Corporation
                      physical id: 0
                      bus info: pci@0000:3b:00.0
                      version: 06
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress xhci cap_list
                      configuration: driver=xhci_hcd latency=0
                      resources: irq:130 memory:a4000000-a400ffff
                    *-usbhost:0
                         product: xHCI Host Controller
                         vendor: Linux 5.3.0-23-generic xhci-hcd
                         physical id: 0
                         bus info: usb@3
                         logical name: usb3
                         version: 5.03
                         capabilities: usb-2.00
                         configuration: driver=hub slots=2 speed=480Mbit/s
                    *-usbhost:1
                         product: xHCI Host Controller
                         vendor: Linux 5.3.0-23-generic xhci-hcd
                         physical id: 1
                         bus info: usb@4
                         logical name: usb4
                         version: 5.03
                         capabilities: usb-3.10
                         configuration: driver=hub slots=2 speed=10000Mbit/s
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:3000(size=4096) memory:bb000000-bbffffff ioport:90000000(size=301989888)
           *-display
                description: 3D controller
                product: GP108M [GeForce MX250]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:3c:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: irq:197 memory:bb000000-bbffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:3000(size=128)
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.4
             bus info: pci@0000:00:1d.4
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 memory:bc100000-bc1fffff
           *-storage
                description: Non-Volatile memory controller
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:3d:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:bc100000-bc103fff
        *-pci:3
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.6
             bus info: pci@0000:00:1d.6
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:125 memory:bc000000-bc0fffff
           *-storage
                description: Non-Volatile memory controller
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:3e:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msix pciexpress msi nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:18 memory:bc000000-bc003fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: iomemory:600-5ff iomemory:600-5ff irq:196 memory:6023118000-602311bfff memory:6023000000-60230fffff
        *-serial:2
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: iomemory:600-5ff irq:16 memory:6023124000-60231240ff ioport:efa0(size=32)
        *-serial:3 UNCLAIMED
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe010000-fe010fff
     *-pnp00:00
          product: PnP device PNP0c02
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: 2
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 3
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device PNP0c02
          physical id: 4
          capabilities: pnp
          configuration: driver=system
     *-pnp00:04
          product: PnP device PNP0b00
          physical id: 5
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:05
          product: PnP device INT3f0d
          physical id: 6
          capabilities: pnp
          configuration: driver=system
     *-pnp00:06
          product: PnP device PNP0303
          physical id: 7
          capabilities: pnp
          configuration: driver=i8042 kbd
     *-pnp00:07
          product: PnP device DLL0951
          physical id: 8
          capabilities: pnp
          configuration: driver=i8042 aux
     *-pnp00:08
          product: PnP device PNP0c02
          physical id: 9
          capabilities: pnp
          configuration: driver=system
     *-pnp00:09
          product: PnP device PNP0c02
          physical id: a
          capabilities: pnp
          configuration: driver=system
  *-battery
       product: DELL X77XY97
       vendor: LG
       physical id: 1
       version: 07/14/2019
       serial: [REMOVED]
       slot: Sys. Battery Bay
       capacity: 68000mWh
       configuration: voltage=7.6V
  *-power UNCLAIMED
       description: To Be Filled by O.E.M.
       product: To Be Filled by O.E.M.
       vendor: To Be Filled by O.E.M.
       physical id: 2
       version: To Be Filled by O.E.M.
       serial: [REMOVED]
       capacity: 32768mWh
```

---

### Post by oldfred on 2019-11-18
You can add the AHCI drivers into Windows, so both are happy with that.
Windows AHCI instructions
[https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation](https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation) & 
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)
AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)
[https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html](https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html)

---

### Post by jeff-kane1 on 2019-11-20
Thanks everyone for all the tips.  Here is last nights adventure.

Changed the Intel Raid Storage driver to the Microsoft one.
Changed the BIOS to have AHCI instead of RAID.
Booted Windows and it came up.  But, a weird drive D: showed up.
I don't recall exactly everything I did, but was testing some headphones and added some drivers for that in Windows.  Also looked at that D: Drive.  It was bitlocker encrypted.  I did enter the key to try and look at what was on it.  I think it said it was not formatted.  But that makes no sense.  How could it be encrypted and not formatted.  I mention this, because this may have something to do with why the next thing happens.
After another reboot, Windows would not boot anymore.
Left the BIOS to AHCI.
Let the Repair tool reinstall windows.  I thought that letting the BIOS be AHCI during the install may clean things up better.
Windows booted and seemed good to go.
Ubuntu would not boot!  Just the beep and into a memory test.
Tried a few things.  Nothing worked.  Decided to re-install Ubuntu.
Got an error during install just before disk partitioning that no EUFI boot partition could be found!  DOH!
Tried a few more things.  Windows continues to boot, but not Ubuntu.  GRRRR!
I tried to let Recovery fix the boot record, but it kept saying there was nothing wrong with it!
In Windows I removed the Ubuntu partition and expanded the Windows one back to it's original size.
In BIOS I set Storage back to RAID On and turned Secure Boot back on.
I told Recovery to reset Windows back to factory.

Booted into Windows and it worked.
The D: drive was gone again.
The Storage drivers were both the Intel Raid one and the Microsoft one!  Plus 2 others that have been there all along.
I removed the Intel Raid One.  Now I wish I had left it to test what happens when both are there.
Changed BIOS to have Storage be AHCI and turned Secure Boot back off.
Rebooted and Windows still boots OK.
Shrunk the Windows partition down to 100GB.
Rebooted and still OK.
Booted from USB and installed Ubuntu 19.10.
Install went well and was able to boot to Ubuntu.
Boot back to Windows.
Windows wants me to enter the bitlocker key.
Notice that the D: drive is back.  Only have the Microsoft Storage driver and the 2 other ones.
Boot back to Ubuntu.  Works OK.
Boot back to Windows.  Bitlocker wants my key again.  Grrrr.
Go into settings and turn bitlocker off and wait for the drive to decrypt.
Reboot to Windows, and now it comes right up.

I booted back and forth between Ubuntu and Windows trying every combination I could.  Using F12 to pick one, picking one from grub, restarting the O/S vs shutting down the O/S.  Every combination worked.

I now have a dual boot system.  :-)

I can't leave well enough alone!  That D: drive bothers me!  I can't help but think it is the Intel Optane Cache.  Maybe the Intel Raid Storage Driver must be there for it to work.  I plan to try reinstalling that driver and see what happens.  I will need to play with the BIOS switching back and forth between RAID On and AHCI.  I will likely hose either Windows or Ubuntu again doing that.  But I just have to know if using AHCI is disabling the Cache.

In the long run, I will be using Ubuntu most of the time, so I will have to live with AHCI.  But now is the time to find out if D: is the cache before I put many days worth of customization and app installing in.

---

### Post by oldfred on 2019-11-20
Windows hides various partitions, you do not normally see ESP nor recovery partitions unless you mount them.
Post these:

sudo parted -l
sudo fdisk -lu

---

### Post by jeff-kane1 on 2019-11-20
Set the BIOS back to RAID.  Booted to Windows, and the D: Drive went away.  The SATA Driver is back too.  Booted again and turned AHCI back on.  Booted into Windows and the SATA Driver went away and the D: Drive came back. It is almost 32GB, which is the size of the Optane Cache.  It is not a partition.  It is a different drive.

Booted back to Ubuntu.  Yep.  It's a separate drive and is 32GB.

Looks like using ACHI might disable the cache.  Then again, maybe it is working, but ACHI makes it visible.  Sad that Ubuntu doesn't support the RAID On ... yet.  I can always hope it will some day!  :-)

```
parted:

Error: /dev/nvme0n1: unrecognised disk labelModel: H10 HBRPEKNX0202AO NVMe INTEL 32GB (nvme)                          
Disk /dev/nvme0n1: 29.3GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 


fdisk:


Model: H10 HBRPEKNX0202A NVMe INTEL 512GB (nvme)
Disk /dev/nvme1n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Disk /dev/nvme0n1: 27.26 GiB, 29260513280 bytes, 57149440 sectors
Disk model: H10 HBRPEKNX0202AO NVMe INTEL 32GB      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000001


```

---

### Post by oldfred on 2019-11-20
Please use code tags. I also removed loops as they do not matter.

Linux sees that you have two NVMe drives and first is unformatted.

Not seen this with NVMe drives, but with early Windows 8 Microsoft required vendors to speed up Windows boot from HDD, beyond UEFI fast boot and Windows fast start up. Many vendors added a small 16 to 32GB SSD to system for boot cache using Intel RST. As cache only for booting. It was unformatted and only used the amount of RAM. Those with 32GB SSD, often keep Windows cache but made it smaller and installed Ubuntu's / onto SSD so all of Ubuntu was faster. Some with 16GB just made it all / for Ubuntu.

Not sure now if you can format it, if Windows is not using it, but would bet if you turn RAID back on in Windows if then it gets erased. But you could possibly use as / for Ubuntu.

Also Ubiquity wants to install grub to first drive it sees. And if you do not have ESP - efi system partition on first drive it does not install grub and throws errors.
You can then manually install grub to another ESP from live installer.  There is a work around during install to force a different ESP to be target for grub install.
Since your 32GB drive is first, you may get that grub install error.

---

### Post by jeff-kane1 on 2019-11-21
Sorry, I will try to remember to use code tags.

I have not tried to format it.  I was afraid that doing that would somehow break it as a cache.  At one point it was locked with bitlocker.  I unlocked it to see what was on it.  Windows said it was not formatted after that.  Which was weird since I did not think you could put bitlocker on an unformatted drive.  

I did a little research on Intel Optane.  This 2 in 1 has a 512GB SSD.  So, the 32GB Optane is not really doing much!  Earlier Inspiron 7000 models had HHD's and it was helping with them.  I guess they left the Optane in this model even though it only has an SSD.  I guess that means I "could" use it for something, but don't need to since it won't be much faster.

However ... what is frustrating now is that on every other boot, Ubuntu changes the device number between the 512GB SSD and the 32GB Optane.  One time the 512 SSD with the partitions on it is /dev/nvme1n1 and then on the next boot it is /dev/nvme0n1.  This is making setting up a VirtualBox for running the Windows partition a pain.  Each boot of Ubuntu, I have to edit the Windows.vdmk to change the device name.  :-(

---

### Post by oldfred on 2019-11-21
Normally drive enumeration is done by UEFI/BIOS.
Or operating system/grub  when booting see drives in order that UEFI adds them.

While reconfiguring system, you want UEFI fast boot off, as that does not check for new/changed hardware or configuration and immediately starts boot.
My motherboard has a delay on fast start, so I can press a key to get into UEFI or one time boot. I do not think most systems do that.
And if fast boot is on, you need to know how to get to UEFI when needed. Windows has a way, grub has a way, systemD has a way and cold boot not warm reboot usually does a full system check to give time to press a key.

You may want to try turning UEFI fast start up on. Then it should be consistent.

---

### Post by jeff-kane1 on 2019-11-23
Too many issues and it turns out there are things I need Windows for with this 2 in 1 more than Ubuntu.  I gave up on running Windows as the guest and Ubuntu as the host.  I now have Windows as the host and am running Ubuntu in a guest.  I think if I had stuck with it, I my have found a combination of settings that would have worked.  Good luck to the next victim who tries to make a Dell Inspiron 7000 2 in 1 model 7791 work with Ubuntu as the host and Windows as the guest using the same disk with separate partitions.

---

### Post by kimjay on 2019-12-14
> **jeff-kane1 said:**
> Too many issues and it turns out there are things I need Windows for with this 2 in 1 more than Ubuntu.  I gave up on running Windows as the guest and Ubuntu as the host.  I now have Windows as the host and am running Ubuntu in a guest.  I think if I had stuck with it, I my have found a combination of settings that would have worked.  Good luck to the next victim who tries to make a Dell Inspiron 7000 2 in 1 model 7791 work with Ubuntu as the host and Windows as the guest using the same disk with separate partitions.

First, thanks to all for this thread. Helped me out after I bought the same laptop (Dell Inspiron 7591 2 in1), assuming I could probably get Linux dual-booting with Windows on it. That wasn't the case. But after reading this I (think I) have it working. 

Jeff, sorry for my ignorance but I don't know what you mean when you refer to an ubuntu or windows as guest vs. host. For me that evokes a VM. Are you talking about which manages the boot up? So, what I have working might not be what you were trying to do exactly. But here's what I did and did not do. I dinked around and read a lot of articles before finding this one. So, it's not inconceivable that I am forgetting something, but I think this is it:


[LIST]
[*]Disabled Bitlocker and partitioned drive according to this: [https://www.ctrl.blog/entry/dual-boot-bitlocker-device.html](https://www.ctrl.blog/entry/dual-boot-bitlocker-device.html)
[LIST]
[*]I reenabled Bitlocker after I partitioned the drive and my ubuntu install kept hanging.
[/LIST]

[*]Switched Sata mode to AHCI
[*]I turned off Optane Acceleration. I think this is the real key. You mention seeing 2 drives but I do not, though I expected to. I would be nice to use the 32 GB Optane drive as additional storage but neither OS seems to see it. Perhaps that's a feature/limitation of how the motherboard sees it given it's primary function of acceleration in RAID mode.
[*]I again disabled Bitlocker and got the error in this thread's subject.
[*]UPDATED BIOS to 1.3.1 (This was what made it start working and where this thread helped me)
[*]I DID NOT do these things. I'm surprised, but after BIOS update I thought  I'd try it and i worked for me
[LIST]
[*]Edit Grub config to add NOMODESET
[*]Turn off Fast Startup
[*]Disable Safe Boot (I kind of think I should have. I was asked to create a password and I think I failed to enter it on first reboot after install due to confusion over a blue screen that said something like "MDK Configuration" (print was tiny and hard to read). So, Nvidia drivers may not be working. Need to look into that.
[/LIST]

[*]Installed Ubuntu 19.10 from live usb (Again this thread convinced me not to keep trying 18.04 as I had been trying various OS flavors and versions)
[/LIST]

I've barely used either system so far. So, I can't say there are no issues. But so far so good. Machine boots to Grub menu then to Ubuntu or Windows. Touchscreen works in both. 

Curious to know why mine worked, but I strongly suspect it's Dell's BIOS update. Would be curious to hear others' thoughts.
Jay

---

### Post by kimjay on 2019-12-15
I might have been premature in saying that all was well. Indeed the first time I did screw up and miss the input of my password to enable proprietary drivers in MDK management after install with 3rd party software and reboot. So, I don't think Nvidia was working. I decided to just turn off Safe Boot and reinstall Ubuntu. I think the Nvidia graphics are working now, though I'm not 100% sure how to know. But since then a couple of times the system has gotten incredibly slow. The GUI elements like pointer and scrolling seem to start lagging. Last time it froze and I had to hard boot the system. After reboot it's working ok so far. Time will tell, I guess.

I also see one "Unknown" Intel entry under additional drivers that says "device is not working." One of the bullets makes it look like it's the wifi, but wifi is working. So, not sure what to make of that nor if I should be at all concerned.

Jeff-kane1 - What did you mean by enabling Safe Video Mode? Wondering if perhaps I'm seeing similar problems to what you saw.

Also, now I do see the Optane drive in Gparted. I guess it doesn't show up in Nautilus or Windows Explorer because it's unformatted.

---

### Post by oldfred on 2019-12-15
This will show if driver is installed in your kernel(s).
       #What is installed
dkms status

I have old nVidia card (GT620), and nouveau driver seemed to be just as good. But then found that Intel chip was slightly better so now not using nVidia.
So this is what mine shows (nVidia card not even installed now).
```
fred@bionic-z97:~$ dkms status
fred@bionic-z97:~$ 

fred@bionic-z97:~$ lspci -nnk | grep -iA3 vga 
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [1043:8534]
    Kernel driver in use: i915
    Kernel modules: i915



```

---

### Post by gsouf on 2020-01-03
Thanks for sharing all those info, managed to boot on linux from USB key and saved lot of time.

However my dell laptop has no "AHCI" option. And thus we cannot install linux on that laptop. End of the story, asking for a refund and never buy dell again.

I'm not the only one affected: [https://www.dell.com/community/Inspiron/Not-able-to-set-SATA-operation-to-AHCI-in-BIOS-Inspiron-7490/td-p/7393794](https://www.dell.com/community/Inspiron/Not-able-to-set-SATA-operation-to-AHCI-in-BIOS-Inspiron-7490/td-p/7393794)
Dell just doesn't give a **** about linux. All they do on that computer is windows driven.

Conclusion: DONT buy dell if you want to install linux. You'll waste your time and your money.

---

### Post by oldfred on 2020-01-03
This 7791  user commented that he was able to change to AHCI. But needed some other boot parameters also.
[https://askubuntu.com/questions/1182270/ubuntu-startup-stuck-on-black-screen-with-dev-nvme0n1p2-clean](https://askubuntu.com/questions/1182270/ubuntu-startup-stuck-on-black-screen-with-dev-nvme0n1p2-clean)

Did you update UEFI to latest from Dell. They often release drivers -see sputnik, but then they may not be included in Linux unless a version or two later.

---

### Post by kimjay on 2020-01-06
Hi gsouf,

Sorry to hear that it's not working for. As oldfred said, did you update the BIOS? I have the 7591, which I think is just the 15" version of what you have. And I'm happily running Ubuntu 19.10 dual-booted with Win10. It works near flawlessly, touchscreen and all.

Before I got it to work, I updated the BIOS through the Dell app in Windows. Bios were 1.0 or 1.1 when I got the laptop and nothing worked. After updating the BIOS I was on version 1.3.1 and from there it was smooth sailing. Maybe the AHCI option will show up after you update the BIOS. What is your current BIOS version?

To install Ubuntu, you also probably need to disable Optane acceleration; I believe this based upon my experience. Did you try that? I also disabled bitlocker encryption but I'm not sure if that's necessary or not.

Dell seems to have broader support for linux than any other Windows OEM I know of. Short of using a dedicated linux laptop, like System76, who would you recommend for running Linux?

Best,
kimjay

> **gsouf said:**
> Thanks for sharing all those info, managed to boot on linux from USB key and saved lot of time.

However my dell laptop has no "AHCI" option. And thus we cannot install linux on that laptop. End of the story, asking for a refund and never buy dell again.

I'm not the only one affected: [https://www.dell.com/community/Inspiron/Not-able-to-set-SATA-operation-to-AHCI-in-BIOS-Inspiron-7490/td-p/7393794](https://www.dell.com/community/Inspiron/Not-able-to-set-SATA-operation-to-AHCI-in-BIOS-Inspiron-7490/td-p/7393794)
Dell just doesn't give a **** about linux. All they do on that computer is windows driven.

Conclusion: DONT buy dell if you want to install linux. You'll waste your time and your money.

---

### Post by kimjay on 2020-01-06
Thanks oldfred,

dkms status does show that Nvidia is installed. How do I know what the system is using? 

My system has the Nvidia MX250. According to userbenchmark the Nvidia card crushes the Intel integrated graphics, but I don't know how to verify this on my system. [https://gpu.userbenchmark.com/Compare/Nvidia-GeForce-MX250-vs-Intel-UHD-Graphics-620-Mobile-Kaby-Lake-R/m762458vsm320744](https://gpu.userbenchmark.com/Compare/Nvidia-GeForce-MX250-vs-Intel-UHD-Graphics-620-Mobile-Kaby-Lake-R/m762458vsm320744) Not sure if my system shows that difference nor if I need it.

4k streaming in Chrome doesnt' work well. It's very choppy and sometimes freezes altogether. Not sure if that could be a GPU issue. In reality I don't need 4k. The 1080p stream looks great for most everything.

---

### Post by gsouf on 2020-01-07
Thanks for your answers, I confirm that I upgraded UEFI and I cannot get the AHCI option.

Kimjay, that's weird indeed because your model is very similar to mine, probably they have used different motherboard.
I sent it back for a refund because anyway it was also getting weird issue (laptop not powering up sometimes for a few hours for no obvious reasons). I will maybe stick to Asus that has worked very well with linux for me. I also used MSI in the past that was also perfect for linux. I'll also check system76 I didn't know this one!

---

### Post by kimjay on 2020-01-08
gsouf, Maybe you're right about the motherboard. Clearly something was different. Too bad it didn't work for you. Good luck finding something.

---

### Post by kimjay on 2020-01-18
Update: Sadly 3 days after the return period ended for this laptop I discovered that audio input is not working properly. I can sort of get it to work plugging in a headset, but it's scratchy sounding. And the built-in microphone isn't detected at all. I suspect it's this issue below. Mentioning this here n case anyone comes here trying to get Ubuntu to work on this machine. Everything else seems to be working ok. Hopefully the audio issue will be fixed.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1840725](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1840725)

---

