---
title: "Install fails part way through"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by Cee64E on 2010-12-08
I'm totally new to this linux thing and I have a very strange problem.  I downloaded the .iso and burned it to CD as per instructions.  I had intended to install alongside existing WinXP Pro Sp3.  Everything seemed to be going fine until it the installer got to the "User Info" Screen where it asks for my name, the computer's name, password, etc.  At that point nothing I did would allow the "forward" button to work.  I backed up a step or two and went forward again to no avail.    I ended up hitting the hard reset button to get out of it.  I never saw any error messages even though I scrolled through the install log at the bottom of the install window.  Now my HDD is 60 Gb smaller (The part intended for Ubuntu) under Win XP and I have no idea what to do about it.

My system:

Asus P5NE-SLI Mobo
Intel Core2 Duo 8400 3.0 Ghz
2 Gb ram at 800Mhz
Nvidia 9800GT GPU 512Mb

Win XP seems to be working normally except for the loss of HDD space.

Any suggestions for the noob?

---

### Post by Quackers on 2010-12-08
Welcome to UF :-)
Try using no capitals in the username field.

---

### Post by sikander3786 on 2010-12-09
And in addition to Quackers post, no spaces either ;-)

As your disk space has been used up (the installer created partitions for Ubuntu) so when you plan to install Ubuntu, if you need some help, go to Applications > Accessories > Terminal and post the output of this command to let us know about your partitions.

```
sudo fdisk -l
```

If you feel confident and can do it yourself, from the installer's partitioning page select Manual Partitioning and you'll see the space that installer assigned previously to Ubuntu. Delete all those partitions (there should be 2 of them) and then create 3 new partitions. As you are giving 60 GB space to Ubuntu, my suggestion would be,

1. / Ubuntu System Partition. Filesystem Ext4, Size = 15 GB (10GB at least), Mount Point '/'

2. /home partition, Filesystem Ext4, Size = Custom, Mount Point '/home'

3. Swap partition, Size = RAM x 2

Having a separate /home partition is always a big Plus. It saves all the settings and your personal documents, files as well so in case of a re-install you don't need to extract your data from the root partition. Just use your existing /home partition in installer and choose not to format it ;-)

If you don't need a separate /home, then you just need 2 partitions for installation of Ubuntu. Add up your space to the '/' partition instead.

Feel free to post as many queries as you've got :-)

Good Luck!

---

### Post by Cee64E on 2010-12-10
> **sikander3786 said:**
> And in addition to Quackers post, no spaces either ;-)

As your disk space has been used up (the installer created partitions for Ubuntu) so when you plan to install Ubuntu, if you need some help, go to Applications > Accessories > Terminal and post the output of this command to let us know about your partitions.

```
sudo fdisk -l
```If you feel confident and can do it yourself, from the installer's partitioning page select Manual Partitioning and you'll see the space that installer assigned previously to Ubuntu. Delete all those partitions (there should be 2 of them) and then create 3 new partitions. As you are giving 60 GB space to Ubuntu, my suggestion would be,

1. / Ubuntu System Partition. Filesystem Ext4, Size = 15 GB (10GB at least), Mount Point '/'

2. /home partition, Filesystem Ext4, Size = Custom, Mount Point '/home'

3. Swap partition, Size = RAM x 2

Having a separate /home partition is always a big Plus. It saves all the settings and your personal documents, files as well so in case of a re-install you don't need to extract your data from the root partition. Just use your existing /home partition in installer and choose not to format it ;-)

If you don't need a separate /home, then you just need 2 partitions for installation of Ubuntu. Add up your space to the '/' partition instead.

Feel free to post as many queries as you've got :-)

Good Luck!


Thanks, Fellas.  That fixed it.  Thanks also for the good instructions.  They really helped.

---

