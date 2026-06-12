---
title: "No bootable device after Server 20.04.3 install"
date: 2021-12-07
forum: Installation &amp; Upgrades
---

### Post by Dustin Wyatt on 2021-12-07
Installing from USB flash drive with ISO burned with rufus.

i7-4790k on an Asus Z87A motherboard.

One SSD in the system, installing to whole disk without LVM.

Install progresses until I get a [[Reboot Now] button which I "click"]("https://i.imgur.com/Qnm9bNu.jpeg"). 

After prompting, I remove the flash drive and press ENTER.

System now only boots directly to BIOS.  In an attempt to fix, I can bring up the BIOS "Boot Menu" and select the SSD but it again just boots to BIOS.

I attempt using Boot-Repair-Disk, but it did not fix the problem.  [Here is the pastebin of the results of that]("https://pastebin.ubuntu.com/p/jHYYVM4WVF/").

In an attempt to diagnose if this is a hardware problem of some sort, I downloaded the 20.04.01 iso that uses the old debian installer.  I burned this to flash drive using rufus. **This installs correctly and makes a bootable system!**

At this point, I do not know what to try next.

---

### Post by sudodus on 2021-12-07
I suggest that you continue to use the system that you installed via the 20.04.01 iso that uses the old debian installer. You can either stay with the original kernel series or upgrade it via the HWE stack according to [this link](https://wiki.ubuntu.com/Kernel/LTSEnablementStack).

Let us hope that the next LTS version of the server will get a better installer [than the current curtin installer] because the debian installer will no longer be available.

---

### Post by tea for one on 2021-12-07
> **sudodus said:**
> I suggest that you continue to use the system that you installed via the 20.04.01 iso that uses the old debian installer. You can either stay with the original kernel series or upgrade it via the HWE stack according to [this link](https://wiki.ubuntu.com/Kernel/LTSEnablementStack).

Let us hope that the next LTS version of the server will get a better installer [than the current curtin installer] because the debian installer will no longer be available.

Yes, I agree with [COLOR="#0000FF"]sudodus[/COLOR] - as you are up and running then continue with a working system.

I will add that you have installed in the older BIOS mode rather than UEFI mode as shown by
[COLOR="#0000FF"]Line 58[/COLOR]  - File system:       BIOS Boot partition
[COLOR="#0000FF"]Line 103[/COLOR] - sda	: is-GPT,	hasBIOSboot,	has-noESP, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes

Was that a deliberate choice?

---

### Post by ActionParsnip on 2021-12-07
If you boot the USB but select to boot the first disk from there does it boot OK (I think that's a feature of the USB installer)

---

