---
title: "Boot Loader Error"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by mohamedshaji on 2012-02-06
Sir,

I am not expert in ubuntu. But I like it very much. In my last computer I used Ubuntu and Win Xp in a single hard disk. now i bought a new machine with single HDD. I installed windows 7. After some days I used the shrink option and made a new unused partition. In this partition installed UBUNTU 9.10. in the ubuntu space used the custom mode partition like this,

200 MB /boot
2 GB   swap
4 GB   /home
15 GB  / (balance used)

after the installation machine rebooted and I got an error like this

error: no such partition
grub rescue>

I tried to install 2 or 3 times with some setup changes but the error continues. finally using the machine boot loader removed using the windows 7 setup DVD. I search net this error but I can't get any correct post. 

expecting reply

---

### Post by oldfred on 2012-02-06
Welcome to the forums.

Often better for standard desktops not to have the separate /boot. It is often needed for old systems with BIOS that cannot boot from beyond 137GB, or server or server type configurations with RAID or LVM.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. Be sure to also tell it you have a separate /boot so it reinstalls grub2's boot loader correctly.

---

