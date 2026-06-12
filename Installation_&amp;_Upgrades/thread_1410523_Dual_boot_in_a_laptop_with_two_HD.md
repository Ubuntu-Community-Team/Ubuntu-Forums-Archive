---
title: "Dual boot in a laptop with two HD"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by antonio-ptg on 2010-02-18
I'll should like to upgrade my laptop by adding a second hard drive (at present a single 160GB HD) and installing a second OS (Linux-Ubuntu) in the second HD.
Is there a BIOS limitation with regards to HD size?
Can the BIOS recognize GRUB in the second HD at start up?
Has someone knowledges about problems or specific procedures with regard a dual-boot system with GRUB in a physical partition on the second HD?
Could someone help me?

Thanks in advance, Antonio.

---

### Post by Herman on 2010-02-19
> Is there a BIOS limitation with regards to HD size?No, probably not if your laptop is made within the last few years. Most modern BIOSes should support modern hard drives sizes. If yours doesn't, complain to your laptop manufacturer and ask for a BIOS update.
> Can the BIOS recognize GRUB in the second HD at start up?No, unless you install a little code in your first hard disk's mbr you will need to go through the inconvenience of having to be watching each time your computer boots and waiting for the right time to hit some key on your keyboard to bring up your BIOS boot menu when you want to boot your non-first hard disk. However, once the BIOS in most computers is guided to the right non-first hard disk it should be okay. Another way is to use some kind of boot loader on a CD to point your BIOS to a non-first MBR.
> Has someone knowledges about problems or specific procedures with regard a dual-boot system with GRUB in a physical partition on the second HD?You may choose the mbr of a non-first hard disk to install the grub mbr code to in step 7 of the installation by pressing the 'advanced' button. Any good installation website should show you how to do that.
Another way might be to unplug your first hard disk and plug in the new one in the first hard drive bay. Just leave the old hard disk out or put the old hard disk in your second hard drive bay and try out Ubuntu for a while. Just ignore the other hard disk and if you need to boot the other operating system then switch hard drive bays again. 

For most computers it's best to just install GRUB to MBR in the first hard disk. In the long run it's more convenient unless you have something different about your computer that you haven't told anyone yet. 

Anyway, it's your computer and it's up to you what you want to do with it. The main thing is to install Ubuntu and have fun. :D

---

