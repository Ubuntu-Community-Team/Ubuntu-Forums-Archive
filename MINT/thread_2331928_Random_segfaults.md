---
title: "Random segfaults"
date: 2016-07-26
forum: MINT
---

### Post by Ghjnut on 2016-07-26
Hey everyone. I seem to keep getting random segfaults and I'm pretty sure the graphics card is the culprit but I'm not sure how to troubleshoot any further. This has been happening for 2 to 3 years and doesn't seem exclusive to Ubuntu (I dual-boot windows and occasionally get blue screens). The faults only result in the application terminating and requiring a restart. I've seen it across Steam, Dota2, Chrome, and the window manager which all would seem to have graphics utilization. I'm just looking to have a bit more of a smoking gun before purchasing a new graphics card. Any help is appreciated! Here's a sample of kern.log outputs from different crashes:

```

Jun 28 02:11:20 derek kernel: [ 1937.712655] chrome[2913]: segfault at 0 ip           (null) sp 00007ffc1c06b388 error 14
Jun 28 02:11:20 derek kernel: [ 1937.985832] chrome[22579]: segfault at 0 ip           (null) sp 00007ffe1607b7e8 error 14
Jun 28 02:11:20 derek kernel: [ 1938.288703] chrome[22588]: segfault at 0 ip           (null) sp 00007fff02b1de28 error 14
Jun 28 16:09:08 derek kernel: [52176.564842] chrome[7631]: segfault at 29b41c100008 ip 00007f731c4f3564 sp 00007ffcdce74480 error 4 in chrome[7f7319b3c000+5d99000]
Jun 28 17:22:15 derek kernel: [56560.881114] chrome[2827]: segfault at 400008 ip 00007f33aec36748 sp 00007ffeed206310 error 6 in chrome[7f33ad7f8000+5d99000]
Jun 28 20:12:40 derek kernel: [66780.706171] chrome[5421]: segfault at 0 ip           (null) sp 00007ffc466eb8d8 error 14
Jun 28 20:12:41 derek kernel: [66780.971843] chrome[5517]: segfault at 0 ip           (null) sp 00007fff21fd6d58 error 14
Jun 28 20:12:41 derek kernel: [66781.287519] chrome[5565]: segfault at 0 ip           (null) sp 00007ffe55c6be28 error 14
Jun 29 18:06:49 derek kernel: [ 2421.523893] dota2[12238]: segfault at 0 ip 00007f84257905d1 sp 00007fff26bf6c30 error 6 in libtier0.so[7f8425760000+64000]
Jun 29 18:06:55 derek kernel: [ 2427.538359] dota2[12319]: segfault at 0 ip 00007f3fc0e655d1 sp 00007fffb0ff02e0 error 6 in libtier0.so[7f3fc0e35000+64000]
Jun 29 18:07:06 derek kernel: [ 2437.668433] dota2[12370]: segfault at 0 ip 00007f6e0d5605d1 sp 00007ffc5b4d7de0 error 6 in libtier0.so[7f6e0d530000+64000]
Jun 29 18:07:26 derek kernel: [ 2458.134652] dota2[12677]: segfault at 0 ip 00007f1a431835d1 sp 00007ffedc0b5470 error 6 in libtier0.so[7f1a43153000+64000]
Jun 29 18:07:34 derek kernel: [ 2465.650657] dota2[12758]: segfault at 0 ip 00007f84744a95d1 sp 00007ffc4e7f71e0 error 6 in libtier0.so[7f8474479000+64000]
Jun 29 18:07:39 derek kernel: [ 2471.114900] dota2[12838]: segfault at 0 ip 00007f79368645d1 sp 00007ffec5925d20 error 6 in libtier0.so[7f7936834000+64000]
Jul  1 01:29:36 derek kernel: [115322.536804] dota2[19847]: segfault at 0 ip 00007f8df7c5b5d1 sp 00007ffc932ac590 error 6 in libtier0.so[7f8df7c2b000+64000]
Jul  4 17:56:40 derek kernel: [433562.100764] chrome[29694]: segfault at fffffffc02285cbf ip 00007fbaf44f94f0 sp 00007ffc5c9732b0 error 5 in chrome[7fbaf3719000+5d99000]
Jul  5 08:41:52 derek kernel: [486643.899341] chrome[23560]: segfault at 400008 ip 00007f14ca173748 sp 00007fff6333e390 error 6 in chrome[7f14c8d35000+5d99000]
Jul  7 18:11:35 derek kernel: [693506.937229] chrome[13768]: segfault at 400008 ip 00007f14a070e748 sp 00007ffc01ab0470 error 6 in chrome[7f149f2d0000+5d99000]
Jul  8 00:34:50 derek kernel: [  170.434150] chrome[3250]: segfault at c ip 00000fa5021cb7a8 sp 00007ffdd4250d70 error 4
Jul  8 00:46:59 derek kernel: [  899.143974] Chrome_ChildIOT[5489]: segfault at 2de9a4f2 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:12 derek kernel: [  912.268485] Chrome_ChildIOT[5508]: segfault at 2de9a402 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:21 derek kernel: [  921.169348] Chrome_ChildIOT[3220]: segfault at ca409302 ip 00007f155ba9c3f3 sp 00007f154a629858 error 6 in chrome[7f1559e16000+5d99000]
Jul  8 00:47:21 derek kernel: [  921.378915] Chrome_ChildIOT[5522]: segfault at 4adcbaf2 ip 00007fed4f0653f3 sp 00007fed3dbf2858 error 6 in chrome[7fed4d3df000+5d99000]
Jul  8 00:47:21 derek kernel: [  921.933838] Chrome_ChildIOT[5527]: segfault at 2de99502 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:24 derek kernel: [  924.647821] Chrome_ChildIOT[5532]: segfault at 2de994f2 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:28 derek kernel: [  928.640206] Chrome_ChildIOT[5537]: segfault at 2de9a472 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:31 derek kernel: [  931.295348] Chrome_ChildIOT[5542]: segfault at 2de9a472 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:31 derek kernel: [  931.608857] Chrome_ChildIOT[5547]: segfault at 2de9a472 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:31 derek kernel: [  931.820342] Chrome_ChildIOT[5552]: segfault at 2de9a472 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:32 derek kernel: [  931.988665] Chrome_ChildIOT[5554]: segfault at 2de9a472 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:32 derek kernel: [  932.142594] Chrome_ChildIOT[5560]: segfault at 2de9a472 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:32 derek kernel: [  932.285148] Chrome_ChildIOT[5565]: segfault at 2de9a402 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:32 derek kernel: [  932.429273] Chrome_ChildIOT[5567]: segfault at 2de9a472 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:32 derek kernel: [  932.558503] Chrome_ChildIOT[5569]: segfault at 2de9a472 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:32 derek kernel: [  932.701409] Chrome_ChildIOT[5574]: segfault at 2de9a472 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:43 derek kernel: [  943.165068] Chrome_ChildIOT[5625]: segfault at 2de99502 ip 00007f44d4f713f3 sp 00007f44c471b858 error 6 in chrome[7f44d32eb000+5d99000]
Jul  8 00:47:50 derek kernel: [  950.388956] Chrome_ChildIOT[5764]: segfault at ac033e82 ip 00007f1cfd6f93f3 sp 00007f1cecea3858 error 6 in chrome[7f1cfba73000+5d99000]
Jul  8 00:47:50 derek kernel: [  950.416633] Chrome_ChildIOT[5765]: segfault at ac033e82 ip 00007f1cfd6f93f3 sp 00007f1cecea3858 error 6 in chrome[7f1cfba73000+5d99000]
Jul  8 00:47:50 derek kernel: [  950.427941] Chrome_ChildIOT[5771]: segfault at ac033e82 ip 00007f1cfd6f93f3 sp 00007f1cecea3858 error 6 in chrome[7f1cfba73000+5d99000]
Jul  8 00:47:50 derek kernel: [  950.427989] Chrome_ChildIOT[5775]: segfault at ac033e82 ip 00007f1cfd6f93f3 sp 00007f1cecea3858 error 6 in chrome[7f1cfba73000+5d99000]
Jul  8 00:47:50 derek kernel: [  950.431385] Chrome_ChildIOT[5782]: segfault at ac033e82 ip 00007f1cfd6f93f3 sp 00007f1cecea3858 error 6 in chrome[7f1cfba73000+5d99000]
Jul  8 00:47:50 derek kernel: [  950.432915] Chrome_ChildIOT[5780]: segfault at ac033e82 ip 00007f1cfd6f93f3 sp 00007f1cecea3858 error 6 in chrome[7f1cfba73000+5d99000]
Jul  8 00:47:50 derek kernel: [  950.433615] Chrome_ChildIOT[5784]: segfault at ac033e82 ip 00007f1cfd6f93f3 sp 00007f1cecea3858 error 6 in chrome[7f1cfba73000+5d99000]
Jul  8 00:47:50 derek kernel: [  950.434302] Chrome_ChildIOT[5773]: segfault at ac033e82 ip 00007f1cfd6f93f3 sp 00007f1cecea3858 error 6 in chrome[7f1cfba73000+5d99000]
Jul  8 00:47:50 derek kernel: [  950.436530] Chrome_ChildIOT[5777]: segfault at ac033e82 ip 00007f1cfd6f93f3 sp 00007f1cecea3858 error 6 in chrome[7f1cfba73000+5d99000]
Jul 10 23:45:43 derek kernel: [166618.410277] Chrome_IOThread[3013]: segfault at 39 ip 00007f945dc4b200 sp 00007f94490486e8 error 6 in chrome[7f945ccf5000+5d99000]
Jul 11 19:32:30 derek kernel: [237783.898998] dota2[17437]: segfault at 0 ip           (null) sp 00007ffecacd1358 error 14
Jul 14 17:26:03 derek kernel: [56944.490511] chrome[13638]: segfault at 2500000000 ip 000009d29fcf17fd sp 00007ffd38642a70 error 6
Jul 17 00:13:50 derek kernel: [ 4017.514369] chrome[3103]: segfault at f7e00008 ip 00007f6b7b831f4e sp 00007ffd8041e440 error 4 in chrome[7f6b78e95000+5d99000]
Jul 17 02:04:38 derek kernel: [10661.329946] dota2[8503]: segfault at 1001f ip 00007fe8d809a03a sp 00007fff3857c520 error 4 in libscaleformui_4_vulkan.so[7fe8d7db6000+b0a000]
Jul 17 09:20:31 derek kernel: [18954.140113] chrome[2857]: segfault at 4 ip 00007f208ea396f0 sp 00007ffdb9ae8800 error 4 in chrome[7f208cab4000+5d99000]
Jul 17 15:08:14 derek kernel: [39805.528246] chrome[12316]: segfault at 331f9490424c ip 00007fb55ee38404 sp 00007fff39d379b0 error 4 in chrome[7fb55c49c000+5d99000]
Jul 18 00:45:13 derek kernel: [  482.396679] chrome[3123]: segfault at 0 ip           (null) sp 00007ffc32e3c48f error 14
Jul 18 00:45:15 derek kernel: [  484.167254] chrome[5691]: segfault at 0 ip           (null) sp 00007ffc32e3c48f error 14
Jul 18 00:45:17 derek kernel: [  485.955740] chrome[5700]: segfault at 0 ip           (null) sp 00007ffc32e3c48f error 14
Jul 18 00:45:18 derek kernel: [  487.433481] chrome[5709]: segfault at 0 ip           (null) sp 00007ffc32e3c48f error 14
Jul 18 00:45:28 derek kernel: [  496.681828] chrome[5718]: segfault at 0 ip           (null) sp 00007ffc32e3c48f error 14
Jul 18 00:45:28 derek kernel: [  497.278088] chrome[5727]: segfault at 0 ip           (null) sp 00007ffc32e3c48f error 14
Jul 18 19:14:10 derek kernel: [66409.816857] chrome[3283]: segfault at 15615a04368 ip 00007f8600e89795 sp 00007ffe6e9462e0 error 4 in chrome[7f85fe4f7000+5d99000]
Jul 19 08:49:07 derek kernel: [25813.964733] chrome[3134]: segfault at 400008 ip 00007fd67345041e sp 00007ffd9816f3a0 error 4 in chrome[7fd6724e6000+5d99000]
Jul 23 01:39:52 derek kernel: [92102.531490] GlobPool0[31110]: segfault at 48 ip 00007fdb0c70dae4 sp 00007fdb16564fb0 error 4 in libnvidia-glcore.so.367.35[7fdb0b3b0000+1397000]
Jul 25 23:52:47 derek kernel: [ 9824.684258] Compositor[3329]: segfault at 1044 ip 00007f2062aa9046 sp 00007f2051bd2280 error 4 in chrome[7f2060fa7000+5d99000]

```

---

### Post by T.J. on 2016-07-26
[QUOTE=Ghjnut;13523030]Hey everyone. I seem to keep getting random segfaults and I'm pretty sure the graphics card is the culprit but I'm not sure how to troubleshoot any further. This has been happening for 2 to 3 years and doesn't seem exclusive to Ubuntu (I dual-boot windows and occasionally get blue screens). The faults only result in the application terminating and requiring a restart. I've seen it across Steam, Dota2, Chrome, and the window manager which all would seem to have graphics utilization. I'm just looking to have a bit more of a smoking gun before purchasing a new graphics card. Any help is appreciated! Here's a sample of kern.log outputs from different crashes:

Could be a bad RAM bank.  I wouldn't blame the video card just yet.  Have you run a memory test?

---

### Post by DuckHook on 2016-07-26
> **Ghjnut said:**
> …This has been happening for 2 to 3 years…well, I must say that you have certainly been patient. Constant segfaults would have driven me nuts long before now. I would not automatically point the finger at the video card, although it is a likely culprit, especially given…> …doesn't seem exclusive to Ubuntu (I dual-boot windows and occasionally get blue screens).I agree that this points to HW.

We appreciate your kern.log and this shows that you've done a lot of homework already. But when suspecting HW issues, it is important to post info on your HW. The link in my sig: ***How to Ask for Help*** contains instructions about what apps query HW and what output to post on a support thread. To shortcut that process, please post output of:```
sudo lshw -sanitize
``````
lspci -vk | grep -iA15 vga
``````
cat /var/log/syslog | egrep -i 'error|warn|fault|fatal|fail'
```Also, post your entire apport logs which can be found under /var/log/

The next time an app crashes with such segfault, also look under /var/crash
Post anything that is in there back to this thread. You must also let us know what flavour and version you are running. Do:```
uname -a
``````
lsb_release -a
```…and what you've done to your system, like installing any proprietary drivers (vs default open source). The lspci query above will show what drivers you are using for video. Have you installed apps from outside the repos? What, if any, PPAs?

---

### Post by Ghjnut on 2016-07-27
Sorry, I seem to be getting an error posting all my outputs
```
Your submission could not be processed because a security token was missing.
```

---

### Post by Ghjnut on 2016-07-27
Okay, time to eat crow. I'm actually running Mint 17.3 but I figured it's derived from Ubuntu Trusty and the larger ecosystem would yield better results. Any way, I understand if that puts me in the dog house and you have to turn me away. Here's the logs you asked for and I really appreciate it if you do end up taking the time to offer a hand.


```

ghjnut@derek ~/projects $ sudo lshw -sanitize[sudo] password for ghjnut:
computer
    description: Desktop Computer
    product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Z77 Extreme3
       vendor: ASRock
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.40
          date: 01/16/2013
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cache:0
          description: L2 cache
          physical id: c
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-through unified
     *-cache:1
          description: L1 cache
          physical id: d
          slot: CPU Internal L1
          size: 256KiB
          capacity: 256KiB
          capabilities: internal write-through data
     *-cache:2
          description: L3 cache
          physical id: e
          slot: CPU Internal L3
          size: 6MiB
          capacity: 6MiB
          capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 1600 CL9 Series
             vendor: 8502
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [REMOVED]
             slot: ChannelA-DIMM1
        *-bank:2
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 1600 CL9 Series
             vendor: 8502
             physical id: 2
             serial: [REMOVED]
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [REMOVED]
             slot: ChannelB-DIMM1
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 10
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz
          slot: CPUSocket
          size: 2866MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e0000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GK106 [GeForce GTX 660]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:47 memory:f6000000-f6ffffff memory:e0000000-e7ffffff memory:e8000000-e9ffffff ioport:e000(size=128) memory:f7000000-f707ffff
           *-multimedia
                description: Audio device
                product: GK106 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7080000-f7083fff
        *-display
             description: Display controller
             product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=i915 latency=0
             resources: irq:44 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:41 memory:f7800000-f780ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:45 memory:f781a000-f781a00f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7818000-f78183ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:f7810000-f7813fff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) ioport:ea100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 06
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:42 ioport:d000(size=256) memory:ea104000-ea104fff memory:ea100000-ea103fff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
           *-pci
                description: PCI bridge
                product: ASM1083/1085 PCIe to PCI Bridge
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pci subtractive_decode bus_master cap_list
                resources: iomemory:202001f10-202001f0f
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7817000-f78173ff
        *-isa
             description: ISA bridge
             product: Z77 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7816000-f78167ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7815000-f78150ff ioport:f040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 850
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2B6Q
             serial: [REMOVED]
             size: 476GiB (512GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=77f48a7e-1e38-40b5-84e2-725eed12282a sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: [REMOVED]
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                logical name: /var/lib/docker/aufs
                version: 1.0
                serial: [REMOVED]
                size: 302GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-11-11 00:02:06 filesystem=ext4 lastmountpoint=/ modified=2016-07-26 01:23:57 mount.fstype=ext4 mount.options=rw,noatime,errors=remount-ro,data=ordered mounted=2016-07-26 01:23:57 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: [REMOVED]
                size: 15GiB
                capacity: 15GiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:3
                description: reserved partition
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                serial: [REMOVED]
                capacity: 127MiB
                capabilities: nofs precious readonly hidden nomount
                configuration: name=Microsoft reserved partition
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: [REMOVED]
                size: 157GiB
                capacity: 157GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2015-11-11 09:02:25 filesystem=ntfs name=Basic data partition state=clean
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SanDisk SDSSDHII
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 10RL
             serial: [REMOVED]
             size: 894GiB (960GB)
             configuration: ansiversion=5 sectorsize=512
     *-scsi:2
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: iHAS124   W
             vendor: ATAPI
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: HL03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

```


```

ghjnut@derek ~/projects/reference $ uname -a
Linux derek.jaked.in 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```


```

ghjnut@derek ~/projects/reference $ lsb_release -a
No LSB modules are available.
Distributor ID: LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:        17.3
Codename:       rosa

```






Here are my deb sources. Probably more than I should have but I guess it's all kind of built up over the years
```

ghjnut@derek ~/projects/reference $ cat /etc/apt/sources.list.d/*
# mouse drivers
deb http://ppa.launchpad.net/berfenger/roccat/ubuntu trusty main
deb-src http://ppa.launchpad.net/berfenger/roccat/ubuntu trusty main


# chrome remote desktop
deb [arch=amd64] http://dl.google.com/linux/chrome-remote-desktop/deb/ stable main


# deluge torrent
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu trusty main


# docker
deb https://apt.dockerproject.org/repo ubuntu-trusty main


# gnome 3
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu trusty main
deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu trusty main


# chrome
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


# graphics drivers?
deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu trusty main


#neovim
deb http://ppa.launchpad.net/neovim-ppa/unstable/ubuntu trusty main
deb-src http://ppa.launchpad.net/neovim-ppa/unstable/ubuntu trusty main


deb http://packages.linuxmint.com rosa main upstream import
deb http://extra.linuxmint.com rosa main
deb http://archive.ubuntu.com/ubuntu trusty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ trusty partner


# spotify
deb http://repository.spotify.com stable non-free


# steam
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam


# ubuntu-wine
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main


# java
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main


# wine
deb http://ppa.launchpad.net/wine/wine-builds/ubuntu trusty main
deb-src http://ppa.launchpad.net/wine/wine-builds/ubuntu trusty main

```


Again, I completely understand if there's nothing you can do for me, at the very least I appreciate some of the informative commands I wasn't aware of. Also, for some reason I get security token issues when trying to paste the logs in this response.

---

### Post by Ghjnut on 2016-07-27
Here's the logs
```

ghjnut@derek ~/projects/reference $ cat /var/log/syslog | egrep -i 'error|warn|fault|fatal|fail' && zgrep -i 'error\|warn\|fault\|fatal\|fail' /var/log/syslog.[2-7].gz
Jul 26 18:03:44 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
Jul 26 18:41:38 derek kernel: [62226.485458] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:38 derek kernel: [62226.485460] Buffer I/O error on device sr0, logical block 0
Jul 26 18:41:38 derek kernel: [62226.485461] Buffer I/O error on device sr0, logical block 1
Jul 26 18:41:38 derek kernel: [62226.485462] Buffer I/O error on device sr0, logical block 2
Jul 26 18:41:38 derek kernel: [62226.485463] Buffer I/O error on device sr0, logical block 3
Jul 26 18:41:38 derek kernel: [62226.485464] Buffer I/O error on device sr0, logical block 4
Jul 26 18:41:38 derek kernel: [62226.485465] Buffer I/O error on device sr0, logical block 5
Jul 26 18:41:38 derek kernel: [62226.485466] Buffer I/O error on device sr0, logical block 6
Jul 26 18:41:38 derek kernel: [62226.485467] Buffer I/O error on device sr0, logical block 7
Jul 26 18:41:38 derek kernel: [62226.485469] Buffer I/O error on device sr0, logical block 8
Jul 26 18:41:38 derek kernel: [62226.485470] Buffer I/O error on device sr0, logical block 9
Jul 26 18:41:38 derek kernel: [62226.637161] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:38 derek kernel: [62226.729319] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:38 derek kernel: [62226.789289] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:38 derek kernel: [62226.845252] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:39 derek kernel: [62227.297023] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:39 derek kernel: [62227.352985] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:39 derek kernel: [62227.408939] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:39 derek kernel: [62227.460899] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:39 derek kernel: [62227.520860] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:44 derek kernel: [62232.210141] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:44 derek kernel: [62232.210143] quiet_error: 598 callbacks suppressed
Jul 26 18:41:44 derek kernel: [62232.210144] Buffer I/O error on device sr0, logical block 0
Jul 26 18:41:44 derek kernel: [62232.210146] Buffer I/O error on device sr0, logical block 1
Jul 26 18:41:44 derek kernel: [62232.210146] Buffer I/O error on device sr0, logical block 2
Jul 26 18:41:44 derek kernel: [62232.210147] Buffer I/O error on device sr0, logical block 3
Jul 26 18:41:44 derek kernel: [62232.210148] Buffer I/O error on device sr0, logical block 4
Jul 26 18:41:44 derek kernel: [62232.210149] Buffer I/O error on device sr0, logical block 5
Jul 26 18:41:44 derek kernel: [62232.210150] Buffer I/O error on device sr0, logical block 6
Jul 26 18:41:44 derek kernel: [62232.210151] Buffer I/O error on device sr0, logical block 7
Jul 26 18:41:44 derek kernel: [62232.210154] Buffer I/O error on device sr0, logical block 8
Jul 26 18:41:44 derek kernel: [62232.210154] Buffer I/O error on device sr0, logical block 9
Jul 26 18:41:45 derek kernel: [62233.989116] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:48 derek kernel: [62236.399717] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:52 derek kernel: [62240.545312] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:52 derek kernel: [62240.545314] quiet_error: 86 callbacks suppressed
Jul 26 18:41:52 derek kernel: [62240.545315] Buffer I/O error on device sr0, logical block 0
Jul 26 18:41:52 derek kernel: [62240.545316] Buffer I/O error on device sr0, logical block 1
Jul 26 18:41:52 derek kernel: [62240.545317] Buffer I/O error on device sr0, logical block 2
Jul 26 18:41:52 derek kernel: [62240.545318] Buffer I/O error on device sr0, logical block 3
Jul 26 18:41:52 derek kernel: [62240.545319] Buffer I/O error on device sr0, logical block 4
Jul 26 18:41:52 derek kernel: [62240.545320] Buffer I/O error on device sr0, logical block 5
Jul 26 18:41:52 derek kernel: [62240.545321] Buffer I/O error on device sr0, logical block 6
Jul 26 18:41:52 derek kernel: [62240.545322] Buffer I/O error on device sr0, logical block 7
Jul 26 18:41:52 derek kernel: [62240.545324] Buffer I/O error on device sr0, logical block 8
Jul 26 18:41:52 derek kernel: [62240.545325] Buffer I/O error on device sr0, logical block 9
Jul 26 18:41:58 derek kernel: [62246.645787] end_request: I/O error, dev sr0, sector 0
Jul 26 18:41:58 derek kernel: [62246.645789] quiet_error: 22 callbacks suppressed
Jul 26 18:41:58 derek kernel: [62246.645790] Buffer I/O error on device sr0, logical block 0
Jul 26 18:41:58 derek kernel: [62246.645793] Buffer I/O error on device sr0, logical block 1
Jul 26 18:41:58 derek kernel: [62246.645794] Buffer I/O error on device sr0, logical block 2
Jul 26 18:41:58 derek kernel: [62246.645794] Buffer I/O error on device sr0, logical block 3
Jul 26 18:41:58 derek kernel: [62246.645795] Buffer I/O error on device sr0, logical block 4
Jul 26 18:41:58 derek kernel: [62246.645796] Buffer I/O error on device sr0, logical block 5
Jul 26 18:41:58 derek kernel: [62246.645797] Buffer I/O error on device sr0, logical block 6
Jul 26 18:41:58 derek kernel: [62246.645798] Buffer I/O error on device sr0, logical block 7
Jul 26 18:41:58 derek kernel: [62246.645802] Buffer I/O error on device sr0, logical block 8
Jul 26 18:41:58 derek kernel: [62246.645802] Buffer I/O error on device sr0, logical block 9
Jul 26 18:41:59 derek kernel: [62247.777131] end_request: I/O error, dev sr0, sector 0
Jul 26 18:42:01 derek kernel: [62249.108376] end_request: I/O error, dev sr0, sector 0
Jul 26 18:42:02 derek kernel: [62250.183736] end_request: I/O error, dev sr0, sector 0
Jul 26 18:42:02 derek kernel: [62250.599486] end_request: I/O error, dev sr0, sector 0
Jul 26 20:36:24 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
/var/log/syslog.2.gz:Jul 24 13:36:46 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
/var/log/syslog.4.gz:Jul 22 01:13:02 derek kernel: [ 4143.014657] systemd-hostnamed[13796]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
/var/log/syslog.4.gz:Jul 22 20:21:58 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
/var/log/syslog.4.gz:Jul 22 23:22:54 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
/var/log/syslog.4.gz:Jul 23 01:39:52 derek kernel: [92102.531490] GlobPool0[31110]: segfault at 48 ip 00007fdb0c70dae4 sp 00007fdb16564fb0 error 4 in libnvidia-glcore.so.367.35[7fdb0b3b0000+1397000]
/var/log/syslog.4.gz:Jul 23 02:06:36 derek kernel: [93705.014743] systemd-hostnamed[32191]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
/var/log/syslog.4.gz:Jul 23 03:49:26 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
/var/log/syslog.5.gz:Jul 21 04:03:30 derek kernel: [  672.148003] ata1.00: failed command: SEND FPDMA QUEUED
/var/log/syslog.5.gz:Jul 21 04:03:30 derek kernel: [  672.148015] ata1.00: failed command: WRITE FPDMA QUEUED
/var/log/syslog.5.gz:Jul 21 04:03:30 derek kernel: [  672.148025] ata1.00: failed command: WRITE FPDMA QUEUED
/var/log/syslog.5.gz:Jul 21 04:03:30 derek kernel: [  672.148034] ata1.00: failed command: WRITE FPDMA QUEUED
/var/log/syslog.5.gz:Jul 21 04:03:30 derek kernel: [  672.148043] ata1.00: failed command: WRITE FPDMA QUEUED
/var/log/syslog.5.gz:Jul 21 04:03:30 derek kernel: [  672.148052] ata1.00: failed command: WRITE FPDMA QUEUED
/var/log/syslog.5.gz:Jul 21 04:03:30 derek kernel: [  672.148061] ata1.00: failed command: WRITE FPDMA QUEUED
/var/log/syslog.5.gz:Jul 21 04:03:31 derek kernel: [  672.470809] end_request: I/O error, dev sda, sector 280705520
/var/log/syslog.5.gz:Jul 21 18:29:43 derek mdm[1486]: WARNING: Couldn't authenticate user
/var/log/syslog.5.gz:Jul 21 18:29:48 derek mdm[1486]: GLib-CRITICAL: g_key_file_get_string: assertion 'key_file != NULL' failed
/var/log/syslog.5.gz:Jul 21 18:29:48 derek mdm[1486]: GLib-CRITICAL: g_key_file_free: assertion 'key_file != NULL' failed
/var/log/syslog.5.gz:Jul 21 18:29:51 derek pulseaudio[3539]: [pulseaudio] sink.c: Default and alternate sample rates are the same.
/var/log/syslog.5.gz:Jul 21 20:11:20 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
/var/log/syslog.5.gz:Jul 21 20:59:35 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
/var/log/syslog.5.gz:Jul 21 21:03:55 derek cinnamon-session[3310]: WARNING: t+9245.78658s: Playing logout sound '/usr/share/mint-artwork-cinnamon/sounds/logout.ogg'
/var/log/syslog.5.gz:Jul 21 21:03:55 derek cinnamon-session[3310]: WARNING: t+9245.89155s: Finished playing logout sound
/var/log/syslog.5.gz:Jul 21 21:03:55 derek cinnamon-session[3310]: WARNING: t+9245.89159s: Resuming logout sequence...
/var/log/syslog.5.gz:Jul 21 21:03:56 derek cinnamon-session[3310]: WARNING: t+9246.83987s: Requesting system restart...
/var/log/syslog.5.gz:Jul 21 21:03:56 derek cinnamon-session[3310]: WARNING: t+9246.84068s: Attempting to restart using consolekit...
/var/log/syslog.5.gz:Jul 21 21:03:56 derek cinnamon-session[3310]: WARNING: t+9246.85043s: Requesting system restart...
/var/log/syslog.5.gz:Jul 21 21:03:56 derek cinnamon-session[3310]: WARNING: t+9246.85071s: Attempting to restart using consolekit...
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    0.000000] MTRR default type: uncachable
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    0.000026] pid_max: default: 32768 minimum: 301
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    0.156841] NetLabel:  unlabeled traffic allowed by default
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    0.211018] PCI: CLS 64 bytes, default 64
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    0.520526] io scheduler deadline registered (default)
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    1.471886] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    1.471894] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    1.471896] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    1.471899] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    1.471900] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    1.471902] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    1.471904] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    1.486140] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    1.581669] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
/var/log/syslog.5.gz:Jul 21 21:56:18 derek kernel: [    1.838378] init: failsafe main process (776) killed by TERM signal
/var/log/syslog.5.gz:Jul 21 21:56:18 derek NetworkManager[995]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.5.gz:Jul 21 21:56:18 derek NetworkManager[995]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/eth0
/var/log/syslog.5.gz:Jul 21 21:56:18 derek NetworkManager[995]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
/var/log/syslog.5.gz:Jul 21 21:56:18 derek NetworkManager[995]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
/var/log/syslog.5.gz:Jul 21 21:56:18 derek nvidia-persistenced: Failed to open PID file: File exists
/var/log/syslog.5.gz:Jul 21 21:56:18 derek mdm[1480]: WARNING: Plymouth is running, asking it to stop...
/var/log/syslog.5.gz:Jul 21 21:56:18 derek mdm[1480]: WARNING: Plymouth stopped
/var/log/syslog.5.gz:Jul 21 21:56:20 derek ModemManager[899]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0': not supported by any plugin
/var/log/syslog.5.gz:Jul 21 21:56:22 derek NetworkManager[995]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
/var/log/syslog.5.gz:Jul 21 21:56:22 derek NetworkManager[995]: <warn> dnsmasq not available on the bus, can't update servers.
/var/log/syslog.5.gz:Jul 21 21:56:22 derek NetworkManager[995]: <error> [1469159782.332739] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog.5.gz:Jul 21 21:56:22 derek NetworkManager[995]: <warn> DNS: plugin dnsmasq update failed
/var/log/syslog.5.gz:Jul 21 21:56:22 derek dnsmasq[1773]: warning: no upstream servers configured
/var/log/syslog.5.gz:Jul 21 21:56:22 derek NetworkManager[995]: <warn> dnsmasq appeared on DBus: :1.13
/var/log/syslog.5.gz:Jul 21 21:56:23 derek mdm[1480]: GLib-CRITICAL: g_key_file_get_string: assertion 'key_file != NULL' failed
/var/log/syslog.5.gz:Jul 21 21:56:23 derek mdm[1480]: GLib-CRITICAL: g_key_file_free: assertion 'key_file != NULL' failed
/var/log/syslog.5.gz:Jul 21 21:56:23 derek kernel: [    7.621887] audit: type=1400 audit(1469159783.527:45): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="docker-default" pid=2126 comm="apparmor_parser"
/var/log/syslog.5.gz:Jul 21 21:56:23 derek NetworkManager[995]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.5.gz:Jul 21 21:56:23 derek NetworkManager[995]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.5.gz:Jul 21 21:56:23 derek NetworkManager[995]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.5.gz:Jul 21 21:56:23 derek NetworkManager[995]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.5.gz:Jul 21 21:56:26 derek pulseaudio[2453]: [pulseaudio] sink.c: Default and alternate sample rates are the same.
/var/log/syslog.5.gz:Jul 21 21:56:40 derek NetworkManager[995]: <info> (eth0): IP6 addrconf timed out or failed.
/var/log/syslog.5.gz:Jul 21 23:25:16 derek cinnamon-session[2046]: WARNING: t+5333.02344s: Playing logout sound '/usr/share/mint-artwork-cinnamon/sounds/logout.ogg'
/var/log/syslog.5.gz:Jul 21 23:25:16 derek cinnamon-session[2046]: WARNING: t+5333.08930s: Finished playing logout sound
/var/log/syslog.5.gz:Jul 21 23:25:16 derek cinnamon-session[2046]: WARNING: t+5333.08939s: Resuming logout sequence...
/var/log/syslog.5.gz:Jul 21 23:25:17 derek cinnamon-session[2046]: WARNING: t+5334.03847s: Requesting system restart...
/var/log/syslog.5.gz:Jul 21 23:25:17 derek cinnamon-session[2046]: WARNING: t+5334.03885s: Attempting to restart using consolekit...
/var/log/syslog.5.gz:Jul 21 23:25:17 derek cinnamon-session[2046]: WARNING: t+5334.04722s: Requesting system restart...
/var/log/syslog.5.gz:Jul 21 23:25:17 derek cinnamon-session[2046]: WARNING: t+5334.04753s: Attempting to restart using consolekit...
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    0.000000] MTRR default type: uncachable
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    0.000027] pid_max: default: 32768 minimum: 301
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    0.156826] NetLabel:  unlabeled traffic allowed by default
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    0.211000] PCI: CLS 64 bytes, default 64
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    0.520488] io scheduler deadline registered (default)
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    1.476132] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    1.508746] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    1.508754] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    1.508755] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    1.508758] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    1.508759] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    1.508762] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    1.508763] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    1.568497] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
/var/log/syslog.5.gz:Jul 22 00:03:58 derek kernel: [    1.840518] init: failsafe main process (791) killed by TERM signal
/var/log/syslog.5.gz:Jul 22 00:03:58 derek NetworkManager[948]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.5.gz:Jul 22 00:03:58 derek NetworkManager[948]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/eth0
/var/log/syslog.5.gz:Jul 22 00:03:58 derek NetworkManager[948]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
/var/log/syslog.5.gz:Jul 22 00:03:58 derek NetworkManager[948]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
/var/log/syslog.5.gz:Jul 22 00:03:59 derek nvidia-persistenced: Failed to open PID file: File exists
/var/log/syslog.5.gz:Jul 22 00:03:59 derek mdm[1462]: WARNING: Plymouth is running, asking it to stop...
/var/log/syslog.5.gz:Jul 22 00:03:59 derek mdm[1462]: WARNING: Plymouth stopped
/var/log/syslog.5.gz:Jul 22 00:04:00 derek ModemManager[923]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0': not supported by any plugin
/var/log/syslog.5.gz:Jul 22 00:04:02 derek NetworkManager[948]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
/var/log/syslog.5.gz:Jul 22 00:04:02 derek NetworkManager[948]: <warn> dnsmasq not available on the bus, can't update servers.
/var/log/syslog.5.gz:Jul 22 00:04:02 derek NetworkManager[948]: <error> [1469167442.920774] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog.5.gz:Jul 22 00:04:02 derek NetworkManager[948]: <warn> DNS: plugin dnsmasq update failed
/var/log/syslog.5.gz:Jul 22 00:04:02 derek dnsmasq[1774]: warning: no upstream servers configured
/var/log/syslog.5.gz:Jul 22 00:04:02 derek NetworkManager[948]: <warn> dnsmasq appeared on DBus: :1.11
/var/log/syslog.5.gz:Jul 22 00:04:04 derek kernel: [    7.219759] audit: type=1400 audit(1469167444.127:45): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="docker-default" pid=1975 comm="apparmor_parser"
/var/log/syslog.5.gz:Jul 22 00:04:04 derek NetworkManager[948]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.5.gz:Jul 22 00:04:04 derek NetworkManager[948]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.5.gz:Jul 22 00:04:04 derek NetworkManager[948]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.5.gz:Jul 22 00:04:04 derek NetworkManager[948]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.5.gz:Jul 22 00:04:05 derek mdm[1462]: GLib-CRITICAL: g_key_file_get_string: assertion 'key_file != NULL' failed
/var/log/syslog.5.gz:Jul 22 00:04:05 derek mdm[1462]: GLib-CRITICAL: g_key_file_free: assertion 'key_file != NULL' failed
/var/log/syslog.5.gz:Jul 22 00:04:07 derek pulseaudio[2459]: [pulseaudio] sink.c: Default and alternate sample rates are the same.
/var/log/syslog.5.gz:Jul 22 00:04:21 derek NetworkManager[948]: <info> (eth0): IP6 addrconf timed out or failed.
/var/log/syslog.6.gz:Jul 20 17:18:49 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
/var/log/syslog.6.gz:Jul 20 18:12:33 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
/var/log/syslog.6.gz:Jul 20 20:09:11 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
/var/log/syslog.6.gz:Jul 20 20:24:37 derek cinnamon-session[2233]: WARNING: t+153948.43666s: Playing logout sound '/usr/share/mint-artwork-cinnamon/sounds/logout.ogg'
/var/log/syslog.6.gz:Jul 20 20:24:37 derek cinnamon-session[2233]: WARNING: t+153948.54160s: Finished playing logout sound
/var/log/syslog.6.gz:Jul 20 20:24:37 derek cinnamon-session[2233]: WARNING: t+153948.54165s: Resuming logout sequence...
/var/log/syslog.6.gz:Jul 20 20:24:38 derek cinnamon-session[2233]: WARNING: t+153949.49037s: Requesting system restart...
/var/log/syslog.6.gz:Jul 20 20:24:38 derek cinnamon-session[2233]: WARNING: t+153949.49161s: Attempting to restart using consolekit...
/var/log/syslog.6.gz:Jul 20 20:24:38 derek cinnamon-session[2233]: WARNING: t+153949.50079s: Requesting system restart...
/var/log/syslog.6.gz:Jul 20 20:24:38 derek cinnamon-session[2233]: WARNING: t+153949.50106s: Attempting to restart using consolekit...
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    0.000000] MTRR default type: uncachable
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    0.000027] pid_max: default: 32768 minimum: 301
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    0.156845] NetLabel:  unlabeled traffic allowed by default
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    0.207022] PCI: CLS 64 bytes, default 64
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    0.516685] io scheduler deadline registered (default)
/var/log/syslog.6.gz:Jul 20 20:44:57 derek bluetoothd[768]: Failed to init deviceinfo plugin
/var/log/syslog.6.gz:Jul 20 20:44:57 derek bluetoothd[768]: Failed to init proximity plugin
/var/log/syslog.6.gz:Jul 20 20:44:57 derek bluetoothd[768]: Failed to init time plugin
/var/log/syslog.6.gz:Jul 20 20:44:57 derek bluetoothd[768]: Failed to init alert plugin
/var/log/syslog.6.gz:Jul 20 20:44:57 derek bluetoothd[768]: Failed to init thermometer plugin
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    1.459844] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    1.484624] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    1.484635] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    1.484637] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    1.484645] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    1.484647] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    1.484656] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    1.484664] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    1.516119] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
/var/log/syslog.6.gz:Jul 20 20:44:57 derek bluetoothd[768]: Failed to init gatt_example plugin
/var/log/syslog.6.gz:Jul 20 20:44:57 derek failsafe: Failsafe of 120 seconds reached.
/var/log/syslog.6.gz:Jul 20 20:44:57 derek kernel: [    1.816727] init: failsafe main process (822) killed by TERM signal
/var/log/syslog.6.gz:Jul 20 20:44:57 derek NetworkManager[943]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 20 20:44:57 derek NetworkManager[943]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/eth0
/var/log/syslog.6.gz:Jul 20 20:44:57 derek NetworkManager[943]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
/var/log/syslog.6.gz:Jul 20 20:44:57 derek NetworkManager[943]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
/var/log/syslog.6.gz:Jul 20 20:44:58 derek nvidia-persistenced: Failed to open PID file: File exists
/var/log/syslog.6.gz:Jul 20 20:44:58 derek mdm[1513]: WARNING: Plymouth is running, asking it to stop...
/var/log/syslog.6.gz:Jul 20 20:44:58 derek mdm[1513]: WARNING: Plymouth stopped
/var/log/syslog.6.gz:Jul 20 20:44:59 derek ModemManager[910]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0': not supported by any plugin
/var/log/syslog.6.gz:Jul 20 20:45:01 derek NetworkManager[943]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
/var/log/syslog.6.gz:Jul 20 20:45:01 derek NetworkManager[943]: <warn> dnsmasq not available on the bus, can't update servers.
/var/log/syslog.6.gz:Jul 20 20:45:01 derek NetworkManager[943]: <error> [1469069101.928973] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog.6.gz:Jul 20 20:45:01 derek NetworkManager[943]: <warn> DNS: plugin dnsmasq update failed
/var/log/syslog.6.gz:Jul 20 20:45:01 derek dnsmasq[1785]: warning: no upstream servers configured
/var/log/syslog.6.gz:Jul 20 20:45:01 derek NetworkManager[943]: <warn> dnsmasq appeared on DBus: :1.13
/var/log/syslog.6.gz:Jul 20 20:45:03 derek kernel: [    7.214163] audit: type=1400 audit(1469069103.123:45): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="docker-default" pid=1984 comm="apparmor_parser"
/var/log/syslog.6.gz:Jul 20 20:45:03 derek NetworkManager[943]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 20 20:45:03 derek NetworkManager[943]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 20 20:45:03 derek NetworkManager[943]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 20 20:45:03 derek NetworkManager[943]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 20 20:45:04 derek mdm[1513]: GLib-CRITICAL: g_key_file_get_string: assertion 'key_file != NULL' failed
/var/log/syslog.6.gz:Jul 20 20:45:04 derek mdm[1513]: GLib-CRITICAL: g_key_file_free: assertion 'key_file != NULL' failed
/var/log/syslog.6.gz:Jul 20 20:45:08 derek pulseaudio[2464]: [pulseaudio] sink.c: Default and alternate sample rates are the same.
/var/log/syslog.6.gz:Jul 20 20:45:17 derek NetworkManager[943]: <info> (eth0): IP6 addrconf timed out or failed.
/var/log/syslog.6.gz:Jul 20 21:50:11 derek cinnamon-session[2235]: WARNING: t+3908.90574s: Playing logout sound '/usr/share/mint-artwork-cinnamon/sounds/logout.ogg'
/var/log/syslog.6.gz:Jul 20 21:50:11 derek cinnamon-session[2235]: WARNING: t+3908.97533s: Finished playing logout sound
/var/log/syslog.6.gz:Jul 20 21:50:11 derek cinnamon-session[2235]: WARNING: t+3908.97537s: Resuming logout sequence...
/var/log/syslog.6.gz:Jul 20 21:50:12 derek cinnamon-session[2235]: WARNING: t+3909.92882s: Requesting system restart...
/var/log/syslog.6.gz:Jul 20 21:50:12 derek cinnamon-session[2235]: WARNING: t+3909.92939s: Attempting to restart using consolekit...
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    0.000000] MTRR default type: uncachable
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    0.000027] pid_max: default: 32768 minimum: 301
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    0.156742] NetLabel:  unlabeled traffic allowed by default
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    0.211922] PCI: CLS 64 bytes, default 64
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    0.521467] io scheduler deadline registered (default)
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    1.470745] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    1.470753] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    1.470755] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    1.470758] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    1.470759] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    1.470761] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    1.470763] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    1.473125] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    1.558977] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
/var/log/syslog.6.gz:Jul 20 22:48:07 derek kernel: [    1.784541] init: failsafe main process (765) killed by TERM signal
/var/log/syslog.6.gz:Jul 20 22:48:07 derek NetworkManager[943]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 20 22:48:07 derek NetworkManager[943]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/eth0
/var/log/syslog.6.gz:Jul 20 22:48:07 derek NetworkManager[943]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
/var/log/syslog.6.gz:Jul 20 22:48:07 derek NetworkManager[943]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
/var/log/syslog.6.gz:Jul 20 22:48:08 derek nvidia-persistenced: Failed to open PID file: File exists
/var/log/syslog.6.gz:Jul 20 22:48:08 derek mdm[1479]: WARNING: Plymouth is running, asking it to stop...
/var/log/syslog.6.gz:Jul 20 22:48:08 derek mdm[1479]: WARNING: Plymouth stopped
/var/log/syslog.6.gz:Jul 20 22:48:09 derek ModemManager[914]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0': not supported by any plugin
/var/log/syslog.6.gz:Jul 20 22:48:11 derek NetworkManager[943]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
/var/log/syslog.6.gz:Jul 20 22:48:11 derek NetworkManager[943]: <warn> dnsmasq not available on the bus, can't update servers.
/var/log/syslog.6.gz:Jul 20 22:48:11 derek NetworkManager[943]: <error> [1469076491.927517] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog.6.gz:Jul 20 22:48:11 derek NetworkManager[943]: <warn> DNS: plugin dnsmasq update failed
/var/log/syslog.6.gz:Jul 20 22:48:11 derek dnsmasq[1780]: warning: no upstream servers configured
/var/log/syslog.6.gz:Jul 20 22:48:11 derek NetworkManager[943]: <warn> dnsmasq appeared on DBus: :1.11
/var/log/syslog.6.gz:Jul 20 22:48:12 derek mdm[1479]: GLib-CRITICAL: g_key_file_get_string: assertion 'key_file != NULL' failed
/var/log/syslog.6.gz:Jul 20 22:48:12 derek mdm[1479]: GLib-CRITICAL: g_key_file_free: assertion 'key_file != NULL' failed
/var/log/syslog.6.gz:Jul 20 22:48:13 derek kernel: [    7.222367] audit: type=1400 audit(1469076493.127:45): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="docker-default" pid=2130 comm="apparmor_parser"
/var/log/syslog.6.gz:Jul 20 22:48:13 derek NetworkManager[943]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 20 22:48:13 derek NetworkManager[943]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 20 22:48:13 derek NetworkManager[943]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 20 22:48:13 derek NetworkManager[943]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 20 22:48:17 derek pulseaudio[2466]: [pulseaudio] sink.c: Default and alternate sample rates are the same.
/var/log/syslog.6.gz:Jul 20 22:48:30 derek NetworkManager[943]: <info> (eth0): IP6 addrconf timed out or failed.
/var/log/syslog.6.gz:Jul 21 01:24:49 derek cinnamon-session[2055]: WARNING: t+9395.47265s: Playing logout sound '/usr/share/mint-artwork-cinnamon/sounds/logout.ogg'
/var/log/syslog.6.gz:Jul 21 01:24:49 derek cinnamon-session[2055]: WARNING: t+9395.53530s: Finished playing logout sound
/var/log/syslog.6.gz:Jul 21 01:24:49 derek cinnamon-session[2055]: WARNING: t+9395.53534s: Resuming logout sequence...
/var/log/syslog.6.gz:Jul 21 01:24:50 derek cinnamon-session[2055]: WARNING: t+9396.48324s: Requesting system restart...
/var/log/syslog.6.gz:Jul 21 01:24:50 derek cinnamon-session[2055]: WARNING: t+9396.48361s: Attempting to restart using consolekit...
/var/log/syslog.6.gz:Jul 21 01:24:50 derek cinnamon-session[2055]: WARNING: t+9396.49035s: Requesting system restart...
/var/log/syslog.6.gz:Jul 21 01:24:50 derek cinnamon-session[2055]: WARNING: t+9396.49068s: Attempting to restart using consolekit...
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    0.000000] MTRR default type: uncachable
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    0.000026] pid_max: default: 32768 minimum: 301
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    0.156745] NetLabel:  unlabeled traffic allowed by default
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    0.210916] PCI: CLS 64 bytes, default 64
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    0.520612] io scheduler deadline registered (default)
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    1.449912] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    1.489934] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    1.489941] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    1.489943] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    1.489945] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    1.489947] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    1.489949] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPR2) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    1.489951] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    1.556271] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
/var/log/syslog.6.gz:Jul 21 03:52:19 derek failsafe: Failsafe of 120 seconds reached.
/var/log/syslog.6.gz:Jul 21 03:52:19 derek kernel: [    1.779149] init: failsafe main process (815) killed by TERM signal
/var/log/syslog.6.gz:Jul 21 03:52:19 derek NetworkManager[934]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 21 03:52:19 derek NetworkManager[934]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/eth0
/var/log/syslog.6.gz:Jul 21 03:52:19 derek NetworkManager[934]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
/var/log/syslog.6.gz:Jul 21 03:52:19 derek NetworkManager[934]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
/var/log/syslog.6.gz:Jul 21 03:52:20 derek nvidia-persistenced: Failed to open PID file: File exists
/var/log/syslog.6.gz:Jul 21 03:52:20 derek mdm[1486]: WARNING: Plymouth is running, asking it to stop...
/var/log/syslog.6.gz:Jul 21 03:52:20 derek mdm[1486]: WARNING: Plymouth stopped
/var/log/syslog.6.gz:Jul 21 03:52:21 derek ModemManager[915]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0': not supported by any plugin
/var/log/syslog.6.gz:Jul 21 03:52:23 derek NetworkManager[934]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
/var/log/syslog.6.gz:Jul 21 03:52:23 derek NetworkManager[934]: <warn> dnsmasq not available on the bus, can't update servers.
/var/log/syslog.6.gz:Jul 21 03:52:23 derek NetworkManager[934]: <error> [1469094743.974676] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog.6.gz:Jul 21 03:52:23 derek NetworkManager[934]: <warn> DNS: plugin dnsmasq update failed
/var/log/syslog.6.gz:Jul 21 03:52:23 derek dnsmasq[1784]: warning: no upstream servers configured
/var/log/syslog.6.gz:Jul 21 03:52:24 derek NetworkManager[934]: <warn> dnsmasq appeared on DBus: :1.13
/var/log/syslog.6.gz:Jul 21 03:52:25 derek kernel: [    7.263472] audit: type=1400 audit(1469094745.172:45): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="docker-default" pid=1983 comm="apparmor_parser"
/var/log/syslog.6.gz:Jul 21 03:52:25 derek NetworkManager[934]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 21 03:52:25 derek NetworkManager[934]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 21 03:52:25 derek NetworkManager[934]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 21 03:52:25 derek NetworkManager[934]: <warn> failed to allocate link cache: (-12) Object not found
/var/log/syslog.6.gz:Jul 21 03:52:42 derek NetworkManager[934]: <info> (eth0): IP6 addrconf timed out or failed.
/var/log/syslog.7.gz:Jul 19 08:49:07 derek kernel: [25813.964733] chrome[3134]: segfault at 400008 ip 00007fd67345041e sp 00007ffd9816f3a0 error 4 in chrome[7fd6724e6000+5d99000]
/var/log/syslog.7.gz:Jul 19 18:02:03 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error
/var/log/syslog.7.gz:Jul 19 21:06:47 derek cinnamon-screensaver-dialog: pam_ecryptfs: seteuid error

```

---

### Post by bapoumba on 2016-07-27
> **Ghjnut said:**
> Sorry, I seem to be getting an error posting all my outputs
```
Your submission could not be processed because a security token was missing.
```
Please report your posting problems here (with the date -u output) : [https://ubuntuforums.org/showthread.php?t=2331266](https://ubuntuforums.org/showthread.php?t=2331266) thanks !

---

### Post by DuckHook on 2016-07-27
*Thread moved to **MINT** as the more appropriate forum.*

The reason that we don't support Mint is because, even though it is based on Ubuntu, there are enough differences to throw any attempted solutions offside. This is the same reason Debian doesn't support Ubuntu, even though Ubuntu is based on Debian. In my case, I don't run Mint so I can't even reproduce your system state on my equipment. If I assume that your system has certain apps and services on it when it actually is running something else, then the process becomes an exercise in confusion, misunderstanding, frustration and a waste of everyone's time&#8213;including yours.

You can still try the solutions offered: a RAM integrity check, further detective work on your logs, etc, but I don't even know if Mint uses *apport* or what differences there are in their crash reporting, so by far your best avenue now is to post your problem to the Mint forums.

I have moved your thread to this Mint subforum so that Ubuntu users who may have some Mint experience will see it.

---

### Post by Ghjnut on 2016-08-09
Can anyone provide any insight from this forum? Simply looking for a means to ensure I replace the correct part.

---

