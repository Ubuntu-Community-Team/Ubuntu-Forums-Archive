---
title: "Install through &quot;OEM/Recovery&quot; partition"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by Noccy on 2010-07-19
I'm sure someone can help me with this. I have a machine that refuses to boot from USB (including USB CD-Drive) and I have exhausted all other sane options to install Ubuntu on the box.

So, my first (in)sane idea would be to create an install partition as an image file, containing all the files needed to install. I could then partition the drive, slap the install partition on the drive, put it back into the computer, and install from the actual system.

How would I pull this off? :)

---

### Post by gordintoronto on 2010-07-19
Good luck with that.

What brand and model of computer do you have? If it's fairly modern, it should boot from USB. Can you get into the BIOS to select a boot device?

---

### Post by Noccy on 2010-07-20
> **gordintoronto said:**
> Good luck with that.

What brand and model of computer do you have? If it's fairly modern, it should boot from USB. Can you get into the BIOS to select a boot device?

Homebuilt, based on a dell motherboard that is completely unaware about the existence of USB boot devices :(

How would I go about invoking the installation through grub, telling it to use /dev/sda1 as source?

---

### Post by boof1988 on 2010-07-20
I have used [UNetBootIn]("http://unetbootin.sourceforge.net/") to create what you want with some success.  Though it has been a few years since I've tried it.  So it may not work for you.

I partitioned the drive before using UNetBootIn, if I recall correctly.

---

### Post by Noccy on 2010-07-20
> **boof1988 said:**
> I have used [UNetBootIn]("http://unetbootin.sourceforge.net/") to create what you want with some success.

Thanks for the suggestion. Installed it and it looks sane, fingers crossed my drive will show up with the adapter plugged in :)

The installation created by unetbootin, is that to be considered a "real" install, or does it make use of any clever hacks to function? Since the box will become an internet gateway, that's kinda good to know :)

---

### Post by boof1988 on 2010-07-20
> **Noccy said:**
> The installation created by unetbootin, is that to be considered a "real" install, or does it make use of any clever hacks to function?

My understanding is that UNetBootIn copies the os-file.iso to the selected partition.  Then it writes the proper code to the master-boot-record of the drive to make the drive bootable.

---

