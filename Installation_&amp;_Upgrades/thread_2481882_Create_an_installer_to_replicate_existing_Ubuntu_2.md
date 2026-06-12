---
title: "Create an installer to replicate existing Ubuntu 22.04 System on another machines"
date: 2022-12-12
forum: Installation &amp; Upgrades
---

### Post by umangmahajan on 2022-12-12
Hello,

We want to replicate the setup of partitions, applications & data of a system having Ubuntu 22.04 running to another machines by means of an installer.

The existing system has 2 partitions, i.e., 'EFI' & 'root'.
We are planning to shrink 'root' partition to 4GB (to store filesystem only) & use the remaining available space as a data partition.

Is it possible to make an installer which will create these partitions as per above scheme on a new system and copy the applications & related data to respective partitions during a fresh installation?
Any inputs or guidelines or reference links are much appreciated.

---

### Post by MAFoElffen on 2022-12-12
Yes. If you install the first machine, then copy the file /var/log/installer/autoinstall-user-data from that first machine, you can use that file as your autoinstall config file to replicate that configuration.

---

### Post by TheFu on 2022-12-12
> **umangmahajan said:**
> Hello,

We want to replicate the setup of partitions, applications & data of a system having Ubuntu 22.04 running to another machines by means of an installer.

The existing system has 2 partitions, i.e., 'EFI' & 'root'.
We are planning to shrink 'root' partition to 4GB (to store filesystem only) & use the remaining available space as a data partition.

Is it possible to make an installer which will create these partitions as per above scheme on a new system and copy the applications & related data to respective partitions during a fresh installation?
Any inputs or guidelines or reference links are much appreciated.

If everything is the same, you can just clone the full storage using any of the cloning tools.  Just be aware that after the cloning, no 2 of those storage devices should be connected to the same machine, since the disk, partition and file system  UUIDs will be identical.  Being on the same network is fine, just not physically connected to the same computer.

BTW, for 22.04, I think 4G for the OS is overly optimistic.  Since 20.04, even 25G is optimistic for a normal desktop given to most people:
```
$ dft
Filesystem             Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00--root ext4   19G   13G  4.7G  74% /
/dev/mapper/vg00--home ext4   12G   11G  230M  98% /home
/dev/vda1              vfat  511M  7.1M  504M   2% /boot/efi
```
The OS is using 13G today. It is a "minimal" install.  No media files are stored on the system.

I had to add more storage (10G) because my initial allocation of 30G total wasn't sufficient once the needed swap was addressed (moved from a swap file to a swap LV) and local documents restored.  I'm using a minimal GUI and only have specific tools used installed.  If it were me, I'd start with a larger amount of storage for testing and get it slimmed down to what you need.  There are lighter Linux versions than any Ubuntu can touch, if the goal is to have just a few programs for specific users and nothing else.  Tiny Core Linux comes with a GUI and fits in 22MB if you seek something small, say for a kiosk system with only a web browser.  They make a 64MB version (or used to) that comes with a few more tools.

---

### Post by umangmahajan on 2022-12-13
@MAFoElffen
Yes, this might be useful to install all the apt/snap packages on the destination system.

Alternately, we can take 'dd' of the necessary partitions & create ISO file of the modified system, as pointed out by @TheFu.

However, what we are looking for is an auto-installer script which can run at the grub level, create partitions as per scheme & install the contents in the respective partitions.

---

### Post by tea for one on 2022-12-13
> **umangmahajan said:**
> 
We want to replicate the setup of partitions, applications & data of a system having Ubuntu 22.04 running to another machines by means of an installer.
Have you created any users in this system?

---

### Post by umangmahajan on 2022-12-13
Yes, there is one additional user along with default 'root' user.

---

### Post by TheFu on 2022-12-13
> **umangmahajan said:**
> Yes, there is one additional user along with default 'root' user.

Normal Ubuntu (desktop nor server) doesn't enable 'root'. The first userid created is placed into the sudo group and that's the end of that.  It is only the bastardized installs that enable root logins, by companies who aren't following the Ubuntu Security model.

---

### Post by tea for one on 2022-12-13
> **umangmahajan said:**
> Yes, there is one additional user along with default 'root' user.
I cannot quite understand what you are trying to achieve?
If you reproduce this system on different machines, then each machine would have the same user, same login password and insecure root login access.
This doesn't seem sensible at all?

I think that you need to explore OEM (Original Equipment Manufacturer) installations.
You can set up identical partitions in advance.
When the end user boots the PC for the first time, he/she will be taken to the system setup wizard where location, keyboard layout, user name etc is available for user choices.

---

### Post by MAFoElffen on 2022-12-13
At the recycler I used to volunteer for, What TheFU said jogged my memory to what we did there... 6 standardized configs with the partitions shrunken down to the minimums, so that copying them to machines over the network was down to a minimum. It was all PXE boot to log into the server, transfer, expand out the partitions, done. For deploying lots of machines that were all the same configs, that was really fast and the way to go.

---

