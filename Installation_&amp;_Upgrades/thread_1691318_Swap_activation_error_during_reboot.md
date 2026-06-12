---
title: "Swap activation error during reboot"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by nabilalk on 2011-02-19
Getting the following error upon reboot after attempting to upgrade from Karmic to Lucid

```
init: ureadahead main process (485) terminated with status 5
swapon: /dev/sda2: read swap header failed: Invalid argument
mountall: swapon dev/sda2 [504] terminated with status 255
mountall: Problem activating swap: dev/sda2
fsck from util-linux-ng 2.16
/dev/sda1: clean, 198765/684096 files, 1386596/2751123 blocks
init: ureadahead-other  main process (526) terminated with status 4
udevd[509]: can not read '/etc/udev/rules.d/z80_user.rules''

* Starting init crypto disks....                                            [ OK ]

```

Error occurred after attempting Karmic to Lucid upgrade at next reboot ```
# Make sure your current release is the latest and greatest
sudo aptitude update
sudo aptitude safe-upgrade
```[http://ubuntuforums.org/showpost.php?p=8194888&postcount=9](http://ubuntuforums.org/showpost.php?p=8194888&postcount=9)
If I reboot into recovery and updage GRUB, then select normal start, I am able to login but without a GUI. 
How can I fix this? Thanks.

---

