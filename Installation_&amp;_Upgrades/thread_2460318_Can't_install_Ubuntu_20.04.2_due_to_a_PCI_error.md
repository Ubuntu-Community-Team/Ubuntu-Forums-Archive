---
title: "Can't install Ubuntu 20.04.2 due to a PCI error?"
date: 2021-04-07
forum: Installation &amp; Upgrades
---

### Post by rbelli97 on 2021-04-07
First of all, hi! I'm new in this forum. In fact, I created this account just because this problem I'm facing is a long standing one and I wanted to install Ubuntu for a long time but this always prevented me from doing it. Alright so here it is:

Whenever I try to install any flavor of *buntu, I ALWAYS run into this problem; a process taking up all of my CPU and after a while, it crashes. It shows some PCI errors non-stop also, and following some guides online i tried to fix it but never actually succeeded. I wanted to try again now but still couldn't.

My PC is a laptop, it's an ASUS X541UVK with an i7 7500U and Geforce 920MX. At first I thought that there was a problem with the Nvidia GPU but it appears to be with the realtek BT card. I went to follow this guide: 

[https://forums.linuxmint.com/viewtopic.php?t=305970](https://forums.linuxmint.com/viewtopic.php?t=305970)

(since using pci=nomsi once solved the issue some time ago)
And the reproduced steps from the guide above are here (from the live usb):

[https://imgur.com/a/enq5UCt](https://imgur.com/a/enq5UCt)

Now, after the final step using modprobe nothing happens. How do I solve this? I really want to use Ubuntu on this pc, but in this condition I can't even use the live desktop from "Try Ubuntu without installing". Thanks for your patience.


[IMG]https://imgur.com/a/enq5UCt[/IMG]

---

### Post by CelticWarrior on 2021-04-07
Welcome.

Before anything else, update UEFI and SSD's firmware if available.

---

### Post by rbelli97 on 2021-04-07
Hi, thanks for the reply. I already updated everything but the issue still persists

---

### Post by CelticWarrior on 2021-04-07
Exactly what errors are you getting and when?

---

### Post by rbelli97 on 2021-04-07
I get this error: [https://i.imgur.com/PPZ49lL.jpg](https://i.imgur.com/PPZ49lL.jpg) after a while of using the live desktop. Gnome starts with max cpu, then crashes, then this appears, then gnome restarts and after a while it freezes.. only thing I can do next it to force shutdown with the power button. This also happens with a KDE-based distro

---

### Post by CelticWarrior on 2021-04-07
Try the following boot parameter instead
```
[COLOR=#242729][FONT=Consolas]pcie_aspm=off[/FONT][/COLOR]
```

---

### Post by rbelli97 on 2021-04-07
All right, I tried with both this option AND this option + pci=nomsi.
Here is the first video showing the result using pci=nomsi and pcie_aspm=off:

[https://streamable.com/5ayfnh](https://streamable.com/5ayfnh)

In this video the text in black says:
tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xSomething-0xSomething flags 0x200] vs fed40080 f80
tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xSomething-0xSomething flags 0x200] vs fed40080 f80
nouveau 0000:01:00.0: bus: MMIO read of 00000000 FAULT at 6013d4

And here is the video using only the extra option pcie_aspm=off:

[https://streamable.com/2ppixz](https://streamable.com/2ppixz)

This produces the same behavior as described above; Ubuntu's main screen appears, then it crashes for a few seconds showing the black text as I described, and then the desktop resumes normally. I don't know what to do now, what does noveau mean? I thought the problem didn't have to do nothing with the Nvidia GPU? I'm at a loss honestly, but I don't feel secure to go ahead and wipe install Ubuntu on my laptop since it's the only pc I have...

---

### Post by oldfred on 2021-04-07
Seems to be an issue with many systems &  Linux versions.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173)

Various reports of fixes or what may work, but not consistent.
Suggest reviewing entire bug report
These were all mentioned.
UEFI update and change fastboot to  "Minimal" instead of "Through"
pcie_aspm=off seemed best but these also mentioned
pci=nomsi or pci=noaer

If nVidia you also need nomodeset or better to install nVidia driver.

---

### Post by rbelli97 on 2021-04-07
Ok, thanks. What's the difference between the two? Also, in case I install the full OS, will a future update to the system break this? Can I use all of them or one excludes the others? The Nvidia Drivers you mean the proprietary ones?
Sorry for the number of questions I just want to be very safe this is my only pc. Thanks again for your time and patience.

---

### Post by bjorn-helgaas on 2021-09-09
Please try booting with "pci=noaer".  This turns off the Advanced Error Reporting feature, which is what prints the messages like:

  PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
  ...

I think there's a Linux defect in the AER code that means we don't clear the error report, so we log it again and again.

"pcie_aspm=off" turns off some Active State Power Management, and is probably unrelated to the problem you're seeing.  "pci=nomsi" turns off Message Signaled Interrupts, which is probably also unrelated.

I don't know how Ubuntu updates handle kernel parameters.  But "pci=noaer" is very safe to use.  The AER reporting can help diagnose hardware problems, but in your case I don't think you're seeing a real hardware problem, just a software problem in handling the interrupt.  If the update loses "pci=noaer", worst case is that you'll start seeing these errors again.

---

### Post by rbelli97 on 2021-09-23
Ok so I created a new bug report with some new information and with some additional output from suggestions received. You can find it here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1944752](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1944752)
Cheers!

---

