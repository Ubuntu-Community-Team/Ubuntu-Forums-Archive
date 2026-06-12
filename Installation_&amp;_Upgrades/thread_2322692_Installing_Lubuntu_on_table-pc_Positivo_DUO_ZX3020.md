---
title: "Installing Lubuntu on table-pc Positivo DUO ZX3020"
date: 2016-04-29
forum: Installation &amp; Upgrades
---

### Post by Hugo_Fernando_Maia on 2016-04-29
Hi guys,

I've a pc-table (two-in-one, Brazilian branch) with Win10 and I tried to install Ubuntu (preferred Lubuntu) once but found it really difficult. I found a link on the web (cannot find it anymore) with a LiveCD that I could boot but the wireless neither the touchscreen were working. I did a search on Brazilian website but no one knew how to get rid of Win10. Considering the new Ubuntu flavor 16.04 (and that Win10 is astonishing slow) I'd like to get help from you guys to see if there is a way to install Lubuntu and use the touchscreen.

Details of the tablet-pc:
Positivo DUO ZX3020
Processor: Intel(R) Atom(TM) CPU Z3735G @ 1.33 GHz - 64bits
RAM: 1 GB
HD: 16 GB
Wireless card: RTL8723BS Wireless LAN 802.11n SDIO
Touchscreen compatible with HID I2C (only information I found)
Kionix KXTJ9 3-axis accelerometer

Thank you,
Hugo

---

### Post by RobGoss on 2016-04-29
Hello and welcome, I've never attempted to install Ubuntu on a tablet but I would think it would not be to hard I'm sure the tablet would need to be Rooted for this process

Here's a YouTube video that might help
[https://www.youtube.com/watch?v=qIYKKLX8lJM](https://www.youtube.com/watch?v=qIYKKLX8lJM)

---

### Post by Hugo_Fernando_Maia on 2016-04-29
Thank you!

However, mine is not a table nor a pc. It is a hybrid and it runs Windows....

For our purposes, I'd like to consider it as a PC and I would like to install Lubuntu on it as it was a PC. You can see some pictures if you want to at [http://www.casasbahia.com.br/Informatica/Notebook/Notebook-2-em-1-Touch-Positivo-Duo-ZX3020-com-Intel-Atom-Quad-Core-1GB-16GB-SSD-Leitor-de-Cartoes-Micro-HDMI-Webcam-LED-10-1-e-Windows-8-1-3806890.html](http://www.casasbahia.com.br/Informatica/Notebook/Notebook-2-em-1-Touch-Positivo-Duo-ZX3020-com-Intel-Atom-Quad-Core-1GB-16GB-SSD-Leitor-de-Cartoes-Micro-HDMI-Webcam-LED-10-1-e-Windows-8-1-3806890.html)

any other idea?

---

### Post by mörgæs on 2016-04-30
I'm not sure that Lubuntu supports touchscreen. I would try a live boot of Ubuntu first. 

It's common that a wirefree netcard does not work in a live boot. Better to solve this problem after installation.

---

### Post by RobGoss on 2016-04-30
It look like maybe you might be able to boot it as you would a PC from a USB drive, I'm assuming it has USB ports in it....

---

### Post by oldfred on 2016-04-30
Is this one of the systems that vendors configured as Windows only using UEFI 32 bit as then Linux did not have a 32 bit UEFI version.
The 32 bit UEFI is not recommended, so distributions do not have that as standard, but you can download the .efi file to make it work.

Also issues with some Bay Trail Atoms:
 Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

### Post by Hugo_Fernando_Maia on 2016-04-30
I couldn't boot... I disabled "fast boot" from Windows 10 and selected my LiveCD (Ubuntu 16.04). However, no boot... I think that may be what oldfred said, some thing related to UEFI. I looked at the links but couldn't find how to download .efi and make it work. Any suggestions?

---

### Post by oldfred on 2016-04-30
This was for an Asus, so may be similar?
 Asus X205TA hardware support in Ubuntu 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2254322](http://ubuntuforums.org/showthread.php?t=2254322)
[http://ubuntuforums.org/showthread.php?t=2312465&p=13470344#post13470344](http://ubuntuforums.org/showthread.php?t=2312465&p=13470344#post13470344) 

But you should not have to compile your own bootia32.efi, I have seen, but not saved any links to download it pre-compiled. 

Some other threads, if yours is 32 bit UEFI, then process should be similar.

 [http://ubuntuforums.org/showthread.php?t=2307022&p=13410393#post13410393](http://ubuntuforums.org/showthread.php?t=2307022&p=13410393#post13410393)
Trying to install Ubuntu on an Acer one 10 (S1002)  32 bit
[http://ubuntuforums.org/showthread.php?t=2305272](http://ubuntuforums.org/showthread.php?t=2305272)
Instructions to install Ubuntu 14.10 on ASUS EeeBook X205TA - Atom Bay Trail 32 bit UEFI
[https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md)
Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)

---

### Post by Hugo_Fernando_Maia on 2016-05-01
Thanks!
I'll give it a try and will report what I found later.

---

### Post by Hugo_Fernando_Maia on 2016-10-25
I'd like to report that I was able to install Lubuntu 16.10 (I'm actually writing from Lubuntu 16.10 using this machine! That's awesome) in this pc-tablet using the instruction and CDs from here [https://linuxiumcomau.blogspot.com/2016/10/running-ubuntu-on-intel-bay-trail-and.html](https://linuxiumcomau.blogspot.com/2016/10/running-ubuntu-on-intel-bay-trail-and.html)

Although I could install Lubuntu, I see that some hardware are not working properly. Could you help me figure out if there's a way to set them up?

What is not working?
power management (doesn't detect when charging/charge percentage)
 bluetooth
sound
accelerometer
touchscreen

What is working?
Wifi
Memory card
Brightness management
HDMI video
many others too =)

I tried setting up the additional driver on Software & updates (intel-microcode) but that didn't seem to have any effect. Any ideas?

---

### Post by mörgæs on 2016-10-25
It does not surprise me. As already posted I have my doubts that Lubuntu (targeting old hardware) supports touchscreens.

---

### Post by Hugo_Fernando_Maia on 2016-11-05
I tried a live boot of Ubuntu but the problems that I described were the same. It also had the drawback of consuming too much ram memory (at least for that table-pc, which has only 1 gb).

---

### Post by mörgæs on 2016-11-06
I think we need to take a look at the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Hugo_Fernando_Maia on 2016-11-07
```

 computer    description: Notebook
    product: WCBT1013 (3600907)
    vendor: Positivo Informatica SA
    version: To be filled by O.E.M.
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: boot=normal chassis=notebook family=To be filled by O.E.M. sku=3600907 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: WCBT1013
       vendor: Positivo Informatica SA
       physical id: 0
       version: Standard
       serial: [REMOVED]
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1.4
          date: 10/15/2014
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 1GiB
          capabilities: ecc
          configuration: errordetection=multi-bit-ecc
        *-bank
             description: DIMM DDR3 1333 MHz (0.8 ns)
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: A1_DIMM0
             size: 1GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cache:0
          description: L1 cache
          physical id: 30
          slot: CPU Internal L1
          size: 224KiB
          capacity: 224KiB
          capabilities: internal write-back
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 31
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU  Z3735G @ 1.33GHz
          vendor: Intel Corp.
          physical id: 32
          bus info: cpu@0
          version: Intel(R) Atom(TM) CPU Z3735G @ 1.33GHz
          slot: SOCKET 0
          size: 499MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 83MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-pci
          description: Host bridge
          product: Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0f
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:205 memory:50000000-503fffff memory:40000000-4fffffff ioport:1000(size=8) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0f
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:203 memory:50800000-5080ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.8.0-26-linuxium xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 2
                   bus info: usb@1:2
                   version: 85.36
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: ITE Device(8595)
                      vendor: ITE Tech. Inc.
                      physical id: 1
                      bus info: usb@1:2.1
                      version: 0.03
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
                 *-usb:1
                      description: USB hub
                      product: Dell USB Keyboard Hub
                      vendor: Dell
                      physical id: 2
                      bus info: usb@1:2.2
                      version: 2.00
                      capabilities: usb-1.10
                      configuration: driver=hub maxpower=90mA slots=3 speed=12Mbit/s
                    *-usb:0
                         description: Keyboard
                         product: Dell USB Keyboard Hub
                         vendor: Dell
                         physical id: 1
                         bus info: usb@1:2.2.1
                         version: 2.00
                         capabilities: usb-1.10
                         configuration: driver=usbhid speed=12Mbit/s
                    *-usb:1
                         description: Mouse
                         product: USB OPTICAL MOUSE
                         vendor: PIXART
                         physical id: 3
                         bus info: usb@1:2.2.3
                         version: 1.00
                         capabilities: usb-1.10
                         configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.8.0-26-linuxium xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.08
                capabilities: usb-3.00
                configuration: driver=hub slots=1 speed=5000Mbit/s
        *-generic
             description: Encryption controller
             product: Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:206 memory:50700000-507fffff memory:50600000-506fffff
        *-isa
             description: ISA bridge
             product: Atom Processor Z36xxx/Z37xxx Series Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723bs ip=[REMOVED] multicast=yes wireless=IEEE 802.11gn



```

---

### Post by mörgæs on 2016-11-08
Sorry, I don't see anything which could explain why the touchscreen does not work.
Hoping someone else does.

---

### Post by Hugo_Fernando_Maia on 2016-11-08
Thanks anyway.

BTW, the sound never worked... When I open a music file (or any stuff that is supposed to play music, like youtube), the music never starts. It hangs out at 0 and never goes up. I tried different files and websites but got nothing. Using PulseAudio, I see "IntelHDMI".

---

