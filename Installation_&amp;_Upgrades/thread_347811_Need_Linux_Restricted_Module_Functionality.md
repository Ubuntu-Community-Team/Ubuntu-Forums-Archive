---
title: "Need Linux Restricted Module Functionality"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by mlissner on 2007-01-27
I just upgraded my kernel in hopes that it would fix a problem I've been having, as mentioned here (still unresolved), and now I have a new problem. The new kernel, 2.6.19.2, doesn't make my wireless card work. In fact, my wireless card doesn't even show up in the network manager list, so I guess that's where to start. It does show up in my lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
05:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8167 (rev 10)
```

In the past I fixed this by installing the restricted kernel modules via synaptic, but those are for a different kernel version.

Any ideas on how to make my wireless work? I've searched around to no avail. Lots of complicated ideas, but none that will work for me...

My card is an Intel 3945ABG, and my computer is an Asus A69F.

---

### Post by bernied on 2007-01-27
I'm not familiar with the card myself, but I found [this](http://ipw3945.sourceforge.net/)
Post back if you have trouble translating - it might be worth looking for a ubuntu package called ipw3945 before you do anything else. 
Read all README files that you see along the way, and google anything you don't understand.

Are you sure this could not have been done with the standard ubuntu kernel?

---

### Post by bernied on 2007-01-27
Just read your hard-drive thread, ouch!
I feel your pain.
(but alas no solutions from me)

---

### Post by mlissner on 2007-01-27
Yeah, getting new hardware on a laptop to work is even harder than I had ever imagined. 

I did discover one thing a moment ago that is somewhat interesting regarding the harddrive problems - My swap space wasn't enabled for some reason when edgy got upgraded. That's fixed, so we'll see if all is well in a few hours if nothing has gone wrong.

About that link, I've more than looked there, I've tried the thing it suggests, and they are ludicrously complicated. It involves enabling kernel modules, installing about four different binaries from different places, and doing about 20 things that I have no idea what they mean (which says, something, but not a whole lot). I'd like avoid the route of that website if possible. It's WAY complicated.

On a side note, I've booted into my old kernel for the moment, and the wireless still works on it, though I did like the concept of a somewhat more custom kernel.

---

### Post by mlissner on 2007-01-28
Update: I installed ipw3945 that I found here:
[http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fcontrib%2Fi%2Fipw3945%2Fipw3945-source_1.1.2-7_all.deb&md5sum=9668f95fb5b25ba563941ea4f873fcce&arch=all&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fcontrib%2Fi%2Fipw3945%2Fipw3945-source_1.1.2-7_all.deb&md5sum=9668f95fb5b25ba563941ea4f873fcce&arch=all&type=main)

Installed OK. Still no wireless.

---

### Post by mlissner on 2007-01-28
Another note: I've been at this ALL DAY. The amount of difficulty I'm experiencing is more than I have ever dealt with, and I'm beginning to lose it. Can somebody please help? Maybe you'll see something I'm missing.

So far, I've installed the ipw3945d, the ipw3945 modules, the microcode, the ieee80211 thing. I don't really know what any of this does, but it seems that it's all conflicting with other stuff, failing giving weird and useless tips as to make it work, etc.

I know this isn't that hard? Are there just some debs I can install or something to make this work? Please help me. I can't continue working on this problem anymore, and I feel like I've read everything possible on the subject.

---

### Post by bernied on 2007-01-28
> **mlissner said:**
> I know this isn't that hard? Are there just some debs I can install or something to make this work? Please help me. I can't continue working on this problem anymore, and I feel like I've read everything possible on the subject.

I think that this stuff is very hard, and fiddling with the guts of your machine is not always pleasant. Wireless networking is not straightforward in linux, that's why we let the ubuntu folk compile our kernels and sort out our drivers. 

Are you convinced that this new kernel is what you need to fix your hard-drive problems? Because if it is not, then you can stick with the generic kernel and modules.

---

### Post by mlissner on 2007-01-28
Well, actually, I've discovered the harddrive problem is actually a DVD drive problem, and no, the new kernel didn't fix that. However, it did give me a bit of a speed boost ( think), and it did make suspend work, as well as a number of other small improvements, so I'd like to stay with the new kernel, despite it not working with wireless.

So there're three problems: The DVD drive problem (formerly the HD problem, which I have "fixed" by removing the drive for the moment), the suspend/hibernate problem, wherein they don't work unless I have kernel 2.6.19, and the wireless problem (wherein it doesn't work in kernel 2.6.19, but does in 2.16.17).

None of these problems seem to have fixes that are really anything more than "fixes".

---

### Post by mlissner on 2007-02-01
I finally had an epiphany tonight, though I'll tell you up front - my DVD problems remain. To get the wireless in an updated kernel, the trick is to use the feisty kernel with the feisty restricted modules package as described [here]("http://www.ubuntuforums.org/showthread.php?t=333808&highlight=fiesty+kernel").

So I guess that's one problem down...I still need to figure out my ata2 stalling problem though...

---

