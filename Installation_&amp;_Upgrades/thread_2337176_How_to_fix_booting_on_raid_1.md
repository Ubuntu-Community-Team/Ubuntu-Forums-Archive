---
title: "How to fix booting on raid 1?"
date: 2016-09-15
forum: Installation &amp; Upgrades
---

### Post by 700 on 2016-09-15
I'm trying to access my Ubuntu 14.04 LTS machine.
Unfortunately there are some booting problems detected. I can't even access GRUB main menu, so probably I have to reinstall GRUB.

While trying to reinstall GRUB this message appears:
> GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

I have 2 disks on my machine in Raid 1 (mirrored data on 2 disks for better performance).
But GParted returns 4 directories:
[ATTACH=CONFIG]271200[/ATTACH]

I don't know what is **/dev/mapper/pdc_cfajdidif** (110.86 GiB) partition, but it looks like below on GParted:
[ATTACH=CONFIG]271201[/ATTACH]

Partitions in **/dev/sda** (111.79 GiB) on GParted look like below:
[ATTACH=CONFIG]271204[/ATTACH]

Partitions in **/dev/sdb** (111.79 GiB) on GParted look like below:
[ATTACH=CONFIG]271205[/ATTACH]

As we can see, the size of: [FONT=courier new]/dev/sdx[/FONT] addresses is greater than [FONT=courier new]/dev/mapper/pdc_cfajdidif[/FONT] address of about 0.93 GiB and I don't know why.
Directory **/dev/sdc** (on GParted mouted as /cdrom) is just my USB device with Ubuntu installer with temporary Ubuntu 12.04.03 LTS session. This is the only way I can use my Ubuntu 14.04 LTS machine (and access very limited internet).

More details (shortlist):
- Ubuntu 14.04 LTS on hard drive (no access);
- Ubuntu 12.04.03 LTS session on USB (temporary trial version access = "try new Ubuntu without install" version);
- access only to temporary Ubuntu 12... session on 'nomodeset' from USB GRUB ('shift'+'e' on boot);
- only dotted screen visible without 'nomodeset' on Ubuntu 14... machine - similar to:
[http://i.stack.imgur.com/gdUvs.jpg](http://i.stack.imgur.com/gdUvs.jpg)
[http://i.imgur.com/gupkLDH.jpg](http://i.imgur.com/gupkLDH.jpg)
- **no tty** access on Ubuntu 14... machine (ctrl+alt+F1, F2... F6 = black screen);
- **login loop** on Ubuntu 14... machine (password input = black screen + return to login prompt);
- limited internet access :(

My question is:
What should I do now to bring back booting on my Ubuntu 14.04 LTS device?

---

