---
title: "No Grub menu for OS on USB HD-GPT"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by phredbull on 2011-01-25
Hi, I have an external USB drive with Mint9 Fluxbox installed on it. At one point, I wiped the drive and set it up using GPT instead of MFT, then partitioned the drive in GParted and installed the OS.
This setup was working fine, but now I have a new laptop, and the OS won't boot. I just saw the errors, "No such partition: UUID=xxx", "Could not find kernel, hit any key to continue". So I attempted to reinstall GRUB via terminal, but saw errors saying that GPT requires a grub_bios partition. So I made a 1mb partition at the end of the drive, (the only unallocated space without moving anything) and selected the grub_bios flag.
I was then able to reinstall Grub without incident, rebooted, selected the USB drive to boot first in bios, but still no Grub menu!?! It just boots from the next device in the bios list.
I'm currently using Crunchbang on a USB stick, which is where I'm running terminal commands from. I want to be able to boot from my external drive on any computer.
Help please?

---

### Post by srs5694 on 2011-01-25
It's possible you've run into a computer with a GPT incompatibility. Check [here](http://www.rodsbooks.com/gdisk/bios.html) for some possible causes and solutions. Making the protective EFI partition in the MBR bootable is probably the most likely to work around this problem.

If you can't seem to get anywhere, please post the make and model number of the laptop, as well as information on the BIOS it uses. It's unlikely that I'll be able to offer any more help with that information, but it's conceivable it'll ring a bell for me or somebody else.

---

### Post by phredbull on 2011-01-26
srs5694:
Thanks for the suggestions; I checked the page you linked to, but honestly, a lot if it goes over my head. I Google'd on fdisk usage, but I could only find instructions on listing a partition table, creating, and deleting partitions.

My machine is an HP Compaq nx9110, 2.8gHz P4, ATI Radeon 9100, Phoenix bios, which I just updated to the latest firmware from the HP website.

BTW, I assume reinstalling Mint would not fix this, that I'd need to restore the drive to MBR instead of GPT? Would gdisk be able to do this, or will it mess things up further?

If it needs a total wipe and reformat, is Gparted ok for this, or do I need to make a proper MBR w/another program first?

---

### Post by srs5694 on 2011-01-26
> **phredbull said:**
> srs5694:
Thanks for the suggestions; I checked the page you linked to, but honestly, a lot if it goes over my head. I Google'd on fdisk usage, but I could only find instructions on listing a partition table, creating, and deleting partitions.

```

$ **sudo fdisk /dev/sdc**

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): **p**

Disk /dev/sdc: 8015 MB, 8015314944 bytes
121 heads, 42 sectors/track, 3080 cylinders
Units = cylinders of 5082 * 512 = 2601984 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3081     7827455+  ee  GPT

Command (m for help): **a**
Partition number (1-4): **1**

Command (m for help): **p**

Disk /dev/sdc: 8015 MB, 8015314944 bytes
121 heads, 42 sectors/track, 3080 cylinders
Units = cylinders of 5082 * 512 = 2601984 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3081     7827455+  ee  GPT

Command (m for help): **w**
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
```

I've bolded what you need to type. Change the device identifier for your system. Note that the "Boot" column changes after you use the "a" command; that's the key.

Also, most Linux command-line tools have online help available in the form of "man pages" (short for "manual pages"). Type "man <command-name>", where "<command-name>" is (you guessed it!) the command name, as in "man fdisk", to read the man pages. Man pages tend to be fairly technical, but they can be very helpful.

> BTW, I assume reinstalling Mint would not fix this, that I'd need to restore the drive to MFT instead of GPT? Would gdisk be able to do this, or will it mess things up further?

I assume you mean [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) rather than "MFT"; I'm not aware of any relevant acronym called "MFT" in this context.

Certainly MBR is better supported than GPT; as the Web page I reference in my last post details, some BIOSes have bugs that prevent them from booting on GPT disks, at least without jumping through some extra hoops. GPT does offer some advantages, but for your purpose, they're pretty minimal.

My GPT fdisk (gdisk) program does have a GPT-to-MBR conversion function; it's "g" on the recovery & transformation menu (launch the program, then type "r" followed by "g"). This will make the disk unbootable on any computer, though; you'll have to re-install your boot loader to restore the disk to bootability.

> If it needs a total wipe and reformat, is Gparted ok for this, or do I need to make a proper MFT w/another program first?

GParted can create a fresh MBR (it calls it an "ms-dos" partition table), wiping all the old GPT data. Some programs leave GPT data lying around, which can cause confusion, so if you want to do a complete wipe and re-install, GParted is better than most. Alternatively, you could use the "z" function on the experts' menu in gdisk (type "x" followed by "z") This will wipe the GPT data, but it won't create a fresh MBR; you'll need to use fdisk, GNU Parted, GParted, or some other program to do that.

---

### Post by oldfred on 2011-01-26
Mixed msdos (MBR) gpt drives had issues with older versions of grub2. 10.10 's grub2 works without problem.

Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos"

---

