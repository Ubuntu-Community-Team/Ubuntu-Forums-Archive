---
title: "Need to add windows partition :("
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by Bandit on 2005-07-26
Hello Everyone,
I am using the best distro in the world "Ubuntu :)"
But unfortanatly I want to install XP on my system to just play games. 
I just subscribed to Cedega, but it isnt stable enough yet.
Plus some of the games I want to use are not supported or barely work.
I have a 160GB HD.. I belive I used ext3 file system "or what ever uby 5.04 defaults to" when installing Ubuntu. Is there a way I can re-partition this drive so I can install XP on a partition without loosing my data? Also if I can add windows, how can I re add linux to my mbr without reinstall linux?
Thanks,
Joey

---

### Post by varunus on 2005-07-26
I believe you can use gparted to repartition your drive with no data loss.  (Could be wrong though.)  I think there are instructions at [www.ubuntuguide.org](www.ubuntuguide.org) on how to install it.

You can use the Ubuntu install disk and type "rescue" to boot in recovery mode off a grubless hard drive with an Ubuntu partition.  I think there's a "grub-install" utility from there.  Do a little reading on grub-install though, I'm not sure.

---

### Post by Bandit on 2005-07-26
Sweet, its worth a shot.. Do you think its available via Apt-Get?
Thanks,
Joey

---

### Post by DancingSun on 2005-07-26
I'm not sure if it's possible to do this without the loss of data.

I'm guessing right now the entire HDD is used by Ubuntu.  If that's case, you have a problem, as Windows does not like to be added to the end of the drive.  It likes to live in the beginning of the drive.  If GParted can safely clear out some space in the beginning of the drive, then it should be an easy task.  If not, then you might be up for some headaches.

Also beware that Windows might decide to use your entire drive and overwrite Ubuntu.

---

