---
title: "Wine not working prpoerly after upgrade to 24.04.1LTS"
date: 2024-11-27
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2024-11-27
After the last upgrade, when I run a wine program it doe not run full screen.  I have followed a few different sets of instructions which I found online, but no change.
Please let me know what you need to see in order to trouble shoot this problem.

Thank you,
Reuven

---

### Post by wyattwhiteeagle on 2024-11-28
> **reut2 said:**
> After the last upgrade, when I run a wine program it doe not run full screen.  I have followed a few different sets of instructions which I found online, but no change.
Please let me know what you need to see in order to trouble shoot this problem.

Thank you,
Reuven
Most times, something like this is due to the installation commands used to install wine.
You don't mention which sets of instructions you followed, just that you followed a few sets found online.

What DE & version? (Lubuntu 24.10, Xubuntu 24.04 LTS)
What commands did you use to install wine?
What all have you tried in the attempt to correct the problem?

---

### Post by reut2 on 2024-11-28
> **wyattwhiteeagle said:**
> Most times, something like this is due to the installation commands used to install wine.
You don't mention which sets of instructions you followed, just that you followed a few sets found online.

What DE & version? (Lubuntu 24.10, Xubuntu 24.04 LTS)
What commands did you use to install wine?
What all have you tried in the attempt to correct the problem?

I am using Xubuntu 24.04.1 LTS

Here is the list of commands I used--two attempts 
```

1443  sudo install wine
 1444  sudo apt install --install-recommends winehq-stable
 1445  sudo dpkg --add-architecture i386
 1446  sudo mkdir -pm755 /etc/apt/keyrings
 1447  sudo wget -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key
 1448  lsb_release -sc
 1449  sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/$(lsb_release -sc)/winehq-$(lsb_release -sc).sources
 1450  sudo apt update
 1451  sudo apt install --install-recommends winehq-stable
 1452  WINEARCH=win32 winecfg
 1453  wget -nc https://dl.winehq.org/wine-builds/Release.key && sudo apt-key add Release.key && sudo apt-add-repository -y https://dl.winehq.org/wine-builds/ubuntu/ && sudo apt update && sudo apt install wine-devel winehq-devel winetricks
 1454  winecfg
 1455  lsb_release -sc
 1456  lsb_release
 1457  lsb_release -a
 1458  $ dpkg --print-architecture
 1459  dpkg --print-architecture
 1460  dpkg --print-foreign-architectures
 1461  sudo mkdir -pm755 /etc/apt/keyrings
 1462  sudo wget -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key
 1463  sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/noble/winehq-noble.sources
 1464  sudo apt update
 1465  wine --version
 1466  sudo apt install --install-recommends winehq-stable
 1467  wine64 --version
 1468  cd ~
 1469  rm -R .wine
 1470  wine winecfg
 1471  wine clock
 1472  wine iexplore
 1473  wine64 iexplore
 1474  wine iexplore
 1475  wine uninstaller
 1476  winecfg
 1477  wine uninstaller
 1478  winecfg
 1479  wine
 1480  wine64
 1481  winecfg
 1482  wine uninstaller
 1483  winecfg
 1484  sudo apt-get uninstall wine
 1485  apt-get --help
 1486  sudo apt-get purge wine
 1487  sudo apt-get purge wine64
 1488  wine uninstaller
 1489  sudo apt autoremove
 1490  sudo purge  wine
 1491  sudo apt-get purge  wine
 1492  sudo apt autoremove
 1493  lsb_release -a
 1494  sudo apt purge  winehq-stable
 1495  sudo apt autoremove
 1496  sudo dpkg --add-architecture i386 && sudo apt install wine
 1497  winecfg
 1498  sudo ln -s /usr/share/doc/wine/examples/wine.desktop /usr/share/applications/
 1499  sudo mkdir -p /etc/apt/keyrings
 1500  wget -qO - https://dl.winehq.org/wine-builds/winehq.key | gpg --dearmor | sudo tee /etc/apt/keyrings/winehq-archive.key
 1501  sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/$(lsb_release -sc)/winehq-$(lsb_release -sc).sources
 1502  sudo apt update
 1503  sudo apt install winehq-stable
 1504  winecfg
 1505  lscpu
 1506  sudo apt update && sudo apt upgrade
 1507  sudo apt install wine64
 1508  wine --version
 1509  sudo wget -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key
 1510  sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/winehq-jammy.sources
 1511  sudo apt update
 1512  sudo apt install --install-recommends winehq-stable
 1513  wine --version

```

---

### Post by wyattwhiteeagle on 2024-11-29
> **reut2 said:**
> I am using Xubuntu 24.04.1 LTS

Here is the list of commands I used--two attempts 
```
...edited to reserve space in post...will refer back to this content in near future...
```

Ok, I am seeing a few issue's with those commands.
It looks like you have installed multiple branches of wine for multiple versions, ie, 22.04 and 24.04

what's the output of (to check which one it's defaulting to)
```
wine --version
```

---

