---
title: "Upgrade 22.04 to 24.04.1 won't upgrade broken packages"
date: 2024-09-03
forum: Installation &amp; Upgrades
---

### Post by ryanrk on 2024-09-03
Looking at the logs it seems to be system packages.

Is there a way to fix this minus a full reinstall?  

Thank you!

```
Investigating (0) coreutils:amd64 < 8.32-4.1ubuntu1.2 -> 9.4-3ubuntu6 @ii umU Ib >
Broken coreutils:amd64 Breaks on usrmerge:amd64 < 25ubuntu2 @ii mK > (< 39)
  Considering usrmerge:amd64 -3 as a solution to coreutils:amd64 5112
  Added usrmerge:amd64 to the remove list
  MarkDelete usrmerge:amd64 < 25ubuntu2 @ii mK > FU=0
  Fixing coreutils:amd64 via remove of usrmerge:amd64
Investigating (0) python3:amd64 < 3.10.6-1~22.04.1 -> 3.12.3-0ubuntu2 @ii umU Ib >
Broken python3:amd64 Conflicts on python3-distutils:amd64 < 3.10.8-1~22.04 @ii mK Ib >
  Considering python3-distutils:amd64 -2 as a solution to python3:amd64 508
  Added python3-distutils:amd64 to the remove list
  MarkDelete python3-distutils:amd64 < 3.10.8-1~22.04 @ii mK Ib > FU=0
  Fixing python3:amd64 via remove of python3-distutils:amd64
Investigating (0) libkwinglutils14:amd64 < none -> 4:5.27.11-0ubuntu3 @un uN Ib >
Broken libkwinglutils14:amd64 Breaks on libkwinglutils13:amd64 < 4:5.24.7-0ubuntu0.2 @ii mK >
  Considering libkwinglutils13:amd64 -2 as a solution to libkwinglutils14:amd64 14
  Added libkwinglutils13:amd64 to the remove list
  MarkDelete libkwinglutils13:amd64 < 4:5.24.7-0ubuntu0.2 @ii mK > FU=0
  Fixing libkwinglutils14:amd64 via remove of libkwinglutils13:amd64
Investigating (0) libtss2-mu-4.0.1-0t64:amd64 < none -> 4.0.1-7.1ubuntu5.1 @un umN Ib >
Broken libtss2-mu-4.0.1-0t64:amd64 Conflicts on libtss2-mu0:amd64 < 3.2.0-1ubuntu1.1 @ii mK >
  Considering libtss2-mu0:amd64 -3 as a solution to libtss2-mu-4.0.1-0t64:amd64 14
  Added libtss2-mu0:amd64 to the remove list
  MarkDelete libtss2-mu0:amd64 < 3.2.0-1ubuntu1.1 @ii mK > FU=0
  Fixing libtss2-mu-4.0.1-0t64:amd64 via remove of libtss2-mu0:amd64
Investigating (0) libkwineffects14:amd64 < none -> 4:5.27.11-0ubuntu3 @un uN Ib >
Broken libkwineffects14:amd64 Breaks on libkwineffects13:amd64 < 4:5.24.7-0ubuntu0.2 @ii mK Ib >
  Considering libkwineffects13:amd64 -3 as a solution to libkwineffects14:amd64 11
  Added libkwineffects13:amd64 to the remove list
  MarkDelete libkwineffects13:amd64 < 4:5.24.7-0ubuntu0.2 @ii mK Ib > FU=0
  Fixing libkwineffects14:amd64 via remove of libkwineffects13:amd64
Investigating (0) libkf5screen-data:amd64 < none -> 4:5.27.11-0ubuntu2 @un uN Ib >
Broken libkf5screen-data:amd64 Breaks on libkf5screen7:amd64 < 4:5.24.4-0ubuntu1 @ii mK > (< 4:5.27.0~)
  Considering libkf5screen7:amd64 -3 as a solution to libkf5screen-data:amd64 10
  Added libkf5screen7:amd64 to the remove list
  MarkDelete libkf5screen7:amd64 < 4:5.24.4-0ubuntu1 @ii mK > FU=0
  Fixing libkf5screen-data:amd64 via remove of libkf5screen7:amd64
Investigating (0) wireplumber:amd64 < none -> 0.4.17-1ubuntu4 @un uN Ib >
Broken wireplumber:amd64 Conflicts on pipewire-media-session:amd64 < 0.4.1-2ubuntu1 @ii gK Ib >
  Considering pipewire-media-session:amd64 -3 as a solution to wireplumber:amd64 7
  Added pipewire-media-session:amd64 to the remove list
  MarkDelete pipewire-media-session:amd64 < 0.4.1-2ubuntu1 @ii gK Ib > FU=0
  Fixing wireplumber:amd64 via remove of pipewire-media-session:amd64
Investigating (0) libtss2-tctildr0t64:amd64 < none -> 4.0.1-7.1ubuntu5.1 @un umN Ib >
Broken libtss2-tctildr0t64:amd64 Depends on libtss2-tcti-libtpms0t64:amd64 < none | 4.0.1-7.1ubuntu5.1 @un umH >
  Considering libtss2-tcti-libtpms0t64:amd64 1 as a solution to libtss2-tctildr0t64:amd64 3
  MarkKeep libtss2-tctildr0t64:amd64 < none -> 4.0.1-7.1ubuntu5.1 @un umN Ib > FU=0
  Holding Back libtss2-tctildr0t64:amd64 rather than change libtss2-tcti-libtpms0t64:amd64
Investigating (0) libkpmcore12:amd64 < none -> 23.08.5-0ubuntu3 @un uN Ib >
Broken libkpmcore12:amd64 Breaks on libkpmcore11:amd64 < 21.12.3-0ubuntu1 @ii mK >
  Considering libkpmcore11:amd64 -3 as a solution to libkpmcore12:amd64 2
  Added libkpmcore11:amd64 to the remove list
  MarkDelete libkpmcore11:amd64 < 21.12.3-0ubuntu1 @ii mK > FU=0
  Fixing libkpmcore12:amd64 via remove of libkpmcore11:amd64
Investigating (0) libiw30t64:amd64 < none -> 30~pre9-16.1ubuntu2 @un uN Ib >
Broken libiw30t64:amd64 Conflicts on libiw30:amd64 < 30~pre9-13.1ubuntu4 @ii mK > (< 30~pre9-16.1ubuntu2)
  Considering libiw30:amd64 -3 as a solution to libiw30t64:amd64 2
  Added libiw30:amd64 to the remove list
  MarkDelete libiw30:amd64 < 30~pre9-13.1ubuntu4 @ii mK > FU=0
  Fixing libiw30t64:amd64 via remove of libiw30:amd64
Investigating (0) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (0) libgs-common:amd64 < none -> 10.02.1~dfsg1-0ubuntu7.3 @un uN Ib >
Broken libgs-common:amd64 Breaks on libgs9-common:amd64 < 9.55.0~dfsg1-0ubuntu5.9 @ii mK > (< 10)
  Considering libgs9-common:amd64 -2 as a solution to libgs-common:amd64 0
  Added libgs9-common:amd64 to the remove list
  MarkDelete libgs9-common:amd64 < 9.55.0~dfsg1-0ubuntu5.9 @ii mK > FU=0
  Fixing libgs-common:amd64 via remove of libgs9-common:amd64
Investigating (0) python3.10-venv:amd64 < 3.10.12-1~22.04.5 @ii mK Ib >
Broken python3.10-venv:amd64 Depends on python3.10-distutils:amd64 < none @un mH >
  Considering python3-distutils:amd64 -2 as a solution to python3.10-venv:amd64 -2
  Removing python3.10-venv:amd64 rather than change python3.10-distutils:amd64
  MarkDelete python3.10-venv:amd64 < 3.10.12-1~22.04.5 @ii mK Ib > FU=0
Investigating (0) libgs9:amd64 < 9.55.0~dfsg1-0ubuntu5.9 @ii mK Ib >
Broken libgs9:amd64 Depends on libgs9-common:amd64 < 9.55.0~dfsg1-0ubuntu5.9 @ii mR > (= 9.55.0~dfsg1-0ubuntu5.9)
  Considering libgs9-common:amd64 -2 as a solution to libgs9:amd64 -2
  Removing libgs9:amd64 rather than change libgs9-common:amd64
  MarkDelete libgs9:amd64 < 9.55.0~dfsg1-0ubuntu5.9 @ii mK Ib > FU=0
Investigating (0) libpulsedsp:amd64 < 1:15.99.1+dfsg1-1ubuntu2.2 @ii mK Ib >
Broken libpulsedsp:amd64 Depends on libpulse0:amd64 < 1:15.99.1+dfsg1-1ubuntu2.2 -> 1:16.1+dfsg1-2ubuntu10 @ii umU > (= 1:15.99.1+dfsg1-1ubuntu2.2)
  Considering libpulse0:amd64 105 as a solution to libpulsedsp:amd64 -2
  Removing libpulsedsp:amd64 rather than change libpulse0:amd64
  MarkDelete libpulsedsp:amd64 < 1:15.99.1+dfsg1-1ubuntu2.2 @ii mK Ib > FU=0
Investigating (0) libgnustep-base1.28:amd64 < 1.28.0-4build1 @ii mK Ib >
Broken libgnustep-base1.28:amd64 Depends on gnustep-base-common:amd64 < 1.28.0-4build1 -> 1.29.0-7ubuntu4 @ii umU > (= 1.28.0-4build1)
  Considering gnustep-base-common:amd64 5 as a solution to libgnustep-base1.28:amd64 -2
  Removing libgnustep-base1.28:amd64 rather than change gnustep-base-common:amd64
  MarkDelete libgnustep-base1.28:amd64 < 1.28.0-4build1 @ii mK Ib > FU=0
Investigating (0) libgsasl7:amd64 < 1.10.0-5ubuntu0.1~esm1 @ii mK Ib >
Broken libgsasl7:amd64 Depends on gsasl-common:amd64 < 1.10.0-5ubuntu0.1~esm1 -> 2.2.1-1willsync1build2 @ii umU > (= 1.10.0-5ubuntu0.1~esm1)
  Considering gsasl-common:amd64 1 as a solution to libgsasl7:amd64 -2
  Removing libgsasl7:amd64 rather than change gsasl-common:amd64
  MarkDelete libgsasl7:amd64 < 1.10.0-5ubuntu0.1~esm1 @ii mK Ib > FU=0
Investigating (0) libfwupdplugin5:amd64 < 1.7.9-1~22.04.3 @ii mK Ib >
Broken libfwupdplugin5:amd64 Depends on libfwupd2:amd64 < 1.7.9-1~22.04.3 -> 1.9.16-1 @ii umU > (= 1.7.9-1~22.04.3)
  Considering libfwupd2:amd64 6 as a solution to libfwupdplugin5:amd64 -2
  Removing libfwupdplugin5:amd64 rather than change libfwupd2:amd64
  MarkDelete libfwupdplugin5:amd64 < 1.7.9-1~22.04.3 @ii mK Ib > FU=0
Investigating (1) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (1) libopenconnect5:amd64 < 8.20-1 -> 9.12-1build5 @ii umU Ib >
Broken libopenconnect5:amd64 Depends on libtss2-tctildr0t64:amd64 < none | 4.0.1-7.1ubuntu5.1 @un umH > (>= 3.0.1)
  Considering libtss2-tctildr0t64:amd64 3 as a solution to libopenconnect5:amd64 4
  MarkKeep libopenconnect5:amd64 < 8.20-1 -> 9.12-1build5 @ii umU Ib > FU=0
  Removing libopenconnect5:amd64 rather than change libtss2-tctildr0t64:amd64
  MarkDelete libopenconnect5:amd64 < 8.20-1 | 9.12-1build5 @ii umH Ib > FU=0
Investigating (1) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (1) openconnect:amd64 < none -> 9.12-1build5 @un uN Ib >
Broken openconnect:amd64 Depends on libopenconnect5:amd64 < 8.20-1 | 9.12-1build5 @ii umR > (>= 9.12)
  Considering libopenconnect5:amd64 4 as a solution to openconnect:amd64 0
  MarkKeep openconnect:amd64 < none -> 9.12-1build5 @un uN Ib > FU=0
  Holding Back openconnect:amd64 rather than change libopenconnect5:amd64
Investigating (1) network-manager-openconnect:amd64 < none -> 1.2.10-3build2 @un uN Ib >
Broken network-manager-openconnect:amd64 Depends on openconnect:amd64 < none | 9.12-1build5 @un uH >
  Considering openconnect:amd64 0 as a solution to network-manager-openconnect:amd64 0
  MarkKeep network-manager-openconnect:amd64 < none -> 1.2.10-3build2 @un uN Ib > FU=0
  Holding Back network-manager-openconnect:amd64 rather than change openconnect:amd64
Investigating (2) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (2) plasma-nm:amd64 < 4:5.24.5-0ubuntu0.1 -> 4:5.27.11-0ubuntu2 @ii umU Ib >
Broken plasma-nm:amd64 Depends on libopenconnect5:amd64 < 8.20-1 | 9.12-1build5 @ii umR > (>= 9.00)
  Considering libopenconnect5:amd64 4 as a solution to plasma-nm:amd64 4
  MarkKeep plasma-nm:amd64 < 4:5.24.5-0ubuntu0.1 -> 4:5.27.11-0ubuntu2 @ii umU Ib > FU=0
  Removing plasma-nm:amd64 rather than change libopenconnect5:amd64
  MarkDelete plasma-nm:amd64 < 4:5.24.5-0ubuntu0.1 | 4:5.27.11-0ubuntu2 @ii umH Ib > FU=0
Investigating (2) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (3) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (3) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (4) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (4) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (5) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (5) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (6) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (6) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (7) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (7) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (8) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (8) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (9) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (9) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (10) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (10) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (11) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (11) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (12) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (12) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (13) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (13) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (14) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (14) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (15) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (15) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (16) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (16) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (17) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (17) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (18) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (18) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
Investigating (19) fontconfig-config:amd64 < 2.13.1-4.2ubuntu5 -> 2.15.0-1.1ubuntu2 @ii umU Ib >
Broken fontconfig-config:amd64 Breaks on kubuntu-settings-desktop:amd64 < 1:22.04.10 | 1:24.04.12 @ii umH > (< 1:23.04.3)
  Considering kubuntu-settings-desktop:amd64 1 as a solution to fontconfig-config:amd64 50
  Upgrading kubuntu-settings-desktop:amd64 due to Breaks field in fontconfig-config:amd64
Investigating (19) kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib >
Broken kubuntu-settings-desktop:amd64 Conflicts on desktop-base:amd64 < 11.0.3ubuntu1 -> 12.0.6+nmu1ubuntu1 @ii umU >
  Considering desktop-base:amd64 1 as a solution to kubuntu-settings-desktop:amd64 1
  MarkKeep kubuntu-settings-desktop:amd64 < 1:22.04.10 -> 1:24.04.12 @ii umU Ib > FU=0
  Holding Back kubuntu-settings-desktop:amd64 rather than change desktop-base:amd64
```

---

### Post by TheFu on 2024-09-04
[LIST=1]
[*]Restore from the backup you made before starting.
[*]Ensure that the system is 100% fully patched and without any package system issues.  
[*]If you haven't already, install the HWE kernel and do a "full-upgrade" too.
[*]If you haven't, reboot, to ensure all of that is working too.
[*]Make a new backup.
[*]Use the system upgrade tool, but only if there aren't any issues.
[/LIST]

That's the expected, normal, process for upgrading an OS.

Expecting an OS upgrade to fix package management issues isn't a winning strategy.

If you skip the backup step, Murphy seems to know and will cause issues.  I consider the backup step "preventative", since whenever I have them, things seem to go well and they aren't needed.  There are a few times when the backups were needed badly, of course.  It made for a bad day, not a terrible day.  I want to avoid terrible days.

---

