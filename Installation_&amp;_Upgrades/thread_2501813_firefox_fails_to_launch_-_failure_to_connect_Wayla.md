---
title: "firefox fails to launch - failure to connect Wayland. want to use xorg display."
date: 2024-10-21
forum: Installation &amp; Upgrades
---

### Post by uglybug on 2024-10-21
[FONT=Ubuntu]i am trying to uses Mozilla Firefox 131.0.3 on WSL2 with ubuntu 24.04.1 LTS & Windows Remote Desktop Connection but after trying launch from the FireFox icon, nothing happens.

however from the terminal mode, the output is shown below:

[1664] Wayland Proxy [0x7f598f454020] Error: CheckWaylandDisplay(): Failed to connect to Wayland display ‘/run/user/1000/snap.firefox/wayland-0’ error: No such file or directory[/FONT]
[FONT=Ubuntu]
even with configuration set to wayland=false to force xorg to be the default display.
i have tried to install firefox from several sources with reboots in between;
including this site - [Install firefox on Ubuntu using the Snap Store | Snapcraft]("https://snapcraft.io/install/firefox/ubuntu") 
sudo snap install firefox[/FONT]
[FONT=Ubuntu]none of the installation attempts on ubuntu 24.04.1 LTS, work.

the contents of "/run/user/1000/snap.firefox" 
is this problem related to permissions ?

[/FONT]
[EMAIL="uglybug@NTL0W10:/run/user/1000/snap.firefo"]uglybug@NTL0W10:/run/user/1000/snap.firefo[/EMAIL]x$ ls -la
total 0
drwx------  3 uglybug uglybug  60 Oct 21 12:40 .
drwx------ 14 uglybug uglybug 520 Oct 21 12:40 ..
drwxrwxr-x  2 uglybug uglybug  60 Oct 21 13:11 dconf
[EMAIL="uglybug@NTL0W10:/run/user/1000/snap.firefo"]uglybug@NTL0W10:/run/user/1000/snap.firefo[/EMAIL]x$

---

