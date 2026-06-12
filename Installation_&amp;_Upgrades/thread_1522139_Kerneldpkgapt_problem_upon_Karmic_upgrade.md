---
title: "Kernel/dpkg/apt problem upon Karmic upgrade"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by The_Pheonix_Project on 2010-07-01
Everytime I install a new package or update via command line or in this case try to fix broken packages I get the following errors-it's saying my kernel image is unconfigured but I ran ```
sudo dpkg --configure -a
``` and this is what I get:

```
root@Admin:~# dpkg --configure -a
Setting up linux-image-2.6.31-22-386 (2.6.31-22.60) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-22-386
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.31-22-386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-22-generic (2.6.31-22.60) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-22-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.31-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-22-generic; however:
  Package linux-image-2.6.31-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.22.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.31.22.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-22-386
 linux-image-2.6.31-22-generic
 linux-image-generic
 linux-generic
 linux-image

```
GETTING FRUSTRATED--WHAT CAN I DO?

---

### Post by The_Pheonix_Project on 2010-07-01
Furthermore:
```
guest@Admin:~$ sudo apt-get dselect-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ant ant-gcj ant-optional ant-optional-gcj bash-completion
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 3,941kB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com karmic-proposed/main bash-completion 1:1.0-3ubuntu2.1 [104kB]
Get:2 http://archive.ubuntu.com karmic-proposed/main ant-optional 1.7.1-4ubuntu0.1 [648kB]
Get:3 http://archive.ubuntu.com karmic-proposed/main ant 1.7.1-4ubuntu0.1 [1,299kB]      
Get:4 http://archive.ubuntu.com karmic-proposed/main ant-gcj 1.7.1-4ubuntu0.1 [1,220kB]  
Get:5 http://archive.ubuntu.com karmic-proposed/main ant-optional-gcj 1.7.1-4ubuntu0.1 [669kB]
Fetched 3,941kB in 30s (131kB/s)                                                         
(Reading database ... 346962 files and directories currently installed.)
Preparing to replace bash-completion 1:1.0-3ubuntu2 (using .../bash-completion_1%3a1.0-3ubuntu2.1_all.deb) ...
Unpacking replacement bash-completion ...
Preparing to replace ant-optional 1.7.1-4 (using .../ant-optional_1.7.1-4ubuntu0.1_all.deb) ...
Unpacking replacement ant-optional ...
Preparing to replace ant 1.7.1-4 (using .../ant_1.7.1-4ubuntu0.1_all.deb) ...
Unpacking replacement ant ...
Preparing to replace ant-gcj 1.7.1-4 (using .../ant-gcj_1.7.1-4ubuntu0.1_i386.deb) ...
Unpacking replacement ant-gcj ...
Preparing to replace ant-optional-gcj 1.7.1-4 (using .../ant-optional-gcj_1.7.1-4ubuntu0.1_i386.deb) ...
Unpacking replacement ant-optional-gcj ...
Processing triggers for man-db ...
Setting up linux-image-2.6.31-22-386 (2.6.31-22.60) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-22-386
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.31-22-386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-22-generic (2.6.31-22.60) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-22-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.31-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-22-generic; however:
  Package linux-image-2.6.31-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.22.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.31.22.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
Setting up bash-completion (1:1.0-3ubuntu2.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already

Setting up ant (1.7.1-4ubuntu0.1) ...
Setting up ant-optional (1.7.1-4ubuntu0.1) ...
Setting up ant-gcj (1.7.1-4ubuntu0.1) ...

Setting up ant-optional-gcj (1.7.1-4ubuntu0.1) ...

Errors were encountered while processing:
 linux-image-2.6.31-22-386
 linux-image-2.6.31-22-generic
 linux-image-generic
 linux-generic
 linux-image
[ Rootkit Hunter version 1.3.4 ]
File updated: searched for 154 files, found 131
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

???????????????????????????!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by The_Pheonix_Project on 2010-07-02
cAN ANYONE HELP ME?

---

### Post by nothingspecial on 2010-07-02
Have you tried ```
sudo apt-get install -f
```

---

### Post by The_Pheonix_Project on 2010-07-02
I did that--sudo apt-get install -f and this is what I get:

guest@Admin:~$ sudo apt-get install -f
[sudo] password for guest: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.31-22-386 (2.6.31-22.60) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-22-386
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.31-22-386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-22-generic (2.6.31-22.60) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-22-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.31-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-22-generic; however:
  Package linux-image-2.6.31-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.22.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.31.22.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                  Errors were encountered while processing:
 linux-image-2.6.31-22-386
 linux-image-2.6.31-22-generic
 linux-image-generic
 linux-generic
 linux-image

---

### Post by dino99 on 2010-07-02
which kernel is used now ?

retry after rebooting

---

### Post by The_Pheonix_Project on 2010-07-03
> **dino99 said:**
> which kernel is used now ?

retry after rebooting

2.6.28-19-generic #61-Ubuntu SMP Wed May 26 23:35:15 UTC 2010 i686 GNU/Linux
 that is the kernel and I have rebooted and tried several times I also tried installinga new kernel but synaptic nor apt-get will install anything because it's saying that the kernel is unconfigured...

---

### Post by The_Pheonix_Project on 2010-07-04
Tried installing a new kernel now as well-still no good..submitted bug report...I know quite a bit about linux but not enough to figure out what would mess up the kerbel like that-when I tried booting into the alternative kernel which was an older one that came with karmic like 2.6.31.17 I think:  it said my x server was running in low graphics mode-could my nvidea card be the cause of all of this?

---

### Post by dino99 on 2010-07-04
sometimes ago ive read that users have had issues causing either by plymouth or flashplugin-installer: remove/purge them into synaptic (right click)

---

### Post by The_Pheonix_Project on 2010-07-06
tried that still no good

---

