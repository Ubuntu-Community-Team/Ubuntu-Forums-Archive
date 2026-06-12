---
title: "Partition list didn't appear"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by azophy on 2010-06-26
Today, i was installing Ubuntu 10.04 on my laptop. But when the installer reach step 4, i cannot see my partitions on my computer that i has previously made. I already enter the manual partition editor sectin, but the list show that my harddisk has no parition no it.
The weird thing is that i can normally access my partition on ubuntu live-cd's file browser, but it didn't appear on my installation wizard. Here is a screenshot of my desktop:
[IMG]http://img685.imageshack.us/img685/1101/gambarlayar12.png[/IMG]

Thank for the help. And, sorry if my english is not pretty good.

---

### Post by darkod on 2010-06-26
This usually happens if the disk has been used in raid earlier. Raid meta data is still on the disk, and the installer ignores it.
From live mode, assuming the disk name is /dev/sda, just execute:

sudo dmraid -r -E /dev/sda

That will remove the raid data. Do this only if you are NOT running raid. If you are, you should install another way.

And depending how you created the partitions in advance, you might need to delete them and create them again with the installer. If they are ntfs, they can't be used. In fact, there is rarely need to create partitions in advance for linux, you can always do it during the install. It's double work, now you have to select how to use them anyway.

---

