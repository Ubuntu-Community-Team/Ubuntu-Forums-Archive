---
title: "booting into karmic using the older grub"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by zubin71 on 2010-02-02
hi, 

i had a system running ubuntu karmic and grub2. Last day i installed fedora 12 on another partition and also installed the older version of grub that came along with it(because i was more used to it). 


**The current status is:**1. can boot into fedora, cannot boot into ubuntu.
2. can boot into fedora, chroot into the ubuntu partition
3. no data loss

However, i just can`t boot into ubuntu from the older version of grub which i have presently.

**Question is:**
How do i boot into karmic from the older version of grub? :) do take some time off and reply of you know the answer! :)

---

### Post by yogesh.girikumar on 2010-02-03
Hi,

      I was in the same kind of pickle a few weeks earlier and this is what I tried and got my Ubuntu to work without affecting WinXP. The procedure should be similar in your case too..

1. Booted into the live CD 
2. Opened terminal in the live cd
3. Typed the following.

    Mounted sda1 into /mnt temporary directory
   ```
$ sudo bash
# mkdir /mnt
# mount /dev/sda1 /mnt
```      Chrooted into th directory and created a device file and then installed grub afresh.
   ```
# chroot /mnt
# mknod /dev/sda b 8 0
# mknod /dev/sda1 b 8 1
# cd /boot/grub
# grub-install /dev/sda
# exit
# reboot
``` Here is an informative link that can help: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

       You may try this in Fedora itself. I believe Fedora 12 has a live CD install too like Ubuntu. SO you can boot into that and try this or something similar. Hope it works.

GRUB 2 is a bit different from the older GRUB. But although the configuration of GRUB2 may be different from the older GRUB and unfamiliar, I'd say it's better in functionality. You can not edit the main GRUB file, it's constructed every time from supporting config files. Which is a good thing IMO.

Here are some informative links. 

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://www.gnu.org/software/grub/grub-2.en.html](http://www.gnu.org/software/grub/grub-2.en.html)
[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)
[URL="http://ubuntuforums.org/showthread.php?t=1285897"]
[/URL]Let me know if this helps.

---

