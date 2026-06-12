---
title: "Does 24.04 Live USB do verification on startup?"
date: 2024-10-03
forum: Installation &amp; Upgrades
---

### Post by echaskaris on 2024-10-03
I remember this being a thing in older usbs I made.
I'm trying to install 24.04, but there is no progress shown on screen, just purple and the USB flashing, and occasionally stopping.
I'm installing on a Legacy Bios laptop with USB 2.0.
Any idea what's wrong? Thank you.

---

### Post by echaskaris on 2024-10-03
Booted from a desktop and booted fast with no issue and no file verification.
There must be some bug preventing it from working on the laptop. I can't blame it though, laptop is a bit old.

---

### Post by ajgreeny on 2024-10-03
It's impossible to help much without some idea about the hardware of your laptop. A laptop which is legacy boot only and does not offer UEFI must be earlier than the hardware needed for Ubuntu 24.04

I suggest firstly you should try a lower resource requiring version (Xubuntu, Lubuntu) rather than the default gnome Ubuntu which needs better hardware than you probably have at present.

If you really want Ubuntu, see if it will boot to the live desktop GUI, open a terminal and run command **inxi -fzx** then post back here the output you see.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by echaskaris on 2024-10-03
The laptop runs 22.04 fine. It's a Lenovo Thinkpad L520 with 4GB RAM.
It doesn't enter gnome I think. If I remove the quiet and splash boot parameters it doesn't get stuck with an error.
Maybe I'll do more testing and report a bug.

---

### Post by ajgreeny on 2024-10-03
4G ram is minimal for Ubuntu 24.04 so I still suspect your low resource hardware but to be more sure please run the inxi command I asked for earlier.

---

### Post by grahammechanical on 2024-10-03
I am not sure what you mean by verification. My experience installing Ubuntu 20.04 LTS and 20.10 beta is that it takes time. A lot of time. Even on a NVME drive and longer on a SATA hard drive. I almost gave up waiting thinking the process had stopped.

From 24.04 LTS a different installer program is used. After some time we get a Ubuntu splash screen with the Ubuntu icon screen bottom & centre. Then, after a time a purple screen with a line drawing of a numbat (24.04) or an oriole (24.10) appears. Following this is a white panel that says "processing Ubuntu."  All of this takes a long time. Once we have worked our way through the install choices the slide show begins.

In the past the installer would inform us of what packages were being installed. This does not happen anymore. We are told "Installing system" and "setting up the system." All the while red stripes chase each other from left to right at the bottom of the panel.

In the past when we installed from DVD we could hear the DVD spinning and the hard drive spinning. With USB memory stick and SSD/NVME there is no sound. It is easy to get fooled into thinking the process has stopped.

Regards

---

### Post by guiverc on 2024-10-03
Ubuntu has various products & release, and there is variation between them.

Yes modern Ubuntu install media does self-verify; however the verification process has varied over time.  A decade+ ago there was a menu items that triggered that verification, then it was moved to a *automatic* process that was very visible & caused boot to pause (*though the verification could be cancelled** if you were fast enough*), but due to complaints about waiting, the process was switched to a background one which is still used today.

Myself, if I've not verified the install media before, I'll wait for the background verification to complete before I actually install, I do that as the machine is more responsive when its completed AND I know media problems won't negatively impact installs.

If you want to know more about media checks; I'll provide a link to an answer I've written on another support site - [https://askubuntu.com/questions/1311183/do-i-need-to-check-the-integrity-of-a-ubuntu-install](https://askubuntu.com/questions/1311183/do-i-need-to-check-the-integrity-of-a-ubuntu-install)

You only specify release, Ubuntu 24.04 LTS ISOs are available using three installers and what I mentioned I know applies to `calamares` and `ubuntu-desktop-installer` (Ubuntu 24.04 Desktop & *flavors*) but I believe would also apply to `subiquity` ISOs (Ubuntu 24.04 LTS Server)

---

### Post by echaskaris on 2024-10-04
Thank you for the replies, here is the inxi command output

```
CPU:
  Info: dual core model: Intel Pentium B960 bits: 64 type: MCP
    arch: Sandy Bridge rev: 7 cache: L1: 128 KiB L2: 512 KiB L3: 2 MiB
  Speed (MHz): avg: 798 min/max: 800/2200 cores: 1: 798 2: 798
    bogomips: 8780
  Flags: acpi aperfmperf apic arat arch_perfmon bts clflush cmov
    constant_tsc cpuid cx16 cx8 de ds_cpl dtes64 dtherm dts epb est flush_l1d
    fpu fxsr ht ibpb ibrs lahf_lm lm mca mce md_clear mmx monitor msr mtrr
    nonstop_tsc nopl nx pae pat pbe pcid pclmulqdq pdcm pebs pge pln pni
    popcnt pse pse36 pti pts rdtscp rep_good sep ssbd sse sse2 sse4_1 sse4_2
    ssse3 stibp syscall tm tm2 tsc tsc_deadline_timer vme x2apic xsave
    xsaveopt xtopology xtpr



```

I still think it's some bug, 22.04 live usb opened and installed fine, and fast too.

---

### Post by echaskaris on 2024-10-06
Setting "nomodeset" kernel parameter fixed the booting issue, will try to upgrade 22.04 to 24.04 sometime.

---

### Post by oldfred on 2024-10-06
Similar thread. Suggest more RAM, faster drive, and lightweight flavor for older BIOS only systems.
[https://ubuntuforums.org/showthread.php?t=2501391](https://ubuntuforums.org/showthread.php?t=2501391)

---

