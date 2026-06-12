---
title: "System Fan &amp; Karmic alpha 5"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Robin Nixon on 2009-09-08
I have noticed that the fan on my computer now spins very noisily having upgraded from 9.04 to 9.10 a5 (previously it was whisper quiet).

Obviously something is using the processor a considerable amount, even though I haven't installed anything new, ensure no programs are running and just the desktop is in view.

Please can anyone tell me how I can find out culprit?

---

### Post by forumache on 2009-09-08
There is a problem with the new kernel and the sensors on the motherboard.
Due to this problem, the fancontrol (which uses sensors) cannot work as expected.

Let's see. Give me the output of

dmesg|grep -i acpi

---

### Post by Robin Nixon on 2009-09-08
Thanks for replying. Here's the output I got from dmesg:

[    0.000000]  BIOS-e820: 000000007ffd0000 - 000000007ffde000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffde000 - 0000000080000000 (ACPI NVS)
[    0.000000]  modified: 000000007ffd0000 - 000000007ffde000 (ACPI data)
[    0.000000]  modified: 000000007ffde000 - 0000000080000000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000fc560 00014 (v00 HPQOEM)
[    0.000000] ACPI: RSDT 7ffd0000 0003C (v01 HPQOEM SLIC-CPC 11000629 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffd0200 00084 (v02 HPQOEM OEMFACP  11000629 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffd05c0 05F2F (v01 HPQOEM OEMDSDT  00000000 INTL 20060210)
[    0.000000] ACPI: FACS 7ffde000 00040
[    0.000000] ACPI: APIC 7ffd0390 00070 (v01 HPQOEM OEMAPIC  11000629 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffd0400 0003C (v01 HPQOEM OEMMCFG  11000629 MSFT 00000097)
[    0.000000] ACPI: SLIC 7ffd0440 00176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
[    0.000000] ACPI: OEMB 7ffde040 00063 (v01 HPQOEM AMI_OEM  11000629 MSFT 00000097)
[    0.000000] ACPI: HPET 7ffd64f0 00038 (v01 HPQOEM OEMHPET0 11000629 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.018474] ACPI: Core revision 20090521
[    0.152447] ACPI: bus type pci registered
[    0.161056] ACPI: EC: Look up EC in DSDT
[    0.211018] ACPI: Interpreter enabled
[    0.211027] ACPI: (supports S0 S1 S3 S4 S5)
[    0.211061] ACPI: Using IOAPIC for interrupt routing
[    0.214545] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.224147] ACPI Warning: Incorrect checksum in table [OEMB] - AD, should be A0 20090521 tbutils-246
[    0.224264] ACPI: No dock devices found.
[    0.224410] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.225640] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.225897] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.225978] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.226059] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[    0.226186] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.240513] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *15
[    0.240513] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.240740] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.240992] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *10
[    0.241244] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *10
[    0.241506] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.241758] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.242009] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.242261] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *7
[    0.242512] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *15
[    0.242762] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[    0.244095] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.244347] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.244598] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.244851] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5
[    0.245102] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *11
[    0.245353] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10
[    0.245603] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
[    0.245898] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.245960] ACPI: WMI: Mapper loaded
[    0.245960] PCI: Using ACPI for IRQ routing
[    0.284020] pnp: PnP ACPI init
[    0.284039] ACPI: bus type pnp registered
[    0.288739] pnp: PnP ACPI: found 12 devices
[    0.288742] ACPI: ACPI bus type pnp unregistered
[    0.288747] PnPBIOS: Disabled by ACPI PNP
[    1.020536] ACPI: Power Button [PWRF]
[    1.020671] ACPI: Power Button [PWRB]
[    1.021240] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.391055] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    1.402150] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    1.412972] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[    1.584671] ata3: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:900:0x11)
[    2.090660] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    2.211798] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[   13.671133] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 18
[   14.341940] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 17
[   15.177758] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23

---

### Post by forumache on 2009-09-08
OK, I don't see the sensors problem, I don' remember if sensors are installed by default. But if you don't remember configuring sensors/fancontrol then it is a different problem.

Type

top

in a terminal. You'll see on the first line the cpu usage and then a list of processes, with the most CPU intensive first).

Type k (this will stop the top command from updating and will ask you PID to kill. Do not type anything here, just copy the first 10 lines and post them here).
Press Enter (to get read of that PID to kill) and then q (to quit)

P.S. Even if you don't have applications running visible on screen, there might be processes running in background. "top" will display them.

---

### Post by dino99 on 2009-09-08
what is the output of sensors ?
may be run sensor-detect & if you have an nvidia card, install nvidia-setting because sensors need it.

---

### Post by Robin Nixon on 2009-09-08
Hello again,

The result of **top** is:

 3207 robin     20   0 95624 4964 3408 R   87  0.2  27:28.82 pulseaudio         
 3203 robin     20   0  3220 1416  648 S    5  0.1   1:29.06 dbus-daemon        
 3295 robin     20   0 30936  14m 8272 S    2  0.7   0:23.11 python             
 3162 robin     20   0 26624 6512 5252 S    1  0.3   0:21.07 gnome-session      
 3284 robin     20   0 42976  20m  14m S    1  1.0   0:26.79 gnome-panel        
 3308 robin     20   0 26980  11m 8764 S    1  0.6   0:12.13 update-notifier    
 1448 syslog    20   0 28312 1472  940 S    1  0.1   0:19.36 rsyslogd           
 3224 robin     20   0  6272 2220 1836 S    1  0.1   0:09.73 gvfsd              
 3250 robin     20   0 19220 7676 6308 S    1  0.4   0:11.47 notify-osd         
 3312 robin     20   0 18968 8652 7160 S    1  0.4   0:16.91 gnome-power-man    

And **sensors** reports:

 k8temp-pci-00c3
 Adapter: PCI adapter
 Core0 Temp:  +67.0°C                                    
 Core1 Temp:  +73.0°C

(I installed lm-sensors as it wasn't there already)

Thanks!

---

### Post by dino99 on 2009-09-08
Que calor :lolflag:

mine is : cpu temp 17° c     core temp 47°c
          (q9550 with 4 cores full crunching on boinc)

---

### Post by forumache on 2009-09-08
@Robin Nixon,

you can see that process pulseaudio is taking 87% of the CPU.
Kill it by typing in a terminal:

pulseaudio --kill

You can do it, since it was launched as a user process.

See if the fan will return to normal after a couple of minutes.

@dino99,
do you keep your computer in the wine celar? I thought that the CPU temperature cannot be less than the room were it sits.

---

### Post by Robin Nixon on 2009-09-08
I think you have solved it forumache,

When I killed it the fan slowed a little but it restarted itself again after a few seconds. So I went to Synaptic and uninstalled pulseaudio.

sensors now reports:

Core0 Temp:  +55.0°C                                    
Core1 Temp:  +60.0°C

... and falling.

Curiously the sound still seems to work just fine.

Is this a bug I should file?

And thanks again!

---

### Post by lcohen999 on 2009-09-08
add me to that list:

dmesg|grep -i acpi 

[    0.000000] ACPI: RSDP 00000000000fbbf0 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000dfe6f200 0005C (v01 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: FACP 00000000dfe6f09c 000F4 (v04 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: DSDT 00000000dfe6f800 05733 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 00000000dfe7e000 00040
[    0.000000] ACPI: HPET 00000000dfe6f300 00038 (v01 DELL    M08     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 00000000dfe6f400 00068 (v01 DELL    M08     27D80708 ASL  00000047)
[    0.000000] ACPI: MCFG 00000000dfe6f3c0 0003E (v16 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: SLIC 00000000dfe6f49c 00176 (v01 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: BOOT 00000000dfe6efc0 00028 (v01 DELL    M08     27D80708 ASL  00000061)
[    0.000000] ACPI: SSDT 00000000dfe6d9bc 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.006898] ACPI: Core revision 20090521
[    0.148173] ACPI: bus type pci registered
[    0.152633] ACPI: EC: Look up EC in DSDT
[    0.166729] ACPI: SSDT 00000000dfe7e080 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.181726] ACPI: Interpreter enabled
[    0.181729] ACPI: (supports S0 S3 S4 S5)
[    0.181746] ACPI: Using IOAPIC for interrupt routing
[    0.224169] ACPI: No dock devices found.
[    0.239742] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.241257] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.243597] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.243835] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.243947] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.244024] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.244093] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.244163] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.244233] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.256274] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[    0.256274] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.256329] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.256444] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.256560] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.256676] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.256793] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.256898] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.256965] ACPI: WMI: Mapper loaded
[    0.256965] PCI: Using ACPI for IRQ routing
[    0.300685] pnp: PnP ACPI init
[    0.300695] ACPI: bus type pnp registered
[    0.339580] pnp: PnP ACPI: found 12 devices
[    0.339582] ACPI: ACPI bus type pnp unregistered
[    0.535439] ACPI: AC Adapter [AC] (on-line)
[    0.536118] ACPI: Lid Switch [LID]
[    0.536193] ACPI: Power Button [PBTN]
[    0.536259] ACPI: Sleep Button [SBTN]
[    0.536929] ACPI: SSDT 00000000dfe6e4f2 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.537365] ACPI: SSDT 00000000dfe6de88 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.537774] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.537833] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.538157] ACPI: SSDT 00000000dfe6e778 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.538428] ACPI: SSDT 00000000dfe6e46d 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.538846] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.538896] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.545985] ACPI: Thermal Zone [THM] (39 C)
[    0.572963] ACPI: Battery Slot [BAT0] (battery present)
[    1.128351] acpi device:32: registered as cooling_device2
[    1.129495] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)

and top

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3840 lcohen    20   0 46812 6716 2348 S   17  0.2   8:12.99 gconfd-2           
 3279 root      20   0  274m  60m  20m S   16  1.5   7:08.44 Xorg               
 4079 lcohen    20   0  301m  53m  18m S    5  1.4   2:04.04 compiz.real        
  752 lcohen    20   0 23208  19m  644 S    4  0.5   1:01.09 wineserver         
 3798 lcohen    20   0 22000 1684  644 S    3  0.0   1:13.49 dbus-daemon        
 3502 lcohen    20   0  159m 7828 5756 S    2  0.2   0:54.83 gnome-session      
 3982 lcohen    20   0  352m  26m  15m S    2  0.7   0:31.00 gnome-panel        
26318 lcohen    20   0  631m 167m  29m S    2  4.2   0:47.01 firefox    

sensors
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +64.5°C  (crit = +104.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +59.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +57.0°C  (high = +100.0°C, crit = +100.0°C)

---

### Post by dino99 on 2009-09-08
> **forumache said:**
> @Robin Nixon,

you can see that process pulseaudio is taking 87% of the CPU.
Kill it by typing in a terminal:

pulseaudio --kill

You can do it, since it was launched as a user process.

See if the fan will return to normal after a couple of minutes.

@dino99,
do you keep your computer in the wine celar? I thought that the CPU temperature cannot be less than the room were it sits.

i don't use my cpu for cooking, no wine celar over there but good fan   :lolflag:

---

### Post by forumache on 2009-09-08
> **Robin Nixon said:**
> I think you have solved it forumache,

When I killed it the fan slowed a little but it restarted itself again after a few seconds. So I went to Synaptic and uninstalled pulseaudio.

...

Curiously the sound still seems to work just fine.

Is this a bug I should file?

And thanks again!

Great, glad that it is working. Some explanations:
The sound is working, using ALSA (another sound system). PulseAudio is much better, because it permits individual sound volume control for applications (play music at low volume while watching a movie on loud volume, but still be notified even louder when an email arrives). PulseAudio also is able to send music to speakers connected to other computers, etc.

So, PulseAudio is not required, but, if you want to make Ubuntu better, report a bug saying that PulseAudio is taking too much CPU. Check if this is not already reported. Maybe it depends on your sound card, because here works without problems.

---

### Post by NCLI on 2009-09-08
CPU temperature really isn't problematic as long as it stays below 80 C guys, take it from someone who has overclocked(and killed) quite a few CPUs.

---

### Post by Robin Nixon on 2009-09-11
The pulseaudio problem is now solved with today's update - it has gone from 80% CPU usage to less than 8%.

---

### Post by forumache on 2009-09-11
> **Robin Nixon said:**
> The pulseaudio problem is now solved with today's update - it has gone from 80% CPU usage to less than 8%.

I'm happy that you didn't give up.

There are some people I know who, when they have a software problem, they just remove the offending software and that's it. But this doesn't help in the long term.
The real solution is to reinstall the offending software (from time to time), see when the problems is solved, report back if an update fixed your problem, etc. Exactly what you did.

Of course, the next step is to participate on launchpad with comments on bugs, then to test an updated package on your computer if the developer want to check if it fixes the bug, and the list can continue ;)

Have a nice weekend, everyone.

---

### Post by autark on 2009-09-11
> **Robin Nixon said:**
> The pulseaudio problem is now solved with today's update - it has gone from 80% CPU usage to less than 8%.

That still sounds like an awful lot of CPU for a daemon. 0.8% or less should be more appropriate, in my opinion.

---

