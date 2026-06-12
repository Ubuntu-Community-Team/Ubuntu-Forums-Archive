---
title: "Problem with boot loader even after boot-repair"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by ravi6456 on 2013-01-19
I have been facing a very long time time to boot into my system which runs on Ubuntu 12.04 LTS.

I have followed this thread "https://help.ubuntu.com/community/BootPartition" and using gparted created a gb partition and did a "boot-repair" ( log after this step: [http://paste.ubuntu.com/1549333/](http://paste.ubuntu.com/1549333/)

But when I restart it is again taking a very long time (about 20mins) to get to welcome screen & boot-repair again shows the same message: "The boot files of [The OS now in use - Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted"
any help is more than welcome, as I'm in a middle of a big academic project and loading  new os again is not an option.

---

### Post by oldfred on 2013-01-19
Did you check the option on separate /boot with boot repair? You have boot files still in / (root) and /boot. Boot-Repair does not look like it used the /boot on the reinstall?

I generally prefer smaller / (root) partition of 25GB and separate /home or data partition(s) for desktops especially those with large drives. Boot repair suggest the /boot as it is often easier to squeeze in a small /boot near front of drive.

But long boot time should not be that issue. Usually system just does not boot when it cannot find boot files and reports errors.

Use Log File Viewer and look at dmesg first. Then look for errors, drivers trying to install several times & failing, or just very long times between entries.  Do not post entire dmesg but you can post any entries you may have questions on. That may lead to what the issue is.

---

