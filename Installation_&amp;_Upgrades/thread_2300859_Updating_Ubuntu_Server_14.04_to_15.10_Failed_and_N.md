---
title: "Updating Ubuntu Server 14.04 to 15.10 Failed and Now I can Boot 14.04"
date: 2015-10-28
forum: Installation &amp; Upgrades
---

### Post by adam.vadala_roth on 2015-10-28
so I was attempting to update my server running Ubuntu 14.04 to the new 15.10. An error occurred (forgot to write it down) and I was left at the terminal, I tried to reboot it with "sudo reboot" and "sudo shutdown -r 0" but it kept saying that the commands were not found. I then manually powered down the machine and attempted a reboot. When I boot I get the following error:

ubuntu target filesystem doesn't have requested /sbin/init.
/bin/sh: 0: can't access tty; job control turned off

I tried the following and still can get it to boot
1. booted from a Live USB and ran sudo fsck -f on the boot volume
2. When that didn't work I created the empty /fsck file in the root directory to invoke fsck before boot
3. I check the fstab file to see if it was corrupted or inccorect and it checked out fine. 

Anyone know of a fix ? I want to get the system booting if I can.

---

### Post by TheFu on 2015-10-29
There is no direct 14.04-->15.10 upgrade.

IMHO, servers should only run LTS releases. 14.04 is the current LTS. 16.04 will be the next LTS.

The only fix is to restore from the backup you made before attempting a major system update.

---

### Post by jabowery2 on 2015-12-03
> **TheFu said:**
> There is no direct 14.04-->15.10 upgrade.

There is, and has been for about 2 months, an [Update Manager]("http://www.ubuntu.com/download/desktop/upgrade") supported [upgrade path direct from 14.04 LTS -> 15.04]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1510920") and it leaves the system in a state where not even the GRUB recovery boot option works.

This upgrade path came into being, intentionally, as part of this bug fix:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024)

The failure of this upgrade path may be related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1497688](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1497688)

It is still unassigned although it was finally recognized as a real bug last week.

---

### Post by SeijiSensei on 2015-12-03
Regardless, as TheFu says, servers should run LTS versions not transitional ones like 15.10.

---

### Post by TheFu on 2015-12-03
a) he's running a server, not a desktop. That Upgrade Manager link is for desktops.
b) Production servers belong on LTS releases. Test boxes - do whatever you like.
     [https://help.ubuntu.com/lts/serverguide/installing-upgrading.html](https://help.ubuntu.com/lts/serverguide/installing-upgrading.html)
> Please make sure you have a backup of your important data. For more on disk cloning, please see here. 

c) [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) ... 
    shows the old pattern of NN.04 --> NN.10 --> NN+1.04 upgrades 
OR
    NN.04 --> NN+2.04 (LTS-to-LTS) upgrades.
> If you wish to 'skip' a version, you can back up your data and do a fresh installation, or **progressively upgrade to each successive version**. For example, to upgrade from Ubuntu 11.10 to Ubuntu 12.10, first upgrade to 12.04, then upgrade 12.04 to 12.10.  Perhaps this is out of date and needs to be updated to reflect the new, hotness of skip-release updates? I dunno.

So, this skip-a-release upgrade is definitely something new. The fact that there are issues from 14.10 and 15.04 don't bode well for it being ready-for-prod use yet. I find it scary that this is still enabled when there is clearly an issue which can leave people with non-booting systems.

Plus the title is a little confusing.  Perhaps s/can/can't/?
Of course, Linux systems are not one-size fits all, so there is could be a very good reason that 15.10 is required for this server. Can't tell from here.

Anyway, I wish there was a clear answer for the OP. Sadly, it still appears that restoring from the backup made just prior to the upgrade attempt is the best answer. Each of the links above strongly encourage making a backup before attempting the upgrade.  I'd mark this as a learned lesson (which I learned the hard way too, long ago) and move forward.

---

