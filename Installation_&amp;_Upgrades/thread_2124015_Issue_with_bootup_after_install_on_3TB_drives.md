---
title: "Issue with bootup after install on 3TB drives"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by quattrocs on 2013-03-09
i have been able to do dozes on these installs on 2tb drives, this is my first time doing so on 3tb drives and for the life of me i cant get the system to boot.

my best understanding is that grub2 installs perfectly on the 2tb drives due to mbr and because 3tb need gpt it doesnt have the same behaviour

i have made a 100mb partition on each drive and made it bios_grub, then its a 16gb partition on each drive for swap, then a 30gb partition on each that i make into a md device and a 4th with the remainder of the storage for another md device. i have been able to install grub on the 100mb partitions /dev/sda1 /dev/sdb1.

bios is set for ahci

at this point i am at a loss as to why i cant get this to work. any help would be appreciated.

---

### Post by darkod on 2013-03-09
Because you don't install grub2 to a partition. The bios_grub partition is needed for grub2 to use it on gpt table, but it uses it automatically. It knows which partition to use to store part of its code because of the bios_grub flag.

You install grub2 as usuall, to /dev/sda, /dev/sdb, etc. To the MBR, not to the sda1 partition.

If you installed it onto a partition you effectively have no bootloader on the MBR hence nothing is booting.

Also, the bios_grub partition should have NO filesystem, RAW format.

---

### Post by quattrocs on 2013-03-09
thanks darkod

i actually redid the install from scratch, and i deleted the 100mb partition on both drives and recreated it, with just the setting reserved for bios. when it got to the grub install i let it do its thing and it all went smoothly.

the problem was someone had instructed me to format the partitions as ext 2 and to mark them bios_grub and then to install grub to each partition.


the diff then between installing on 2tb drives vs 3tb drives is the extra bios_grub partition needed, and then let grub install into the mbr, which is a bit confusing since 3tb drives are not mbr but gpt. nonetheless in the end it worked.

thank you for your help

---

### Post by papibe on 2013-03-09
Hi quattrocs.

I just installed a server with a similar configuration a few weeks ago.

Some BIOS can't boot from GPT. They should, but there are some that just can't.

Are you sure you motherboard BIOS can boot from GPT?
Have you check if there's a BIOS update for your motherboard/computer?

Regards.

---

### Post by darkod on 2013-03-09
I think it's a situation when mbr as partition type is wrongly used. The Master Boot Record exists on all disks, it's the first sector, unless I'm wrong.

The partition type I usually call msdos, not mbr. If you print the disk details with parted, it will say msdos, not mbr.

It might be a case of how and when a specific term got accustomed to. Like when Microsoft calls partition Drives so it creates hell of a confusion are you talking about a Hard Disk Driver, or just a partition on it. In fact, most windows users won't have a clue to make a difference just by looking into My Computer. Are C and D partition on the same disk, or two physical disks. :)

Bottom line, even on disks with gpt table you still have a MBR. :)

---

### Post by oldfred on 2013-03-09
If using BIOS boot on gpt drive the bios_grub has to be unformatted space and only needs to be 1MB. That is not a boot partition. 
If you want boot partition I would make it 300 to 500MB to have enough room for many kernels, although it can be smaller if you houseclean somewhat regularly.

 Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html)

---

