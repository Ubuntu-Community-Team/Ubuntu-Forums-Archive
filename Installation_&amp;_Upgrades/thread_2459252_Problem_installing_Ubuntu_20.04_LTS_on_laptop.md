---
title: "Problem installing Ubuntu 20.04 LTS on laptop"
date: 2021-03-14
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2021-03-14
Downloaded: ubuntu-20.04.2.0-desktop-amd64.iso, then burned the ISO to a DVD.
Checksum reports this ISO DVD is OK, has no errors.
Did give 20.04 a try out to see what it was like and liked it.

Then did a clean install of 20.04 LTS on Toshiba laptop in my signature below in the 128.52 GiB partition Vista used to be located.
Ubuntu 14.04 LTS is installed on extended 19.06 GiB partition as shown in GParted below. Ubuntu 14.04 still runs fine on laptop.
[IMG]https://i.postimg.cc/vmvkyYYS/gp.png[/IMG]

However cannot get Ubuntu 20.04 LTS to boot up and run and just keep getting this screen below, along with laptop being totally frozen. I cannot log out and have to do a hard shutdown by pressing/holding the power button to shutdown and then restart laptop:
[IMG]https://i.postimg.cc/CxrnQDDv/f.png[/IMG]

Help? What needs to be done to get 20.04 to run?

---

### Post by grahammechanical on 2021-03-14
Where did you install the 20.04 Grub boot loader? When do you see that problem has occurred message? After you see a grub boot menu with Ubuntu 20.04 listed? Try loading Ubuntu 14.04 and then run

```
sudo update-grub
```

The printout should list 20.04. When you reboot do you get a Grub menu with 20.04 listed. Does it load 20.04.

Regards

---

### Post by cybrsaylr on 2021-03-14
Did not  install the 20.04 Grub boot loader, never have in the past. Just let the ISO disc do its thing and auto-install the boot loader. When attempting to boot, up all looked normal. 
Ubuntu is first line in boot loader as shown below:

Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
*Ubuntu 14.04.6 LTS (14.04) (on /dev/sda5)
Advanced options for Ubuntu 14.04.6 LTS (14.04) (on /dev/sda5)

Did run code, 'sudo update-grub' in terminal using Ubuntu 14.04 LTS. Terminal said it was done.

Tried to boot up and it still get the message "Oh no! Something has gone wrong." and laptop locks up again,  forcing me to do another hard shutdown.

Restart laptop into 14.04 and all is running fine.

---

### Post by oldfred on 2021-03-15
So you get grub menu from 20.04 and can choose 14.04 or the 20.04?

Can you boot recovery mode of 20.04, from advanced options?

---

### Post by cybrsaylr on 2021-03-15
Fred, no joy yet.

My boot loader shows this:
[IMG]https://i.postimg.cc/s2NJCLkh/Boot-loader-shows-this.png[/IMG]

Clicked on 
Advanced  options for Ubuntu and get two choices. 
Ubuntu, with Linux 5.8.0-43 generic (recovery mode)
Select the second choice, Ubuntu, with Linux 5.8.0-44 generic (recovery mode) which does start up 20.04 which runs but not as well as on my ISO disc demo where I gave 20.04 a trial run.
Played around with 20.04 a bit then ran Software Updater. Downloaded ~78 megs of updates then installed then. That appeared to go OK. Then was told to restart PC.  Tried to boot up and it still get the message "Oh no! Something has gone wrong." and laptop locks up again, forcing me to do another hard shutdown.

Tried to restart again going into Advanced  options for Ubuntu and get three choices now. 
Select the Ubuntu new choice 3; which is _Linux 5.8.0-45 generic (recovery mode)_ which does start up 20.04 again using (recovery mode).
However when attempting to shutdown and reboot normally,  still get the message "Oh no! Something has gone wrong." and laptop locks up again, forcing me to do another hard shutdown.

So 20.04 seems to run, somewhat in (recovery mode) but not on normal startup.

Discovered running in (recovery mode) Ubuntu Software and a couple other apps will not open.

---

### Post by oldfred on 2021-03-15
Recovery mode includes the nomodeset boot parameter.

But I do not know issues with older AMD video nor what may work.

---

### Post by cybrsaylr on 2021-03-15
> **oldfred said:**
> But I do not know issues with older AMD video nor what may work.

Yes realize this is an older laptop purchased towards the end of 2008. It ran Vista and Ubuntu 14.04 LTS well.

Did a check of its 160 GiB HDD and got OK results in; Disks > SMART Data & Self-Tests.

---

### Post by DuckHook on 2021-03-15
What do your logs tell you? From 14.04, you should be able to peek into your 20.04 partition and see what the last entries were before things went south. dmesg, syslog, kern.log and systemd journal.

Also, please post HW specs using lshw. Without knowing what your HW is, it's just groping around in the dark.

Make sure to post your output between [noparse]```
 and 
```[/noparse] tags to preserve formatting. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by cybrsaylr on 2021-03-16
DuckHook,

Not sure how to get logs? Never did that before. 

```
-Satellite-A215:~$ lshw
WARNING: you should run this program as super-user.
PCI (sysfs)  
SCSI                      
r-satellite-a215   
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3826MiB
     *-cpu
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-60
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid eagerfpu pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall lbrv cpufreq
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:f8000000-f81fffff ioport:f0000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: RS690M [Radeon Xpress 1200/1250/1270]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:44 memory:f0000000-f7ffffff memory:f8100000-f810ffff ioport:9000(size=256) memory:f8000000-f80fffff
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD/ATI]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:f8500000-f86fffff ioport:f8800000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 1)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:a000(size=4096) memory:f8300000-f83fffff ioport:f8a00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 01
                serial: 00:a0:d1:9d:0d:a6
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.22 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:a000(size=256) memory:f8300000-f8300fff memory:f8a00000-f8a1ffff
        *-pci:3
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:f8200000-f82fffff ioport:f8b00000(size=2097152)
           *-network
                description: Wireless interface
                product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:0e:00.0
                logical name: wlan0
                version: 01
                serial: 00:1f:3a:2f:24:a3
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=3.13.0-170-generic firmware=N/A ip=192.168.0.26 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
                resources: irq:18 memory:f8200000-f820ffff
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8440(size=8) ioport:8434(size=4) ioport:8438(size=8) ioport:8430(size=4) ioport:8400(size=16) memory:f8709000-f87093ff
        *-usb:0
             description: USB controller
             product: SB600 USB (OHCI0)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:16 memory:f8704000-f8704fff
        *-usb:1
             description: USB controller
             product: SB600 USB (OHCI1)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:17 memory:f8705000-f8705fff
        *-usb:2
             description: USB controller
             product: SB600 USB (OHCI2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f8706000-f8706fff
        *-usb:3
             description: USB controller
             product: SB600 USB (OHCI3)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:17 memory:f8707000-f8707fff
        *-usb:4
             description: USB controller
             product: SB600 USB (OHCI4)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f8708000-f8708fff
        *-usb:5
             description: USB controller
             product: SB600 USB Controller (EHCI)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:f8709400-f87094ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8410(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:f8700000-f8703fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: memory:f8400000-f84fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:14:06.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:20 memory:f8400000-f84007ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:14:06.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:21 memory:f8400800-f84008ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:14:06.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=r592 latency=64
                resources: irq:21 memory:f8401000-f84010ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:14:06.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=r852 latency=64
                resources: irq:21 memory:f8401400-f84014ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

---

### Post by DuckHook on 2021-03-16
I've edited your post to wrap [noparse]```
 and 
```[/noparse] tags around the output. Please use them for all future postings to prevent the wall of text that was your initial post.

There are many tutorials that show how to get to your logs. Understanding them is admittedly a different matter. The following is a link to a good primer on Linux overall. Friends tell me the site is useful and easy on the eyes. Explanation of logs should be about halfway down: [https://linuxjourney.com/](https://linuxjourney.com/)

Please don't print the entirety of your logs. They can be massive. Just copy and paste the 20 or so lines immediately prior to the crash, but make sure you wrap them in *CODE* tags this time.

---

### Post by cybrsaylr on 2021-03-16
Since having this issue with 20.04 decided to try running 18.04 on this laptop.
Put in the ISO DVD of 18.04 made a few years ago to see what happens.
Well it attempts to bootup off the DVD but stops, just hanging here with this below.
Goes to a terminal black screen with this report:

[https://i.postimg.cc/pLZw19dq/18-04.png](https://i.postimg.cc/pLZw19dq/18-04.png)

Not really sure what it means?
Guessing laptop has problems?

---

### Post by DuckHook on 2021-03-17
Sorry, but I can't read the image you posted. The output is just too blurry for these old eyes.

I've also changed it to the URL link because the forums have a policy against posting large images. They are very problematic for helpers with low speeds, who are on limited data plans, or are viewing from smartphones or small screens. It is also unnecessary to post whole screenshots in most cases. Terminal output can be highlighted with the mouse, copied with a right click and pasted into the posting box between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the button in the *Adv Reply* toolbar.

If you must post resource-intensive images, please post them as attachments using the paperclip icon in the *Adv Reply* toolbar.

Re: your issues:

I doubt that the problem is your laptop. If it were, you would not be able to run 14.04 on it. I suspect that it's more a driver or other incompatibility issue. I would still recommend that you launch your working version of 14.04, mount the partition you are unsuccessfully trying to install into, and see what the logs tell you. In particular, the install logs located in /var/log/installer.

---

### Post by cybrsaylr on 2021-03-17
Thanks.

Tried and got into those logs but as you said they were massive. 
Will try again looking into the ones you showed above.

FWIW 14.04 runs better than 20.04 in rec mode, on my laptop.

---

