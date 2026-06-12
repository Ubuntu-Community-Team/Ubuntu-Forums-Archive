---
title: "apt-get update w/ Wireless: does not stop updating"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by gerdt on 2007-11-15
Hi, here's my problem. When I want to update before upgrading, the apt-get update command keeps on going. It appears that it never stops... This happens when I do it manually, or when the update manager is doing it automatically. Below I am showing you the output of the update after waiting more or less 1 minute. At the bottom you can see my sources.list.

The weird thing is, that this only happens when I try to update through WLAN. When I connect my laptop to the wired LAN, everything goes fine. The other weird thing is, that through WLAN I *am* able to perform apt-get upgrade and I am able to install things with apt-get install.

Here are the specs:
Inspiron 1501
dell_wireless_1390_wlan_minicard
ndiswrapper-1.49 (bcmwl5.inf)

I first thought it might have something to do with the firewall/proxy (P3 w/ IPCOP 1.4.13.). But my desktop and the other wired-connected computers all work fine behind it. My desktop has Xubuntu Gutsy and my server uses Debian. Both work fine when executing apt-get update. Also, my laptop encounters the same problem when I am connected to the WLAN of the university (which does not have IPCOP...).

I have tried to change my sources.list to another country (changing nl into be), but that didn't solve the problem. I don't know whether this is an apt problem, or a WLAN problem, or ... So I hope some of you know how to help me ;)

What I now have to do is, every time the update manager shows its orange star in the system tray, I have to kill apt-get update, connect my laptop to a UTP cable, perform apt-get update. Than, if I want, I can go back to WLAN and perform apt-get upgrade ...

Grtz,
Gerard

```
$ sudo apt-get update > update-vb

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.
```
*I now stopped apt-get update with ^C*

update-vb (589 gets ... ?!?!?!):
```
Get:1 http://archive.canonical.com gutsy Release.gpg [191B]
Get:2 http://wine.budgetdedicated.com gutsy Release.gpg [191B]
Get:3 http://dl.google.com stable Release.gpg [189B]
Get:4 http://nl.archive.ubuntu.com gutsy Release.gpg [191B]
Get:5 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_US
Get:6 http://wine.budgetdedicated.com gutsy Release.gpg [191B]
Get:7 http://nl.archive.ubuntu.com gutsy Release.gpg [191B]
Get:8 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:9 http://packages.medibuntu.org gutsy Release.gpg [189B]
Get:10 http://packages.medibuntu.org gutsy Release.gpg [189B]
Get:11 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://dl.google.com stable/non-free Translation-en_US
Get:12 http://wine.budgetdedicated.com gutsy Release.gpg [191B]
Get:13 http://nl.archive.ubuntu.com gutsy Release.gpg [191B]
Get:14 http://nl.archive.ubuntu.com gutsy Release.gpg [191B]
Get:15 http://nl.archive.ubuntu.com gutsy Release.gpg [191B]
Hit http://dl.google.com stable Release
Get:16 http://nl.archive.ubuntu.com gutsy Release.gpg [191B]
Get:17 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:18 http://nl.archive.ubuntu.com gutsy Release.gpg [191B]
Hit http://dl.google.com stable/non-free Packages
Ign http://packages.medibuntu.org gutsy/free Translation-en_US
Err http://packages.medibuntu.org gutsy/non-free Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 87.98.242.10 80]
Ign http://wine.budgetdedicated.com gutsy/main Translation-en_US
Hit http://archive.canonical.com gutsy Release
Get:19 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Err http://archive.canonical.com gutsy Release
  
Get:20 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:21 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:22 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:23 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:24 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:25 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:26 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Hit http://wine.budgetdedicated.com gutsy Release
Get:27 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:28 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://nl.archive.ubuntu.com gutsy/main Translation-en_US
Err http://nl.archive.ubuntu.com gutsy/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Get:29 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://wine.budgetdedicated.com gutsy/main Packages
Hit http://packages.medibuntu.org gutsy Release
Ign http://nl.archive.ubuntu.com gutsy/universe Translation-en_US
Err http://nl.archive.ubuntu.com gutsy/multiverse Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Hit http://wine.budgetdedicated.com gutsy/main Sources
Get:30 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://packages.medibuntu.org gutsy/free Packages
Hit http://wine.budgetdedicated.com gutsy/main Packages
Get:31 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:32 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:33 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:34 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:35 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:36 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:37 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:38 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:39 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:40 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:41 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:42 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:43 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:44 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:45 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:46 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:47 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:48 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://packages.medibuntu.org gutsy/non-free Packages
Ign http://packages.medibuntu.org gutsy/free Sources
Get:49 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:50 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:51 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:52 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:53 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:54 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:55 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:56 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:57 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:58 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:59 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:60 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:61 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:62 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:63 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:64 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:65 http://archive.canonical.com gutsy Release [6998B]
Ign http://archive.canonical.com gutsy Release
Get:66 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Get:67 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Get:68 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://packages.medibuntu.org gutsy/non-free Sources
Err http://packages.medibuntu.org gutsy/free Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 87.98.242.10 80]
Get:69 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Packages
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Get:70 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Hit http://packages.medibuntu.org gutsy/non-free Packages
Get:71 http://nl.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://nl.archive.ubuntu.com gutsy-updates/main Translation-en_US
Err http://nl.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Ign http://archive.canonical.com gutsy/partner Sources
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Err http://security.ubuntu.com gutsy-security/universe Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Hit http://archive.canonical.com gutsy/partner Packages
Ign http://nl.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com gutsy-security Release
Hit http://archive.canonical.com gutsy/partner Sources
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://packages.medibuntu.org gutsy/free Sources
Ign http://nl.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Err http://nl.archive.ubuntu.com gutsy-backports Release.gpg
  Error reading from server - read (104 Connection reset by peer)
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Ign http://nl.archive.ubuntu.com gutsy-backports/main Translation-en_US
Err http://nl.archive.ubuntu.com gutsy-backports/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Get:72 http://security.ubuntu.com gutsy-security/universe Sources [1863B]
Get:73 http://security.ubuntu.com gutsy-security/universe Sources [1863B]
Ign http://nl.archive.ubuntu.com gutsy-backports/universe Translation-en_US
Err http://nl.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Err http://security.ubuntu.com gutsy-security/universe Sources
  Sub-process bzip2 returned an error code (2)
Hit http://nl.archive.ubuntu.com gutsy Release
Hit http://nl.archive.ubuntu.com gutsy-updates Release
Hit http://nl.archive.ubuntu.com gutsy-backports Release
Hit http://packages.medibuntu.org gutsy/non-free Sources
Hit http://nl.archive.ubuntu.com gutsy/main Packages
Hit http://nl.archive.ubuntu.com gutsy/restricted Packages
Hit http://nl.archive.ubuntu.com gutsy/main Sources
Hit http://nl.archive.ubuntu.com gutsy/restricted Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://nl.archive.ubuntu.com gutsy/universe Packages
Hit http://nl.archive.ubuntu.com gutsy/universe Sources
Hit http://nl.archive.ubuntu.com gutsy/multiverse Packages
Hit http://nl.archive.ubuntu.com gutsy/multiverse Sources
Get:74 http://nl.archive.ubuntu.com gutsy-updates/main Packages [31.2kB]
Get:75 http://nl.archive.ubuntu.com gutsy-updates/restricted Packages [4263B]
Get:76 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:77 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:78 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:79 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:80 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:81 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:82 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:83 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:84 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:85 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:86 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:87 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:88 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:89 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:90 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:91 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:92 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:93 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:94 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:95 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:96 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:97 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:98 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:99 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:100 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:101 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:102 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:103 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:104 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:105 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:106 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:107 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:108 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:109 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:110 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:111 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:112 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:113 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:114 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:115 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:116 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:117 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:118 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:119 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:120 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:121 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:122 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:123 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:124 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:125 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:126 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:127 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:128 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:129 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:130 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:131 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:132 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:133 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:134 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:135 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:136 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:137 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:138 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:139 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:140 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:141 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:142 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:143 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:144 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:145 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:146 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:147 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:148 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:149 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:150 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:151 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:152 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:153 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:154 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:155 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:156 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:157 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:158 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:159 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:160 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:161 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:162 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:163 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:164 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:165 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:166 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:167 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:168 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:169 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:170 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:171 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:172 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:173 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:174 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:175 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:176 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:177 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:178 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:179 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:180 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:181 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:182 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:183 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:184 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:185 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:186 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:187 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:188 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:189 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:190 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:191 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:192 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:193 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:194 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:195 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:196 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:197 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:198 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:199 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:200 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:201 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:202 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:203 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:204 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:205 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:206 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:207 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:208 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:209 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:210 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:211 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:212 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:213 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:214 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:215 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:216 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:217 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:218 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:219 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:220 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:221 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:222 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:223 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:224 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:225 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:226 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:227 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:228 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:229 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:230 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:231 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:232 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:233 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:234 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:235 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:236 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:237 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Get:238 http://nl.archive.ubuntu.com gutsy-updates/main Sources [8963B]
Err http://nl.archive.ubuntu.com gutsy-updates/main Sources
  Sub-process bzip2 returned an error code (2)
Get:239 http://nl.archive.ubuntu.com gutsy-updates/restricted Sources [937B]
Get:240 http://nl.archive.ubuntu.com gutsy-updates/restricted Sources [937B]
Get:241 http://nl.archive.ubuntu.com gutsy-updates/universe Packages [14.2kB]
Get:242 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:243 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:244 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:245 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:246 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:247 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:248 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:249 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:250 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:251 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:252 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:253 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:254 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:255 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:256 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:257 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:258 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:259 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:260 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:261 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:262 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:263 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:264 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:265 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:266 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:267 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:268 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:269 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:270 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:271 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:272 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:273 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:274 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:275 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:276 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:277 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:278 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:279 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:280 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:281 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:282 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:283 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:284 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:285 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:286 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:287 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:288 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:289 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:290 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:291 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:292 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:293 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:294 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:295 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:296 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:297 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:298 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:299 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:300 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:301 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:302 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:303 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:304 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:305 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:306 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:307 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:308 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:309 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:310 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:311 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:312 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:313 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:314 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:315 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:316 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:317 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:318 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:319 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:320 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:321 http://nl.archive.ubuntu.com gutsy-updates/universe Sources [2560B]
Get:322 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:323 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:324 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:325 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:326 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:327 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:328 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:329 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:330 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:331 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:332 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:333 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:334 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:335 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:336 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:337 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:338 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:339 http://nl.archive.ubuntu.com gutsy-updates/multiverse Packages [3202B]
Get:340 http://nl.archive.ubuntu.com gutsy-updates/multiverse Sources [14B]
Get:341 http://nl.archive.ubuntu.com gutsy-updates/multiverse Sources [14B]
Get:342 http://nl.archive.ubuntu.com gutsy-updates/multiverse Sources [14B]
Get:343 http://nl.archive.ubuntu.com gutsy-updates/multiverse Sources [14B]
Get:344 http://nl.archive.ubuntu.com gutsy-updates/multiverse Sources [14B]
Get:345 http://nl.archive.ubuntu.com gutsy-updates/multiverse Sources [14B]
Get:346 http://nl.archive.ubuntu.com gutsy-updates/multiverse Sources [14B]
Get:347 http://nl.archive.ubuntu.com gutsy-updates/multiverse Sources [14B]
Get:348 http://nl.archive.ubuntu.com gutsy-updates/multiverse Sources [14B]
Get:349 http://nl.archive.ubuntu.com gutsy-backports/main Packages [3648B]
Get:350 http://nl.archive.ubuntu.com gutsy-backports/main Packages [3648B]
Get:351 http://nl.archive.ubuntu.com gutsy-backports/main Packages [3648B]
Get:352 http://nl.archive.ubuntu.com gutsy-backports/main Packages [3648B]
Get:353 http://nl.archive.ubuntu.com gutsy-backports/main Packages [3648B]
Get:354 http://nl.archive.ubuntu.com gutsy-backports/main Packages [3648B]
Get:355 http://nl.archive.ubuntu.com gutsy-backports/main Packages [3648B]
Get:356 http://nl.archive.ubuntu.com gutsy-backports/main Packages [3648B]
Get:357 http://nl.archive.ubuntu.com gutsy-backports/main Packages [3648B]
Get:358 http://nl.archive.ubuntu.com gutsy-backports/main Packages [3648B]
Get:359 http://nl.archive.ubuntu.com gutsy-backports/main Packages [3648B]
Get:360 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:361 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:362 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:363 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:364 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:365 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:366 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:367 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:368 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:369 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:370 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:371 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:372 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:373 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:374 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:375 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:376 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:377 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:378 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:379 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:380 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:381 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:382 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:383 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:384 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:385 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:386 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:387 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:388 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:389 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:390 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:391 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:392 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:393 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:394 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:395 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:396 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:397 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:398 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:399 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:400 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:401 http://nl.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:402 http://nl.archive.ubuntu.com gutsy-backports/universe Packages [5537B]
Get:403 http://nl.archive.ubuntu.com gutsy-backports/universe Packages [5537B]
Get:404 http://nl.archive.ubuntu.com gutsy-backports/universe Packages [5537B]
Get:405 http://nl.archive.ubuntu.com gutsy-backports/universe Packages [5537B]
Get:406 http://nl.archive.ubuntu.com gutsy-backports/universe Packages [5537B]
Get:407 http://nl.archive.ubuntu.com gutsy-backports/universe Packages [5537B]
Get:408 http://nl.archive.ubuntu.com gutsy-backports/universe Packages [5537B]
Get:409 http://nl.archive.ubuntu.com gutsy-backports/universe Packages [5537B]
Get:410 http://nl.archive.ubuntu.com gutsy-backports/universe Packages [5537B]
Get:411 http://nl.archive.ubuntu.com gutsy-backports/universe Packages [5537B]
Get:412 http://nl.archive.ubuntu.com gutsy-backports/multiverse Packages [14B]
Get:413 http://nl.archive.ubuntu.com gutsy-backports/multiverse Packages [14B]
Get:414 http://nl.archive.ubuntu.com gutsy-backports/main Sources [1792B]
Get:415 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:416 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:417 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:418 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:419 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:420 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:421 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:422 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:423 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:424 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:425 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:426 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:427 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:428 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:429 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:430 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:431 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:432 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:433 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:434 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:435 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:436 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:437 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:438 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:439 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:440 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:441 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:442 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:443 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:444 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:445 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:446 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:447 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:448 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:449 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:450 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:451 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:452 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:453 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:454 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:455 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:456 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:457 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:458 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:459 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:460 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:461 http://nl.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:462 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:463 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:464 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:465 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:466 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:467 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:468 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:469 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:470 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:471 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:472 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:473 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:474 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:475 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:476 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:477 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:478 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:479 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:480 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:481 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:482 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:483 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:484 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:485 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:486 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:487 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:488 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:489 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:490 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:491 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:492 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:493 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:494 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:495 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:496 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:497 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:498 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:499 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:500 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:501 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:502 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:503 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:504 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:505 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:506 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:507 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:508 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:509 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:510 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:511 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:512 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:513 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:514 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:515 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:516 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:517 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:518 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:519 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:520 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:521 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:522 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:523 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:524 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:525 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:526 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:527 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:528 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:529 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:530 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:531 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:532 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:533 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:534 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:535 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:536 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:537 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:538 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:539 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:540 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:541 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:542 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:543 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:544 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:545 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:546 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:547 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:548 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:549 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:550 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:551 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:552 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:553 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:554 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:555 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:556 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:557 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:558 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:559 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:560 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:561 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:562 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:563 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:564 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:565 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:566 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:567 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:568 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:569 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:570 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:571 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:572 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:573 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:574 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:575 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:576 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:577 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:578 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:579 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:580 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:581 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:582 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:583 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:584 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:585 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:586 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:587 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:588 http://nl.archive.ubuntu.com gutsy-backports/universe Sources [2268B]
Get:589 http://nl.archive.ubuntu.com gutsy-backports/multiverse Sources [14B]
```

sources.list:
```
# Gerard's Ubuntu Gutsy Gibbon 7.10 Sources list
# 
# Repository List based on standard gutsy with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
#  gpg --keyserver subkeys.pgp.net --recv KEY
#  gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
#  wget -q URL -O- | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
#  sudo apt-key add FILE

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

# Medibuntu - Ubuntu 7.10 "gutsy gibbon"
# GPG key-file: http://packages.medibuntu.org/medibuntu-key.gpg
deb http://packages.medibuntu.org/ gutsy free non-free
deb-src http://packages.medibuntu.org/ gutsy free non-free

## Google software repository
deb http://dl.google.com/linux/deb/ stable non-free

## IE6
#deb http://de.archive.ubuntu.com/ubuntu feisty universe
```

---

### Post by unerau on 2007-11-15
look for any abnormalities in the /dev files, if it doesnt appear there because its a network program, look for how to configure manually, in other words turn off the pnp, sometimes the BIOS doesnt support it.



if its in the terminal only and the hardware is fine just then maybe its corrupted and i dont quiet remember what to do.

=) good luck.:)

---

### Post by gerdt on 2007-11-15
> **unerau said:**
> look for any **abnormalities** in the /dev files, **if it doesnt appear there** because its a network program, look for how to configure manually, in other words **turn off the pnp**, sometimes the BIOS doesnt support it.

I am sorry, but I don't understand exactly what you mean by this.

What kind of abnormalities in /dev would I be looking for?
If *what* doesn't appear *where*?
I don't understand what pnp has to do with my problem.
I always understood that Linux doesn't do anything with BIOS. So it doesn't matter what the BIOS support and what not. Or am I wrong?

I am sorry for not understanding you... :$

---

### Post by gerdt on 2007-11-17
anyone???

---

