---
title: "Installation on a thin client for efficiency and silence!"
date: 2017-03-04
forum: Installation &amp; Upgrades
---

### Post by guy.joseph on 2017-03-04
Hi


Looking to Install Ubuntu Server 16.02 (i686) to run OwnCloud on a HP T5740 thin client.  OwnCloud is a Dropboxesque package which I really like, based on a LAMP stack.  I am expecting to use the latest versions of Apache and MySQL.

It is fitted with a 2GB flash memory drive and a 500gb Hard Drive. I could also install extra USB sticks if the 2gb module isn't enough memory.


The unit will be used infrequently, by a single user and most of the time will be sitting idle.  What I'd love to achieve is that everything "vital" that LAMP stack and Owncloud need to stay alive is kept on the flash drive, which would mean that the hard drive isn't being accessed when the machine is not being actively used, and therefore could be spun down... this would make for a completely silent machine most of the time.


I'm quite new to Linux, and I'm guessing so far that this setup will require installing with different partitions of the OS on different physical drives, but I am not sure which to put where!


I would really appreciate any help in how to set this up to work in this way. It would be amazing if I could have the machine sitting there silently for most of the time. I'm quite happy to accept a fractional delay on the first request when the hard drive has to spin up.


Cheers

---

### Post by DuckHook on 2017-03-04
Ubuntu will not install dynamically on 2GB of flash. You might get it to install as a static LiveUSB image—though I don't know if this can be done with server—but this means no persistence, updates, patches or /home. In a server environment, not patching is a bad idea.

Your best bet is your own idea to install onto a USB stick. GUI environments tend to be sluggish when run this way, but CLI-only servers aren't too bad.

Your use-case is not that complicated:

[LIST=1]
[*]Install the whole OS (including /home) dynamically to the USB stick.
[*]Install autofs (see its man page).
[*]***Do not*** mount your 500 GB HDD in fstab.
[*]Instead mount it through autofs.
[*]Create a data partition in your HDD.
[*]Move *only* your LAMP data to the HDD.
[*]Symlink this data back to where your apps expect to find them (on the USB stick).
[*]Make sure hdparm sets your HDD to standby at boot (see its man page).
[/LIST]
Segmenting your installation directories is neither needed nor desired. In fact, you must put absolutely no system files on your HDD. Do not put the swap partition there. hdparm will not work on any disk that has system partitions/files.

Once set up this way, your HDD will only be mounted when data needs to be written/read. After a small period of inactivity, autofs automatically unmounts the drive. And by turning on standby, the drive will then spin down after a user-defined period of inactivity.

---

### Post by guy.joseph on 2017-03-12
Hi

Thanks very much for your advice here.  It certainly seems to achieve what I wanted.  I have sucessfully installed Ubuntu on a USB stick, and I have set up the 2gb built in memory as Swap.

However I run in to an issue at step 4: I have a single Ext4 partition on my Hard drive, and I have set up AutoFS to mount to /data/.  This is all working perfectly, but I have a permissions issue somewhere... anytime I try to modify something in /data, I get a Permission Denied error, even when using sudo.

All the tutorials that google has shown me so far are for connecting to a network share with autofs, so I wonder if you can help me out again.

Otherwise looks great, I think I can manage everything there!

Cheers

---

