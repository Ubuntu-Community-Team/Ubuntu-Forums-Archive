---
title: "Installation Risc-V VisionFive 2 Single Board Computer (SBC) from FiveStar fails"
date: 2023-06-06
forum: Installation &amp; Upgrades
---

### Post by xenonflash on 2023-06-06
I have a VisionFive 2 Single Board Computer and installed according to
[https://wiki.ubuntu.com/RISC-V/StarFive%20VisionFive%202](https://wiki.ubuntu.com/RISC-V/StarFive%20VisionFive%202)
date stamp at the bottom today is
2023-05-18 15:06:55

The bios of the SBC is up-to-date.


I exctracted and prepared the image on a SD-card with balenaEtcher-Portable-1.18.4

I also tried [COLOR=#333333]as stated in the instructions: [/COLOR]
 
> [COLOR=#333333]xzcat ubuntu-23.04-preinstalled-server-riscv64+visionfive2.img.xz | sudo dd bs=1M conv=fsync of=/dev/sdX[/COLOR][COLOR=#333333]
[/COLOR][COLOR=#333333]on a Raspberry Pi 4.

Any attempt to boot these efforts fails with error message
[/COLOR]> BOOT fail,Error is 0xffffffff[COLOR=#333333]

How can I fix this?

Regards, XF

[/COLOR]

---

### Post by MAFoElffen on 2023-06-06
Those Ubuntu Wiki instructions started off by saying that you need to first update the SPL and uboot, which is in Section 4.3 of this: [https://doc-en.rvspace.org/VisionFive2/PDF/VisionFive2_QSG.pdf](https://doc-en.rvspace.org/VisionFive2/PDF/VisionFive2_QSG.pdf)

That is the bootloader for the SBC... You followed those instructions there right? I'm thinking that Etcher and / or the caoomnds you used to write to the MicroSD card is only part of that... Thus the detailed instructions on how to do that to update the flash on the SBC, with the manual commands to do so.

The way the wiki is worded and laid out, it has the bootloader added in separate steps than the system image.

Just an observation. I don't have a Star5, but I have installed it in a RISC-V KVM Guest. So I (myself) have not had to install to a MicroSD. When I did it, I had to do the same, but differently, because I was working with image files, and treated uboot as a QEMU firmware image:
```

  <os>
    <type arch="riscv64" machine="virt">hvm</type>
    <kernel>/usr/lib/u-boot/qemu-riscv64_smode/u-boot.bin</kernel>
    <bootmenu enable="yes"/>
  </os>
...
  <devices>
    <emulator>/usr/bin/qemu-system-riscv64</emulator>
    <disk type="file" device="disk">
      <driver name="qemu" type="qcow2" cache="none"/>
      <source file="/data/KVM-VM/ubuntu-22.04.2-server-riscv64-01.qcow2"/>
      <target dev="vda" bus="virtio"/>
      <boot order="2"/>
      <address type="pci" domain="0x0000" bus="0x04" slot="0x00" function="0x0"/>
    </disk>
...
  </devices>
 
```
So following that same logic... Just saying... There are some more steps than you described, right?

---

