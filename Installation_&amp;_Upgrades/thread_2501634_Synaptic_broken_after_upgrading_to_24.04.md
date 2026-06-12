---
title: "Synaptic broken after upgrading to 24.04"
date: 2024-10-15
forum: Installation &amp; Upgrades
---

### Post by anutosho on 2024-10-15
Hi,
I just upgraded my second PC from Kuuntu 22.04 to 24.04.1.
Both upgrades seems to work well so far - but.

On both computers, the Synaptic package manager no longer displays any package sources (Paketquellen). The window shows an empty list field.
Any idea?

---

### Post by Rubi1200 on 2024-10-15
Please show us the output for the following commands, wrapped in code tags:

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/

```

---

### Post by ajgreeny on 2024-10-16
It would also be useful to see the full output of command
**sudo apt update**
Please use **Code-tags** for terminal output as shown in my signature below.

---

### Post by anutosho on 2024-10-16
/etc/apt/sources.list doesn't exist anymore:
```
[FONT=monospace][COLOR=#000000]# cat /etc/apt/sources.list [/COLOR]
# Ubuntu sources have moved to /etc/apt/sources.list.d/ubuntu.sources
[/FONT]
```
everything is now in /etc/apt/sources.list.d 
```
[FONT=monospace][COLOR=#000000]# ls -l /etc/apt/sources.list.d/ [/COLOR]
insgesamt 112 
-rw-r--r-- 1 root root    47 Okt 16 00:51 anydesk-stable.list.distUpgrade 
-rw-r--r-- 1 root root    82 Okt 16 01:21 anydesk-stable.sources 
-rw-r--r-- 1 root root   199 Okt 16 00:51 boltgolt-ubuntu-howdy-jammy.list.distUpgrade 
-rw-r--r-- 1 root root  1805 Okt 16 01:21 boltgolt-ubuntu-howdy-jammy.sources 
-rw-r--r-- 1 root root  1752 Okt 16 01:21 boltgolt-ubuntu-howdy-noble.sources 
-rw-r--r-- 1 root root   130 Okt 16 00:51 brave-browser-release.list.distUpgrade 
-rw-r--r-- 1 root root   240 Okt 16 00:51 google-earth-pro.list.distUpgrade 
-rw-r--r-- 1 root root    99 Okt 16 01:21 google-earth-pro.sources 
-rw-r--r-- 1 root root   212 Okt 16 00:51 kicad-ubuntu-kicad-8_0-releases-jammy.list.distUpgrade 
-rw-r--r-- 1 root root  1811 Okt 16 01:21 kicad-ubuntu-kicad-8_0-releases-jammy.sources 
-rw-r--r-- 1 root root   226 Okt 16 00:51 maarten-fonville-ubuntu-android-studio-jammy.list.distUpgrade 
-rw-r--r-- 1 root root  1862 Okt 16 01:21 maarten-fonville-ubuntu-android-studio-jammy.sources 
-rw-r--r-- 1 root root   202 Okt 16 00:51 mozillateam-ubuntu-ppa-jammy.list.distUpgrade 
-rw-r--r-- 1 root root 10138 Okt 16 01:21 mozillateam-ubuntu-ppa-jammy.sources 
-rw-r--r-- 1 root root   111 Okt 16 00:51 nodesource.list.distUpgrade 
-rw-r--r-- 1 root root   206 Okt 16 00:51 savoury1-ubuntu-chromium-jammy.list.distUpgrade 
-rw-r--r-- 1 root root  1812 Okt 16 01:21 savoury1-ubuntu-chromium-jammy.sources 
-rw-r--r-- 1 root root   135 Okt 16 00:51 signal-xenial.list.distUpgrade 
-rw-r--r-- 1 root root    94 Okt 16 00:51 spotify.list.distUpgrade 
-rw-r--r-- 1 root root  1812 Okt 16 01:21 spotify.sources 
-rw-r--r-- 1 root root  1254 Okt 16 00:51 teamviewer.list.distUpgrade 
-rw-r--r-- 1 root root  1159 Jan 31  2024 [COLOR=#686868]teamviewer.list.dpkg-old[/COLOR]
-rw-r--r-- 1 root root   386 Okt 16 01:21 ubuntu.sources 
-rw-r--r-- 1 root root   138 Okt 16 00:51 VirtualBox.list.distUpgrade 
-rw-r--r-- 1 root root   248 Okt 16 00:51 vscode.list.distUpgrade 
-rw-r--r-- 1 root root   103 Okt 16 01:21 vscode.sources
[/FONT]
```

Oh, good hint. Everything is renamed to .distUpgrade except for ubuntu.sources which contains strange (to me) things 
```
[FONT=monospace][COLOR=#000000]# cat /etc/apt/sources.list.d/ubuntu.sources [/COLOR]
Types: deb 
URIs: http://de.archive.ubuntu.com/ubuntu/ 
Suites: noble noble-updates noble-backports 
Components: main restricted universe multiverse 
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg 

Types: deb 
URIs: http://security.ubuntu.com/ubuntu/ 
Suites: noble-security 
Components: main restricted universe multiverse 
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
[/FONT]
```
I don't understand that. Have never seen that before.

Output of apt update:
[FONT=monospace] [/FONT]```
[FONT=monospace][COLOR=#000000]# apt update [/COLOR]
OK:1 http://de.archive.ubuntu.com/ubuntu noble InRelease 
Holen:2 http://de.archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]                                 
OK:3 https://ppa.launchpadcontent.net/boltgolt/howdy/ubuntu noble InRelease                                           
OK:4 http://de.archive.ubuntu.com/ubuntu noble-backports InRelease[COLOR=#b26818]                                                   [/COLOR][COLOR=#000000] [/COLOR]
Holen:5 http://de.archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [597 kB] 
Holen:6 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB] 
Holen:7 http://de.archive.ubuntu.com/ubuntu noble-updates/main i386 Packages [316 kB] 
Holen:8 http://de.archive.ubuntu.com/ubuntu noble-updates/main Translation-en [146 kB][COLOR=#b26818]  [/COLOR][COLOR=#000000] [/COLOR]
Holen:9 http://de.archive.ubuntu.com/ubuntu noble-updates/main amd64 c-n-f Metadata [10,3 kB][COLOR=#b26818] [/COLOR][COLOR=#000000] [/COLOR]
Holen:10 http://de.archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Packages [388 kB] 
Holen:11 http://de.archive.ubuntu.com/ubuntu noble-updates/restricted Translation-en [74,8 kB] 
Holen:12 http://de.archive.ubuntu.com/ubuntu noble-updates/universe i386 Packages [435 kB] 
Holen:13 http://de.archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages [706 kB] 
Holen:14 http://security.ubuntu.com/ubuntu noble-security/main i386 Packages [189 kB] 
Holen:15 http://de.archive.ubuntu.com/ubuntu noble-updates/universe Translation-en [209 kB] 
Holen:16 http://de.archive.ubuntu.com/ubuntu noble-updates/universe amd64 c-n-f Metadata [19,8 kB] 
Holen:17 http://de.archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Packages [14,8 kB] 
Holen:18 http://de.archive.ubuntu.com/ubuntu noble-updates/multiverse i386 Packages [2.804 B] 
Holen:19 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages [428 kB] 
Holen:20 http://security.ubuntu.com/ubuntu noble-security/main Translation-en [92,5 kB] 
Holen:21 http://security.ubuntu.com/ubuntu noble-security/restricted amd64 Packages [385 kB] 
Holen:22 http://security.ubuntu.com/ubuntu noble-security/restricted Translation-en [74,4 kB] 
Holen:23 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Packages [553 kB] 
Holen:24 http://security.ubuntu.com/ubuntu noble-security/universe i386 Packages [351 kB] 
Holen:25 http://security.ubuntu.com/ubuntu noble-security/universe amd64 c-n-f Metadata [13,5 kB] 
Es wurden 5.259 kB in 2 s geholt (2.600 kB/s).[COLOR=#b26818]      [/COLOR][COLOR=#000000] [/COLOR]
Paketlisten werden gelesen&#8230; Fertig 
Abhängigkeitsbaum wird aufgebaut&#8230; Fertig 
Statusinformationen werden eingelesen&#8230; Fertig 
Aktualisierung für 19 Pakete verfügbar. Führen Sie »apt list --upgradable« aus, um sie anzuzeigen.[/FONT]
[FONT=monospace] [/FONT]
```

---

