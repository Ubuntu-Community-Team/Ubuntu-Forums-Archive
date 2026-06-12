---
title: "Grub And Audio problem after fresh install"
date: 2020-09-16
forum: Installation &amp; Upgrades
---

### Post by dejavih on 2020-09-16
Hello all!

After several years without using Ubuntu I have decided to give it another try and I have installed version 20.04 in my new HP Spectre x360 15". However, I am facing two main issues that makes me think about going back to Windows:

1. GRUB menu freezes completely if I have a USB device connected. I only have one USB port so I cannot try with others. This happens with my USB Logitech receiver and me keyboard connected by USB. This does not happen with my laptop fan base. I think the problem is that GRUB messes around these devices and then get frozen. However, the fan base is a "dummy" device so then is ok. Any clue of what I could do to solve this?

2. Audio problems; Speakers do not work, but headphones connected to the jack port do. Also mic seems to record very low. I have done several things like pavucontrol, etc. But the only thing I have done that triggers a difference is the use of "hdajackretask". I managed to listen two speakers yesterday, though this laptop has 4 speakers and when I did so I "kill" the mic. How do people know which pins needs to be configured to what? Is there a datasheet somewhere? 

Thank you in advance and kind regards.

---

### Post by dejavih on 2020-09-22
Nothing?

---

### Post by oldfred on 2020-09-22
seems like a lot of posts:

HP Spectre x360 Disable Optane (should use gpt to boot installer in UEFI mode, but MBR may work)
[https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume](https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume)
HP X360 Update UEFI F20
[https://ubuntuforums.org/showthread.php?t=2439220](https://ubuntuforums.org/showthread.php?t=2439220)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086)
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)

---

