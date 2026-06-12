---
title: "Starting chromium triggers apparmor pop ups"
date: 2018-11-01
forum: Installation &amp; Upgrades
---

### Post by buzlite on 2018-11-01
I'm running lubuntu 18.04.1
When I start chromium, I get a whole bunch of popups from apparmor. This started happening after an update to my lubuntu installation. Could you tell me how to go about solving this problem? I've included an image of the popups.

```
$ cat /var/log/kern.log
...
Nov  1 06:44:33 wtmaui kernel: [  112.426064] audit: type=1400 audit(1541069073.873:366): apparmor="STATUS" operation="profile_load" profile="unconfined" name="docker-default" pid=2912 comm="apparmor_parser"
...
Nov  1 07:30:25 wtmaui kernel: [ 2864.492720] audit: type=1400 audit(1541071825.881:367): apparmor="DENIED" operation="file_lock" profile="/usr/share/hplip/systray.py" name="/etc/xdg/Trolltech.conf" pid=4090 comm="python" requested_mask="k" denied_mask="k" fsuid=1000 ouid=0
Nov  1 08:20:12 wtmaui kernel: [ 5851.176278] audit: type=1400 audit(1541074812.525:368): apparmor="ALLOWED" operation="capable" profile="/usr/lib/chromium-browser/chromium-browser" pid=7169 comm="chromium-browse" capability=21  capname="sys_admin"
Nov  1 08:20:12 wtmaui kernel: [ 5851.176286] audit: type=1400 audit(1541074812.525:369): apparmor="ALLOWED" operation="open" profile="/usr/lib/chromium-browser/chromium-browser" name="/proc/7169/gid_map" pid=7169 comm="chromium-browse" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
Nov  1 08:20:12 wtmaui kernel: [ 5851.176324] audit: type=1400 audit(1541074812.525:370): apparmor="ALLOWED" operation="open" profile="/usr/lib/chromium-browser/chromium-browser" name="/proc/7169/uid_map" pid=7169 comm="chromium-browse" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
Nov  1 08:20:12 wtmaui kernel: [ 5851.294908] audit: type=1400 audit(1541074812.641:371): apparmor="ALLOWED" operation="capable" profile="/usr/lib/chromium-browser/chromium-browser" pid=7162 comm="chromium-browse" capability=21  capname="sys_admin"
Nov  1 08:20:12 wtmaui kernel: [ 5851.295854] audit: type=1400 audit(1541074812.645:372): apparmor="ALLOWED" operation="capable" profile="/usr/lib/chromium-browser/chromium-browser" pid=7170 comm="chromium-browse" capability=21  capname="sys_admin"
Nov  1 08:20:12 wtmaui kernel: [ 5851.295878] audit: type=1400 audit(1541074812.645:373): apparmor="ALLOWED" operation="open" profile="/usr/lib/chromium-browser/chromium-browser" name="/proc/7170/uid_map" pid=7170 comm="chromium-browse" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
Nov  1 08:20:12 wtmaui kernel: [ 5851.295926] audit: type=1400 audit(1541074812.645:374): apparmor="ALLOWED" operation="open" profile="/usr/lib/chromium-browser/chromium-browser" name="/proc/7170/gid_map" pid=7170 comm="chromium-browse" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
Nov  1 08:20:12 wtmaui kernel: [ 5851.569833] audit: type=1400 audit(1541074812.917:375): apparmor="ALLOWED" operation="open" profile="/usr/lib/chromium-browser/chromium-browser" name="/proc/7170/gid_map" pid=7170 comm="chromium-browse" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
Nov  1 08:20:12 wtmaui kernel: [ 5851.569841] audit: type=1400 audit(1541074812.917:376): apparmor="ALLOWED" operation="open" profile="/usr/lib/chromium-browser/chromium-browser" name="/proc/7170/uid_map" pid=7170 comm="chromium-browse" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
Nov  1 08:20:12 wtmaui kernel: [ 5851.570438] audit: type=1400 audit(1541074812.917:377): apparmor="ALLOWED" operation="capable" profile="/usr/lib/chromium-browser/chromium-browser" pid=7191 comm="chromium-browse" capability=18  capname="sys_chroot"
Nov  1 08:20:19 wtmaui kernel: [ 5857.731173] kauditd_printk_skb: 53 callbacks suppressed
Nov  1 08:20:19 wtmaui kernel: [ 5857.731177] audit: type=1400 audit(1541074819.077:431): apparmor="ALLOWED" operation="capable" profile="/usr/lib/chromium-browser/chromium-browser" pid=7192 comm="chromium-browse" capability=21  capname="sys_admin"
Nov  1 08:20:19 wtmaui kernel: [ 5857.900389] audit: type=1400 audit(1541074819.249:432): apparmor="ALLOWED" operation="open" profile="/usr/lib/chromium-browser/chromium-browser//xdgsettings" name="/etc/xdg/lubuntu/applications/" pid=7270 comm="xdg-settings" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov  1 08:20:19 wtmaui kernel: [ 5857.908254] audit: type=1400 audit(1541074819.257:433): apparmor="ALLOWED" operation="open" profile="/usr/lib/chromium-browser/chromium-browser//xdgsettings" name="/etc/xdg/lubuntu/applications/" pid=7276 comm="xdg-settings" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov  1 08:20:19 wtmaui kernel: [ 5857.917553] audit: type=1400 audit(1541074819.265:434): apparmor="ALLOWED" operation="open" profile="/usr/lib/chromium-browser/chromium-browser//xdgsettings" name="/etc/xdg/lubuntu/applications/" pid=7299 comm="xdg-mime" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov  1 08:20:19 wtmaui kernel: [ 5857.922333] audit: type=1400 audit(1541074819.269:435): apparmor="ALLOWED" operation="open" profile="/usr/lib/chromium-browser/chromium-browser//xdgsettings" name="/etc/xdg/lubuntu/applications/" pid=7308 comm="xdg-mime" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Nov  1 08:20:19 wtmaui kernel: [ 5858.262614] audit: type=1400 audit(1541074819.613:436): apparmor="ALLOWED" operation="mknod" profile="/usr/lib/chromium-browser/chromium-browser" name="/dev/shm/shmfd-nlMctu" pid=7230 comm="chromium-browse" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
Nov  1 08:20:19 wtmaui kernel: [ 5858.262620] audit: type=1400 audit(1541074819.613:437): apparmor="ALLOWED" operation="open" profile="/usr/lib/chromium-browser/chromium-browser" name="/dev/shm/shmfd-nlMctu" pid=7230 comm="chromium-browse" requested_mask="wrc" denied_mask="wrc" fsuid=1000 ouid=1000
Nov  1 08:20:19 wtmaui kernel: [ 5858.262622] audit: type=1400 audit(1541074819.613:438): apparmor="ALLOWED" operation="unlink" profile="/usr/lib/chromium-browser/chromium-browser" name="/dev/shm/shmfd-nlMctu" pid=7230 comm="chromium-browse" requested_mask="d" denied_mask="d" fsuid=1000 ouid=1000
Nov  1 08:20:19 wtmaui kernel: [ 5858.262673] audit: type=1400 audit(1541074819.613:439): apparmor="ALLOWED" operation="truncate" profile="/usr/lib/chromium-browser/chromium-browser" name="/dev/shm/shmfd-nlMctu" pid=7227 comm="chromium-browse" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
Nov  1 08:20:19 wtmaui kernel: [ 5858.369804] audit: type=1400 audit(1541074819.717:440): apparmor="ALLOWED" operation="mknod" profile="/usr/lib/chromium-browser/chromium-browser" name="/dev/shm/shmfd-IM8cJ7" pid=7230 comm="chromium-browse" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000

```

Thanks in advanced.

---

### Post by dino99 on 2018-11-01
I use ubuntu, and these entries are also logged, or so, but no popup; its a Lubuntu error you might report. (does not know if there is a special setting for poping, (via tweaks, dconf, system settings))

---

