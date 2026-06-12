---
title: "Where does update-manager grab its temporary space?"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by m-brooks on 2014-08-21
A while back I received an informational alert saying that a new version of lubuntu was available (I'm currently running 12.10 - quantal). When I tried to upgrade it failed, reporting that there was insuffucuent space on the root drive. My EeePC has a primary 4GB solid state drive at / and a secondary 8GB one at /usr. The primary drive has less than 700MB free while the secondary has 3.7GB free.
Now I can't even attempt to do upgrades because when I run update-manager it reports that it can't find gb.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources.
I could try installing 14.04.01 afresh, but then I would lose the various applications and configurations that I have (painfully - I'm not a Linux expert) managed to tweak to my liking. I have at least copied a set of files that I had stored under my home directory onto a flash drive, so at worst I can do a fresh install and then copy these back.

However, a fresh install will likely just leave me in the same position w.r.t. major upgrades. I at least need to understand where in the file system the automatic upgrade needs to grab workspace so that I can create a link from this location to an area on the larger drive.

Ideally I would like to do an upgrade to 14.04.01 rather than an installation. I have downloaded and burnt the "alternate" CD-ROM, but I'm afraid to try using this without knowing what it's likely to do.

Any suggestions anyone?

Regards.

---

### Post by ajgreeny on 2014-08-21
If you make sure that all the files and folders your /home folder are backed up, including all the hidden ones (that have names starting with . such as ~/.config) you can do a clean install of 14.04, using the alternate installer if you want to, and then restore all the files and folders from your backup into to the new installation.  That should make sure that the configurations that you have spent a lot of time getting to what you want, are there in your new installation.

You may still find that there is not a lot of free space in the root partition as 14.04 takes up more space than 12.04 or 12.10, I think, and my virtual machine installation of 14.04 takes abut 2.8 - 2.9 GB of space for the root partition, and that is with nothing extra installed, however, your 4GB should be enough assuming you are not using it as a main machine and trying to store masses of large videos or music files.

---

### Post by ian-weisser on 2014-08-21
Package downloads go to /var/cache/apt/archives

---

### Post by m-brooks on 2014-08-21
Thanks for the replies guys.
Ian, are upgrades of the overall system (including the kernel) also handled as package upgrades or do they use a separate mechanism that uses a separate directory for temporary storage?

---

### Post by ajgreeny on 2014-08-21
> **m-brooks said:**
> Thanks for the replies guys.
Ian, are upgrades of the overall system (including the kernel) also handled as package upgrades or do they use a separate mechanism that uses a separate directory for temporary storage?
It's all the same; everything goes into /var/cache/apt/archives.

If you want to you can set the upgrade-manager or synaptic, whichever you use, to to delete all the downloaded packages after installing them, which can be useful in a space restricted setup as that archive folder can get very big if you never empty it.

---

### Post by m-brooks on 2014-08-21
Thanks - that's all very helpful. Much appreciated. :)

Michael

---

