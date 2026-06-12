---
title: "nvidia drivers is not working ubuntu still uses onboard card."
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by merajul_islam2 on 2014-10-26
Heello I am new to ubuntu. I have installed Ubuntu LTS 14.04. 
After installing it I have inStalled nvdia 331.38 for my eternal graphics (GT9500). Then it was orking properly but the problem started when I updated my ubuntu.I have onboard graphics(intel) and i think it
got installed and crating problem. The graphics setting xorg.conf is not working every time I restart pc I have to change the settings. Pc restarted ferquently and graphics got hang. I check there is to graphics the output is bello: 




**lshw -c video | grep 'configuration':- **


configuration: driver=nvidia latency=0
configuration: latency=0

**lshw -c video:-**


 *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9500 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:45 memory:c2000000-c2ffffff memory:a0000000-bfffffff memory:c0000000-c1ffffff ioport:e000(size=128) memory:c3000000-c307ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller cap_list
       configuration: latency=0
       resources: memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:f0f0(size=8)




Please help me in this situation. tell me what to do

---

### Post by Vladlenin5000 on 2014-10-26
Hi, welcome.

No, you aren't using the integrated graphics but in order to be sure you can - and should - disable it at BIOS/UEFI and never connect any cable to the onboard's output(s).

---

### Post by merajul_islam2 on 2014-10-26
Then why my pc is restarting ? also desired refresh rate is not staying what i choose it changes every time i restart.

---

### Post by merajul_islam2 on 2014-10-26
[COLOR=#000000]Then why my pc is restarting ? also desired refresh rate is not staying what i choose it changes every time i restart.[/COLOR]

---

### Post by Vladlenin5000 on 2014-10-26
> **merajul_islam2 said:**
> [COLOR=#000000]Then why my pc is restarting ? also desired refresh rate is not staying what i choose it changes every time i restart.[/COLOR]

A non sequitur fallacy. 
Again, if you don't intend to use the integrated graphics just disable it at BIOS/UEFI. Then we can start some troubleshooting.

---

### Post by merajul_islam2 on 2014-10-26
I disabled it but same thing happening . :(

---

### Post by Vladlenin5000 on 2014-10-26
Thank you. It was a "just in case" thing anyway because from the start the integrated one was showing as unclaimed and the nvidia apparently is running with the correct drivers. That said just a couple of questions that hopefully will clarify some additional details:
Why do you have a xorg.conf? Is it because you have an old monitor? If so, what monitor and what connection are you using?
Please also try to make the changes you (think) you need at "NVIDIA X Server Settings" then reboot and check what happens.

Obs.: All this troubleshooting assumes the hardware is fine. Have you tested it before, let's say, with a different OS?

---

### Post by merajul_islam2 on 2014-10-26
My monitor is old one. My monitor is Samsung syncmaster 550. I am using vga with vga to dvi converter. I did it at a [COLOR=#000000]NVIDIA X Server Settings a[/COLOR]nd nothing happens.

---

