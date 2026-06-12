---
title: "Wont see Windows"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2011-05-29
I unplugged the Windows drive, during the installation of Ubuntu 9 (to make things easier). 2 separate drives. When installation was complete, I plugged the other drive back in (now both are plugged in). I went to the BIOS and made sure the Linux drive was the set to boot before the windows drive. The only thing that comes before that of course is the cd drive

CD-0
HDD-1 (linux)
HDD-0 (windows)

I booted into linux after this and ran 'sudo update-grub'. The cmd was successful. However, when rebooting it does not give me the option to boot to windows. Why not?

PS. If I go to Places (under GNOME bar), Then I can see (and mount) the windows drive. So it is accessible.

---

### Post by kakashi_12 on 2011-05-29
Not sure if this makes a difference but...
during installation, i setup manual partitions so that i could make my swap partition.
When I made the ext3 partition for linux, i checked the option that said "flag bootable". I'm not sure what that means. Im assuming that means that partition would be a bootable one.

---

### Post by kakashi_12 on 2011-05-29
i wonder if it will make a difference if i switch the jumpers on the drive. make linux drive master and windows drive slave.

---

### Post by kakashi_12 on 2011-05-29
nope. no difference.

---

