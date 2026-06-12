---
title: "Cant reinstall apt sources after 9.10-&gt;10.04 upgrade"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by teddan on 2010-06-11
Upgraded from 9.10 to 10.04 after which I can't get any packages to build. 
HP TX2000,AMD Turion 64 X2 TL-66 2.30Ghz processor,NVIDIA GeForce Go 6150
Linux kitt 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

1. So I attempted upgrade. During upgrade the computer gave an error about too little disk space and then I had to do a hard reboot because nothing was responding and it was stuck at
"After this operation, 897kB of additional disk space will be used.
(Reading database ... 315988 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.10.91.9+bdcom-0ubuntu4 (using .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules"

2. After reboot I got login screen but couldn't log in. It just kept going to back to startup screen. 

3. Reboot into and grub'd into root command line found that I had no disk space left which was weird because I had 45GB free before upgrade

4. Eventually I found "-rw-r--r--  1 root root 47729156096 2010-06-09 18:45 modules.ccwmap.temp" in "/lib/modules/2.6.31-15-generic". File contained this over and over: "nvidia               0x2887      0xfbad  0x00      0x0000  0x00"

5. I deleted it booted up again and could log in.

6. when I log in I get: "software index is broken
It is impossible to install or remove any software please use the package manager "synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue."

7. sudo apt-get install -f 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
 sudo dpkg --configure -a
dpkg: error processing bcmwl-kernel-source (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 bcmwl-kernel-source

8. sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nvidia-185-kernel-source libfreebob0 python-beagle libxml++2.6-2
  kdebase-runtime-data-common python-urwid libswfdec-0.8-0
  libknotificationitem1 mplayer-nogui libiso9660-5 libass3 nvidia-185-libvdpau
  khelpcenter4 liblzma0 kde-icons-oxygen libgee1 gnash-common mplayer-skins
  libcelt0 libffado1 kdebase-runtime-bin-kde4
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  bcmwl-kernel-source
1 upgraded, 0 newly installed, 0 to remove and 374 not upgraded.
1 not fully installed or removed.
Need to get 0B/896kB of archives.
After this operation, 897kB of additional disk space will be used.
(Reading database ... 315988 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.10.91.9+bdcom-0ubuntu4 (using .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb) ...
Removing all DKMS Modules

9. And then /lib/modules/2.6.31-15-generic/modules.ccwmap.temp fills up with "nvidia               0x2887      0xfbad  0x00      0x0000  0x00" again. When this happens computer gets very slow. I can close terminal window but process keeps running I have to reboot again.

10. Then whole thing repeats. Go to grub, command line, delete "/lib/modules/2.6.31-15-generic/modules.ccwmap.temp" and then continue booting. After boot I get: "software index is broken
It is impossible to install or remove any software please use the package manager "synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue." 

Since I am running 2.6.32-22-generic should I just delete the /lib/modules/2.6.31-15-generic/ directory? I saw other posts with Nvidia problems but none matched mine.

---

