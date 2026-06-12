---
title: "install ubuntu over another linux distro"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by rogergreenlaw on 2007-05-11
Does anyone know if it is possible to install ubunto over another linux ditro without losing existing data that has been created?  I would like to keep my current /home directory structure and contents without backing up those files and restoring.

I'm not opposed to backing up, would just like to skip the restore process after installing.  I have been using RedHat linux for years - both as a server and desktop and I am looking for a different distribution that would be easier for new linux users.  I need to be able to successfully test any disto that I am to recommend using.

Thanks for any assistance.

I will be creating a small test network within the next couple of weeks and plan to use either Ubunto or RedHat based on the success or failure of my Ubunto installation and testing.

---

### Post by aysiu on 2007-05-11
You would probably create a separate /home partition and then reinstall... but I wouldn't advise using the same /home between two distros, as distros sometimes store/use config files differently. I'd mount it as /documents or /data instead of /home and then symlink the appropriate directories.

---

### Post by rogergreenlaw on 2007-05-13
Thanks for the reply.  Is there any difficulty accessing the logical volumes (lvm) created by Fedora core 4?  I allowed the default install on my system which created logical volumes instead of mapping hard drive partitions.

I am writing this using the bootable Ubuntu desktop CD.  I like the look of Ubuntu so far.

Roger.

---

### Post by FuturePast on 2007-05-13
To install onto lvm you will need the alternate install cd, but otherwise there will be no problem.

---

