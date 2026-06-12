---
title: "Alienware 17 r4 ubuntu 16.04 BUG:soft lockup"
date: 2017-05-30
forum: Installation &amp; Upgrades
---

### Post by liuvay on 2017-05-30
Hi,all
Alienware 17  r4 GTX1071 GPU i7 7700HQ CPU Windows 10 521G SSD and 1T HDD, I want install Ubuntu 16.04 into HDD,but there is some problem as flows:
```
  nouveau 0000:01:00.0:priv:HUBO:00d054 000000007 (1e408216)
  nouveau 0000:01:00.0:DRM: fail to creat kernel channel, -22
  sd 4:0:0:0:[sda] No Caching mode page found
  sd 4:0:0:0:[sda] Assuming drive cache:wirte through
  NMI watchdog: BUG: soft lockup - CPU#3 stuck for 22s! [plymouthd:312]
```

[IMG]http://imgsrc.baidu.com/forum/w%3D580/sign=529436d95082b2b7a79f39cc01afcb0a/6c1db012c8fcc3ce302d67ee9b45d688d53f200f.jpg[/IMG]
[COLOR=#DF402A][FONT=Tahoma]****[/FONT][/COLOR][FONT=Tahoma]**When I the **[/FONT][COLOR=#DF402A][FONT=Tahoma]**Change **[/FONT][/COLOR][FONT=Tahoma]the `linux` line:[/FONT]
[FONT=Tahoma]Code:[/FONT]
[FONT=Tahoma]**linux    /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---**[/FONT]
[COLOR=#DF402A][FONT=Tahoma]**to**[/FONT][/COLOR][FONT=Tahoma]:[/FONT]
[FONT=Tahoma]Code:[/FONT]
[FONT=Tahoma][B]linux    /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash nomodeset vga=791 ---
it can boot into ubuntu, but here the question,it can not find the disks:[/B][/FONT]
[IMG]http://forum.ubuntu.org.cn/download/file.php?id=182776&t=1[/IMG]

---

