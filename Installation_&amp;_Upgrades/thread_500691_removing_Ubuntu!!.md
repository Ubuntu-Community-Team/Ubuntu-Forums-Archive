---
title: "removing Ubuntu!!"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by ENN0 on 2007-07-14
Hello,i have a lartop and am running the 64 bit of ubuntu fiesty fawn...i have windows xp on my laptops HDD and ubuntu on my external HDD...whenever i start up my computer without the HDD on and plugged in i get ```
error loading bios command
```...so this makes my laptop not portable...so how do i remove it from my external HDD???

---

### Post by bernied on 2007-07-14
It sounds like your bootloader is installed on the external hdd, so the only way you can boot is if it is connected. This means that the master boot record (mbr) of your internal disk is pointing at the external device, where grub (the bootloader) is installed. grub then boots either windows or feisty, but not if the disk is not attached.

You could either:
- install grub onto the mbr of the external drive, reinstate the windows mbr on the internal drive, then set your bios to boot to the external drive first and the internal drive second (this might be limited by your bios, check that it can boot to the device before reinstating your windows mbr)
OR
- create a small (10MB is plenty) partition on the internal hdd, where you install grub and nothing else. Then setup grub to boot either to the external disk (ubuntu) or the internal disk. 

Make sure you understand what you are trying to do before you start, or you will end up with a mcahine that boots nothing.

---

### Post by ENN0 on 2007-07-14
ok..so i installed a new OS like feodra where my windows was would i be able to start me computer normally without the externam HDD?or would i dtill get the same msg?

---

### Post by bernied on 2007-07-14
that might solve the problem, so long as the new install added a bootloader. you would then have to figure out how to add ubuntu to that bootloader's options, if it didn't happen automatically

---

### Post by ENN0 on 2007-07-14
the main thing i would like to do is just completely wipe ubuntu off my External HDD...is there any chance of that?

---

### Post by AusIV4 on 2007-07-14
> **ENN0 said:**
> the main thing i would like to do is just completely wipe ubuntu off my External HDD...is there any chance of that?

You could just format your external hard drive, but that isn't going to fix the problem. You need to tell the laptop that the bootloader is on the hard drive in the laptop. You can do this either with Grub, or using repair functions from the Windows install CD.

---

### Post by bernied on 2007-07-14
What AusIV4 said - use a windows cd to reinstall the windows mbr. You can also a free alternative like FreeDOS. I believe the command is fixmbr, once you get a DOS shell from either the Windows cd or FreeDOS.

Once you know you have windows running independently, you can merrily format the external drive - or whatever.

---

### Post by ENN0 on 2007-07-14
thanks alot for the help :)

---

