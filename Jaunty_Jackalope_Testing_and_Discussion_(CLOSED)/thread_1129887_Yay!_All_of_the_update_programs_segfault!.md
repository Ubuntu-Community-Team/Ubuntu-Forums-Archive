---
title: "Yay! All of the update programs segfault!"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2009-04-19
Read next post for my solution. :)

Since an update last night all update/package management apps segfault:
$ tail /var/log/syslog:
```
Apr 19 11:23:36 penryn kernel: [ 2220.162661] update-manager[7896]: segfault at 29a9816a ip b7f395eb sp bfab672c error 4 in libc-2.9.so[b7ec2000+15c000]
Apr 19 11:25:37 penryn kernel: [ 2341.312560] apt-get[8102]: segfault at 2bdba16a ip b7c5d5eb sp bff6906c error 4 in libc-2.9.so[b7be6000+15c000]
Apr 19 11:27:16 penryn kernel: [ 2440.380537] aptitude[8163]: segfault at 2bc4b16a ip b7af75eb sp bfcfb17c error 4 in libc-2.9.so[b7a80000+15c000]
Apr 19 11:29:20 penryn kernel: [ 2564.192061] synaptic[8217]: segfault at 2a49116a ip b70c15eb sp bff4dccc error 4 in libc-2.9.so[b704a000+15c000]
```This has been brought up before and was fixed by an update installed from the CLI - trouble is, I can't install any updates! All I need to know is what has been updated so I can roll back (or forward). The last set of updates that completed successfully (from /var/log/dpkg.log): ```
2009-04-19 01:45:16 startup archives unpack
2009-04-19 01:45:51 upgrade update-manager 1:0.111.6 1:0.111.7
2009-04-19 01:45:51 status half-configured update-manager 1:0.111.6
2009-04-19 01:46:01 status unpacked update-manager 1:0.111.6
2009-04-19 01:46:01 status half-installed update-manager 1:0.111.6
2009-04-19 01:46:01 status triggers-pending man-db 2.5.5-1build1
2009-04-19 01:46:01 status half-installed update-manager 1:0.111.6
2009-04-19 01:46:01 status half-installed update-manager 1:0.111.6
2009-04-19 01:46:13 status unpacked update-manager 1:0.111.7
2009-04-19 01:46:13 status unpacked update-manager 1:0.111.7
2009-04-19 01:46:13 upgrade update-manager-core 1:0.111.6 1:0.111.7
2009-04-19 01:46:13 status half-configured update-manager-core 1:0.111.6
2009-04-19 01:46:13 status unpacked update-manager-core 1:0.111.6
2009-04-19 01:46:14 status half-installed update-manager-core 1:0.111.6
2009-04-19 01:46:14 status half-installed update-manager-core 1:0.111.6
2009-04-19 01:46:14 status unpacked update-manager-core 1:0.111.7
2009-04-19 01:46:14 status unpacked update-manager-core 1:0.111.7
2009-04-19 01:46:15 upgrade notify-osd 0.9.11-0ubuntu2 0.9.11-0ubuntu3
2009-04-19 01:46:15 status half-configured notify-osd 0.9.11-0ubuntu2
2009-04-19 01:46:15 status unpacked notify-osd 0.9.11-0ubuntu2
2009-04-19 01:46:15 status half-installed notify-osd 0.9.11-0ubuntu2
2009-04-19 01:46:15 status half-installed notify-osd 0.9.11-0ubuntu2
2009-04-19 01:46:15 status unpacked notify-osd 0.9.11-0ubuntu3
2009-04-19 01:46:15 status unpacked notify-osd 0.9.11-0ubuntu3
2009-04-19 01:46:15 trigproc man-db 2.5.5-1build1 2.5.5-1build1
2009-04-19 01:46:15 status half-configured man-db 2.5.5-1build1
2009-04-19 01:46:17 status installed man-db 2.5.5-1build1
2009-04-19 01:46:18 startup packages configure
2009-04-19 01:46:18 configure update-manager-core 1:0.111.7 1:0.111.7
2009-04-19 01:46:18 status unpacked update-manager-core 1:0.111.7
2009-04-19 01:46:18 status unpacked update-manager-core 1:0.111.7
2009-04-19 01:46:18 status unpacked update-manager-core 1:0.111.7
2009-04-19 01:46:18 status half-configured update-manager-core 1:0.111.7
2009-04-19 01:46:21 status installed update-manager-core 1:0.111.7
2009-04-19 01:46:21 configure update-manager 1:0.111.7 1:0.111.7
2009-04-19 01:46:21 status unpacked update-manager 1:0.111.7
2009-04-19 01:46:21 status half-configured update-manager 1:0.111.7
2009-04-19 01:46:25 status installed update-manager 1:0.111.7
2009-04-19 01:46:25 configure notify-osd 0.9.11-0ubuntu3 0.9.11-0ubuntu3
2009-04-19 01:46:25 status unpacked notify-osd 0.9.11-0ubuntu3
2009-04-19 01:46:25 status half-configured notify-osd 0.9.11-0ubuntu3
2009-04-19 01:46:25 status installed notify-osd 0.9.11-0ubuntu3
```I've already tried installing update-manager and update-manager-core 0.111.6 from /var/cache/apt/archives (thankfully I don't run 'aptitude clean' as often as I used to) and that doesn't seem to make any difference (at least, everything still segfaults). Looking at packages.ubuntu.com 0.111.7 is the latest version so no changes have been yet to those packages - maybe it's not update-manager that is at fault?

Oh, just thought, I should probably try rebooting with 2.6.28-11 rather than 2.6.29.1 just to narrow it down (though I don't see how it would make much difference ;))

--edit
Tried downloading and installing aptitude and menu .debs from packages.ubuntu.com - no difference.

--edit 2
Tried running just $ aptitude :
```
Ouch!  Got SIGSEGV, dying..
Segmentation fault
```Seen this in other posts during searches. Not one solution. Time to try an fsck.

---

### Post by jfernyhough on 2009-04-19
No change after an fsck -fy ... this is looking increasingly like a reinstallation job.

--edit
$ sudo apt-get update works fine... $ sudo apt-get install or upgrade both immediately segfault.

So somewhere in between there's an answer...

--edit 2
$ sudo apt-get check -o dir::cache=/tmp works, $ sudo apt-get check does not. Hence there is something wrong with the cache and/or cache directory.

--edit 3
Well, there you go. Moving /var/cache/apt and recreating /var/cache/apt, /var/cache/apt/archives, /var/cache/apt/archives/partial lets everything work as normal.

---

### Post by olskar on 2009-04-19
```
cd /var/cache/apt
rm pkgcache.bin srcpkgcache.bin

```

Does that do anything good?

Edit: Ah, I was a bit late ;)

---

### Post by jfernyhough on 2009-04-19
Better late than never. :D And yes, that would have been the easy way. :P

---

