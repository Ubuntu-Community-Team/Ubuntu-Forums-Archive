---
title: "Need advice for installing to ATA slave HD"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by NutrOn on 2006-03-02
What file system should I format the HD slave to?, its a new seagate ATA and my system is a new Athlon chip, Asus bios
Current HD master is XP and NFTS. Also, do I need bios on slave?, and can I do an Ubuntu install as the only system on the slave and will I be able to boot into either XP or Ubuntu during a Bios bootscreen drive selection or through the bootloader option? Thanks for any help in advance.
NutrOn:???:

---

### Post by drfloob on 2006-03-02
> What file system should I format the HD slave to?That's personal preference ... the most common for linux are ext2, ext3, and reiserfs.  I haven't found a strict comparison between the filesystems yet.> do I need bios on slave?the BIOS is on the motherboard.  maybe you mean boot loader???  Ubuntu provides Grub by default, which (in most cases) will automatically detect your Windows partition and allow you to boot into it ... > can I do an Ubuntu install as the only system on the slave and will I be able to boot into either XP or UbuntuYou sure can.  There's tons of tutorials online about how to do just that ... you can start [here]("http://users.bigpond.net.au/hermanzone/p3.htm") or [here]("https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28boot%29%7C%28dual%29")

---

### Post by Coelocanth on 2006-03-02
IIRC, the difference (or at least, the major difference) between ext2 and ext3 is ext3 is a journalled file system, which means you won't suffer horrible data loss in the case of an unexpected shutdown. Reiserfs is journalled as well, but I'm not sure of the differences between it and ext3.

---

### Post by NutrOn on 2006-03-03
Thanks for the input.
N

---

