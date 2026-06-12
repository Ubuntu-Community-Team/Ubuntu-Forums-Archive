---
title: "can't boot live cd or install due to videocard"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by azimech49 on 2010-01-04
hi everyone, i been looking for a solution but i just can't find a solution for this, so here i am.

My specs:

Intel D945GCNL (bios updated) mobo
Pentium Dual CPU E2180 @ 2ghz
2GB RAM @ 667mhz
Geforce 8400GS 256Mb pcie (the culprit)

i've tried live cd boot from these OS:

Ubuntu: 6.06, 7.04, 8.(something), 9.04
Kubuntu: 6.10

computer stops working while on booting logo.

I also removed video card and installed flawlessly all of above os' and it will freeze in the same point once i install videocard again.

Safe mode leads to same results so can't boot in any way to try to solve it.

Suggestions?

---

### Post by presence1960 on 2010-01-04
> **azimech49 said:**
> hi everyone, i been looking for a solution but i just can't find a solution for this, so here i am.

My specs:

Intel D945GCNL (bios updated) mobo
Pentium Dual CPU E2180 @ 2ghz
2GB RAM @ 667mhz
Geforce 8400GS 256Mb pcie (the culprit)

i've tried live cd boot from these OS:

Ubuntu: 6.06, 7.04, 8.(something), 9.04
Kubuntu: 6.10

computer stops working while on booting logo.

I also removed video card and installed flawlessly all of above os' and it will freeze in the same point once i install videocard again.

Safe mode leads to same results so can't boot in any way to try to solve it.

Suggestions?

When booting the Live CD at the menu hit F4. Then select safe graphics mode. This should allow you to install with the Nvidia card. See [here]("https://help.ubuntu.com/community/BootOptions") for more details.

Once installed boot back into Ubuntu & open a terminal and run these commands one at a time:

```
sudo apt-get install envyng-core
sudo apt-get install envyng-qt
sudo apt-get install envyng-gtk
```

This will install EnvyNG which should be able to install the driver for your Nvidia card. To do this in terminal run ```
envyng -t
```
Follow the prompts to install the driver for your Nvidia card.

If by chance you can't boot into Ubuntu try booting into recovery mode. Let it load may take a while. Select netroot then run those commands listed above to install EnvyNG and then run ```
envyng -t
```

P.S. Don't use any version lower than 8.04 as they are unsupported now.

---

### Post by azimech49 on 2010-01-27
Hello Im back here.
 
Today i deleted my hard drive so i could try again and found this:
 
When booting, i received an 'abnormal exit' from this pci device:

pci: v00008086d00002770sv00008086sd0000d606bc06sc00i00
 
I did a small research and determined it was not related to the video card, but Intel Corporation's "Host Bridge/DRAM Controller".
 
I deactivated 'Compliance Test Pattern' on PCI settings on Bios. This setting allows Integrated Video Card to work along with pci-e video card so i can have up to three monitors on windows, useless for me and that was the conflict.
 
That made the trick, I can start ubuntu normally now. Wrote all this as reference for others.
 
Now I have to install the network card (CNET PRO200WL) because integrated is broken :p.
 
Thank you very much for your help :D.

---

