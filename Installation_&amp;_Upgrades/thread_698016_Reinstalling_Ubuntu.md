---
title: "Reinstalling Ubuntu"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by motorbreath on 2008-02-15
I am running Gutsy on a Toshiba Satellite A100 dual booting with Vista. I have been upgrading since 5.10 using apt-get. I have everything running as I like but  I have noticed my system slowing down and am having a few little problems with sound, compiz and it just doesn't seem to be as stable as it used to be. I would like to give it a spring clean. Is the best way to do this reinstalling Ubuntu and can I do this without losing my home directory? (my wife and kids also have accounts)

Would appreciate any advice

---

### Post by Pumalite on 2008-02-15
If you have a separate /home directory, you are fine; just use it in the next installation (don't format it!) If not, you have to save home and data somewhere else, and later restore.

---

### Post by Tatty on 2008-02-15
Always a good idea to back up your /home to some sort of external drive first though - you never know what may happen! :)

---

### Post by Herman on 2008-02-15
You should always have a backup of your important files at least, at all times and especially before doing any hard disk partitioning work or re-installing an operating system.

If you want to re-install you can use the Live CD to delete all your operating system directories and just leave your /home directory in the partition. Then use a partition editor (GParted) to resize your partition to a smaller size. At least make 5.0 GB of free space for the / (root) file system of a new installation. You could create a new partition in the free space for a fresh install, and during the installation, have the partition with your /home directory mounted as /home.
Then when you reboot, your files will still be there and when you re-install your software it will mostly get back the same settings.

I am not sure if re-installing Ubuntu will help, but it might. Ubuntu doesn't normally tend to slow down over time like certain other operating systems for many different reasons. 

How full is your partition, is there more then 20% free space?
It might help to copy some files to some other media if the Ubuntu partition is getting more than 80% full and delete them from the hard disk. Most people keep a lot of files on the hard disk they never use. Videos you've already seen, music you hardly ever listen to and so on. They can be stored on a DVDs or an external USB disk maybe.
Sometimes emptying the Garbage bin helps too and so can a file system check from the command line or with GParted.

[                         Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_") a user freindly GUI method

[                      Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line

I'd try some of those things first before i decide to re-install. 

Regards Herman :)

---

