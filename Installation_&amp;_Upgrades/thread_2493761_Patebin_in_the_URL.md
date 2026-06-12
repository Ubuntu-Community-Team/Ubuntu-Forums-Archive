---
title: "Patebin in the URL"
date: 2023-12-24
forum: Installation &amp; Upgrades
---

### Post by kannanbkm on 2023-12-24
Hi there,

Thank you for helping me out. I'm not able to boot a drive copied from a debien linux server. I installed boot-repair and tried to install boot-repair a disk connected as /dev/sdb and no luck. I have attached pastebin in the URL below.

[https://paste.ubuntu.com/p/KFqd2wxQ9B](https://paste.ubuntu.com/p/KFqd2wxQ9B)

Please let me know if you need an further information to resolve.

Best regards,
Kannan

---

### Post by MAFoElffen on 2023-12-24
Welcome To Ubuntu Forums.

Since this is an Ubuntu Support Section, and in your post you only mentioned "Debian Server", [s]but in the 'boot-info' report I see that you do have "Ubuntu 22.04.3 LTS on sda3" installed on your system...[/s] You do not have Ubuntu Installed anywhere...

[COLOR=#ff0000]***<<Asking the Moderators to please move this to the Debian or Vistualization sections>>***[/COLOR]

So we can continue to help you... Elsewhere

Looking at the 'boot-info' report right now. BRB. (Continued in next post)

[s]Can you boot either installation or you having problems booting just one of the two? (Problem with Grub2 or one of the installs?)

Why are you dual-booting Server Editions? Does this machine have a job or is it a multi-purpose test machine? Just curious.[/s]

---

### Post by MAFoElffen on 2023-12-24
This a Debian virtual server VM Guest on Windows Hyper-V. (On what looks what might be you trying to mount a live physical disk as a vdisk.)

Which Version of Windows? 10 or 11?

Which Generation of VM Guest is the machine? Gen 1 or Gen 2?

Tell me more about how you have your vdisk defined in your configuration... Because that is your problem in that report.

Do not tried to repair it or do anything else until we clear up a few things or you will destroy what is on it.

Look at line numbers: 52, 101, 126, 131, 189, 195, 199, 210, etc...

Especially lines around 131... Then mount options of the machine. None of those mention anything about any partitions on that device. It appears only as /dev/sbb without partitions.

*** --> This is why that is "unbootable". Nothing is going to boot on that disk device until (first) it appears to the machine as a valid disk device with a valid partition table with valid partitions.

There may be either nothing wrong with the underlying vdisk, or it may have problems in the vdisk with the partition table on it. That would be the thing to fid out and resolve first.

---

