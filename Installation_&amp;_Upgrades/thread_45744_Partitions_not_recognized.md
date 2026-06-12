---
title: "Partitions not recognized"
date: 2005-07-01
forum: Installation &amp; Upgrades
---

### Post by ubuntufriend on 2005-07-01
Hello everybody! (Sorry for my English, I'm not a native speaker...)
I have a problem with the ubuntu-installation. I have a 13GB harddisk and I had installed Ubuntu, but then I had to change the Motherboard and now I have to reinstall Ubuntu. But now, there are no partitions listed in the partition-manager. When I boot Mepis or DSL they are recognized.
What can I do?

PS: I'm not the only one with this problem, in the german ubuntu-forum, there are some others with this problem.

---

### Post by mingus on 2005-07-01
[QUOTE=ubuntufriend]
. . . now I have to reinstall Ubuntu. But now, there are no partitions listed in the partition-manager. When I boot Mepis or DSL they are recognized.
What can I do?
[/QUOTE]

What is the "partition manager" where you are looking?  

If you are going to reinstall Ubuntu, why not just repartition the disk?

---

### Post by ubuntufriend on 2005-07-02
During the installation, there is a step where you have to choose the partitions. There you can also change the partitions. That's what I mean with "partition manager". There's only the device listed, no partitions.
Sure, I can repartition the disk, but then I have to backup the "/home". And there are some problems with some files, I can't copy them.
I think I'm going to try again to backup the /home. I use "Evolution". Which files do I have to backup, if I don't want to lose any mails and adresses? Because I can't just backup the .evolution folder, it doesn't work.

---

### Post by mingus on 2005-07-02
*Sure, I can repartition the disk, but then I have to backup the "/home". And there are some problems with some files, I can't copy them. I think I'm going to try again to backup the /home.*

I guess I still do not understand.  You are going to reinstall Ubuntu, but you want to keep the /home that is already on the disk?  If you are able to access this disk with Knoppix, you could create a partition and use the cp -a command to copy /home to it.  After reinstall, you could copy the contents of the old /home to the new /home - but you need to be careful how you do this; there are several HowTo's on the web with recommended procedure.

BTW, are you positive that you must reinstall?

Regarding why the Ubuntu partitioner does not see the partitions but DSL does, I don't know.  It should, as long as the partition table is good.  Be sure that you were in the "manual partitioning" option and did not tell Ubuntu to "take over the disk."

---

