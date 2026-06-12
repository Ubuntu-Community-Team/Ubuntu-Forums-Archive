---
title: "Question about Grub 2 dual-boot after final 10.04 LTS is released"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by OGpmpdog on 2010-03-03
Hi All,

I just celebrated my 1-year anniversary converting to Linux...I got tired of the inevitable slowdowns of Windoze, bluescreens, and the constant virus watch...

Anyway, I'm running Karmic now...and it is awesome! I'm finally getting comfortable navigating thru the menus and tinkering with my system settings...Hell, I'm even getting bolder and experimenting with the CLI.

I have dedicated an entire HD to Ubuntu; I'd like to partition some space in anticipation of Lucid.

My question: Can I just leave the Grub2 bootloader alone in Karmic(where Grub will also "see" Lucid?) - or should I also install the bootloader on the new partition created for Lucid?

Thanks for reading....

---

### Post by darkod on 2010-03-03
Your Grub2 right now is probably on the MBR of the hdd, not on the Karmic partition unless you specifically installed it there. You could disable Lucid from installing a bootloader in the last screen of the installer by clicking on the Advanced button. Then just boot Karmic and do update-grub.

You could also let Lucid install its Grub2 on the MBR of the hdd and it will probably detect Karmic and create an entry in the boot menu for it.

Either way, you can easily restore the bootloader from Karmic or Lucid onto the MBR when ever you decide.

---

### Post by OGpmpdog on 2010-03-03
> **darkod said:**
> Your Grub2 right now is probably on the MBR of the hdd, not on the Karmic partition unless you specifically installed it there. You could disable Lucid from installing a bootloader in the last screen of the installer by clicking on the Advanced button. Then just boot Karmic and do update-grub.

You could also let Lucid install its Grub2 on the MBR of the hdd and it will probably detect Karmic and create an entry in the boot menu for it.

Either way, you can easily restore the bootloader from Karmic or Lucid onto the MBR when ever you decide.

Oh, the MBR has its own partition?
I just clicked 'Use Full Disk Install', thanks for sharing knowledge!!

---

### Post by oldfred on 2010-03-03
MBR is master boot record and is not a partition, but just the first sector set aside for booting. It goes back 20 years from the first IBM PC so has become somewhat dated.

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

