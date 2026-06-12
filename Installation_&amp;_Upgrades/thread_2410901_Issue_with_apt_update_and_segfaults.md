---
title: "Issue with apt update and segfaults"
date: 2019-01-22
forum: Installation &amp; Upgrades
---

### Post by bautsche on 2019-01-22
I'm confused and google didn't enlighten, so here goes....
I got this error over night:
/etc/cron.daily/ubuntu-advantage-tools:
E: The package cache file is corrupted, it has the wrong hash

So I did a bit of digging and it suggested I had an issue with the files in /var/lib/apt/lists and to remove them and re-create them using apt update.
So:

```
root@nexon # ls -la
total 108
drwxr-xr-x  6 root root  4096 Jan 18 15:44 .
drwxr-xr-x 52 root root  4096 Nov 29 15:20 ..
-rw-r--r--  1 root root   227 Nov 29 18:37 cdroms.list
-rw-r--r--  1 root root   227 Nov 29 18:36 cdroms.list~
-rw-r--r--  1 root root     0 Jan 22 07:24 daily_lock
-rw-r--r--  1 root root 62729 Jan 18 15:44 extended_states
drwxr-xr-x  2 root root  4096 Nov 29 18:36 keyrings
drwxr-xr-x  4 root root 16384 Jan 22 07:53 lists
drwxr-xr-x  3 root root  4096 Nov 29 18:36 mirrors
drwxr-xr-x  2 root root  4096 Nov 30 11:19 periodic
root@nexon # mv lists lists.org
root@nexon # mkdir lists
root@nexon # ls -la
total 112
drwxr-xr-x  7 root root  4096 Jan 22 07:54 .
drwxr-xr-x 52 root root  4096 Nov 29 15:20 ..
-rw-r--r--  1 root root   227 Nov 29 18:37 cdroms.list
-rw-r--r--  1 root root   227 Nov 29 18:36 cdroms.list~
-rw-r--r--  1 root root     0 Jan 22 07:24 daily_lock
-rw-r--r--  1 root root 62729 Jan 18 15:44 extended_states
drwxr-xr-x  2 root root  4096 Nov 29 18:36 keyrings
drwxr-xr-x  2 root root  4096 Jan 22 07:54 lists
drwxr-xr-x  4 root root 16384 Jan 22 07:53 lists.org
drwxr-xr-x  3 root root  4096 Nov 29 18:36 mirrors
drwxr-xr-x  2 root root  4096 Nov 30 11:19 periodic
root@nexon # apt update
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease [242 kB]
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main i386 Packages [1,007 kB]
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages [242 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages [1,019 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 Packages [185 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main Translation-en [516 kB]  
Get:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main Translation-en_GB [432 kB]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main Translation-en [91.6 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security i386 Contents (deb) [9,542 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security amd64 Contents (deb) [14.4 MB]
Ign:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security i386 Contents (deb)   
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages [113 kB]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 Packages [110 kB]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe Translation-en [64.2 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse i386 Packages [1,608 B]
Get:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 Packages [1,444 B]
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse Translation-en [996 B]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security i386 Contents (deb) [9,542 kB]
Get:21 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic i386 Contents (deb) [38.8 MB]
Ign:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb)         
Get:22 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/restricted amd64 Packages [9,184 B]
Get:23 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/restricted i386 Packages [9,156 B]
Get:24 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/restricted Translation-en [3,584 B]
Get:25 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/restricted Translation-en_GB [2,072 B]
Get:26 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe i386 Packages [8,531 kB]
Get:27 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages [8,570 kB]
Get:28 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe Translation-en_GB [4,118 kB]
Get:29 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/universe Translation-en [4,941 kB]
Get:30 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/multiverse amd64 Packages [151 kB]
Get:31 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/multiverse i386 Packages [144 kB]
Get:32 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/multiverse Translation-en [108 kB]
Get:33 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/multiverse Translation-en_GB [82.1 kB]
Get:34 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [489 kB]
Get:35 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [423 kB]
Get:36 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/main Translation-en [182 kB]
Get:37 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates i386 Contents (deb) [14.2 MB]
Get:38 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates amd64 Contents (deb) [19.7 MB]
Get:39 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 Packages [6,992 B]
Get:40 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/restricted i386 Packages [6,928 B]
Get:41 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/restricted Translation-en [3,076 B]
Get:42 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [705 kB]
Get:43 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [713 kB]
Get:44 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [176 kB]
Get:45 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse i386 Packages [6,524 B]
Get:46 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 Packages [6,376 B]
Get:47 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates/multiverse Translation-en [3,356 B]
Get:48 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports i386 Contents (deb) [4,484 B]
Get:49 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports amd64 Contents (deb) [4,486 B]
Get:50 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 Packages [3,472 B]
Get:51 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe i386 Packages [3,472 B]
Get:52 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports/universe Translation-en [1,604 B]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Ign:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb)         
Err:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb)         
  gzread: Read error (-3: <fd:3>: incorrect data check)
Fetched 170 MB in 2min 12s (1,291 kB/s)                                        
Reading package lists... Done
E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/bionic/Contents-amd64](http://gb.archive.ubuntu.com/ubuntu/dists/bionic/Contents-amd64)  gzread: Read error (-3: <fd:3>: incorrect data check)
E: Some index files failed to download. They have been ignored, or old ones used instead.
root@nexon # apt update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease [242 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages [1,019 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main i386 Packages [1,007 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main Translation-en_GB [432 kB]
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main Translation-en [516 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Ign:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb)          
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Ign:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb)          
Err:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb)          
  gzread: Read error (-3: <fd:3>: incorrect data check)
Fetched 39.8 MB in 53s (751 kB/s)                                              
Reading package lists... Done
munmap_chunk(): invalid pointer
Abort(coredump)
root@nexon # apt update
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease [242 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages [1,019 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main i386 Packages [1,007 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main Translation-en [516 kB]
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic/main Translation-en_GB [432 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic amd64 Contents (deb) [39.5 MB]
Fetched 39.8 MB in 27s (1,449 kB/s)                                            
Memory fault(coredump).. 34%
root@nexon # apt update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
root@nexon # apt update
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package lists... Done                      
Memory fault(coredump)ee... 50%
root@nexon # apt update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Memory fault(coredump).. 34% 
root@nexon # apt update
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Memory fault(coredump).. 9%  
root@nexon # apt update
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package lists... Done                     
Memory fault(coredump)ee... 50%
root@nexon # apt update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
root@nexon # apt update
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package lists... Done                     
E: The package cache file is corrupted, it has the wrong hash
root@nexon # apt update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
corrupted size vs. prev_size 
Abort(coredump)
root@nexon # apt update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Memory fault(coredump).. 34%                       
root@nexon # apt update
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Memory fault(coredump).. 85% 
root@nexon # apt update
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package lists... Done                     
Memory fault(coredump)ee... 50%
root@nexon # 
```




Not exactly what one might call a consistent result.
Meanwhile in /var/log/syslog, it doesn't look good either:
```
Jan 22 07:58:04 nexon kernel: [230953.865601] traps: apport[8288] general protection ip:5a1cef sp:7ffdcbd5b7d0 error:0 in python3.6[400000+3b2000]
Jan 22 07:58:04 nexon kernel: [230953.865609] Process 8288(apport) has RLIMIT_CORE set to 1
Jan 22 07:58:04 nexon kernel: [230953.865609] Aborting core
Jan 22 07:58:52 nexon kernel: [231001.857560] apt[9354]: segfault at 7f1208a0cbe8 ip 00007f0da65b441a sp 00007ffcb6c905d8 error 4 in libapt-pkg.so.5.0.2[7f0da646a000+1b2000]
Jan 22 07:59:15 nexon kernel: [231025.031530] apt[12288]: segfault at 7f2253c80d40 ip 00007f21f8cb3ad1 sp 00007ffd03d20598 error 4 in libapt-pkg.so.5.0.2[7f21f8b69000+1b2000]
Jan 22 07:59:19 nexon kernel: [231028.081370] apt[12933]: segfault at 7f7e92395400 ip 00007f7d12b0a298 sp 00007fffb8713840 error 4 in libapt-pkg.so.5.0.2[7f7d129b9000+1b2000]
Jan 22 07:59:21 nexon kernel: [231030.274739] apt[13512]: segfault at 7f685a38c2a0 ip 00007f684923e298 sp 00007fff4c9ab9c0 error 4 in libapt-pkg.so.5.0.2[7f68490ed000+1b2000]
Jan 22 07:59:23 nexon kernel: [231032.929319] apt[13763]: segfault at 562143cbf648 ip 00007f410857ce32 sp 00007ffc90d1fbd0 error 4 in libapt-pkg.so.5.0.2[7f410846a000+1b2000]
Jan 22 07:59:47 nexon kernel: [231056.599072] apt[15989]: segfault at 7f83b5c062d9 ip 00007f7c752481af sp 00007ffe302519f0 error 4 in libapt-pkg.so.5.0.2[7f7c750f5000+1b2000]
Jan 22 07:59:50 nexon kernel: [231059.406738] apt[16247]: segfault at 7ff0b2528ff4 ip 00007fddbca6ce1b sp 00007fff1eb027a0 error 4 in libapt-pkg.so.5.0.2[7fddbc923000+1b2000]
Jan 22 07:59:53 nexon kernel: [231062.138225] apt[16773]: segfault at 7f41e709e4a4 ip 00007f308a23acd1 sp 00007ffe6c7222a0 error 4 in libapt-pkg.so.5.0.2[7f308a128000+1b2000]
```


Any great idea what's going on here?

I'm running 18.04.1:
root@nexon # lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic
root@nexon # 


I last did an upgrade a couple of days ago (without issue).

Any pointers greatly appreciated.

Thanks.
Eric

---

