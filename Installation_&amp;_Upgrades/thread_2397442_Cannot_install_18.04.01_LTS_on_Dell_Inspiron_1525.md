---
title: "Cannot install 18.04.01 LTS on Dell Inspiron 1525"
date: 2018-07-29
forum: Installation &amp; Upgrades
---

### Post by ftirapelle on 2018-07-29
Hi 

Two problems on my Dell Inspiron 1525:

1) After a recent update of Kubuntu 16.04 LTS x64 some buttons (for example the menu button of firefox or the downloads button do not work. I click on the button but nothing appears

2) I'm not able to install the latest version 18.04.01 of Kubuntu x64. Errors in the image ([ATTACH=CONFIG]280569[/ATTACH]) . 

I have tried to modify the GRUB inserting nomodeset or nvidia-drm.modeset=1. But this hasn't help

---

### Post by oldfred on 2018-07-29
It looks like that system only has Intel video, so boot parameters for nVidia will not normally help, but you may need Intel video boot parameter(s).

This suggests: video=SVIDEO-1:d
[https://askubuntu.com/questions/893817/boot-very-slow-because-of-drm-kms-helper-errors](https://askubuntu.com/questions/893817/boot-very-slow-because-of-drm-kms-helper-errors)
This suggests:  **sudo apt-get remove xserver-xorg-video-intel**
[https://www.reddit.com/r/archlinux/comments/6m3wi9/drm_atomic_helper_error_flip_done_timed_out/](https://www.reddit.com/r/archlinux/comments/6m3wi9/drm_atomic_helper_error_flip_done_timed_out/)

Issues may be related to:
       Ubuntu & Debian Abandon Intel X.Org Driver For Most Hardware, Moves To Modesetting DDX - anything past the i965GM era
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Debian-Abandon-Intel-DDX](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Debian-Abandon-Intel-DDX)
Ubuntu and Debian (and thus other Debian-based distributions too) have abandoned the xf86-video-intel X.Org driver for all recent generations of Intel graphics hardware and instead makes use of the xf86-video-modesetting generic driver in its place.

---

### Post by ftirapelle on 2018-07-30
I have tried to remove xserver-xorg-video-intel and to modify /etc/default/grub inserting video=SVIDEO-1:d but I have the same problems.
Any other ideas?

---

