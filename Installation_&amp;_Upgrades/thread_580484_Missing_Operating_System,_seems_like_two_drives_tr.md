---
title: "Missing Operating System, seems like two drives trying to boot"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by NJSoria on 2007-10-18
Here is what sudo fdisk -l returns.

Disk /dev/hda: 250.0 GB, 250059350016 bytes
81 heads, 63 sectors/track, 95707 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Disk identifier: 0xdc7e81f8

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       95708   244198552+   b  W95 FAT32

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12711270

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris


Now the first drive hda1 is my storage. Second sda1 is my bood drive. When I try booting I receive the message 'Missing Operating System' from the bios. I'm assuming a bit that the first drive is trying to boot before the sata drive? But being a linux noob. I don't know. I kind of just know I have to do something with GRUB, my bios boot priority is correct.

Thanks for any help! And also, HELLO! It's good to be here.

---

### Post by technoidiot on 2007-10-18
Your BIOS is set to start your IDE drive first. Since your boot is on a sata drive you must change your BIOS to boot from the SATA drive.

---

### Post by NJSoria on 2007-10-19
> **technoidiot said:**
> Your BIOS is set to start your IDE drive first. Since your boot is on a sata drive you must change your BIOS to boot from the SATA drive.

Thank you for your reply, however, my BIOS boot priority is correct.

---

### Post by givver on 2007-10-19
> **NJSoria said:**
> Thank you for your reply, however, my BIOS boot priority is correct.

I had a simular problem today.  It turned out that my second Partition was marked as Active instead of the one with the boot loader on it.  In my case I booted Vista in recovery mode, went to a command prompt and used DISKPART to set the other partition as active and no more Missing Operation System message.

Hope this helps.

---

### Post by technoidiot on 2007-10-19
No matter how you set your boot priority it will boot the IDE (hda) drive first. I have fiddled with mine as I have 3 drives. Can't seem to get SATA drive to boot first. But it is not a big deal for me because I have it set up in my GRUB file to select which will boot. Have you tried setting the boot parameters for "other drive" on all three boot options?

---

### Post by NJSoria on 2007-10-19
> **technoidiot said:**
> No matter how you set your boot priority it will boot the IDE (hda) drive first. I have fiddled with mine as I have 3 drives. Can't seem to get SATA drive to boot first. But it is not a big deal for me because I have it set up in my GRUB file to select which will boot. Have you tried setting the boot parameters for "other drive" on all three boot options?

I guess this is my problem, now my BIOS does know to follow the boot priority, but the bootloader (GRUB?) is saying hey, boot the hda.

So to my real question, how do I modify the bootloader to not try and boot the IDE, I can see under the fdisk -l trigger or whatever that the hda1 is set to boot, I would like to eliminate that, I tried modifying some files within grub but I don't have permissions... and yeah. I'm lost.

Thanks for your help guys :) This is truely my only beef thus far with ubuntu, other than trying to run the KDE built KAlarm... which I never figured out how to get running. I guess I will have my first project to write some software now. :) Off topic, can I develop desktop applications in Ruby for Ubuntu? I am just picking up this language and would love to dive into a project to learn.

---

