---
title: "Problem starting ubuntu 6.10"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by barisilk on 2007-02-11
Hi I installed Ubuntu 6.10 desktop succesfully without errors but after restarting i cant boot to os with a message "Error loading operating system".What can cause this.My configuration is P4 2.8 Ghz HT Nvidia fx5700 vga,80 gb serial ata+30 gb maxtor ide harddisk+asus dvd rw and asus dvd rom...Thanks for your urgent support...

---

### Post by Kateikyoushi on 2007-02-11
I think it is a bug which might not be corrected (might not be possible to correct it)
Mainly the result of using sata and pata drive the same time.
Please let us know where did you install grub and which drive do you try to boot.
Do you have another OS installed ?

---

### Post by barisilk on 2007-02-11
I have no other OS installed,I installed ubuntu GRUB on the SATA Samsung drive and I'm trying to boot forom it.So do I have to disable the parallel ata drive?

---

### Post by rsambuca on 2007-02-11
Check your system bios and make sure that the SATA drive is listed as the first HDD.

---

### Post by barisilk on 2007-02-11
yes it seems to be primary master...

---

### Post by barisilk on 2007-02-11
> **Kateikyoushi said:**
> I think it is a bug which might not be corrected (might not be possible to correct it)
Mainly the result of using sata and pata drive the same time.
Please let us know where did you install grub and which drive do you try to boot.
Do you have another OS installed ?I have no other OS installed,I installed ubuntu GRUB on the SATA Samsung drive and I'm trying to boot forom it.So do I have to disable the parallel ata drive?

---

### Post by Kateikyoushi on 2007-02-11
> **barisilk said:**
> yes it seems to be primary master...

He means check the boot order, try to change it and see if it works.

---

### Post by Kateikyoushi on 2007-02-11
> **barisilk said:**
> I have no other OS installed,I installed ubuntu GRUB on the SATA Samsung drive and I'm trying to boot forom it.So do I have to disable the parallel ata drive?

The problem is that Sata and pata drive order is not consistent between motherboards and bioses i guess due to the external sata chips.

See these links, hope you can solve it.

[grub guessed BIOS disk order incorrectly]("https://launchpad.net/ubuntu/+source/grub/+bug/8497")

[JMicron PATA/SATA Controller does not work]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg160721.html")

---

