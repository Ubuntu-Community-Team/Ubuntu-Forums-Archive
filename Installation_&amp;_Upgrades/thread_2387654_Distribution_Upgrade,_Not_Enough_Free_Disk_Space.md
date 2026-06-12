---
title: "Distribution Upgrade, Not Enough Free Disk Space"
date: 2018-03-22
forum: Installation &amp; Upgrades
---

### Post by arianhf on 2018-03-22
I am trying to upgrade from 16.04 to 17.10 but I get this error, and I dont know what to do as It does not point out where the problem is.
[ATTACH=CONFIG]279035[/ATTACH]
I think I have enough disk space in / , /boot , and my home folder so I don't know why I still get this error.
[ATTACH=CONFIG]279034[/ATTACH]
can someone help me?

---

### Post by Tadaen_Sylvermane on 2018-03-22
only 1.45gb in /var. Not sure the total download size of the upgrade packages. Run an apt clean first, then try the upgrade again. Probably just clogged up with old packages in the cache. That is a ridiculously small /var by the way. Will cause problems again.

I would repartition. 15,20gb for /, 25+ for /var, rest for /home or better yet a data partition and symlink directories into the appropriate /home/$USER/

---

### Post by arianhf on 2018-03-22
I am new to ubuntu, and I followed the recommendations of a stackoverflow post for these partiotions. 
Can I change the partitioning without loss of data? If so how?

I have done apt clean and autoremove and autoclean and these pictures are taken after doing those.

---

### Post by Impavidus on 2018-03-22
You can change partitions without losing your data (gparted can do it if you run it from a live disk), but it's slow and risky. You should make backups of your data. It's probably faster and easier to copy everything to a backup drive (you have to do that anyway), delete partitions, create new ones, restore the backups and make sure your /etc/fstab contains the right UUIDs.

You could (1) backup your OS, (2) change partitions, (3) restore the backup and then (4) replace every file during the upgrade, but it's faster to simply do a fresh install, skipping step 1 and 3. Release upgrades can be very nice (I've got good experiences with them), but when you add complications like changing partitions, a fresh install is better.

It used to be that only upgrades LTS&#8594;LTS or any release&#8594;next release were supported, but apparently LTS&#8594;latest supported non-LTS is offered too. I don't know how reliable these upgrades are.

The web is full of dubious recommendations. Most people have no /boot, /var or /tmp partition. They may occasionally be useful, but most of the time they only complicate matters. A /home or a different kind of data partition is a good idea. Your /home partition is fine, no need to change that.

---

### Post by SeijiSensei on 2018-03-22
On modern machines with large hard drives /boot should be at least 256 MB to avoid problems.  512 MB would ensure never having an issue with running out of space.  On a 1 TB hard drive 512 MB is less than 0.1% of the drive's capacity.

There's no reason to allocate a specific partition for /var.  Just have one root partition, and maybe a separate filesystem for /home.

---

### Post by Tadaen_Sylvermane on 2018-03-23
True no real reason for /var dedicated. I did for my server because i read something about the potential for runaway log files halting the system. Else I would have left it all under /.

---

