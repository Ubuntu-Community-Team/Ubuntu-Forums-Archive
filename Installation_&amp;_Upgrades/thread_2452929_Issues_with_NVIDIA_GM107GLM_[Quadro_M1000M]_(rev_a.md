---
title: "Issues with NVIDIA GM107GLM [Quadro M1000M] (rev a2) on Ubuntu 20.04"
date: 2020-10-30
forum: Installation &amp; Upgrades
---

### Post by etcusr on 2020-10-30
All
I'm having a problem on my HP Zbook, G3 in Ubuntu 20.04 with the video on FoxitReader and Google Chrome browser. I resize the FoxitReader window, the application freezes (see screen shot), and if I close the lid and open Google Chrome browser locks up. I have installed the Nvidia drivers with no issues and problem is mainly with those two applications all the time. 

Here's the output from lspci:  
01:00.0 VGA compatible controller: NVIDIA Corporation GM107GLM [Quadro M1000M] (rev a2)

lshw
*-display
                description: VGA compatible controller
                product: GM107GLM [Quadro M1000M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:143 memory:e4000000-e4ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:3000(size=128) memory:e5080000-e50fffff


Here's a screen shot of the Nvidia and the Foxit PDF Reader issue. Chrome browser locks up, the video pixels fall apart if I mouse over the browser, and I have to kill the process. Thanks for you help in advance.


[ATTACH=CONFIG]287258[/ATTACH][ATTACH=CONFIG]287259[/ATTACH]

---

### Post by CelticWarrior on 2020-10-30
Welcome.

Not sure it helps but it's worth trying:

At "X Server Display Configuration" > Advanced... try enabling "Force full composition pipeline".
Reboot and test the same scenario.

---

### Post by etcusr on 2020-10-30
"Force full composition pipeline" option not available under X Server Display Configuration" > Advanced.

[ATTACH=CONFIG]287260[/ATTACH]

I toggled all the drop downs and no joy.

---

### Post by ubfan1 on 2020-10-31
About 10 months ago when using the M1000M, I recall the 435 driver was the latest it used, even though the 440 was available.  You are using the 450, so try removing it and installing an older driver, like the 435.

---

