---
title: "Screen server cannot load. Nvidia problem?"
date: 2017-02-07
forum: MINT
---

### Post by yoramdavid on 2017-02-07
Hi,

I just installed Linux Mint Mate 18.1 two days ago. (Checksums of the download were verified and the integrity of the install medium was also checked).
Yesterday, I rebooted a few times to test and all was good regarding the screen.
Today as I wanted to boot into the system, I could not. After a few flickers of the screen, I get this message error:
[HTML]The screen server was terminated about 6 times on the last 90 seconds. It is probable that something weird is going on. You will have to wait 2 minutes before trying again the screen :0.[/HTML]

I was having the exact same issue with Linux Mint Mate 18, then I installed 18.1 hoping the problem had been solved.

I tried to boot using the "nomodeset" boot option, but I get the exact same message.
Pressing the space bar brings me to a balck screen with text on it where at the bottom of the message this line appears:
[***] A start job is running for LSB: Start NTP daemon (1min 9s / 5min)
After some time, I get back to the previous error message I mentioned.

When the system was working fine, I went to check the proprietary drivers and there was no nVidia listed there, only a "amd64-microcode" entry. Not selected.
The driver manager did not find any drivers to install.
In synaptic, some nVidia drivers seemed to be installed.
I cannot remember which.

Firefox and Thunderbird & chromium crashes at loading.

I cannot check the hardware specifications as I cannot get into the system, but according to an old threat of mine, it is the following:
Motherboard:
Asus A7N8X Deluxe (5 PCI, 1 AGP Pro, 3 DIMM, Audio, Dual LAN, IEEE-1394)
AGP Pro/8X
Motherboard Chipset:
nVIDIA nForce2 SPP
Graphic card:
NVIDIA GeForce FX 5700LE
Processor: AMD 1.6Ghz

It is similar to this [threat]("https://forums.linuxmint.com/viewtopic.php?t=236381").

---

### Post by howefield on 2017-02-07
Thread moved to the "*MINT*" forum.

---

### Post by yoramdavid on 2017-02-07
Editing the gub menu on boot-up and adding the line > nomodeset  grub_gfxmode=1280x1024x24
Gave me a low resolution desktop. I installed nvidia-304

Still no luck. I get the same error message, now with a lower screen resolution.

There was an warning: > No support for locale: pt_PT.uft8
I use that language system-wide.

---

