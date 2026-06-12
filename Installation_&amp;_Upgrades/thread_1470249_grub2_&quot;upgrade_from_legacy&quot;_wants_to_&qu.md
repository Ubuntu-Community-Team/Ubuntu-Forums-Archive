---
title: "grub2 &quot;upgrade from legacy&quot; wants to &quot;GRUB install devices&quot;"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by AngusM on 2010-05-02
I've installed grub2 on 10.04, when I restarted I selected that option in the menu that seems to go for testing the chainloader. The system seemed to start ok, so I ran upgrade-from-grub-legacy. Now it's asking me for "GRUB install devices" and listing my hard drive (/dev/sda) and the 5 partitions on it as possible options. Which should I choose? I have Linux and Windoze running on this desktop, so grub should be able to start either.

---

### Post by frantid on 2010-05-02
you need it in the MBR, so if you have one drive /dev/sda

The problem some are having is when it installs into the partitions. -- UNLESS you have multiple linux distro's or a dedicated grub partition, put it in the MBR.

---

### Post by Hilko on 2010-05-09
> **frantid said:**
> you need it in the MBR, so if you have one drive /dev/sda

The problem some are having is when it installs into the partitions. -- UNLESS you have multiple linux distro's or a dedicated grub partition, put it in the MBR.

So if I have a dedicated GRUB partition using GRUB legacy, what should I do?

Do I need to upgrade my GRUB partition to GRUB2?

Should I install GRUB2?   If so; Where?

---

### Post by zeefreak on 2011-06-17
> **frantid said:**
> you need it in the MBR, so if you have one drive /dev/sda

The problem some are having is when it installs into the partitions. -- UNLESS you have multiple linux distro's or a dedicated grub partition, put it in the MBR.

i'm afraid this response is very unclear. i'm having a similar problem, and my options [on a system with only one ubuntu install] are:

```
[ ] /dev/sda (8589 MB, VBOX_HARDDISK)
[ ] - /dev/sda5 (254 MB, /boot)
```

is what you mean by 'put it in the MBR' put it outside any partition, in this case /dev/sda?

my understanding of boot loaders is that it would have to go on the disk, outside of any partitions, as the bios wouldn't have any way of determining partitioning information to get to grub if it was at /boot, but maybe i'm wrong.

my understanding of grub specifically is that it has at least 2 stages, stage1 that runs from the disk, and stage2 that runs from /boot. unfortunately, this doesn't help me choose which [or both] selections on the 'configuring grub-pc' screen i have before me.

it has been years since i had to do anything with boot loaders manually, and i'm afraid my brain is a use it or lose it storage medium. ;)

---

### Post by oldfred on 2011-06-17
As long as we are using BIOS and MBR(msdos) partitioning you have to install a boot loader to the MBR or first sector of the boot drive. Or sda in Linux if only one drive.

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

Newer SATA drives have updated BIOS that let you select boot drive with BIOS, but it still has to jump to the MBR to find more code to boot. MBR is tiny so that just jumps somewhere else on drive to continue the boot process.

This shows Vista & XP (mentions lilo at end), but shows MBR, PBR and how BIOS & MBR computers boot. Grub does not use PBR normally and grub2 highly recommends not to use PBR.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

