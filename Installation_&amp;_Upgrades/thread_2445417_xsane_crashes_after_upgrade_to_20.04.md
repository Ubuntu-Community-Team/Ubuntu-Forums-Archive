---
title: "xsane crashes after upgrade to 20.04"
date: 2020-06-13
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2020-06-13
After myt recent upgrade xsane crashes with the following error
```
Jun 14 11:50:25 LeosHomePc1 xsane[24367]: Failed to load module "appmenu-gtk-module"
Jun 14 11:50:25 LeosHomePc1 systemd[2233]: Started Application launched by gnome-shell.
Jun 14 11:50:25 LeosHomePc1 xsane[24367]: Failed to load module "canberra-gtk-module"
Jun 14 11:50:25 LeosHomePc1 kernel: [ 5218.464452] [UFW BLOCK] IN=enp9s0 OUT= MAC= SRC=fe80:0000:0000:0000:16da:e9ff:fec8:c682 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=142191 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Jun 14 11:50:25 LeosHomePc1 kernel: [ 5218.464466] [UFW BLOCK] IN=enp9s0 OUT= MAC= SRC=fe80:0000:0000:0000:16da:e9ff:fec8:c682 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=1009018 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
Jun 14 11:50:25 LeosHomePc1 kernel: [ 5218.474617] [UFW BLOCK] IN=enp9s0 OUT= MAC= SRC=fe80:0000:0000:0000:16da:e9ff:fec8:c682 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=142191 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Jun 14 11:50:25 LeosHomePc1 kernel: [ 5218.474628] [UFW BLOCK] IN=enp9s0 OUT= MAC= SRC=fe80:0000:0000:0000:16da:e9ff:fec8:c682 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=1009018 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
Jun 14 11:50:33 LeosHomePc1 xsane.desktop[24367]: Capability : [(null)]
Jun 14 11:50:33 LeosHomePc1 xsane.desktop[24367]: Capability : [image/jpeg]
Jun 14 11:50:33 LeosHomePc1 xsane.desktop[24367]: message repeated 4 times: [ Capability : [image/jpeg]]
Jun 14 11:50:33 LeosHomePc1 xsane.desktop[24367]: [xsane] ERROR: xsane-startimage not found. Looks like xsane is not installed correct.
Jun 14 11:51:09 LeosHomePc1 kernel: [ 5262.250136] xsane[24367]: segfault at 55c816b10000 ip 00007f7e790728d0 sp 00007ffdfd129eb0 error 4 in libjpeg.so.8.2.2[7f7e7905c000+44000]
Jun 14 11:51:09 LeosHomePc1 kernel: [ 5262.250144] Code: 8d 5c 40 03 66 0f 1f 44 00 00 4c 8b 06 48 8b 01 89 d7 48 83 c1 08 83 c2 01 4d 8b 04 f8 4c 8d 1c 18 45 85 c9 74 21 0f 1f 40 00 <41> 0f b6 38 48 83 c0 03 49 83 c0 01 40 88 78 ff 40 88 78 fe 40 88
Jun 14 11:51:09 LeosHomePc1 systemd[2233]: gnome-launched-xsane.desktop-24367.scope: Succeeded.

```

xsane starte, I can acquire a preview, but when I click on the 'scan' butten xsane crashes.
I have already tried to reinstall xsane, but the result is the same

---

