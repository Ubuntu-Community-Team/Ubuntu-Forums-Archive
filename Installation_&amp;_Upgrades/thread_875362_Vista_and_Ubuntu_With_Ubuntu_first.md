---
title: "Vista and Ubuntu With Ubuntu first?"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by shak541 on 2008-07-30
hello, i am planning on dual booting vista and ubuntu on my hp laptop. It has a single 160GB HDD and ubuntu installed currently. Is there any way i can just use one of my backups from acronis to restore my vista partition back without losing ubuntu? or do i have to backup my ubuntu stuff and then format, install vista then install ubuntu?

---

### Post by sandeepy on 2008-07-30
you can always install Vista with Ubuntu on it. Windows boot loader should detect the ext3 and other Ubuntu partitions on start-up after install. But do make a backup before you go ahead ... Just In Case.

---

### Post by shak541 on 2008-07-30
thanx for the quick reply but i do not own nor have access to vista disks. i only have an backup of my laptop on an external hdd using acronis. say if i put on the vista backup how will i get the vista bootloader to see ubuntu? where do i manually set this up?as i want ubuntu to be the default OS. Also i may just start over... as in reinstall ubuntu and restore vista backup. which should i do first? will grub boot vista without problems?

---

### Post by sandeepy on 2008-07-30
do you already have Vista installed or do you have Ubuntu installed ? Making any OS default is just a matter of changing a couple of lines (boot.ini or grub.conf).

 I do not know much abt acronis but it wud help if you elaborate a little about your system.

---

### Post by shak541 on 2008-07-30
sorry about being confusing.....well i have ubuntu installed and if i use acronis to restore a backup.. the bootloader(grub) will be overwritten by vistas bootloader, but the problem is i want to use grub. so could i just keep ubuntu and restore the vista backup then reinstall grub?

---

### Post by sandeepy on 2008-07-30
yes you can do that but i can't detail out the steps. btw how will it matter if you use grub or windows boot loader ?

---

### Post by shak541 on 2008-07-30
i dont know very much at all about windows bootloaders but i am rather quite fimiliar with grub.

---

### Post by crwmike on 2008-07-30
I don't know if restoring Vista from an Acronis image, depends on if you backed up the whole disk or just a single partition.

Download the Super Grub ISO and burn it to a CD, it will make restoring the grub bootloader after restoring Windows.[HTML]http://www.supergrubdisk.org/[/HTML]

---

