---
title: "Updating a production web server without choking it?"
date: 2014-11-28
forum: Installation &amp; Upgrades
---

### Post by Lido on 2014-11-28
I've got a couple of Ubuntu servers running 12.04 LTS and one is a light load web server and the other is a very light load webserver and also a mail server. Whenever I run apt-get update and upgrade on the web server, it takes a very long time to complete the commands and during that time, pages served by apache are extremely slow if they load at all. On the other machine, it doesn't seem to be bothered at all and updates happen much more quickly. Any idea why this is happening and how to fix it?

---

### Post by SeijiSensei on 2014-11-28
Identical hardware?  Identical network connections?

---

### Post by tgalati4 on 2014-11-28
You typically bring your webserver down and put up a maintenance page.  Perform the maintenance, reboot (so you are running new code if the kernel is involved), run some checks to make sure things are running OK, then start up the web services and anything else that is needed.  That way, pages don't run slow.  They don't run at all, during maintenance.  It is an unreasonable expectation to keep all services alive and snappy during maintenance.  Can you drive your car while changing the oil?

As far as the differences between the two machines:  you would need to examine RAM, swap use, and what specific services are running on each machine.  *iftop* will show if there is a bandwidth bottleneck.  *lsof* will show files in use by your services.  I would guess you are experiencing file-thrashing--one disk is getting hammered by read/write requests during an update.  That same disk is needed by your web server.  You can use *top* to show load.

```
man top
```

---

### Post by Lido on 2014-11-28
Thanks. The hardware on the machine that chokes is newer/faster/more ram/better connection to the net etc so I assume it's mostly associated more with web request load or what packages are running on it than hardware. The two main differences aside from a bigger demand on the server that chokes are that the server in question has a RAID0 as its main drive and runs apache while the other machine that doesn't have trouble with updates is just a single drive and runs nginx. I will try *iftop* and *lsof* next time I run an update.

So you'd suggest just killing apache before updates?

---

### Post by SeijiSensei on 2014-11-29
Maybe the problem is the servers you're using for the updates.  I use MIT's servers because they are physically and topologically nearby, and the Institute has a **lot** of bandwidth.

---

### Post by mastablasta on 2014-11-29
i have setup *unnattended updates* but i don't run a web server

---

### Post by tgalati4 on 2014-11-30
You can try killing apache before updates and see if that improves the update process.  If any updates involve apache or the LAMP stack, then those services will get stopped anyway (as part of the pre-installation process) and will get started again (as part of the post-installation process).  Sometimes updates will result in breakage--known as regressions, so you need to be prepared to deal with breakage after an update.  This can be tedious on a production server.

---

### Post by Lido on 2014-12-05
I stopped apache2 before running apt-get update, but that didn't seem to help. It hangs at this point for a while:

```
...Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
100% [Translation-en 2,884 B] [Waiting for headers
```

Then again here for even longer (5 mins or so):

```
Fetched 4,455 kB in 1min 16s (57.9 kB/s)                                                                                                                   
Reading package lists... 99%
```

Looking at the top command, during much of the update and upgrade process, the cpu is 50% idle and 50% waiting at best, sometimes up to 0% idle and 99% waiting, with no particular process with any cpu or memory percentage over 2 or 3%. The output of lsof is long, but here's that:

```
COMMAND     PID        USER   FD      TYPE             DEVICE  SIZE/OFF       NODE NAME
init          1        root  cwd       DIR                9,1      4096          2 /
init          1        root  rtd       DIR                9,1      4096          2 /
init          1        root  txt       REG                9,1    167192    1310887 /sbin/init
init          1        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
init          1        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
init          1        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
init          1        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
init          1        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
init          1        root  DEL       REG                9,1              6164161 /lib/x86_64-linux-gnu/librt-2.15.so
init          1        root  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
init          1        root  mem       REG                9,1    276392    6160436 /lib/x86_64-linux-gnu/libdbus-1.so.3.5.8
init          1        root  mem       REG                9,1     38888    6160476 /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
init          1        root  mem       REG                9,1     96240    6160438 /lib/x86_64-linux-gnu/libnih.so.1.0.0
init          1        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
init          1        root    0u      CHR                1,3       0t0       5800 /dev/null
init          1        root    1u      CHR                1,3       0t0       5800 /dev/null
init          1        root    2u      CHR                1,3       0t0       5800 /dev/null
init          1        root    3r     FIFO                0,8       0t0       6640 pipe
init          1        root    4w     FIFO                0,8       0t0       6640 pipe
init          1        root    5r     0000                0,9         0       5775 anon_inode
init          1        root    6r     0000                0,9         0       5775 anon_inode
init          1        root    7u     unix 0xffff880124fd8340       0t0       7249 socket
init          1        root    9u     unix 0xffff880124fdad80       0t0       7888 socket
init          1        root   10u     unix 0xffff8800c9ae8000       0t0    2899708 socket
init          1        root   11u     unix 0xffff880124fd89c0       0t0       7928 socket
kthreadd      2        root  cwd       DIR                9,1      4096          2 /
kthreadd      2        root  rtd       DIR                9,1      4096          2 /
kthreadd      2        root  txt   unknown                                         /proc/2/exe
ksoftirqd     3        root  cwd       DIR                9,1      4096          2 /
ksoftirqd     3        root  rtd       DIR                9,1      4096          2 /
ksoftirqd     3        root  txt   unknown                                         /proc/3/exe
migration     6        root  cwd       DIR                9,1      4096          2 /
migration     6        root  rtd       DIR                9,1      4096          2 /
migration     6        root  txt   unknown                                         /proc/6/exe
watchdog/     7        root  cwd       DIR                9,1      4096          2 /
watchdog/     7        root  rtd       DIR                9,1      4096          2 /
watchdog/     7        root  txt   unknown                                         /proc/7/exe
migration     8        root  cwd       DIR                9,1      4096          2 /
migration     8        root  rtd       DIR                9,1      4096          2 /
migration     8        root  txt   unknown                                         /proc/8/exe
ksoftirqd    10        root  cwd       DIR                9,1      4096          2 /
ksoftirqd    10        root  rtd       DIR                9,1      4096          2 /
ksoftirqd    10        root  txt   unknown                                         /proc/10/exe
watchdog/    12        root  cwd       DIR                9,1      4096          2 /
watchdog/    12        root  rtd       DIR                9,1      4096          2 /
watchdog/    12        root  txt   unknown                                         /proc/12/exe
cpuset       13        root  cwd       DIR                9,1      4096          2 /
cpuset       13        root  rtd       DIR                9,1      4096          2 /
cpuset       13        root  txt   unknown                                         /proc/13/exe
khelper      14        root  cwd       DIR                9,1      4096          2 /
khelper      14        root  rtd       DIR                9,1      4096          2 /
khelper      14        root  txt   unknown                                         /proc/14/exe
kdevtmpfs    15        root  cwd       DIR                0,5      4300       1026 /
kdevtmpfs    15        root  rtd       DIR                0,5      4300       1026 /
kdevtmpfs    15        root  txt   unknown                                         /proc/15/exe
netns        16        root  cwd       DIR                9,1      4096          2 /
netns        16        root  rtd       DIR                9,1      4096          2 /
netns        16        root  txt   unknown                                         /proc/16/exe
kworker/u    17        root  cwd       DIR                9,1      4096          2 /
kworker/u    17        root  rtd       DIR                9,1      4096          2 /
kworker/u    17        root  txt   unknown                                         /proc/17/exe
sync_supe    18        root  cwd       DIR                9,1      4096          2 /
sync_supe    18        root  rtd       DIR                9,1      4096          2 /
sync_supe    18        root  txt   unknown                                         /proc/18/exe
bdi-defau    19        root  cwd       DIR                9,1      4096          2 /
bdi-defau    19        root  rtd       DIR                9,1      4096          2 /
bdi-defau    19        root  txt   unknown                                         /proc/19/exe
kintegrit    20        root  cwd       DIR                9,1      4096          2 /
kintegrit    20        root  rtd       DIR                9,1      4096          2 /
kintegrit    20        root  txt   unknown                                         /proc/20/exe
kblockd      21        root  cwd       DIR                9,1      4096          2 /
kblockd      21        root  rtd       DIR                9,1      4096          2 /
kblockd      21        root  txt   unknown                                         /proc/21/exe
ata_sff      22        root  cwd       DIR                9,1      4096          2 /
ata_sff      22        root  rtd       DIR                9,1      4096          2 /
ata_sff      22        root  txt   unknown                                         /proc/22/exe
khubd        23        root  cwd       DIR                9,1      4096          2 /
khubd        23        root  rtd       DIR                9,1      4096          2 /
khubd        23        root  txt   unknown                                         /proc/23/exe
md           24        root  cwd       DIR                9,1      4096          2 /
md           24        root  rtd       DIR                9,1      4096          2 /
md           24        root  txt   unknown                                         /proc/24/exe
khungtask    26        root  cwd       DIR                9,1      4096          2 /
khungtask    26        root  rtd       DIR                9,1      4096          2 /
khungtask    26        root  txt   unknown                                         /proc/26/exe
kswapd0      27        root  cwd       DIR                9,1      4096          2 /
kswapd0      27        root  rtd       DIR                9,1      4096          2 /
kswapd0      27        root  txt   unknown                                         /proc/27/exe
ksmd         28        root  cwd       DIR                9,1      4096          2 /
ksmd         28        root  rtd       DIR                9,1      4096          2 /
ksmd         28        root  txt   unknown                                         /proc/28/exe
khugepage    29        root  cwd       DIR                9,1      4096          2 /
khugepage    29        root  rtd       DIR                9,1      4096          2 /
khugepage    29        root  txt   unknown                                         /proc/29/exe
fsnotify_    30        root  cwd       DIR                9,1      4096          2 /
fsnotify_    30        root  rtd       DIR                9,1      4096          2 /
fsnotify_    30        root  txt   unknown                                         /proc/30/exe
ecryptfs-    31        root  cwd       DIR                9,1      4096          2 /
ecryptfs-    31        root  rtd       DIR                9,1      4096          2 /
ecryptfs-    31        root  txt   unknown                                         /proc/31/exe
crypto       32        root  cwd       DIR                9,1      4096          2 /
crypto       32        root  rtd       DIR                9,1      4096          2 /
crypto       32        root  txt   unknown                                         /proc/32/exe
kthrotld     40        root  cwd       DIR                9,1      4096          2 /
kthrotld     40        root  rtd       DIR                9,1      4096          2 /
kthrotld     40        root  txt   unknown                                         /proc/40/exe
scsi_eh_0    41        root  cwd       DIR                9,1      4096          2 /
scsi_eh_0    41        root  rtd       DIR                9,1      4096          2 /
scsi_eh_0    41        root  txt   unknown                                         /proc/41/exe
scsi_eh_1    42        root  cwd       DIR                9,1      4096          2 /
scsi_eh_1    42        root  rtd       DIR                9,1      4096          2 /
scsi_eh_1    42        root  txt   unknown                                         /proc/42/exe
kworker/u    43        root  cwd       DIR                9,1      4096          2 /
kworker/u    43        root  rtd       DIR                9,1      4096          2 /
kworker/u    43        root  txt   unknown                                         /proc/43/exe
scsi_eh_2    44        root  cwd       DIR                9,1      4096          2 /
scsi_eh_2    44        root  rtd       DIR                9,1      4096          2 /
scsi_eh_2    44        root  txt   unknown                                         /proc/44/exe
scsi_eh_3    45        root  cwd       DIR                9,1      4096          2 /
scsi_eh_3    45        root  rtd       DIR                9,1      4096          2 /
scsi_eh_3    45        root  txt   unknown                                         /proc/45/exe
devfreq_w    69        root  cwd       DIR                9,1      4096          2 /
devfreq_w    69        root  rtd       DIR                9,1      4096          2 /
devfreq_w    69        root  txt   unknown                                         /proc/69/exe
md0_raid1   223        root  cwd       DIR                9,1      4096          2 /
md0_raid1   223        root  rtd       DIR                9,1      4096          2 /
md0_raid1   223        root  txt   unknown                                         /proc/223/exe
md1_raid1   240        root  cwd       DIR                9,1      4096          2 /
md1_raid1   240        root  rtd       DIR                9,1      4096          2 /
md1_raid1   240        root  txt   unknown                                         /proc/240/exe
jbd2/md1-   253        root  cwd       DIR                9,1      4096          2 /
jbd2/md1-   253        root  rtd       DIR                9,1      4096          2 /
jbd2/md1-   253        root  txt   unknown                                         /proc/253/exe
ext4-dio-   254        root  cwd       DIR                9,1      4096          2 /
ext4-dio-   254        root  rtd       DIR                9,1      4096          2 /
ext4-dio-   254        root  txt   unknown                                         /proc/254/exe
sshd        418       myacc  cwd       DIR                9,1      4096          2 /
sshd        418       myacc  rtd       DIR                9,1      4096          2 /
sshd        418       myacc  txt       REG                9,1    517112    7342405 /usr/sbin/sshd
sshd        418       myacc  DEL       REG                0,4              2895813 /dev/zero
sshd        418       myacc  mem       REG                9,1     14392    6160461 /lib/x86_64-linux-gnu/security/pam_env.so
sshd        418       myacc  mem       REG                9,1     18704    6160745 /lib/x86_64-linux-gnu/security/pam_limits.so
sshd        418       myacc  mem       REG                9,1     10240    6160751 /lib/x86_64-linux-gnu/security/pam_mail.so
sshd        418       myacc  mem       REG                9,1     10272    6160754 /lib/x86_64-linux-gnu/security/pam_motd.so
sshd        418       myacc  mem       REG                9,1     10208    6160460 /lib/x86_64-linux-gnu/security/pam_echo.so
sshd        418       myacc  mem       REG                9,1     10304    6160776 /lib/x86_64-linux-gnu/security/pam_umask.so
sshd        418       myacc  mem       REG                9,1      6104    6160757 /lib/x86_64-linux-gnu/security/pam_nologin.so
sshd        418       myacc  mem       REG                9,1      6040    6160758 /lib/x86_64-linux-gnu/security/pam_permit.so
sshd        418       myacc  mem       REG                9,1      5944    6160459 /lib/x86_64-linux-gnu/security/pam_deny.so
sshd        418       myacc  mem       REG                9,1     56088    6160777 /lib/x86_64-linux-gnu/security/pam_unix.so
sshd        418       myacc  DEL       REG                9,1              6164160 /lib/x86_64-linux-gnu/libnss_dns-2.15.so
sshd        418       myacc  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
sshd        418       myacc  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
sshd        418       myacc  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
sshd        418       myacc  DEL       REG                9,1              6164159 /lib/x86_64-linux-gnu/libresolv-2.15.so
sshd        418       myacc  mem       REG                9,1     14360    6160694 /lib/x86_64-linux-gnu/libkeyutils.so.1.4
sshd        418       myacc  mem       REG                9,1     31200    7341700 /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
sshd        418       myacc  mem       REG                9,1    158168    7340880 /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
sshd        418       myacc  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
sshd        418       myacc  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
sshd        418       myacc  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
sshd        418       myacc  mem       REG                9,1     14696    6160396 /lib/x86_64-linux-gnu/libcom_err.so.2.1
sshd        418       myacc  mem       REG                9,1    844648    7340884 /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
sshd        418       myacc  mem       REG                9,1    252720    7340882 /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
sshd        418       myacc  DEL       REG                9,1              6160492 /lib/x86_64-linux-gnu/libcrypt-2.15.so
sshd        418       myacc  mem       REG                9,1     92720    6160612 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
sshd        418       myacc  DEL       REG                9,1              6160392 /lib/x86_64-linux-gnu/libutil-2.15.so
sshd        418       myacc  mem       REG                9,1   1930616    6160426 /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
sshd        418       myacc  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
sshd        418       myacc  mem       REG                9,1    121936    6160447 /lib/x86_64-linux-gnu/libselinux.so.1
sshd        418       myacc  mem       REG                9,1     55744    6160467 /lib/x86_64-linux-gnu/libpam.so.0.83.0
sshd        418       myacc  mem       REG                9,1     36432    6164116 /lib/x86_64-linux-gnu/libwrap.so.0.7.6
sshd        418       myacc  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
sshd        418       myacc  DEL       REG                0,4              2896960 /dev/zero
sshd        418       myacc    0u      CHR                1,3       0t0       5800 /dev/null
sshd        418       myacc    1u      CHR                1,3       0t0       5800 /dev/null
sshd        418       myacc    2u      CHR                1,3       0t0       5800 /dev/null
sshd        418       myacc    3u     IPv4            2896941       0t0        TCP mydomain.com:22->mail.mydomain.com:64852 (ESTABLISHED)
sshd        418       myacc    4u     unix 0xffff8800c9ae9a00       0t0    2895814 socket
sshd        418       myacc    5u     unix 0xffff8800c9ae8340       0t0    2897983 socket
sshd        418       myacc    6r     FIFO                0,8       0t0    2897985 pipe
sshd        418       myacc    7w     FIFO                0,8       0t0    2897985 pipe
sshd        418       myacc    8u      CHR                5,2       0t0       5897 /dev/ptmx
sshd        418       myacc   10u      CHR                5,2       0t0       5897 /dev/ptmx
sshd        418       myacc   11u      CHR                5,2       0t0       5897 /dev/ptmx
bash        420       myacc  cwd       DIR                9,1      4096    9043970 /home/myacc
bash        420       myacc  rtd       DIR                9,1      4096          2 /
bash        420       myacc  txt       REG                9,1    959120    4325410 /bin/bash
bash        420       myacc  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
bash        420       myacc  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
bash        420       myacc  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
bash        420       myacc  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
bash        420       myacc  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
bash        420       myacc  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
bash        420       myacc  mem       REG                9,1    159200    6160452 /lib/x86_64-linux-gnu/libtinfo.so.5.9
bash        420       myacc  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
bash        420       myacc  DEL       REG                9,1              7349412 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
bash        420       myacc  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
bash        420       myacc    0u      CHR              136,1       0t0          4 /dev/pts/1
bash        420       myacc    1u      CHR              136,1       0t0          4 /dev/pts/1
bash        420       myacc    2u      CHR              136,1       0t0          4 /dev/pts/1
bash        420       myacc  255u      CHR              136,1       0t0          4 /dev/pts/1
kworker/1   521        root  cwd       DIR                9,1      4096          2 /
kworker/1   521        root  rtd       DIR                9,1      4096          2 /
kworker/1   521        root  txt   unknown                                         /proc/521/exe
sudo        526        root  cwd       DIR                9,1      4096    9043970 /home/myacc
sudo        526        root  rtd       DIR                9,1      4096          2 /
sudo        526        root  txt       REG                9,1     71288    7342340 /usr/bin/sudo
sudo        526        root  mem       REG                9,1     10304    6160776 /lib/x86_64-linux-gnu/security/pam_umask.so
sudo        526        root  mem       REG                9,1      6040    6160758 /lib/x86_64-linux-gnu/security/pam_permit.so
sudo        526        root  mem       REG                9,1      5944    6160459 /lib/x86_64-linux-gnu/security/pam_deny.so
sudo        526        root  mem       REG                9,1    121936    6160447 /lib/x86_64-linux-gnu/libselinux.so.1
sudo        526        root  DEL       REG                9,1              6160492 /lib/x86_64-linux-gnu/libcrypt-2.15.so
sudo        526        root  mem       REG                9,1     56088    6160777 /lib/x86_64-linux-gnu/security/pam_unix.so
sudo        526        root  mem       REG                9,1     14392    6160461 /lib/x86_64-linux-gnu/security/pam_env.so
sudo        526        root  DEL       REG                9,1              6164159 /lib/x86_64-linux-gnu/libresolv-2.15.so
sudo        526        root  DEL       REG                9,1              6164160 /lib/x86_64-linux-gnu/libnss_dns-2.15.so
sudo        526        root  mem       REG                9,1     55744    6160467 /lib/x86_64-linux-gnu/libpam.so.0.83.0
sudo        526        root  mem       REG                9,1    185288    7471263 /usr/lib/sudo/sudoers.so
sudo        526        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
sudo        526        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
sudo        526        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
sudo        526        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
sudo        526        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
sudo        526        root  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
sudo        526        root  DEL       REG                9,1              6160392 /lib/x86_64-linux-gnu/libutil-2.15.so
sudo        526        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
sudo        526        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
sudo        526        root    0u      CHR              136,0       0t0          3 /dev/pts/0
sudo        526        root    1u      CHR              136,0       0t0          3 /dev/pts/0
sudo        526        root    2u      CHR              136,0       0t0          3 /dev/pts/0
sudo        526        root    3u     unix 0xffff8800ac35d380       0t0    2897100 socket
sudo        526        root    5r     FIFO                0,8       0t0    2897102 pipe
sudo        526        root    6r      REG                0,3         0 4026532027 /proc/stat
sudo        526        root    7w     FIFO                0,8       0t0    2897102 pipe
sudo        526        root    8u     unix 0xffff8800ac35d6c0       0t0    2897103 socket
apt-get     527        root  cwd       DIR                9,1      4096    9043970 /home/myacc
apt-get     527        root  rtd       DIR                9,1      4096          2 /
apt-get     527        root  txt       REG                9,1    192592    7346018 /usr/bin/apt-get
apt-get     527        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
apt-get     527        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
apt-get     527        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
apt-get     527        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
apt-get     527        root  mem       REG                9,1  42222561    4980888 /var/cache/apt/pkgcache.bin
apt-get     527        root  DEL       REG                9,1              6164167 /lib/x86_64-linux-gnu/libm-2.15.so
apt-get     527        root  mem       REG                9,1     92720    6160612 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
apt-get     527        root  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
apt-get     527        root  DEL       REG                9,1              6160392 /lib/x86_64-linux-gnu/libutil-2.15.so
apt-get     527        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
apt-get     527        root  mem       REG                9,1     88384    6160428 /lib/x86_64-linux-gnu/libgcc_s.so.1
apt-get     527        root  mem       REG                9,1    962656    7344996 /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
apt-get     527        root  mem       REG                9,1   1209224    7345625 /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
apt-get     527        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
apt-get     527        root  DEL       REG                9,1              7349412 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
apt-get     527        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
apt-get     527        root    0u      CHR              136,0       0t0          3 /dev/pts/0
apt-get     527        root    1u      CHR              136,0       0t0          3 /dev/pts/0
apt-get     527        root    2u      CHR              136,0       0t0          3 /dev/pts/0
apt-get     527        root    3r      CHR                1,3       0t0       5800 /dev/null
apt-get     527        root    4u      REG                9,1      4425    4982551 /var/log/apt/term.log
apt-get     527        root    5r      REG                9,1    512705    4983949 /var/lib/dpkg/status (deleted)
apt-get     527        root    6r      REG                9,1    350239    4981190 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en
apt-get     527        root    7r      REG                9,1      4573    4981089 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en
apt-get     527        root    8u      REG                9,1      2884    4981432 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en
apt-get     527        root    9r      REG                9,1   2512314    4980875 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en
apt-get     527        root   10r      REG                9,1      7318    4981332 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages
apt-get     527        root   11r      REG                9,1    638872    4981222 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages
apt-get     527        root   12r      REG                9,1     81281    4981183 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages
apt-get     527        root   13r      REG                9,1   3565600    4981163 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages
apt-get     527        root   14r      REG                9,1      6410    4980775 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-amd64_Packages
apt-get     527        root   15r      REG                9,1    580759    4981385 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-amd64_Packages
apt-get     527        root   16r      REG                9,1     81295    4981459 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-amd64_Packages
apt-get     527        root   17r      REG                9,1   3217293    4981317 /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages
apt-get     527        root   18r      REG                9,1    136874    4980845 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en
apt-get     527        root   19r      REG                9,1         0    4983012 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Translation-en
apt-get     527        root   20r      REG                9,1     13610    4981217 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en
apt-get     527        root   21r      REG                9,1     14665    4980894 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en
apt-get     527        root   22r      REG                9,1     19590    4981192 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages
apt-get     527        root   23r      REG                9,1    215371    4981461 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages
apt-get     527        root   24r      REG                9,1         0    4981448 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages
apt-get     527        root   25r      REG                9,1     21644    4981447 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages
apt-get     527        root   26r      REG                9,1     19672    4981437 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-amd64_Packages
apt-get     527        root   27r      REG                9,1    216511    4981434 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-amd64_Packages
apt-get     527        root   28r      REG                9,1         0    4981312 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-amd64_Packages
apt-get     527        root   29r      REG                9,1     21672    4982200 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-amd64_Packages
apt-get     527        root   30r      REG                9,1    774045    4981377 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en
apt-get     527        root   31r      REG                9,1     18599    4981651 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en
apt-get     527        root   32r      REG                9,1     33270    4981195 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en
apt-get     527        root   33r      REG                9,1   3751520    4981479 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en
apt-get     527        root   34r      REG                9,1     73071    4980961 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages
apt-get     527        root   35r      REG                9,1   1424042    4981308 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages
apt-get     527        root   36r      REG                9,1    191718    4981463 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages
apt-get     527        root   37r      REG                9,1   6420379    4981372 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages
apt-get     527        root   38r      REG                9,1     74594    4981198 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-amd64_Packages
apt-get     527        root   39r      REG                9,1   1362989    4981304 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages
apt-get     527        root   40r      REG                9,1    191957    4981420 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-amd64_Packages
apt-get     527        root   41r      REG                9,1   6056048    4981401 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages
apt-get     527        root   42r      REG                9,1  15034875    4983007 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
apt-get     527        root   43r      REG                9,1     10224    4983003 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en
apt-get     527        root   44r      REG                9,1    367466    4983005 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en
apt-get     527        root   45r      REG                9,1   3861559    4983004 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
apt-get     527        root   46r      REG                9,1    591662    4982340 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages
apt-get     527        root   47r      REG                9,1  25568759    4982362 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages
apt-get     527        root   48r      REG                9,1    134582    4982321 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages
apt-get     527        root   49r      REG                9,1   7816415    4982333 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
apt-get     527        root   50r      REG                9,1    581550    4982195 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages
apt-get     527        root   51r      REG                9,1  25546870    4982307 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages
apt-get     527        root   52r      REG                9,1    134705    4982124 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages
apt-get     527        root   53r      REG                9,1   7818931    4981849 /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
apt-get     527        root   54uW     REG                9,1         0    4980749 /var/cache/apt/archives/lock
apt-get     527        root   55w      REG                9,1       426    4981009 /var/log/apt/history.log
apt-get     527        root   56r     FIFO                0,8       0t0    2900509 pipe
apt-get     527        root   58u      CHR                5,2       0t0       5897 /dev/ptmx
rsyslogd    569      syslog  cwd       DIR                9,1      4096          2 /
rsyslogd    569      syslog  rtd       DIR                9,1      4096          2 /
rsyslogd    569      syslog  txt       REG                9,1    384440    7341019 /usr/sbin/rsyslogd
rsyslogd    569      syslog  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
rsyslogd    569      syslog  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
rsyslogd    569      syslog  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
rsyslogd    569      syslog  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
rsyslogd    569      syslog  mem       REG                9,1     27768    7472276 /usr/lib/rsyslog/imklog.so
rsyslogd    569      syslog  mem       REG                9,1    339272    7472987 /usr/lib/rsyslog/imuxsock.so
rsyslogd    569      syslog  mem       REG                9,1     23344    7472278 /usr/lib/rsyslog/lmnet.so
rsyslogd    569      syslog  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
rsyslogd    569      syslog  DEL       REG                9,1              6164161 /lib/x86_64-linux-gnu/librt-2.15.so
rsyslogd    569      syslog  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
rsyslogd    569      syslog  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
rsyslogd    569      syslog  mem       REG                9,1     92720    6160612 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
rsyslogd    569      syslog  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
rsyslogd    569      syslog    0u     unix 0xffff880124fda700       0t0       7783 /dev/log
rsyslogd    569      syslog    1w      REG                9,1      3133    4980776 /var/log/syslog
rsyslogd    569      syslog    2w      REG                9,1     83654    4982623 /var/log/auth.log
rsyslogd    569      syslog    3r      REG                0,3         0 4026532032 /proc/kmsg
rsyslogd    569      syslog    4w      REG                9,1       353    4982303 /var/log/kern.log
hd-audio0   570        root  cwd       DIR                9,1      4096          2 /
hd-audio0   570        root  rtd       DIR                9,1      4096          2 /
hd-audio0   570        root  txt   unknown                                         /proc/570/exe
dbus-daem   605  messagebus  cwd       DIR                9,1      4096          2 /
dbus-daem   605  messagebus  rtd       DIR                9,1      4096          2 /
dbus-daem   605  messagebus  txt       REG                9,1    411720    4325425 /bin/dbus-daemon
dbus-daem   605  messagebus  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
dbus-daem   605  messagebus  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
dbus-daem   605  messagebus  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
dbus-daem   605  messagebus  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
dbus-daem   605  messagebus  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
dbus-daem   605  messagebus  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
dbus-daem   605  messagebus  DEL       REG                9,1              6164161 /lib/x86_64-linux-gnu/librt-2.15.so
dbus-daem   605  messagebus  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
dbus-daem   605  messagebus  mem       REG                9,1    121936    6160447 /lib/x86_64-linux-gnu/libselinux.so.1
dbus-daem   605  messagebus  mem       REG                9,1    170024    6160615 /lib/x86_64-linux-gnu/libexpat.so.1.5.2
dbus-daem   605  messagebus  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
dbus-daem   605  messagebus    0u      CHR                1,3       0t0       5800 /dev/null
dbus-daem   605  messagebus    1u      CHR                1,3       0t0       5800 /dev/null
dbus-daem   605  messagebus    2u      CHR                1,3       0t0       5800 /dev/null
dbus-daem   605  messagebus    3u     unix 0xffff88012710ea40       0t0       7020 /var/run/dbus/system_bus_socket
dbus-daem   605  messagebus    4u      CHR                1,3       0t0       5800 /dev/null
dbus-daem   605  messagebus    5r     0000                0,9         0       5775 anon_inode
dbus-daem   605  messagebus    6u     unix 0xffff88012710e700       0t0       8220 socket
dbus-daem   605  messagebus    7u     unix 0xffff88012710ed80       0t0       8221 socket
dbus-daem   605  messagebus    8u     unix 0xffff880124fdb0c0       0t0       7889 /var/run/dbus/system_bus_socket
dbus-daem   605  messagebus   10u     unix 0xffff880124fdba80       0t0       8981 /var/run/dbus/system_bus_socket
upstart-s   646        root  cwd       DIR                9,1      4096          2 /
upstart-s   646        root  rtd       DIR                9,1      4096          2 /
upstart-s   646        root  txt       REG                9,1    108744    1310884 /sbin/upstart-socket-bridge
upstart-s   646        root  DEL       REG                9,1              6164161 /lib/x86_64-linux-gnu/librt-2.15.so
upstart-s   646        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
upstart-s   646        root  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
upstart-s   646        root  mem       REG                9,1    276392    6160436 /lib/x86_64-linux-gnu/libdbus-1.so.3.5.8
upstart-s   646        root  mem       REG                9,1     38888    6160476 /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
upstart-s   646        root  mem       REG                9,1     96240    6160438 /lib/x86_64-linux-gnu/libnih.so.1.0.0
upstart-s   646        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
upstart-s   646        root    0u      CHR                1,3       0t0       5800 /dev/null
upstart-s   646        root    1u      CHR                1,3       0t0       5800 /dev/null
upstart-s   646        root    2u      CHR                1,3       0t0       5800 /dev/null
upstart-s   646        root    3u     0000                0,9         0       5775 anon_inode
upstart-s   646        root    4u     unix 0xffff880124fd8680       0t0       7926 socket
upstart-s   646        root    5r     FIFO                0,8       0t0       7927 pipe
upstart-s   646        root    6w     FIFO                0,8       0t0       7927 pipe
sshd        783        root  cwd       DIR                9,1      4096          2 /
sshd        783        root  rtd       DIR                9,1      4096          2 /
sshd        783        root  txt       REG                9,1    517112    7342405 /usr/sbin/sshd
sshd        783        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
sshd        783        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
sshd        783        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
sshd        783        root  DEL       REG                9,1              6164159 /lib/x86_64-linux-gnu/libresolv-2.15.so
sshd        783        root  mem       REG                9,1     14360    6160694 /lib/x86_64-linux-gnu/libkeyutils.so.1.4
sshd        783        root  mem       REG                9,1     31200    7341700 /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
sshd        783        root  mem       REG                9,1    158168    7340880 /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
sshd        783        root  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
sshd        783        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
sshd        783        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
sshd        783        root  mem       REG                9,1     14696    6160396 /lib/x86_64-linux-gnu/libcom_err.so.2.1
sshd        783        root  mem       REG                9,1    844648    7340884 /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
sshd        783        root  mem       REG                9,1    252720    7340882 /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
sshd        783        root  DEL       REG                9,1              6160492 /lib/x86_64-linux-gnu/libcrypt-2.15.so
sshd        783        root  mem       REG                9,1     92720    6160612 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
sshd        783        root  DEL       REG                9,1              6160392 /lib/x86_64-linux-gnu/libutil-2.15.so
sshd        783        root  mem       REG                9,1   1930616    6160426 /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
sshd        783        root  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
sshd        783        root  mem       REG                9,1    121936    6160447 /lib/x86_64-linux-gnu/libselinux.so.1
sshd        783        root  mem       REG                9,1     55744    6160467 /lib/x86_64-linux-gnu/libpam.so.0.83.0
sshd        783        root  mem       REG                9,1     36432    6164116 /lib/x86_64-linux-gnu/libwrap.so.0.7.6
sshd        783        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
sshd        783        root    0u      CHR                1,3       0t0       5800 /dev/null
sshd        783        root    1u      CHR                1,3       0t0       5800 /dev/null
sshd        783        root    2u      CHR                1,3       0t0       5800 /dev/null
sshd        783        root    3r     IPv4               8732       0t0        TCP *:22 (LISTEN)
sshd        783        root    4u     IPv6               8734       0t0        TCP *:22 (LISTEN)
getty       865        root  cwd       DIR                9,1      4096          2 /
getty       865        root  rtd       DIR                9,1      4096          2 /
getty       865        root  txt       REG                9,1     32048    1310766 /sbin/getty
getty       865        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
getty       865        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
getty       865        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
getty       865        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
getty       865        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
getty       865        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
getty       865        root  DEL       REG                9,1              7349412 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
getty       865        root  DEL       REG                9,1              7344434 /usr/lib/locale/C.UTF-8/LC_CTYPE
getty       865        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
getty       865        root    0u      CHR                4,4       0t0       5818 /dev/tty4
getty       865        root    1u      CHR                4,4       0t0       5818 /dev/tty4
getty       865        root    2u      CHR                4,4       0t0       5818 /dev/tty4
getty       870        root  cwd       DIR                9,1      4096          2 /
getty       870        root  rtd       DIR                9,1      4096          2 /
getty       870        root  txt       REG                9,1     32048    1310766 /sbin/getty
getty       870        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
getty       870        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
getty       870        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
getty       870        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
getty       870        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
getty       870        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
getty       870        root  DEL       REG                9,1              7349412 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
getty       870        root  DEL       REG                9,1              7344434 /usr/lib/locale/C.UTF-8/LC_CTYPE
getty       870        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
getty       870        root    0u      CHR                4,5       0t0       5819 /dev/tty5
getty       870        root    1u      CHR                4,5       0t0       5819 /dev/tty5
getty       870        root    2u      CHR                4,5       0t0       5819 /dev/tty5
getty       882        root  cwd       DIR                9,1      4096          2 /
getty       882        root  rtd       DIR                9,1      4096          2 /
getty       882        root  txt       REG                9,1     32048    1310766 /sbin/getty
getty       882        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
getty       882        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
getty       882        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
getty       882        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
getty       882        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
getty       882        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
getty       882        root  DEL       REG                9,1              7349412 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
getty       882        root  DEL       REG                9,1              7344434 /usr/lib/locale/C.UTF-8/LC_CTYPE
getty       882        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
getty       882        root    0u      CHR                4,2       0t0       5816 /dev/tty2
getty       882        root    1u      CHR                4,2       0t0       5816 /dev/tty2
getty       882        root    2u      CHR                4,2       0t0       5816 /dev/tty2
getty       883        root  cwd       DIR                9,1      4096          2 /
getty       883        root  rtd       DIR                9,1      4096          2 /
getty       883        root  txt       REG                9,1     32048    1310766 /sbin/getty
getty       883        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
getty       883        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
getty       883        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
getty       883        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
getty       883        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
getty       883        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
getty       883        root  DEL       REG                9,1              7349412 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
getty       883        root  DEL       REG                9,1              7344434 /usr/lib/locale/C.UTF-8/LC_CTYPE
getty       883        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
getty       883        root    0u      CHR                4,3       0t0       5817 /dev/tty3
getty       883        root    1u      CHR                4,3       0t0       5817 /dev/tty3
getty       883        root    2u      CHR                4,3       0t0       5817 /dev/tty3
getty       886        root  cwd       DIR                9,1      4096          2 /
getty       886        root  rtd       DIR                9,1      4096          2 /
getty       886        root  txt       REG                9,1     32048    1310766 /sbin/getty
getty       886        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
getty       886        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
getty       886        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
getty       886        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
getty       886        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
getty       886        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
getty       886        root  DEL       REG                9,1              7349412 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
getty       886        root  DEL       REG                9,1              7344434 /usr/lib/locale/C.UTF-8/LC_CTYPE
getty       886        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
getty       886        root    0u      CHR                4,6       0t0       5820 /dev/tty6
getty       886        root    1u      CHR                4,6       0t0       5820 /dev/tty6
getty       886        root    2u      CHR                4,6       0t0       5820 /dev/tty6
acpid       890        root  cwd       DIR                9,1      4096          2 /
acpid       890        root  rtd       DIR                9,1      4096          2 /
acpid       890        root  txt       REG                9,1     43792    7349094 /usr/sbin/acpid
acpid       890        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
acpid       890        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
acpid       890        root    0u      CHR                1,3       0t0       5800 /dev/null
acpid       890        root    1u      CHR                1,3       0t0       5800 /dev/null
acpid       890        root    2u      CHR                1,3       0t0       5800 /dev/null
acpid       890        root    3u     unix 0xffff88012710f400       0t0       8816 socket
acpid       890        root    4r      REG                0,3         0 4026531978 /proc/acpi/event
acpid       890        root    5u     unix 0xffff88012710d380       0t0       8817 /var/run/acpid.socket
cron        895        root  cwd       DIR                9,1      4096    4981360 /var/spool/cron
cron        895        root  rtd       DIR                9,1      4096          2 /
cron        895        root  txt       REG                9,1     44320    7344889 /usr/sbin/cron
cron        895        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
cron        895        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
cron        895        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
cron        895        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
cron        895        root  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
cron        895        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
cron        895        root  mem       REG                9,1    121936    6160447 /lib/x86_64-linux-gnu/libselinux.so.1
cron        895        root  mem       REG                9,1     55744    6160467 /lib/x86_64-linux-gnu/libpam.so.0.83.0
cron        895        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
cron        895        root    0r      CHR                1,3       0t0       5800 /dev/null
cron        895        root    1w      CHR                1,3       0t0       5800 /dev/null
cron        895        root    2w      CHR                1,3       0t0       5800 /dev/null
cron        895        root    3u      REG               0,15         4       8819 /run/crond.pid
atd         896      daemon  cwd       DIR                9,1      4096    4981996 /var/spool/cron/atjobs
atd         896      daemon  rtd       DIR                9,1      4096          2 /
atd         896      daemon  txt       REG                9,1     23152    7348450 /usr/sbin/atd
atd         896      daemon  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
atd         896      daemon  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
atd         896      daemon  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
atd         896      daemon  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
atd         896      daemon  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
atd         896      daemon  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
atd         896      daemon  mem       REG                9,1     55744    6160467 /lib/x86_64-linux-gnu/libpam.so.0.83.0
atd         896      daemon  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
atd         896      daemon    0u      CHR                1,3       0t0       5800 /dev/null
atd         896      daemon    1u      CHR                1,3       0t0       5800 /dev/null
atd         896      daemon    2u      CHR                1,3       0t0       5800 /dev/null
atd         896      daemon    3uW     REG               0,15         4       8144 /run/atd.pid
mysqld      908       mysql  cwd       DIR                9,1      4096    4982931 /var/lib/mysql
mysqld      908       mysql  rtd       DIR                9,1      4096          2 /
mysqld      908       mysql  txt       REG                9,1  12229264    7342212 /usr/sbin/mysqld
mysqld      908       mysql  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
mysqld      908       mysql  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
mysqld      908       mysql  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
mysqld      908       mysql  mem       REG                9,1     88384    6160428 /lib/x86_64-linux-gnu/libgcc_s.so.1
mysqld      908       mysql  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
mysqld      908       mysql  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
mysqld      908       mysql  DEL       REG                9,1              6164167 /lib/x86_64-linux-gnu/libm-2.15.so
mysqld      908       mysql  mem       REG                9,1    962656    7344996 /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.16
mysqld      908       mysql  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
mysqld      908       mysql  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
mysqld      908       mysql  DEL       REG                9,1              6160492 /lib/x86_64-linux-gnu/libcrypt-2.15.so
mysqld      908       mysql  mem       REG                9,1     36432    6164116 /lib/x86_64-linux-gnu/libwrap.so.0.7.6
mysqld      908       mysql  DEL       REG                9,1              6164161 /lib/x86_64-linux-gnu/librt-2.15.so
mysqld      908       mysql  mem       REG                9,1     92720    6160612 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
mysqld      908       mysql  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
mysqld      908       mysql    0u      CHR                1,3       0t0       5800 /dev/null
mysqld      908       mysql    1w      REG                9,1         0    4981918 /var/log/mysql/error.log
mysqld      908       mysql    2w      REG                9,1         0    4981918 /var/log/mysql/error.log
mysqld      908       mysql    3uW     REG                9,1  18874368    4983735 /var/lib/mysql/ibdata1
mysqld      908       mysql    4u      REG                9,1         0    2752519 /tmp/ibGbCaIs (deleted)
mysqld      908       mysql    5u      REG                9,1         0    2752521 /tmp/ibStHW6K (deleted)
mysqld      908       mysql    6u      REG                9,1         0    2752523 /tmp/ibQY2Iv3 (deleted)
mysqld      908       mysql    7u      REG                9,1         0    2752524 /tmp/ibUKpr8l (deleted)
mysqld      908       mysql    8uW     REG                9,1   5242880    4983736 /var/lib/mysql/ib_logfile0
mysqld      908       mysql    9uW     REG                9,1   5242880    4983737 /var/lib/mysql/ib_logfile1
mysqld      908       mysql   10u     IPv4               9571       0t0        TCP localhost:mysql (LISTEN)
mysqld      908       mysql   11u      REG                9,1         0    2752525 /tmp/ibKnfumI (deleted)
mysqld      908       mysql   12u     unix 0xffff880124fd8000       0t0       9572 /var/run/mysqld/mysqld.sock
mysqld      908       mysql   13u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   14u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   15u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   16u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   17u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   18u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   19u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   20u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   21u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   22u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   23u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   24u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   25u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   26u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   27u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   28u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   29u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   30u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   31u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   32u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   33u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   34u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   35u      REG                9,1   1539132    4983066 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   36u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   37u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   38u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   39u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   40u      REG                9,1   1514496    4982376 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   41u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   42u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   43u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   44u      REG                9,1    147456    4983317 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   45u      REG                9,1    152516    4983318 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   46u      REG                9,1   1181696    4984112 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   47u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   48u      REG                9,1      9216    4983099 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   49u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   50u      REG                9,1      3072    4983096 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   51u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   52u      REG                9,1   1034240    4982508 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   53u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   54u      REG                9,1    431104    4982026 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   55u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   56u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   57u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   58u      REG                9,1    964608    4980844 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   59u      REG                9,1   6157100    4980876 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   60u      REG                9,1     10240    4981750 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   61u      REG                9,1     32966    4981755 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   62u      REG                9,1      3072    4981758 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   63u      REG                9,1      2380    4981763 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   64u      REG                9,1    114688    4982020 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   65u      REG                9,1     63973    4982022 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   66u      REG                9,1    133120    4983105 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   67u      REG                9,1     72340    4983106 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   68u      REG                9,1     98304    4982085 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   69u      REG                9,1     34376    4982116 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   70u      REG                9,1     72340    4983106 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   71u      REG                9,1      6144    4982290 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   72u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   73u      REG                9,1      6144    4982372 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   74u      REG                9,1      9639    4982373 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   75u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   76u      REG                9,1     90112    4982473 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   77u      REG                9,1    152516    4983318 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   78u      REG                9,1      2048    4982605 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   79u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   80u      REG                9,1      5120    4982655 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   81u      REG                9,1      5012    4982657 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   82u      REG                9,1      2048    4982661 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   83u      REG                9,1        40    4982789 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   84u      REG                9,1   1769472    4982815 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   85u      REG                9,1   2022576    4982816 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   86u      REG                9,1    888832    4982822 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   87u      REG                9,1   1251548    4982861 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   88u      REG                9,1    507904    4982939 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   89u      REG                9,1    241605    4982948 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   90u      REG                9,1    567296    4982972 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   91u      REG                9,1    300320    4983009 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   92u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   93u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   94u      REG                9,1   1004544    4983024 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   95u      REG                9,1    500712    4983032 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   96u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   97u      REG                9,1    816128    4983042 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql   98u      REG                9,1   1539132    4983066 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql   99u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  100u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  101u      REG                9,1    393216    4983070 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  102u      REG                9,1   8175372    4983072 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  103u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  104u      REG                9,1   3269632    4983078 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  105u      REG                9,1   1957312    4983079 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  106u      REG                9,1      1024    4983084 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  107u      REG                9,1         0    4983085 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  108u      REG                9,1      9216    4983087 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  109u      REG                9,1      1832    4983088 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  110u      REG                9,1     41984    4983090 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  111u      REG                9,1    103628    4983091 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  112u      REG                9,1     10240    4983093 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  113u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  114u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  115u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  116u      REG                9,1      1024    4983102 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  117u      REG                9,1    440260    4983103 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  118u      REG                9,1      2048    4983108 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  119u      REG                9,1       469    4983109 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  120u      REG                9,1     65536    4983111 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  121u      REG                9,1     29968    4983112 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  122u      REG                9,1     86016    4983114 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  123u      REG                9,1     31717    4983115 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  124u      REG                9,1    102400    4983117 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  125u      REG                9,1     52748    4983118 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  126u      REG                9,1     44032    4983120 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  127u      REG                9,1     19920    4983121 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  128u      REG                9,1      6144    4983123 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  129u      REG                9,1     17732    4983124 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  130u      REG                9,1    246784    4983126 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  131u      REG                9,1   1633868    4983127 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  132u      REG                9,1   1294336    4983129 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  133u      REG                9,1   1410696    4983130 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  134u      REG                9,1    385024    4983132 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  135u      REG                9,1   1661368    4983133 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  136u      REG                9,1  12052480    4983150 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  137u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  138u      REG                9,1      2048    4983158 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  139u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  140u      REG                9,1   1383424    4983161 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  141u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  142u      REG                9,1      1024    4983187 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  143u      REG                9,1   4371012    4983188 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  144u      REG                9,1      2048    4983193 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  145u      REG                9,1       154    4983196 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  146u      REG                9,1     12288    4983200 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  147u      REG                9,1     13872    4983201 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  148u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  149u      REG                9,1      1024    4983209 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  150u      REG                9,1  23663982    4983210 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  151u      REG                9,1      2048    4983212 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  152u      REG                9,1        84    4983213 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  153u      REG                9,1      1024    4983215 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  154u      REG                9,1   1972620    4983216 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  155u      REG                9,1      1024    4983218 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  156u      REG                9,1      6840    4983219 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  157u      REG                9,1      2048    4983222 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  158u      REG                9,1      1184    4983223 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  159u      REG                9,1    117760    4983229 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  160u      REG                9,1    162904    4983231 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  161u      REG                9,1    192512    4983225 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  162u      REG                9,1    354532    4983226 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  163u      REG                9,1      2048    4983233 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  164u      REG                9,1       260    4983234 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  165u      REG                9,1      2048    4983236 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  166u      REG                9,1      2000    4983237 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  167u      REG                9,1      2048    4983242 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  168u      REG                9,1       340    4983244 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  169u      REG                9,1     25600    4983239 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  170u      REG                9,1     34080    4983240 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  171u      REG                9,1      5120    4983246 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  172u      REG                9,1      4840    4983248 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  173u      REG                9,1      4096    4983250 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  174u      REG                9,1      3400    4983251 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  175u      REG                9,1      2048    4983254 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  176u      REG                9,1       160    4983256 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  177u      REG                9,1      2048    4983258 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  178u      REG                9,1       105    4983260 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  179u      REG                9,1      1024    4983263 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  180u      REG                9,1       767    4983264 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  181u      REG                9,1      2048    4983269 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  182u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  183u      REG                9,1        20    4983270 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  184u      REG                9,1      2048    4983272 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  185u      REG                9,1       244    4983273 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  186u      REG                9,1    103424    4983275 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  187u      REG                9,1    122268    4983294 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  188u      REG                9,1      4096    4983309 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  189u      REG                9,1      1960    4983310 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  190u      REG                9,1    152516    4983318 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  191u      REG                9,1     27648    4983341 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  192u      REG                9,1     24484    4983342 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  193u      REG                9,1   3570688    4983352 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  194u      REG                9,1   8175372    4983072 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  195u      REG                9,1     66560    4983362 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  196u      REG                9,1     57940    4983364 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  197u      REG                9,1      2048    4983380 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  198u      REG                9,1       204    4983400 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  199u      REG                9,1     57344    4983410 /var/lib/mysql/folder/mysql_table.MYI
mysqld      908       mysql  200u      REG                9,1     55560    4983411 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  201u      REG                9,1     63973    4982022 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  202u      REG                9,1    103628    4983091 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  203u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  205u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  206u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  207u      REG                9,1     32804    4982476 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  208u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  209u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  210u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  211u      REG                9,1    152516    4983318 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  212u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  213u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  214r      REG                9,1    152516    4983318 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  215u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  216u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  217u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  218u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  219u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  220u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  221u      REG                9,1     32804    4982476 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  222u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  223u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  224u      REG                9,1     32804    4982476 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  225u      REG                9,1    152516    4983318 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  226u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  227u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  228u      REG                9,1   8175372    4983072 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  229u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  230u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  231u      REG                9,1   8175372    4983072 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  232u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  233u      REG                9,1   8175372    4983072 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  234u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  235u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  236u      REG                9,1 186304482    4983355 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  238u      REG                9,1     63973    4982022 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  239u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  240u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  241u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  242u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  243u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  244u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  245u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  246u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  247u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  248u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  249u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  250u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  251u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  252u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  253u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  254u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  255u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  256u      REG                9,1     57940    4983364 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  257u      REG                9,1     63973    4982022 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  258u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  259u      REG                9,1    122268    4983294 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  260u      REG                9,1   8175372    4983072 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  261u      REG                9,1    103628    4983091 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  262u      REG                9,1   6157100    4980876 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  263u      REG                9,1     32966    4981755 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  264u      REG                9,1      2380    4981763 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  265u      REG                9,1    237668    4982027 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  266u      REG                9,1     34376    4982116 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  267u      REG                9,1     72340    4983106 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  268u      REG                9,1      9639    4982373 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  269u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  270u      REG                9,1      5012    4982657 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  271u      REG                9,1        40    4982789 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  272u      REG                9,1    152516    4983318 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  274u      REG                9,1   2022576    4982816 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  275u      REG                9,1   1251548    4982861 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  276u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  277u      REG                9,1    241605    4982948 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  278u      REG                9,1    103628    4983091 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  279u      REG                9,1    300320    4983009 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  280u      REG                9,1    500712    4983032 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  281u      REG                9,1   1957312    4983079 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  282u      REG                9,1         0    4983085 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  283u      REG                9,1      1832    4983088 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  284u      REG                9,1    440260    4983103 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  285u      REG                9,1       469    4983109 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  286u      REG                9,1     29968    4983112 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  287u      REG                9,1     31717    4983115 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  290u      REG                9,1     52748    4983118 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  291u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  292u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  293u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  294u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  295u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  296u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  297u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  298u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  299u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  300u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  301u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  302u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  303u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  304u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  305u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  306u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  307u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  308u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  309u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  310u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  311u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  312u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  313u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  314u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  315u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  317u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  318u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  319u      REG                9,1     19920    4983121 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  320u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  321u      REG                9,1    103628    4983091 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  322u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  323u      REG                9,1     17732    4983124 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  324u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  325u      REG                9,1   1633868    4983127 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  326u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  327u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  328u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  329u      REG                9,1   1410696    4983130 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  330u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  331u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  332u      REG                9,1   1661368    4983133 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  334u      REG                9,1   4371012    4983188 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  335u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  336u      REG                9,1       154    4983196 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  338u      REG                9,1     13872    4983201 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  339u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  340u      REG                9,1  23663982    4983210 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  341u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  342u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  343u      REG                9,1        84    4983213 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  344u      REG                9,1 186304482    4983355 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  345u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  346u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  347u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  348u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  349u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  350u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  351u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  352u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  353u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  354u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  355u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  356u      REG                9,1  31528743    4984113 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  357u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  358u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  359u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  360u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  361u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  362u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  363u      REG                9,1 186304482    4983355 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  364u      REG                9,1   1972620    4983216 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  365u      REG                9,1      6840    4983219 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  366u      REG                9,1   8175372    4983072 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  367u      REG                9,1      1184    4983223 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  368u      REG                9,1    354532    4983226 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  369u      REG                9,1    162904    4983231 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  370u      REG                9,1       260    4983234 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  371u      REG                9,1      2000    4983237 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  372u      REG                9,1 186304482    4983355 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  373u      REG                9,1     34080    4983240 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  374u      REG                9,1       340    4983244 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  375u      REG                9,1 186304482    4983355 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  376u      REG                9,1      4840    4983248 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  377u      REG                9,1      3400    4983251 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  378u      REG                9,1       160    4983256 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  379u      REG                9,1       105    4983260 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  380u      REG                9,1       767    4983264 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  381u      REG                9,1        20    4983270 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  385u      REG                9,1       244    4983273 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  386u      REG                9,1      1960    4983310 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  387u      REG                9,1     24484    4983342 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  388u      REG                9,1       204    4983400 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  390u      REG                9,1     55560    4983411 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  391u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  392u      REG                9,1    103628    4983091 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  394u      REG                9,1    103628    4983091 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  396u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  398u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  402u      REG                9,1    103628    4983091 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  403u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  404u      REG                9,1     32804    4982476 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  407u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  408u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  409u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  410u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  411u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  412u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  413u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  414u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  415u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  416u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  417u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  418u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  419u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  420u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  421u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  422u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  423u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  424u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  425u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  428u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  430u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  432u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  443u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  444u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  445u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  446u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  447u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  448u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  449u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  450u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  451u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  452u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  453u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  454u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  455u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  457u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  458u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  459u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  460u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  461u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  462u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  463u      REG                9,1     27272    4982353 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  466u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  467u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  468u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  469u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  470u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  471u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  472u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  473u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  474u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  475u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  476u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  477u      REG                9,1   7770660    4983163 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  478u      REG                9,1       208    4983159 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  479u      REG                9,1  10644760    4983156 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  480u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  481u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  482u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  485u      REG                9,1    237668    4982027 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  486u      REG                9,1       580    4982646 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  488u      REG                9,1    237668    4982027 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  489u      REG                9,1       580    4982646 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  490u      REG                9,1    237668    4982027 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  491u      REG                9,1    237668    4982027 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  492u      REG                9,1       580    4982646 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  493u      REG                9,1    237668    4982027 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  494u      REG                9,1    237668    4982027 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  495u      REG                9,1    237668    4982027 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  496u      REG                9,1       580    4982646 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  497u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  498u      REG                9,1    237668    4982027 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  499u      REG                9,1       580    4982646 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  500u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  501u      REG                9,1    237668    4982027 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  502u      REG                9,1    683768    4982586 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  503u      REG                9,1    237668    4982027 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  505u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  506u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  512u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  546u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  547u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  548u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  549u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  550u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  551u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  552u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  553u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  554u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  555u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  556u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  557u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  558u      REG                9,1       100    4983094 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  559u      REG                9,1      9192    4983100 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  560u      REG                9,1       320    4983097 /var/lib/mysql/folder/mysql_table.MYD
mysqld      908       mysql  561u      REG                9,1  21074832    4982379 /var/lib/mysql/folder/mysql_table.MYD
irqbalanc   961        root  cwd       DIR                9,1      4096          2 /
irqbalanc   961        root  rtd       DIR                9,1      4096          2 /
irqbalanc   961        root  txt       REG                9,1     27096    7348633 /usr/sbin/irqbalance
irqbalanc   961        root  DEL       REG                9,1              6164161 /lib/x86_64-linux-gnu/librt-2.15.so
irqbalanc   961        root  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
irqbalanc   961        root  mem       REG                9,1    247896    6160471 /lib/x86_64-linux-gnu/libpcre.so.3.12.1
irqbalanc   961        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
irqbalanc   961        root  mem       REG                9,1   1000472    6160411 /lib/x86_64-linux-gnu/libglib-2.0.so.0.3200.4
irqbalanc   961        root  mem       REG                9,1     18304    7348630 /usr/lib/libcap-ng.so.0.0.0
irqbalanc   961        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
irqbalanc   961        root    0u      CHR                1,3       0t0       5800 /dev/null
irqbalanc   961        root    1u      CHR                1,3       0t0       5800 /dev/null
irqbalanc   961        root    2u      CHR                1,3       0t0       5800 /dev/null
flush-9:1   971        root  cwd       DIR                9,1      4096          2 /
flush-9:1   971        root  rtd       DIR                9,1      4096          2 /
flush-9:1   971        root  txt   unknown                                         /proc/971/exe
whoopsie   1229    whoopsie  cwd       DIR                9,1      4096          2 /
whoopsie   1229    whoopsie  rtd       DIR                9,1      4096          2 /
whoopsie   1229    whoopsie  txt       REG                9,1     44480    7340752 /usr/bin/whoopsie
whoopsie   1229    whoopsie  DEL       REG                9,1              6164160 /lib/x86_64-linux-gnu/libnss_dns-2.15.so
whoopsie   1229    whoopsie  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
whoopsie   1229    whoopsie  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
whoopsie   1229    whoopsie  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
whoopsie   1229    whoopsie  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
whoopsie   1229    whoopsie  DEL       REG                9,1              6160492 /lib/x86_64-linux-gnu/libcrypt-2.15.so
whoopsie   1229    whoopsie  mem       REG                9,1    664504    7345121 /usr/lib/x86_64-linux-gnu/libsqlite3.so.0.8.6
whoopsie   1229    whoopsie  mem       REG                9,1    300704    7346028 /usr/lib/x86_64-linux-gnu/libhx509.so.5.0.0
whoopsie   1229    whoopsie  mem       REG                9,1     61264    7346015 /usr/lib/x86_64-linux-gnu/libheimbase.so.1.0.0
whoopsie   1229    whoopsie  mem       REG                9,1    166096    7346025 /usr/lib/x86_64-linux-gnu/libwind.so.0.0.0
whoopsie   1229    whoopsie  mem       REG                9,1     14360    6160694 /lib/x86_64-linux-gnu/libkeyutils.so.1.4
whoopsie   1229    whoopsie  mem       REG                9,1     72752    7348194 /usr/lib/x86_64-linux-gnu/libp11-kit.so.0.0.0
whoopsie   1229    whoopsie  mem       REG                9,1     67864    7340996 /usr/lib/x86_64-linux-gnu/libtasn1.so.3.1.12
whoopsie   1229    whoopsie  mem       REG                9,1     86024    7346003 /usr/lib/x86_64-linux-gnu/libroken.so.18.1.0
whoopsie   1229    whoopsie  mem       REG                9,1    209184    7346009 /usr/lib/x86_64-linux-gnu/libhcrypto.so.4.1.0
whoopsie   1229    whoopsie  mem       REG                9,1    655152    7346006 /usr/lib/x86_64-linux-gnu/libasn1.so.8.0.0
whoopsie   1229    whoopsie  mem       REG                9,1    547488    7346031 /usr/lib/x86_64-linux-gnu/libkrb5.so.26.0.0
whoopsie   1229    whoopsie  mem       REG                9,1     27624    7346034 /usr/lib/x86_64-linux-gnu/libheimntlm.so.0.1.0
whoopsie   1229    whoopsie  mem       REG                9,1     31200    7341700 /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
whoopsie   1229    whoopsie  mem       REG                9,1     14696    6160396 /lib/x86_64-linux-gnu/libcom_err.so.2.1
whoopsie   1229    whoopsie  mem       REG                9,1    158168    7340880 /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
whoopsie   1229    whoopsie  mem       REG                9,1    844648    7340884 /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
whoopsie   1229    whoopsie  mem       REG                9,1    766856    7340264 /usr/lib/x86_64-linux-gnu/libgnutls.so.26.21.8
whoopsie   1229    whoopsie  mem       REG                9,1    252312    7346037 /usr/lib/x86_64-linux-gnu/libgssapi.so.3.0.0
whoopsie   1229    whoopsie  mem       REG                9,1    109288    7348234 /usr/lib/x86_64-linux-gnu/libsasl2.so.2.0.25
whoopsie   1229    whoopsie  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
whoopsie   1229    whoopsie  mem       REG                9,1     14352    6160689 /lib/x86_64-linux-gnu/libgpg-error.so.0.8.0
whoopsie   1229    whoopsie  mem       REG                9,1    105656    7348243 /usr/lib/x86_64-linux-gnu/librtmp.so.0
whoopsie   1229    whoopsie  mem       REG                9,1   1930616    6160426 /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
whoopsie   1229    whoopsie  mem       REG                9,1    383024    6160493 /lib/x86_64-linux-gnu/libssl.so.1.0.0
whoopsie   1229    whoopsie  mem       REG                9,1    252720    7340882 /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
whoopsie   1229    whoopsie  mem       REG                9,1    314936    7343975 /usr/lib/x86_64-linux-gnu/libldap_r-2.4.so.2.8.1
whoopsie   1229    whoopsie  mem       REG                9,1     55528    7345571 /usr/lib/x86_64-linux-gnu/liblber-2.4.so.2.8.1
whoopsie   1229    whoopsie  mem       REG                9,1    207312    7348211 /usr/lib/x86_64-linux-gnu/libidn.so.11.6.6
whoopsie   1229    whoopsie  DEL       REG                9,1              6164161 /lib/x86_64-linux-gnu/librt-2.15.so
whoopsie   1229    whoopsie  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
whoopsie   1229    whoopsie  mem       REG                9,1    247896    6160471 /lib/x86_64-linux-gnu/libpcre.so.3.12.1
whoopsie   1229    whoopsie  mem       REG                9,1     30896    7341472 /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
whoopsie   1229    whoopsie  DEL       REG                9,1              6164159 /lib/x86_64-linux-gnu/libresolv-2.15.so
whoopsie   1229    whoopsie  mem       REG                9,1    121936    6160447 /lib/x86_64-linux-gnu/libselinux.so.1
whoopsie   1229    whoopsie  mem       REG                9,1     92720    6160612 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
whoopsie   1229    whoopsie  mem       REG                9,1     14528    7342102 /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3200.4
whoopsie   1229    whoopsie  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
whoopsie   1229    whoopsie  mem       REG                9,1    520152    6160403 /lib/x86_64-linux-gnu/libgcrypt.so.11.7.0
whoopsie   1229    whoopsie  mem       REG                9,1    381512    7340057 /usr/lib/x86_64-linux-gnu/libcurl.so.4.2.0
whoopsie   1229    whoopsie  mem       REG                9,1   1000472    6160411 /lib/x86_64-linux-gnu/libglib-2.0.so.0.3200.4
whoopsie   1229    whoopsie  mem       REG                9,1    322648    7342108 /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3200.4
whoopsie   1229    whoopsie  mem       REG                9,1   1364896    7342107 /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.3200.4
whoopsie   1229    whoopsie  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
whoopsie   1229    whoopsie  DEL       REG                9,1              7349412 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
whoopsie   1229    whoopsie    0u      CHR                1,3       0t0       5800 /dev/null
whoopsie   1229    whoopsie    1u      CHR                1,3       0t0       5800 /dev/null
whoopsie   1229    whoopsie    2u      CHR                1,3       0t0       5800 /dev/null
whoopsie   1229    whoopsie    3r     0000                0,9         0       5775 anon_inode
whoopsie   1229    whoopsie    4u     0000                0,9         0       5775 anon_inode
whoopsie   1229    whoopsie    5u     sock                0,7       0t0       8976 can't identify protocol
whoopsie   1229    whoopsie    6u     unix 0xffff880124fdb740       0t0       9355 socket
whoopsie   1229    whoopsie    7u     0000                0,9         0       5775 anon_inode
whoopsie   1229    whoopsie    8u     0000                0,9         0       5775 anon_inode
exim4      1230 Debian-exim  cwd       DIR                9,1      4096    4983768 /var/spool/exim4
exim4      1230 Debian-exim  rtd       DIR                9,1      4096          2 /
exim4      1230 Debian-exim  txt       REG                9,1    940632    7347970 /usr/sbin/exim4
exim4      1230 Debian-exim  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
exim4      1230 Debian-exim  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
exim4      1230 Debian-exim  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
exim4      1230 Debian-exim  mem       REG                9,1     14352    6160689 /lib/x86_64-linux-gnu/libgpg-error.so.0.8.0
exim4      1230 Debian-exim  mem       REG                9,1     72752    7348194 /usr/lib/x86_64-linux-gnu/libp11-kit.so.0.0.0
exim4      1230 Debian-exim  mem       REG                9,1     92720    6160612 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
exim4      1230 Debian-exim  mem       REG                9,1    520152    6160403 /lib/x86_64-linux-gnu/libgcrypt.so.11.7.0
exim4      1230 Debian-exim  mem       REG                9,1     67864    7340996 /usr/lib/x86_64-linux-gnu/libtasn1.so.3.1.12
exim4      1230 Debian-exim  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
exim4      1230 Debian-exim  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
exim4      1230 Debian-exim  mem       REG                9,1    247896    6160471 /lib/x86_64-linux-gnu/libpcre.so.3.12.1
exim4      1230 Debian-exim  mem       REG                9,1    766856    7340264 /usr/lib/x86_64-linux-gnu/libgnutls.so.26.21.8
exim4      1230 Debian-exim  mem       REG                9,1   1518928    7340260 /usr/lib/x86_64-linux-gnu/libdb-5.1.so
exim4      1230 Debian-exim  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
exim4      1230 Debian-exim  DEL       REG                9,1              6164167 /lib/x86_64-linux-gnu/libm-2.15.so
exim4      1230 Debian-exim  DEL       REG                9,1              6160492 /lib/x86_64-linux-gnu/libcrypt-2.15.so
exim4      1230 Debian-exim  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
exim4      1230 Debian-exim  DEL       REG                9,1              6164159 /lib/x86_64-linux-gnu/libresolv-2.15.so
exim4      1230 Debian-exim  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
exim4      1230 Debian-exim    0u      CHR                1,3       0t0       5800 /dev/null
exim4      1230 Debian-exim    1u      CHR                1,3       0t0       5800 /dev/null
exim4      1230 Debian-exim    2u      CHR                1,3       0t0       5800 /dev/null
exim4      1230 Debian-exim    3u     IPv4               8969       0t0        TCP localhost:smtp (LISTEN)
mdadm      1264        root  cwd       DIR                9,1      4096          2 /
mdadm      1264        root  rtd       DIR                9,1      4096          2 /
mdadm      1264        root  txt       REG                9,1    462496    1310748 /sbin/mdadm
mdadm      1264        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
mdadm      1264        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
mdadm      1264        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
mdadm      1264        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
mdadm      1264        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
mdadm      1264        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
mdadm      1264        root    0u      CHR                1,3       0t0       5800 /dev/null
mdadm      1264        root    1u      CHR                1,3       0t0       5800 /dev/null
mdadm      1264        root    2u      CHR                1,3       0t0       5800 /dev/null
mdadm      1264        root    4r      REG                0,3         0 4026531970 /proc/mdstat
getty      1646        root  cwd       DIR                9,1      4096          2 /
getty      1646        root  rtd       DIR                9,1      4096          2 /
getty      1646        root  txt       REG                9,1     32048    1310766 /sbin/getty
getty      1646        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
getty      1646        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
getty      1646        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
getty      1646        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
getty      1646        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
getty      1646        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
getty      1646        root  DEL       REG                9,1              7349412 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
getty      1646        root  DEL       REG                9,1              7344434 /usr/lib/locale/C.UTF-8/LC_CTYPE
getty      1646        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
getty      1646        root    0u      CHR                4,1       0t0       5815 /dev/tty1
getty      1646        root    1u      CHR                4,1       0t0       5815 /dev/tty1
getty      1646        root    2u      CHR                4,1       0t0       5815 /dev/tty1
dpkg       1795        root  cwd       DIR                9,1      4096          2 /
dpkg       1795        root  rtd       DIR                9,1      4096          2 /
dpkg       1795        root  txt       REG                9,1    253424    7342118 /usr/bin/dpkg
dpkg       1795        root  mem       REG                9,1     14768    6164182 /lib/x86_64-linux-gnu/libdl-2.15.so
dpkg       1795        root  mem       REG                9,1   1811128    6164140 /lib/x86_64-linux-gnu/libc-2.15.so
dpkg       1795        root  mem       REG                9,1    121936    6160447 /lib/x86_64-linux-gnu/libselinux.so.1
dpkg       1795        root  mem       REG                9,1    149280    6160432 /lib/x86_64-linux-gnu/ld-2.15.so
dpkg       1795        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
dpkg       1795        root    0u      CHR              136,2       0t0          5 /dev/pts/2
dpkg       1795        root    1u      CHR              136,2       0t0          5 /dev/pts/2
dpkg       1795        root    2u      CHR              136,2       0t0          5 /dev/pts/2
dpkg       1795        root    3uW     REG                9,1         0    4980928 /var/lib/dpkg/lock
dpkg       1795        root    4w      REG                9,1      4608    4981796 /var/lib/dpkg/updates/tmp.i
dpkg       1795        root    5u      REG                9,1         0    4980931 /var/lib/dpkg/triggers/Lock
dpkg       1795        root    6w      REG                9,1      8796    4981369 /var/log/dpkg.log
dpkg       1795        root    8r      REG                9,1       268    4981126 /var/lib/dpkg/diversions
dpkg       1795        root   57w     FIFO                0,8       0t0    2900509 pipe
upstart-u  1834        root  cwd       DIR                9,1      4096          2 /
upstart-u  1834        root  rtd       DIR                9,1      4096          2 /
upstart-u  1834        root  txt       REG                9,1     51424    1310794 /sbin/upstart-udev-bridge
upstart-u  1834        root  mem       REG                9,1     31752    6160545 /lib/x86_64-linux-gnu/librt-2.15.so
upstart-u  1834        root  mem       REG                9,1   1811128    6164140 /lib/x86_64-linux-gnu/libc-2.15.so
upstart-u  1834        root  mem       REG                9,1     51080    6160673 /lib/x86_64-linux-gnu/libudev.so.0.13.0
upstart-u  1834        root  mem       REG                9,1    135366    6160487 /lib/x86_64-linux-gnu/libpthread-2.15.so
upstart-u  1834        root  mem       REG                9,1    276392    6160436 /lib/x86_64-linux-gnu/libdbus-1.so.3.5.8
upstart-u  1834        root  mem       REG                9,1     38888    6160476 /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
upstart-u  1834        root  mem       REG                9,1     96240    6160438 /lib/x86_64-linux-gnu/libnih.so.1.0.0
upstart-u  1834        root  mem       REG                9,1    149280    6160432 /lib/x86_64-linux-gnu/ld-2.15.so
upstart-u  1834        root    0u      CHR                1,3       0t0       5800 /dev/null
upstart-u  1834        root    1u      CHR                1,3       0t0       5800 /dev/null
upstart-u  1834        root    2u      CHR                1,3       0t0       5800 /dev/null
upstart-u  1834        root    3u     unix 0xffff8800c9ae8680       0t0    2900529 socket
upstart-u  1834        root    4r     FIFO                0,8       0t0    2900530 pipe
upstart-u  1834        root    5w     FIFO                0,8       0t0    2900530 pipe
upstart-u  1834        root    6u     sock                0,7       0t0    2900531 can't identify protocol
udevd      1836        root  cwd       DIR                9,1      4096          2 /
udevd      1836        root  rtd       DIR                9,1      4096          2 /
udevd      1836        root  txt       REG                9,1    137304    1310777 /sbin/udevd
udevd      1836        root  mem       REG                9,1     52120    6160691 /lib/x86_64-linux-gnu/libnss_files-2.15.so
udevd      1836        root  mem       REG                9,1     47680    6164153 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
udevd      1836        root  mem       REG                9,1     97248    6160553 /lib/x86_64-linux-gnu/libnsl-2.15.so
udevd      1836        root  mem       REG                9,1     35680    6164151 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
udevd      1836        root  mem       REG                9,1    135366    6160487 /lib/x86_64-linux-gnu/libpthread-2.15.so
udevd      1836        root  mem       REG                9,1     14768    6164182 /lib/x86_64-linux-gnu/libdl-2.15.so
udevd      1836        root  mem       REG                9,1   1811128    6164140 /lib/x86_64-linux-gnu/libc-2.15.so
udevd      1836        root  mem       REG                9,1     31752    6160545 /lib/x86_64-linux-gnu/librt-2.15.so
udevd      1836        root  mem       REG                9,1    121936    6160447 /lib/x86_64-linux-gnu/libselinux.so.1
udevd      1836        root  mem       REG                9,1    149280    6160432 /lib/x86_64-linux-gnu/ld-2.15.so
udevd      1836        root    0u      CHR                1,3       0t0       5800 /dev/null
udevd      1836        root    1u      CHR                1,3       0t0       5800 /dev/null
udevd      1836        root    2u      CHR                1,3       0t0       5800 /dev/null
udevd      1836        root    3u     unix 0xffff8800ac35da00       0t0    2899715 /run/udev/control
udevd      1836        root    4u     sock                0,7       0t0    2899716 can't identify protocol
udevd      1836        root    5u      REG               0,15         8    2899718 /run/udev/queue.bin
udevd      1836        root    6r     0000                0,9         0       5775 anon_inode
udevd      1836        root    7u     0000                0,9         0       5775 anon_inode
udevd      1836        root    8u     unix 0xffff8800c9ae9d40       0t0    2900564 socket
udevd      1836        root    9u     unix 0xffff8800c9ae89c0       0t0    2900565 socket
udevd      1836        root   10u     0000                0,9         0       5775 anon_inode
initramfs  1857        root  cwd       DIR                9,1      4096          2 /
initramfs  1857        root  rtd       DIR                9,1      4096          2 /
initramfs  1857        root  txt       REG                9,1    109768    4325384 /bin/dash
initramfs  1857        root  mem       REG                9,1   1811128    6164140 /lib/x86_64-linux-gnu/libc-2.15.so
initramfs  1857        root  mem       REG                9,1    149280    6160432 /lib/x86_64-linux-gnu/ld-2.15.so
initramfs  1857        root    0u      CHR              136,2       0t0          5 /dev/pts/2
initramfs  1857        root    1u      CHR              136,2       0t0          5 /dev/pts/2
initramfs  1857        root    2u      CHR              136,2       0t0          5 /dev/pts/2
initramfs  1857        root   10r      REG                9,1       394    5243223 /var/lib/dpkg/info/initramfs-tools.postinst
update-in  1858        root  cwd       DIR                9,1      4096          2 /
update-in  1858        root  rtd       DIR                9,1      4096          2 /
update-in  1858        root  txt       REG                9,1    109768    4325384 /bin/dash
update-in  1858        root  mem       REG                9,1   1811128    6164140 /lib/x86_64-linux-gnu/libc-2.15.so
update-in  1858        root  mem       REG                9,1    149280    6160432 /lib/x86_64-linux-gnu/ld-2.15.so
update-in  1858        root    0u      CHR              136,2       0t0          5 /dev/pts/2
update-in  1858        root    1w      REG                9,1         0    4981665 /var/lib/initramfs-tools/3.2.0-29-generic
update-in  1858        root    2u      CHR              136,2       0t0          5 /dev/pts/2
update-in  1858        root   10r      REG                9,1      9164    7342449 /usr/sbin/update-initramfs
update-in  1858        root   11u      CHR              136,2       0t0          5 /dev/pts/2
kworker/0  4028        root  cwd       DIR                9,1      4096          2 /
kworker/0  4028        root  rtd       DIR                9,1      4096          2 /
kworker/0  4028        root  txt   unknown                                         /proc/4028/exe
kworker/1  6724        root  cwd       DIR                9,1      4096          2 /
kworker/1  6724        root  rtd       DIR                9,1      4096          2 /
kworker/1  6724        root  txt   unknown                                         /proc/6724/exe
sha1sum    7223        root  cwd       DIR                9,1      4096          2 /
sha1sum    7223        root  rtd       DIR                9,1      4096          2 /
sha1sum    7223        root  txt       REG                9,1     39392    7342557 /usr/bin/sha1sum
sha1sum    7223        root  mem       REG                9,1   1811128    6164140 /lib/x86_64-linux-gnu/libc-2.15.so
sha1sum    7223        root  mem       REG                9,1    149280    6160432 /lib/x86_64-linux-gnu/ld-2.15.so
sha1sum    7223        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
sha1sum    7223        root    0u      CHR              136,2       0t0          5 /dev/pts/2
sha1sum    7223        root    1w      REG                9,1         0    4981665 /var/lib/initramfs-tools/3.2.0-29-generic
sha1sum    7223        root    2u      CHR              136,2       0t0          5 /dev/pts/2
sha1sum    7223        root    3r      REG                9,1  14597865    3145947 /boot/initrd.img-3.2.0-29-generic
sudo       7224        root  cwd       DIR                9,1      4096    9043970 /home/myacc
sudo       7224        root  rtd       DIR                9,1      4096          2 /
sudo       7224        root  txt       REG                9,1     71288    7342340 /usr/bin/sudo
sudo       7224        root  mem       REG                9,1     10304    6160776 /lib/x86_64-linux-gnu/security/pam_umask.so
sudo       7224        root  mem       REG                9,1      6040    6160758 /lib/x86_64-linux-gnu/security/pam_permit.so
sudo       7224        root  mem       REG                9,1      5944    6160459 /lib/x86_64-linux-gnu/security/pam_deny.so
sudo       7224        root  mem       REG                9,1    121936    6160447 /lib/x86_64-linux-gnu/libselinux.so.1
sudo       7224        root  mem       REG                9,1     43288    6160549 /lib/x86_64-linux-gnu/libcrypt-2.15.so
sudo       7224        root  mem       REG                9,1     56088    6160777 /lib/x86_64-linux-gnu/security/pam_unix.so
sudo       7224        root  mem       REG                9,1     14392    6160461 /lib/x86_64-linux-gnu/security/pam_env.so
sudo       7224        root  mem       REG                9,1    105288    6164145 /lib/x86_64-linux-gnu/libresolv-2.15.so
sudo       7224        root  mem       REG                9,1     31104    6164178 /lib/x86_64-linux-gnu/libnss_dns-2.15.so
sudo       7224        root  mem       REG                9,1     55744    6160467 /lib/x86_64-linux-gnu/libpam.so.0.83.0
sudo       7224        root  mem       REG                9,1    185288    7471263 /usr/lib/sudo/sudoers.so
sudo       7224        root  mem       REG                9,1     52120    6160691 /lib/x86_64-linux-gnu/libnss_files-2.15.so
sudo       7224        root  mem       REG                9,1     47680    6164153 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
sudo       7224        root  mem       REG                9,1     97248    6160553 /lib/x86_64-linux-gnu/libnsl-2.15.so
sudo       7224        root  mem       REG                9,1     35680    6164151 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
sudo       7224        root  mem       REG                9,1   1811128    6164140 /lib/x86_64-linux-gnu/libc-2.15.so
sudo       7224        root  mem       REG                9,1     14768    6164182 /lib/x86_64-linux-gnu/libdl-2.15.so
sudo       7224        root  mem       REG                9,1     10632    6164162 /lib/x86_64-linux-gnu/libutil-2.15.so
sudo       7224        root  mem       REG                9,1    149280    6160432 /lib/x86_64-linux-gnu/ld-2.15.so
sudo       7224        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
sudo       7224        root    0u      CHR              136,1       0t0          4 /dev/pts/1
sudo       7224        root    1u      CHR              136,1       0t0          4 /dev/pts/1
sudo       7224        root    2u      CHR              136,1       0t0          4 /dev/pts/1
sudo       7224        root    3u     unix 0xffff8800c9aeb740       0t0    2904209 socket
sudo       7224        root    5r     FIFO                0,8       0t0    2904211 pipe
sudo       7224        root    6w     FIFO                0,8       0t0    2904211 pipe
sudo       7224        root    7u     unix 0xffff8800c9aead80       0t0    2904212 socket
lsof       7225        root  cwd       DIR                9,1      4096    9043970 /home/myacc
lsof       7225        root  rtd       DIR                9,1      4096          2 /
lsof       7225        root  txt       REG                9,1    131312    7348637 /usr/bin/lsof
lsof       7225        root  mem       REG                9,1   1811128    6164140 /lib/x86_64-linux-gnu/libc-2.15.so
lsof       7225        root  mem       REG                9,1    149280    6160432 /lib/x86_64-linux-gnu/ld-2.15.so
lsof       7225        root  mem       REG                9,1     26258    7346211 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
lsof       7225        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
lsof       7225        root    0u      CHR              136,1       0t0          4 /dev/pts/1
lsof       7225        root    1u      CHR              136,1       0t0          4 /dev/pts/1
lsof       7225        root    2u      CHR              136,1       0t0          4 /dev/pts/1
lsof       7225        root    3r      DIR                0,3         0          1 /proc
lsof       7225        root    4u      DIR                0,3         0    2904214 /proc/7225/fd
lsof       7225        root    5w     FIFO                0,8       0t0    2904224 pipe
lsof       7225        root    6r     FIFO                0,8       0t0    2904225 pipe
lsof       7226        root  cwd       DIR                9,1      4096    9043970 /home/myacc
lsof       7226        root  rtd       DIR                9,1      4096          2 /
lsof       7226        root  txt       REG                9,1    131312    7348637 /usr/bin/lsof
lsof       7226        root  mem       REG                9,1   1811128    6164140 /lib/x86_64-linux-gnu/libc-2.15.so
lsof       7226        root  mem       REG                9,1    149280    6160432 /lib/x86_64-linux-gnu/ld-2.15.so
lsof       7226        root  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
lsof       7226        root    4r     FIFO                0,8       0t0    2904224 pipe
lsof       7226        root    7w     FIFO                0,8       0t0    2904225 pipe
kworker/0 23191        root  cwd       DIR                9,1      4096          2 /
kworker/0 23191        root  rtd       DIR                9,1      4096          2 /
kworker/0 23191        root  txt   unknown                                         /proc/23191/exe
sshd      32377        root  cwd       DIR                9,1      4096          2 /
sshd      32377        root  rtd       DIR                9,1      4096          2 /
sshd      32377        root  txt       REG                9,1    517112    7342405 /usr/sbin/sshd
sshd      32377        root  DEL       REG                0,4              2895465 /dev/zero
sshd      32377        root  mem       REG                9,1     14392    6160461 /lib/x86_64-linux-gnu/security/pam_env.so
sshd      32377        root  mem       REG                9,1     18704    6160745 /lib/x86_64-linux-gnu/security/pam_limits.so
sshd      32377        root  mem       REG                9,1     10240    6160751 /lib/x86_64-linux-gnu/security/pam_mail.so
sshd      32377        root  mem       REG                9,1     10272    6160754 /lib/x86_64-linux-gnu/security/pam_motd.so
sshd      32377        root  mem       REG                9,1     10208    6160460 /lib/x86_64-linux-gnu/security/pam_echo.so
sshd      32377        root  mem       REG                9,1     10304    6160776 /lib/x86_64-linux-gnu/security/pam_umask.so
sshd      32377        root  mem       REG                9,1      6104    6160757 /lib/x86_64-linux-gnu/security/pam_nologin.so
sshd      32377        root  mem       REG                9,1      6040    6160758 /lib/x86_64-linux-gnu/security/pam_permit.so
sshd      32377        root  mem       REG                9,1      5944    6160459 /lib/x86_64-linux-gnu/security/pam_deny.so
sshd      32377        root  mem       REG                9,1     56088    6160777 /lib/x86_64-linux-gnu/security/pam_unix.so
sshd      32377        root  DEL       REG                9,1              6164160 /lib/x86_64-linux-gnu/libnss_dns-2.15.so
sshd      32377        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
sshd      32377        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
sshd      32377        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
sshd      32377        root  DEL       REG                9,1              6164159 /lib/x86_64-linux-gnu/libresolv-2.15.so
sshd      32377        root  mem       REG                9,1     14360    6160694 /lib/x86_64-linux-gnu/libkeyutils.so.1.4
sshd      32377        root  mem       REG                9,1     31200    7341700 /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
sshd      32377        root  mem       REG                9,1    158168    7340880 /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
sshd      32377        root  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
sshd      32377        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
sshd      32377        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
sshd      32377        root  mem       REG                9,1     14696    6160396 /lib/x86_64-linux-gnu/libcom_err.so.2.1
sshd      32377        root  mem       REG                9,1    844648    7340884 /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
sshd      32377        root  mem       REG                9,1    252720    7340882 /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
sshd      32377        root  DEL       REG                9,1              6160492 /lib/x86_64-linux-gnu/libcrypt-2.15.so
sshd      32377        root  mem       REG                9,1     92720    6160612 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
sshd      32377        root  DEL       REG                9,1              6160392 /lib/x86_64-linux-gnu/libutil-2.15.so
sshd      32377        root  mem       REG                9,1   1930616    6160426 /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
sshd      32377        root  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
sshd      32377        root  mem       REG                9,1    121936    6160447 /lib/x86_64-linux-gnu/libselinux.so.1
sshd      32377        root  mem       REG                9,1     55744    6160467 /lib/x86_64-linux-gnu/libpam.so.0.83.0
sshd      32377        root  mem       REG                9,1     36432    6164116 /lib/x86_64-linux-gnu/libwrap.so.0.7.6
sshd      32377        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
sshd      32377        root  DEL       REG                0,4              2896638 /dev/zero
sshd      32377        root    0u      CHR                1,3       0t0       5800 /dev/null
sshd      32377        root    1u      CHR                1,3       0t0       5800 /dev/null
sshd      32377        root    2u      CHR                1,3       0t0       5800 /dev/null
sshd      32377        root    3r     IPv4            2896619       0t0        TCP mydomain.com:22->mail.mydomain.com:52155 (ESTABLISHED)
sshd      32377        root    4w     unix 0xffff8800c9ae9380       0t0    2895466 socket
sshd      32377        root    5u      CHR                5,2       0t0       5897 /dev/ptmx
sshd      32377        root    6u     unix 0xffff8800c9ae8d00       0t0    2895582 socket
sshd      32558       myacc  cwd       DIR                9,1      4096          2 /
sshd      32558       myacc  rtd       DIR                9,1      4096          2 /
sshd      32558       myacc  txt       REG                9,1    517112    7342405 /usr/sbin/sshd
sshd      32558       myacc  DEL       REG                0,4              2895465 /dev/zero
sshd      32558       myacc  mem       REG                9,1     14392    6160461 /lib/x86_64-linux-gnu/security/pam_env.so
sshd      32558       myacc  mem       REG                9,1     18704    6160745 /lib/x86_64-linux-gnu/security/pam_limits.so
sshd      32558       myacc  mem       REG                9,1     10240    6160751 /lib/x86_64-linux-gnu/security/pam_mail.so
sshd      32558       myacc  mem       REG                9,1     10272    6160754 /lib/x86_64-linux-gnu/security/pam_motd.so
sshd      32558       myacc  mem       REG                9,1     10208    6160460 /lib/x86_64-linux-gnu/security/pam_echo.so
sshd      32558       myacc  mem       REG                9,1     10304    6160776 /lib/x86_64-linux-gnu/security/pam_umask.so
sshd      32558       myacc  mem       REG                9,1      6104    6160757 /lib/x86_64-linux-gnu/security/pam_nologin.so
sshd      32558       myacc  mem       REG                9,1      6040    6160758 /lib/x86_64-linux-gnu/security/pam_permit.so
sshd      32558       myacc  mem       REG                9,1      5944    6160459 /lib/x86_64-linux-gnu/security/pam_deny.so
sshd      32558       myacc  mem       REG                9,1     56088    6160777 /lib/x86_64-linux-gnu/security/pam_unix.so
sshd      32558       myacc  DEL       REG                9,1              6164160 /lib/x86_64-linux-gnu/libnss_dns-2.15.so
sshd      32558       myacc  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
sshd      32558       myacc  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
sshd      32558       myacc  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
sshd      32558       myacc  DEL       REG                9,1              6164159 /lib/x86_64-linux-gnu/libresolv-2.15.so
sshd      32558       myacc  mem       REG                9,1     14360    6160694 /lib/x86_64-linux-gnu/libkeyutils.so.1.4
sshd      32558       myacc  mem       REG                9,1     31200    7341700 /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
sshd      32558       myacc  mem       REG                9,1    158168    7340880 /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
sshd      32558       myacc  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
sshd      32558       myacc  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
sshd      32558       myacc  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
sshd      32558       myacc  mem       REG                9,1     14696    6160396 /lib/x86_64-linux-gnu/libcom_err.so.2.1
sshd      32558       myacc  mem       REG                9,1    844648    7340884 /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
sshd      32558       myacc  mem       REG                9,1    252720    7340882 /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
sshd      32558       myacc  DEL       REG                9,1              6160492 /lib/x86_64-linux-gnu/libcrypt-2.15.so
sshd      32558       myacc  mem       REG                9,1     92720    6160612 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
sshd      32558       myacc  DEL       REG                9,1              6160392 /lib/x86_64-linux-gnu/libutil-2.15.so
sshd      32558       myacc  mem       REG                9,1   1930616    6160426 /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
sshd      32558       myacc  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
sshd      32558       myacc  mem       REG                9,1    121936    6160447 /lib/x86_64-linux-gnu/libselinux.so.1
sshd      32558       myacc  mem       REG                9,1     55744    6160467 /lib/x86_64-linux-gnu/libpam.so.0.83.0
sshd      32558       myacc  mem       REG                9,1     36432    6164116 /lib/x86_64-linux-gnu/libwrap.so.0.7.6
sshd      32558       myacc  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
sshd      32558       myacc  DEL       REG                0,4              2896638 /dev/zero
sshd      32558       myacc    0u      CHR                1,3       0t0       5800 /dev/null
sshd      32558       myacc    1u      CHR                1,3       0t0       5800 /dev/null
sshd      32558       myacc    2u      CHR                1,3       0t0       5800 /dev/null
sshd      32558       myacc    3u     IPv4            2896619       0t0        TCP mydomain.com:22->mail.mydomain.com:52155 (ESTABLISHED)
sshd      32558       myacc    4u     unix 0xffff8800c9ae9380       0t0    2895466 socket
sshd      32558       myacc    5u     unix 0xffff8800c9aea080       0t0    2895581 socket
sshd      32558       myacc    6r     FIFO                0,8       0t0    2896789 pipe
sshd      32558       myacc    7w     FIFO                0,8       0t0    2896789 pipe
sshd      32558       myacc    8u      CHR                5,2       0t0       5897 /dev/ptmx
sshd      32558       myacc   10u      CHR                5,2       0t0       5897 /dev/ptmx
sshd      32558       myacc   11u      CHR                5,2       0t0       5897 /dev/ptmx
bash      32559       myacc  cwd       DIR                9,1      4096    9043970 /home/myacc
bash      32559       myacc  rtd       DIR                9,1      4096          2 /
bash      32559       myacc  txt       REG                9,1    959120    4325410 /bin/bash
bash      32559       myacc  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
bash      32559       myacc  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
bash      32559       myacc  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
bash      32559       myacc  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
bash      32559       myacc  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
bash      32559       myacc  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
bash      32559       myacc  mem       REG                9,1    159200    6160452 /lib/x86_64-linux-gnu/libtinfo.so.5.9
bash      32559       myacc  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
bash      32559       myacc  DEL       REG                9,1              7349412 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
bash      32559       myacc  mem       REG                9,1   1607664    7346668 /usr/lib/locale/locale-archive
bash      32559       myacc    0u      CHR              136,0       0t0          3 /dev/pts/0
bash      32559       myacc    1u      CHR              136,0       0t0          3 /dev/pts/0
bash      32559       myacc    2u      CHR              136,0       0t0          3 /dev/pts/0
bash      32559       myacc  255u      CHR              136,0       0t0          3 /dev/pts/0
sshd      32733        root  cwd       DIR                9,1      4096          2 /
sshd      32733        root  rtd       DIR                9,1      4096          2 /
sshd      32733        root  txt       REG                9,1    517112    7342405 /usr/sbin/sshd
sshd      32733        root  DEL       REG                0,4              2895813 /dev/zero
sshd      32733        root  mem       REG                9,1     14392    6160461 /lib/x86_64-linux-gnu/security/pam_env.so
sshd      32733        root  mem       REG                9,1     18704    6160745 /lib/x86_64-linux-gnu/security/pam_limits.so
sshd      32733        root  mem       REG                9,1     10240    6160751 /lib/x86_64-linux-gnu/security/pam_mail.so
sshd      32733        root  mem       REG                9,1     10272    6160754 /lib/x86_64-linux-gnu/security/pam_motd.so
sshd      32733        root  mem       REG                9,1     10208    6160460 /lib/x86_64-linux-gnu/security/pam_echo.so
sshd      32733        root  mem       REG                9,1     10304    6160776 /lib/x86_64-linux-gnu/security/pam_umask.so
sshd      32733        root  mem       REG                9,1      6104    6160757 /lib/x86_64-linux-gnu/security/pam_nologin.so
sshd      32733        root  mem       REG                9,1      6040    6160758 /lib/x86_64-linux-gnu/security/pam_permit.so
sshd      32733        root  mem       REG                9,1      5944    6160459 /lib/x86_64-linux-gnu/security/pam_deny.so
sshd      32733        root  mem       REG                9,1     56088    6160777 /lib/x86_64-linux-gnu/security/pam_unix.so
sshd      32733        root  DEL       REG                9,1              6164160 /lib/x86_64-linux-gnu/libnss_dns-2.15.so
sshd      32733        root  DEL       REG                9,1              6164157 /lib/x86_64-linux-gnu/libnss_files-2.15.so
sshd      32733        root  DEL       REG                9,1              6164163 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
sshd      32733        root  DEL       REG                9,1              6160556 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
sshd      32733        root  DEL       REG                9,1              6164159 /lib/x86_64-linux-gnu/libresolv-2.15.so
sshd      32733        root  mem       REG                9,1     14360    6160694 /lib/x86_64-linux-gnu/libkeyutils.so.1.4
sshd      32733        root  mem       REG                9,1     31200    7341700 /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
sshd      32733        root  mem       REG                9,1    158168    7340880 /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
sshd      32733        root  DEL       REG                9,1              6164172 /lib/x86_64-linux-gnu/libdl-2.15.so
sshd      32733        root  DEL       REG                9,1              6164179 /lib/x86_64-linux-gnu/libnsl-2.15.so
sshd      32733        root  DEL       REG                9,1              6160491 /lib/x86_64-linux-gnu/libc-2.15.so
sshd      32733        root  mem       REG                9,1     14696    6160396 /lib/x86_64-linux-gnu/libcom_err.so.2.1
sshd      32733        root  mem       REG                9,1    844648    7340884 /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
sshd      32733        root  mem       REG                9,1    252720    7340882 /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
sshd      32733        root  DEL       REG                9,1              6160492 /lib/x86_64-linux-gnu/libcrypt-2.15.so
sshd      32733        root  mem       REG                9,1     92720    6160612 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
sshd      32733        root  DEL       REG                9,1              6160392 /lib/x86_64-linux-gnu/libutil-2.15.so
sshd      32733        root  mem       REG                9,1   1930616    6160426 /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
sshd      32733        root  DEL       REG                9,1              6164164 /lib/x86_64-linux-gnu/libpthread-2.15.so
sshd      32733        root  mem       REG                9,1    121936    6160447 /lib/x86_64-linux-gnu/libselinux.so.1
sshd      32733        root  mem       REG                9,1     55744    6160467 /lib/x86_64-linux-gnu/libpam.so.0.83.0
sshd      32733        root  mem       REG                9,1     36432    6164116 /lib/x86_64-linux-gnu/libwrap.so.0.7.6
sshd      32733        root  DEL       REG                9,1              6164168 /lib/x86_64-linux-gnu/ld-2.15.so
sshd      32733        root  DEL       REG                0,4              2896960 /dev/zero
sshd      32733        root    0u      CHR                1,3       0t0       5800 /dev/null
sshd      32733        root    1u      CHR                1,3       0t0       5800 /dev/null
sshd      32733        root    2u      CHR                1,3       0t0       5800 /dev/null
sshd      32733        root    3r     IPv4            2896941       0t0        TCP mydomain.com:22->mail.mydomain.com:64852 (ESTABLISHED)
sshd      32733        root    4w     unix 0xffff8800c9ae9a00       0t0    2895814 socket
sshd      32733        root    5u      CHR                5,2       0t0       5897 /dev/ptmx
sshd      32733        root    6u     unix 0xffff8800c9aeb0c0       0t0    2897984 socket
kworker/1 32761        root  cwd       DIR                9,1      4096          2 /
kworker/1 32761        root  rtd       DIR                9,1      4096          2 /
kworker/1 32761        root  txt   unknown                                         /proc/32761/exe
```

---

### Post by tgalati4 on 2014-12-12
Just killing apache won't do it.  You have mysql and something called "whoopsie" running.  Try killing those and see if the speed improves.

---

### Post by ian-weisser on 2014-12-12
Whoopsie is Ubuntu's automatic crash uploader.
Whoopsie uploads Apport .crash reports to Canonical QA's 'daisy' system. See the results at [http://errors.ubuntu.com](http://errors.ubuntu.com)
It takes very few resources (it's little more than an inotify watch on /var/crash) unless it's reporting a crash.
If you discover Whoopsie consuming lots of resources, please file a bug report!

---

