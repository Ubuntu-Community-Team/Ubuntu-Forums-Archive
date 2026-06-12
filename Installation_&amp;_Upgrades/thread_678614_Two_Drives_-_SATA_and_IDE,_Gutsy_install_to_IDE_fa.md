---
title: "Two Drives - SATA and IDE, Gutsy install to IDE fails, sorta"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by Swampfoot on 2008-01-26
System:

Processor: AMD Athlon 64 X2 4200+ Dual-Core - 2.2GHz
Motherboard: Asus M2NBP-VM (nvidia GeForce 6150 Integrated Video, nForce SATA)
1gb RAM
320 gb SATA Hard Drive (XP Pro install there)
160 GB IDE Hard Drive (set to master on its chain)
two DVD-RW drives on the other IDE chain

Don't remember if I have the 160 GB drive on the Primary or Secondary IDE chain. Have to open her up to see about that.

Acronis OS Selector is on the SATA drive, from a previous attempt at OS X.

7.10 i386 Live CD boots perfectly, runs ethernet, graphics and sound perfectly.
(I initially tried the 64-bit AMD CD, but "ubiquity" kept crashing on me)

When I run the installer, I choose the 160GB IDE drive, choose Manual partitioning, set a 50 G partition to ext3, "/", then set a 2 GB swap partition. I leave the rest as a FAT32 partition.

Here's where it gets interesting - when I am presented with that screen that has an "Advanced" button near the bottom, which lets you choose to install the bootloader or not, if I click on "Advanced" and tell it to install the bootloader (it defaults to hd0 I think?), the installer just hangs at a progress window called "finding partitions" (or something like that, I don't recall exactly) at 15%. Nothing proceeds. I even let it sit for two hours to see if it would eventually come to life.

But if I tell the advanced button to NOT install the bootloader, the install proceeds normally, and I get the "restart your computer" prompt at the end. If I boot back into the Live CD, I can see that the installer has deposited a filesystem and folders into the correct partition on the IDE drive.

But I cannot boot from it. If I set the SATA drive to be first in the BIOS, Acronis loads, but it will not see the ext3 partition on the IDE drive, no way, no how. So I can't tell Acronis to boot from the fresh Ubuntu install. If I set the IDE drive to be first in line on boot, then when the machine starts up I just get a flashing white cursor at the top of the screen. No booting into the fresh Ubuntu install.

I don't see any sign of the grub bootloader everyone is talking about.

I really need some help, I guess. I can use the terminal if I am told exactly what to type, so I guess that means I don't really use the terminal. :-)

Thanks for any answers!

---

### Post by bufsabre666 on 2008-01-26
change the boot order inside the bios cause it sounds like the sata gets dominence over the ide, so put the ide ontop and since it instlled the boot manager it should list the other operating system in the grub too

---

### Post by Swampfoot on 2008-01-26
Got it to work!

After searching the forums, the hanging during install issue was solved by simply disconnecting the SATA drive (the one with XP and Acronis OS Selector on it). Installed Ubuntu normally onto the IDE drive. After allowing Ubuntu to do all its updates, I reconnected the SATA drive, chose it as the first boot device in BIOS, and Acronis loaded normally - and it saw the Ubuntu install! Listed it as "Linux."

Now I am dual booting! Without having to use the BIOS screen.

---

