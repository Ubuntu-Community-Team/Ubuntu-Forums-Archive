---
title: "just guest session available, login fails"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by barra2 on 2014-04-21
I'm desperately trying to login into ubuntu 12.04 LTS. After boot I see the guest session asking for my password. After login it appears a black screen for just a half second and I will redirect to the previous login screen.

Yesterday, I installed a ppa for gvfs and gvfs itself via apt but that didn't work correctly so I removed both. After reboot, the described situation started. I checked the gvfs package and tried a lot of recommended commands and finally it seems to be fixed. Furthermore, I reinstalled my nvidia drivers and deleted this .Xauthority file in my home folder.

Every clue is welcome!

Update: Also deleted /tmp/.x0-lock. Didn't help

---

