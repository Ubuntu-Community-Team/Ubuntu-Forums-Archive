---
title: "Software RAID installation"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by floriankerbl on 2012-02-18
Hey folks,

I am quite helpless trying to install Ubuntu 11.10 with mdadm software RAID. I am using 2x 2 TB hard drives that I have partioned identically with the help of the install routine of the Alternate Installation Disk. Here is a screenshot of the partitions (unfortunately only in German).

[IMG]http://www.7up-live.de/intern/tmp.jpg[/IMG]

I have tried lots of things, but the system won't boot. If I try to I
always arrive at the grub rescue prompt. Here's an excerpt of the syslog file.

Feb 13 14:51:11 grub-installer: info: Installing grub on '/dev/sda'
Feb 13 14:51:11 grub-installer: info: grub-install supports --no-floppy
Feb 13 14:51:11 grub-installer: info: Running chroot /target grub-install  --no-floppy --force "/dev/sda"
Feb 13 14:51:15 grub-installer: /usr/sbin/grub-setup: warn:
Feb 13 14:51:15 grub-installer:  
Feb 13 14:51:15 grub-installer: **This GPT partition label has no BIOS Boot Partition**; embedding won't be possible!
Feb 13 14:51:15 grub-installer: .
Feb 13 14:51:15 grub-installer: /usr/sbin/grub-setup: warn:
Feb 13 14:51:15 grub-installer:  
Feb 13 14:51:15 grub-installer: **Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged.**
Feb 13 14:51:15 grub-installer: .
Feb 13 14:51:20 grub-installer: /usr/sbin/grub-setup: error:
Feb 13 14:51:20 grub-installer:  
Feb 13 14:51:20 grub-installer: [B]cannot read `/grub/core.img' correctly
[/B]Feb 13 14:51:20 grub-installer: .
Feb 13 14:51:20 grub-installer: error: Running 'grub-install  --no-floppy --force "/dev/sda"' failed.


I have keyed in mdadm --misc --detail /dev/md? with the results attached to this message.

I hope there is someone out there who can help me?

Thanks a bunch,
Flo

---

### Post by darkod on 2012-02-18
Why do you have /boot on sdb1? Why not inside the array so that it can work when one disk fails too?

Also, if you want to use GPT you will need a small partition (only 1MB is enough) which has the biosgrub flag on. You can try to create this partition inside the array too.

It can't work with GPT without this partition.

Another option is using msdos table on both disks, and not gpt.

---

### Post by floriankerbl on 2012-02-19
Dear Darko or anybody else,

thank you very much for this helpful information. I guess the file system for the boot partition should be ext2. Originally, I did have it as a RAID array, but someone in a forum suggested, this would not work and I shall put it outside of the array. But maybe, I just misunderstood and it was this small parition you suggested.

I guess for this to work, the file system for this small partition should be the one saying "reserved BIOS boot partition" or something along these lines (the box I am installing this onto is down in the basement), plus I have to set the boot flag, correct? Somehow I remember that I was not able to do both things (filesystem BIOS and boot flag) at the same time. Is this possible?

Thanks so much!

Flo

---

### Post by darkod on 2012-02-19
What that told you would be correct for RAID0. For RAID0 you have to have /boot outside the array. But you are using RAID1 so that doesn't apply.

I don't use gpt so I'm not 100% sure, but definitely you don't need the biosgrub partition to be ext2. It was either:
1. Leave it without any filesystem (don't format it), just set the biosgrub flag.
2. Format it as FAT32 or FAT16 and set the biosgrub.

I don't remember which one it was.

---

### Post by floriankerbl on 2012-05-12
Hi there,

quite some time has passed since my last post. I was away from home most of the time. I have now *tried* to make this work again with hints that _darkod_ gave me. However, due to my limited knowledge and experience I still do not have my system up and running.

[IMG]http://www.7up-live.de/intern/20120512-10_20_24-4404.jpg[/IMG]
In this image there are no mount points. They are /boot, / and /data for #0, #1 and #2.

However, it is not the way it should be, yet. This is what I get when I try to boot.
[IMG]http://www.7up-live.de/intern/20120512-10_12_10-4402.jpg[/IMG]

Maybe there is someone out there who'd be able to tell me how to do things right...

Thanks so much,
Flo

---

### Post by darkod on 2012-05-12
Did the installer report the same grub error when installing this time or no?

I see you created the small bios_grub partition only on /dev/sda. On /dev/sdb it's left unused.

I would do it on both, because in raid1 you want to be able to boot if any disk fails. Like this, I assume you will be able to boot only if sdb fails, because if sda fails you don't have the bios_grub partition and the bootloader on sdb. Nothing to boot the machine.

Another option would be to put the bios_grub on the raid1 array. That way it will be on both disks.

Also, I don't know if you are aware, there is no need to create three different md devices, unless you want to. You can have only one or two md devices, and they can have partitions on them. Just as regular hdd.

---

