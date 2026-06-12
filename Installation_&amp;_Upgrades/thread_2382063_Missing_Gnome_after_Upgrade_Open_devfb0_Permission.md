---
title: "Missing Gnome after Upgrade: Open /dev/fb0: Permission denied"
date: 2018-01-08
forum: Installation &amp; Upgrades
---

### Post by Pyork on 2018-01-08
Dear Colleagues, please help, I can't work with my new working device, a Thinkpad T470. 

1. Ubuntu 17.04 startup stops before Gnome desktop comes up.
2. Last message on screen: */dev/nvme0n1p2: clean, xxx/xxxx files, xxx/xxxx blocks*3.
3. Only error message in Xorg.0.log:
...
[I][    89.181] (EE) open /dev/fb0: Permission denied
[    89.181] (WW) Falling back to old probe method for vesa
[    89.181] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support[/I]
...
4. May be the reason: One automatic upgrade of *mesa-vdpau-drivers:amd64 (17.0.3-1ubuntu1, 17.0.7-0ubuntu0.17.04.1)*
5. One obvious? error in dmsg.log:
...
[I][    3.631814] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8265-26.ucode failed with error -2
[    3.631967] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8265-25.ucode failed with error -2
[    3.632286] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8265-24.ucode failed with error -2
[    3.632296] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-8265-23.ucode failed with error -2
[    3.635251] iwlwifi 0000:04:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm[/I]
...
Files are attached!
This is my first post since year 2000. May I have luck with you guys, thank you in advance!
Kind regards, Jörg from Berlin

---

### Post by Pyork on 2018-01-09
Ok, I just reinstalled Gnome, like in [https://www.computersnyou.com/4945/re-install-xorg-xserver-completely-ubuntu/](https://www.computersnyou.com/4945/re-install-xorg-xserver-completely-ubuntu/).
I am so happy with Linux and the abillity to repair things.

---

