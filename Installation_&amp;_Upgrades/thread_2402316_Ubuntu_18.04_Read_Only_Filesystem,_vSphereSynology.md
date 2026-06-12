---
title: "Ubuntu 18.04 Read Only Filesystem, vSphere/Synology/NFS4.1 (After 16.04 Upgrade)"
date: 2018-09-28
forum: Installation &amp; Upgrades
---

### Post by captbrando on 2018-09-28
Folks:

I have a vSphere cluster that is running a mixture of Linux distros (largely split between Debian & Ubuntu). Ever since upgrading my VMs to 18.04, I am often logging into a system on a read only file system. Reboot required, and fsck finds things to fix.

None of my Debian boxes do this.

I'm running vSphere 6.7, a Synology 916+, data source is NFS 4.1. Anyone had anything like this pop up or have any suggestions?

```
$ tail -100 syslog
Sep 28 03:16:03 ubtest kernel: [37392.058571] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=000000003a014cec)
Sep 28 03:16:03 ubtest kernel: [37392.058583] mptscsih: ioc0: attempting task abort! (sc=000000004e893600)
Sep 28 03:16:03 ubtest kernel: [37392.058590] sd 32:0:0:0: [sda] tag#25 CDB: Write(10) 2a 00 00 39 e8 90 00 00 10 00
Sep 28 03:16:03 ubtest kernel: [37392.226567] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=000000004e893600)
Sep 28 03:16:03 ubtest kernel: [37392.226587] mptscsih: ioc0: attempting task abort! (sc=0000000072d8dd7d)
Sep 28 03:16:03 ubtest kernel: [37392.226593] sd 32:0:0:0: [sda] tag#24 CDB: Write(10) 2a 00 00 39 e8 78 00 00 08 00
Sep 28 03:16:03 ubtest kernel: [37392.398562] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=0000000072d8dd7d)
Sep 28 03:16:03 ubtest kernel: [37392.398572] mptscsih: ioc0: attempting task abort! (sc=000000008ea74467)
Sep 28 03:16:03 ubtest kernel: [37392.398577] sd 32:0:0:0: [sda] tag#23 CDB: Write(10) 2a 00 00 39 e8 48 00 00 20 00
Sep 28 03:16:03 ubtest kernel: [37392.566558] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=000000008ea74467)
Sep 28 03:16:03 ubtest kernel: [37392.566568] mptscsih: ioc0: attempting task abort! (sc=000000005c63942c)
Sep 28 03:16:03 ubtest kernel: [37392.566573] sd 32:0:0:0: [sda] tag#22 CDB: Write(10) 2a 00 00 39 e8 38 00 00 08 00
Sep 28 03:16:04 ubtest kernel: [37392.734579] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=000000005c63942c)
Sep 28 03:16:04 ubtest kernel: [37392.734592] mptscsih: ioc0: attempting task abort! (sc=00000000de8ffc9b)
Sep 28 03:16:04 ubtest kernel: [37392.734598] sd 32:0:0:0: [sda] tag#21 CDB: Write(10) 2a 00 00 39 e8 08 00 00 08 00
Sep 28 03:16:04 ubtest kernel: [37392.902639] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000de8ffc9b)
Sep 28 03:16:04 ubtest kernel: [37392.902663] mptscsih: ioc0: attempting task abort! (sc=0000000082c5c9d6)
Sep 28 03:16:04 ubtest kernel: [37392.902675] sd 32:0:0:0: [sda] tag#20 CDB: Write(10) 2a 00 00 39 e7 e0 00 00 10 00
Sep 28 03:16:04 ubtest kernel: [37393.070637] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=0000000082c5c9d6)
Sep 28 03:16:04 ubtest kernel: [37393.070658] mptscsih: ioc0: attempting task abort! (sc=000000000f452650)
Sep 28 03:16:04 ubtest kernel: [37393.070668] sd 32:0:0:0: [sda] tag#19 CDB: Write(10) 2a 00 00 39 e7 c8 00 00 10 00
Sep 28 03:16:04 ubtest kernel: [37393.238563] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=000000000f452650)
Sep 28 03:16:04 ubtest kernel: [37393.238571] mptscsih: ioc0: attempting task abort! (sc=00000000be340170)
Sep 28 03:16:04 ubtest kernel: [37393.238575] sd 32:0:0:0: [sda] tag#18 CDB: Write(10) 2a 00 00 39 e7 28 00 00 08 00
Sep 28 03:16:04 ubtest kernel: [37393.406554] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000be340170)
Sep 28 03:16:04 ubtest kernel: [37393.406563] mptscsih: ioc0: attempting task abort! (sc=00000000a03b8351)
Sep 28 03:16:04 ubtest kernel: [37393.406567] sd 32:0:0:0: [sda] tag#17 CDB: Write(10) 2a 00 00 39 e7 08 00 00 10 00
Sep 28 03:16:04 ubtest kernel: [37393.574584] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000a03b8351)
Sep 28 03:16:04 ubtest kernel: [37393.574597] mptscsih: ioc0: attempting task abort! (sc=0000000077ce3c82)
Sep 28 03:16:04 ubtest kernel: [37393.574603] sd 32:0:0:0: [sda] tag#16 CDB: Write(10) 2a 00 00 39 e6 50 00 00 08 00
Sep 28 03:16:05 ubtest kernel: [37393.746639] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=0000000077ce3c82)
Sep 28 03:16:05 ubtest kernel: [37393.746659] mptscsih: ioc0: attempting task abort! (sc=00000000fcb53f2c)
Sep 28 03:16:05 ubtest kernel: [37393.746671] sd 32:0:0:0: [sda] tag#15 CDB: Write(10) 2a 00 00 39 e6 28 00 00 08 00
Sep 28 03:16:05 ubtest kernel: [37393.914555] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000fcb53f2c)
Sep 28 03:16:05 ubtest kernel: [37393.914566] mptscsih: ioc0: attempting task abort! (sc=00000000b9bdbc43)
Sep 28 03:16:05 ubtest kernel: [37393.914571] sd 32:0:0:0: [sda] tag#14 CDB: Write(10) 2a 00 00 39 e5 c8 00 00 08 00
Sep 28 03:16:05 ubtest kernel: [37394.082529] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000b9bdbc43)
Sep 28 03:16:05 ubtest kernel: [37394.082538] mptscsih: ioc0: attempting task abort! (sc=00000000b7e57ff7)
Sep 28 03:16:05 ubtest kernel: [37394.082542] sd 32:0:0:0: [sda] tag#13 CDB: Write(10) 2a 00 00 39 e4 38 00 00 20 00
Sep 28 03:16:05 ubtest kernel: [37394.250510] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000b7e57ff7)
Sep 28 03:16:05 ubtest kernel: [37394.250519] mptscsih: ioc0: attempting task abort! (sc=00000000386f0692)
Sep 28 03:16:05 ubtest kernel: [37394.250523] sd 32:0:0:0: [sda] tag#12 CDB: Write(10) 2a 00 00 39 e3 78 00 00 08 00
Sep 28 03:16:05 ubtest kernel: [37394.418555] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000386f0692)
Sep 28 03:16:05 ubtest kernel: [37394.418565] mptscsih: ioc0: attempting task abort! (sc=000000005c5d0cd6)
Sep 28 03:16:05 ubtest kernel: [37394.418569] sd 32:0:0:0: [sda] tag#11 CDB: Write(10) 2a 00 00 39 e3 58 00 00 08 00
Sep 28 03:16:05 ubtest kernel: [37394.586549] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=000000005c5d0cd6)
Sep 28 03:16:05 ubtest kernel: [37394.586557] mptscsih: ioc0: attempting task abort! (sc=00000000895653a6)
Sep 28 03:16:05 ubtest kernel: [37394.586567] sd 32:0:0:0: [sda] tag#10 CDB: Write(10) 2a 00 00 39 e3 38 00 00 08 00
Sep 28 03:16:06 ubtest kernel: [37394.754548] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000895653a6)
Sep 28 03:16:06 ubtest kernel: [37394.754558] mptscsih: ioc0: attempting task abort! (sc=000000001ed2b39c)
Sep 28 03:16:06 ubtest kernel: [37394.754563] sd 32:0:0:0: [sda] tag#9 CDB: Write(10) 2a 00 00 39 e2 b8 00 00 08 00
Sep 28 03:16:06 ubtest kernel: [37394.922541] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=000000001ed2b39c)
Sep 28 03:16:06 ubtest kernel: [37394.922550] mptscsih: ioc0: attempting task abort! (sc=0000000029bd84bb)
Sep 28 03:16:06 ubtest kernel: [37394.922555] sd 32:0:0:0: [sda] tag#8 CDB: Write(10) 2a 00 00 39 de 08 00 00 10 00
Sep 28 03:16:06 ubtest kernel: [37395.090537] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=0000000029bd84bb)
Sep 28 03:16:06 ubtest kernel: [37395.090544] mptscsih: ioc0: attempting task abort! (sc=00000000b50a6414)
Sep 28 03:16:06 ubtest kernel: [37395.090548] sd 32:0:0:0: [sda] tag#7 CDB: Write(10) 2a 00 00 39 dd c8 00 00 08 00
Sep 28 03:16:06 ubtest kernel: [37395.262540] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000b50a6414)
Sep 28 03:16:06 ubtest kernel: [37395.262549] mptscsih: ioc0: attempting task abort! (sc=00000000426d7b1f)
Sep 28 03:16:06 ubtest kernel: [37395.262552] sd 32:0:0:0: [sda] tag#6 CDB: Write(10) 2a 00 00 39 d8 a0 00 00 08 00
Sep 28 03:16:06 ubtest kernel: [37395.430543] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000426d7b1f)
Sep 28 03:16:06 ubtest kernel: [37395.430552] mptscsih: ioc0: attempting task abort! (sc=000000004ab49f44)
Sep 28 03:16:06 ubtest kernel: [37395.430556] sd 32:0:0:0: [sda] tag#5 CDB: Write(10) 2a 00 00 39 d8 38 00 00 08 00
Sep 28 03:16:06 ubtest kernel: [37395.598552] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=000000004ab49f44)
Sep 28 03:16:06 ubtest kernel: [37395.598561] mptscsih: ioc0: attempting task abort! (sc=00000000ebca97a4)
Sep 28 03:16:06 ubtest kernel: [37395.598565] sd 32:0:0:0: [sda] tag#4 CDB: Write(10) 2a 00 00 39 d7 90 00 00 08 00
Sep 28 03:16:07 ubtest kernel: [37395.766535] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000ebca97a4)
Sep 28 03:16:07 ubtest kernel: [37395.766544] mptscsih: ioc0: attempting task abort! (sc=000000000e7701fa)
Sep 28 03:16:07 ubtest kernel: [37395.766549] sd 32:0:0:0: [sda] tag#3 CDB: Write(10) 2a 00 00 39 d2 88 00 00 08 00
Sep 28 03:16:07 ubtest kernel: [37395.934542] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=000000000e7701fa)
Sep 28 03:16:07 ubtest kernel: [37395.934553] mptscsih: ioc0: attempting task abort! (sc=000000006151cc48)
Sep 28 03:16:07 ubtest kernel: [37395.934558] sd 32:0:0:0: [sda] tag#2 CDB: Write(10) 2a 00 00 39 ce 00 00 00 08 00
Sep 28 03:16:07 ubtest kernel: [37396.102538] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=000000006151cc48)
Sep 28 03:16:07 ubtest kernel: [37396.102546] mptscsih: ioc0: attempting task abort! (sc=0000000069e2131b)
Sep 28 03:16:07 ubtest kernel: [37396.102549] sd 32:0:0:0: [sda] tag#1 CDB: Write(10) 2a 00 00 39 cd 58 00 00 08 00
Sep 28 03:16:07 ubtest kernel: [37396.270542] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=0000000069e2131b)
Sep 28 03:16:07 ubtest kernel: [37396.270549] mptscsih: ioc0: attempting task abort! (sc=00000000de138ecc)
Sep 28 03:16:07 ubtest kernel: [37396.270554] sd 32:0:0:0: [sda] tag#0 CDB: Write(10) 2a 00 00 39 ca f8 00 00 08 00
Sep 28 03:16:07 ubtest kernel: [37396.438533] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000de138ecc)
Sep 28 03:16:07 ubtest kernel: [37396.438542] mptscsih: ioc0: attempting task abort! (sc=00000000b7b0393f)
Sep 28 03:16:07 ubtest kernel: [37396.438546] sd 32:0:0:0: [sda] tag#31 CDB: Write(10) 2a 00 00 0f 6c 50 00 00 10 00
Sep 28 03:16:07 ubtest kernel: [37396.606531] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=00000000b7b0393f)
Sep 28 03:16:07 ubtest kernel: [37396.606539] mptscsih: ioc0: attempting task abort! (sc=0000000010087ec9)
Sep 28 03:16:07 ubtest kernel: [37396.606542] sd 32:0:0:0: [sda] tag#30 CDB: Write(10) 2a 00 00 0f 6b 98 00 00 08 00
Sep 28 03:16:08 ubtest kernel: [37396.774536] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=0000000010087ec9)
Sep 28 03:16:39 ubtest kernel: [37428.250511] mptscsih: ioc0: attempting target reset! (sc=0000000010087ec9)
Sep 28 03:16:39 ubtest kernel: [37428.250532] sd 32:0:0:0: [sda] tag#0 CDB: Write(10) 2a 00 00 0f 6b 98 00 00 08 00
Sep 28 03:16:39 ubtest kernel: [37428.418310] mptscsih: ioc0: target reset: SUCCESS (sc=0000000010087ec9)
Sep 28 03:17:10 ubtest kernel: [37458.974059] mptscsih: ioc0: attempting target reset! (sc=0000000086b5e36d)
Sep 28 03:17:10 ubtest kernel: [37458.974066] sd 32:0:0:0: [sda] tag#0 CDB: Write(10) 2a 00 00 19 60 00 00 00 08 00
Sep 28 03:17:23 ubtest kernel: [37472.633990] mptscsih: ioc0: target reset: SUCCESS (sc=0000000086b5e36d)
Sep 28 03:17:24 ubtest CRON[21060]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 28 03:18:11 ubtest kernel: [37520.405649] mptscsih: ioc0: attempting task abort! (sc=000000006946b568)
Sep 28 03:18:11 ubtest kernel: [37520.405656] sd 32:0:0:0: [sda] tag#0 CDB: Write(10) 2a 00 00 d4 28 80 00 00 40 00
Sep 28 03:18:11 ubtest kernel: [37520.573709] mptscsih: ioc0: task abort: SUCCESS (rv=2002) (sc=000000006946b568)
Sep 28 03:18:42 ubtest kernel: [37551.129577] mptscsih: ioc0: attempting target reset! (sc=000000006946b568)
Sep 28 03:18:42 ubtest kernel: [37551.129588] sd 32:0:0:0: [sda] tag#0 CDB: Write(10) 2a 00 00 d4 28 80 00 00 40 00
Sep 28 03:18:42 ubtest kernel: [37551.297492] mptscsih: ioc0: target reset: SUCCESS (sc=000000006946b568)
Sep 28 03:20:10 ubtest kernel: [37639.188785] mptscsih: ioc0: attempting task abort! (sc=00000000e38ee434)
Sep 28 03:20:10 ubtest kernel: [37639.188792] sd 32:0:0:0: [sda] tag#0 CDB: Write(10) 2a 00 00 d4 28 f8 00 00 08 00
```

---

