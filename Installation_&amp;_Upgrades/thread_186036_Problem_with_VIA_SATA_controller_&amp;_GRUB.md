---
title: "Problem with VIA SATA controller &amp; GRUB"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by silencer51 on 2006-06-01
Hi to all,

I have an Asus A8V Deluxe mobo which has 2 sata controllers: a Promise one and a VIA one.

My hdd configuration is as follows:

1) On the Promise controller I have 2 WD 80GB discs in RAID 0 which hold my XP installation and my games

2) On the VIA controller I have 1 WD 250GB disc with 2 partitions for my music and documents.

I have 35gb of free space on my 250GB hdd.

The text-install cd works like a charm, I manually edited the partition tables and created 2 partitions on those 35gb of free space, one for / (34gb) and a 1gb swap partition.

The installation proceeded normally, and then GRUB installed itsself on my 250gb hdd's mbr and configured itsself.

Now, on my previous linux installations, GRUB would sometimes detect the XP installation on the RAID 0 setup but it could not load it properly.

Whenever I wanted to boot into linux, I selected the drive holding it as the first boot device instead of the XP RAID 0 setup.

After the installation completed succesfully, I tried the above and all I got was the "Operating system not found" error message.

What can I do? I did notice that at the beggining of the installation, after the kernel loaded, there were a few error messages concering hdc if I remember correctly. Also, at the end of the installation, right after the system has gone down for reboot I also get a few of these messages.

I do think this is a driver problem.

Has anyone with a similar configuration encountered this? Any help?

Thanks in advance!:)

---

### Post by therunnyman on 2006-06-01
Same problem here, reported as a bug, confirmed as a bug (and not just any bug, but a "major" bug), but the golldarn devs won't do anything about it.

I wrote a post earlier about this...search the forums for "Workaround therunnyman, "and it should show up.  A preliminary tip: Dapper is loading the "card" drives before the mobo drives.

Hope that helps.

therunnyman

---

### Post by silencer51 on 2006-06-01
Somehow I don't think we have the same problem.

I think there's something wrong with GRUB's configuration. What I mean is the problem is in the MBR and not a kernel bug... Your problem, from what I understand is that after the kernel has loaded, it panics saying it can't find the / partition... I can't even get this far.

Note: I have made sure the ext3 / partition on my 250gb SATA drive is flagged as bootable...

Either way I won't be changing my hdd cabling configuration... Let's hope the bug is resolved sometime in the near future... Unfortunately, 'till then, no Dapper for me... :-(

---

