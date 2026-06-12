---
title: "Upgrade from disk, not overwriting data, etc."
date: 2019-06-01
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2019-06-01
This is different from previous questions due to later versions of Ubuntu and the update software.

I have had one failed upgrade, which I restored from a clone copy. As an alternative method to the one offered in update, I'm thinking I might should approach this from an install from disk.

I'm not a command line wizard, though I can easily follow detailed instructions.

I think I understand that I can do this from an ISO install disk. Select "No Format". I don't want or need to select any other options but do select "something else". Does "something else" require any input or intervention from me? If so, exactly what?

Do I need to specify or choose any partitions, or simply none? Accept all defaults, or ???

Are there any other details to this process I need to know ?

Is there any place where all this is fully explained in extreme detail ?

---

### Post by yancek on 2019-06-01
The Something Else option is a manual install so yes, it does require intervention on the part of the user.  If you have a separate /home partition for instance, you can select to not format it and just use the / (root filesystem) partition and format that.  You select a specific partition on which to install the Ubuntu system files or create it from unallocated space.  The link below describes using the Something Else option and is pretty detailed but outdated.  You can create a separate home/data partition but no much point in creating separate tmp or var partition for a regular user.  It's a good place to start.

[https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by Impavidus on 2019-06-01
If I get this right, you tried a release upgrade, which failed. Then you restored your old system from a backup. Now you want to install the new release, keeping your old files. This is also called a dirty install. This is possible.

Use the "something else" option, also known as manual partitioning. You'll have to do everything manually. Select the partition you want to use, set it to be used as root partition (mountpoint /) and make sure it's not marked to be formatted. Also configure the other partitions you want to use, if any (swap, data, ...). Then install. You still have that backup, right?

Dirty installs are rarely recommended. They're a bit dirty. I'd usually try a clean install, followed by restoring data from backups or simply keeping the data on a separate partition.

---

