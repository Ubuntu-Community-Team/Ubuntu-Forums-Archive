---
title: "Error booting Ubuntu 7.04 CD on ProLiant ML530"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by deltwalrus on 2007-10-01
Hi, folks,

Been pulling what's left of my hair out on this one.  I inherited an HP ProLiant ML530, dual 3GHz Xeon with an HP SmartArray 5300 controller and a bunch of HDDs.  I'd love to load Ubuntu on this bad boy and play around, but cannot get the system to boot off the CD.

I have tried setting noacpi, noapic, and various other boot options, with no success.  The error messages I always get are:

```
[   137.811591]  Uhhuh.  NMI received for unknown reason b1 on CPU 0.
[   137.811593]  You have some hardware problem, likely on the PCI bus.
[   137.811595]  Dazed and confused, but trying to continue
[       1.365632]  Kernel panic - not syncing: No init found.  Try passing init= option to kernel.
[       1.365699]
```

I have Googled these errors to death, and I see bug reports, esoteric musings about how crappy Compaq/HP hardware is, and other not-so-helpful content.  I suspect that the PCI hardware error is likely a red herring, as I have tested the hardware (they're NICs) quite thoroughly.  However, I will try removing them all one by one to see if that actually helps.

I also suspect that the real source of my problem is that the default kernel on this CD has no drivers for the HP SmartArray 5300 controller.  I saw an ISO of a Ubuntu CD that someone built a few years ago, but that torrent is long dead and cold.  I have had zero experience compiling kernels, but would be willing to give it a shot if anyone can help me get started.

Then there's that NMI error... no clue what to make of that.  There are so many errors here I'm not sure which are valid and which are bunk.

So if anyone has had any success in getting our favorite Linux flavor running on this sort of hardware, or if you have any thoughts on how I might further troubleshoot this, please do let me know.

Other things I've tried:

--  Installing ESX (this was my initial goal for this server):  The Anaconda-esque installer runs just fine, sees my logical drives created thru the ROM, and seems to complete successfully, but gives a purple screen of death at boot stating -- among other messages -- "no place on disk to dump data"

--  Using HP SmartStart CD -- After the initial menu, it too fails to boot, stating "unable to mount root fs on ram0"

---

### Post by MobiusNZ on 2007-10-01
Experiment with some boot-line parameters. When the boot menu comes up press F8 or whatever it is that gives you "more options". Scroll to the end of the line and add your parameters.
I've found that often "noapic" helps, or "acpi=off". You can separate multiple parameters by spaces. 

[Here is a fairly complete list and what they do]("http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html")

As for the raid.. I believe it works fine if it is set up in hardware, but I'm not 100% sure

---

### Post by deltwalrus on 2007-10-02
Thanks for the link, I will give those options a try... but I have already tried some of the apic and apci options, to no avail.  I guess there's a combination that I need to stumble upon to get it functioning...

As for the hardware RAID, it is set up now to present all 12 drives as one large RAID-5 chunk of space, so I'm not doing anything too tricky there.

---

### Post by carmon_madison on 2007-11-13
I too inherited a Compaq Proliant ML530. I am having similar issues. Has anyone had any luck resolving this problem? I would prefer to use a Ubuntu LAMP server to get my stuff going but this has been tough.

---

### Post by t3hi3x on 2007-12-15
[http://skydisc.de/downloads/ubuntufeistysmartarray.iso](http://skydisc.de/downloads/ubuntufeistysmartarray.iso)

try this iso. it has the kernel fix to allow you to install on the smart array. give that a shot and see how it works.

---

