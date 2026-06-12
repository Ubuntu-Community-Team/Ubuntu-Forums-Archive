---
title: "help reinstalling... disk partitioner..."
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by ichundu on 2008-08-02
hi guys,

i'm relatively new to ubuntu and i've been testing a lot of new things just so to learn and sometimes i mess things up so have te reinstall the os. i have my hard drive divided in 3 partitions (2 for windows and 1 for ubuntu) and want to know how to format the ubuntu partition and install the os without having to delete it.

check out my "idiot" way of setting up ubuntu on my comp: every time i want to reinstall ubuntu, i insert the windows cd and delete the ubuntu partition from the setup. then i insert the ubuntu cd and install it with the option "use the largest continuous disk space", so it sets up again a new partition in the free space (deleted partition) for ubuntu.

i want to reinstall ubuntu without having to delete and recreate partitions, don't know how to format just the existing partition or is it made with manual config?

any help about how to make it different way would be much appreciated.

Thanks for the attention.

---

### Post by forger on 2008-08-02
You'll have to create 3 partitions with the manual partition option in the ubuntu installer. You'll have to format at least one, the root partition.
1) root partition (mount point: /, format as ext3), which will contain everything except your /home/
The root partition can be 8-10GB, I don't think you'll need more
2) swap partition (format as: swap)
The swap should be 1-2GB, not more
3) home partition (mount point: /home, format as ext3), which will contain your home (user) files
The home should be all the rest of free space on your hard drive, since this is the one where you save your files,data and configuration for applications

This way you can format the root (/) partition and keep the application configuration that are stored in /home/yourusername/
You can check whether to format or not a partition in manual partition in ubuntu installer.

Mind you that once you format the root "/" partition, you'll have to reinstall the packages for some applications, that aren't included by default with a fresh Ubuntu installation. The configuration for each application will be picked up automatically from the /home/yourusername :)

Formatting is just the Windows way of fixing stuff, in Linux you'll rarely need to format your hard drive and reinstall ubuntu :)

---

### Post by ichundu on 2008-08-02
thanks. i know i'll rarely have to format in linux but did something wrong with repositories and didn't know how to fix it, it will take some time for me to learn all the stuff in linux. anyway, so far so good :)

---

