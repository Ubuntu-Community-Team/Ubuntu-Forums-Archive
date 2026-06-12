---
title: "apt upgrade problem - intel arc conflict"
date: 2024-04-12
forum: Installation &amp; Upgrades
---

### Post by aaronabrown on 2024-04-12
Hi, I'm having an apt-get upgrade problem with intel arc opengl related packages, newly happening this week.

Linux  abrown-MS-7B86 6.5.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC  Tue Mar 12 10:22:43 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy
I  have an intel arc and installed it's driver a while ago without issues  using this method  [https://dgpu-docs.intel.com/driver/client/overview.html](https://dgpu-docs.intel.com/driver/client/overview.html)

I  normally have automatic updates, but I'm getting an error this week, i'm  assuming because of the packages in the intel method versus something  new available in ubuntu:

a handful of packages are showing some sort of conflict that I can't resolve. any advice would be appreciated
attached are the logs, but a sample of the issue is:
apt-get upgrade gives (truncated sample)
The following packages have unmet dependencies:
 libegl-dev : Depends: libegl1 (= 1.4.0-1) but 1.7.0-2101~22.04 is installed
              Breaks: libegl-dev:i386 (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libegl-dev:i386 : Depends: libegl1:i386 (= 1.7.0-2101~22.04) but 1.4.0-1 is installed
                   Breaks: libegl-dev (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libegl1 : Depends: libglvnd0 (= 1.7.0-2101~22.04) but 1.4.0-1 is installed
           Breaks: libegl1:i386 (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
...
with recommendations to run fix-broken


then when I run apt --fix-broken install i get this (truncated sample)
Preparing to unpack .../00-libopengl-dev_1.7.0-2101~22.04_amd64.deb ...
Unpacking libopengl-dev:amd64 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-Ut2BqB/00-libopengl-dev_1.7.0-2101~22.04_amd64.deb (--unpack):
 trying  to overwrite shared '/usr/share/doc/libopengl-dev/changelog.Debian.gz',  which is different from other instances of package libopengl-dev:amd64

I  tried using remove --purge with the entire list of broken but it  doesn't seem to work because of other app dependencies. Thanks again for  any apt advice. -Aaron
(PS I've had to rewrite this 3 times because each error the forum gives  me deletes all the text! saying I can't use tags, but even when I clear  the tags they come back but it wipes my text This is horrible! I'm on  firefox)

---

### Post by ActionParsnip on 2024-04-12
There is a conflict between 2 debs. You can either find the debs crossing and resolve the issue or force install the deb file.

---

### Post by aaronabrown on 2024-04-13
Thank you for your reply. I see that this list of libgl related debs are in conflict likely from having intel video drivers installed, but when I try to force it with dpkg forcing or apt fixes I get errors like above.

---

### Post by aaronabrown on 2024-04-13
```
[CODE]abrown@abrown-MS-7B86:~$ sudo apt update
[sudo] password for abrown: 
Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 https://repo.fortinet.com/repo/forticlient/7.2/debian stable InRelease                                                                            
Hit:3 http://us.archive.ubuntu.com/ubuntu jammy InRelease                                                                                               
Get:4 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]                                                                              
Get:5 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]                                                                               
Hit:6 https://repositories.intel.com/gpu/ubuntu jammy InRelease                                                                                         
Hit:7 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease                                                                                     
Get:8 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease [7,553 B]                                  
Hit:9 https://ppa.launchpadcontent.net/gns3/ppa/ubuntu jammy InRelease
Get:10 https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates InRelease [7,456 B]
Get:11 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease [7,450 B]
Get:12 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease [7,449 B]
Fetched 259 kB in 1s (182 kB/s)       
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
64 packages can be upgraded. Run 'apt list --upgradable' to see them.
abrown@abrown-MS-7B86:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libegl-dev : Depends: libegl1 (= 1.4.0-1) but 1.7.0-2101~22.04 is installed
              Breaks: libegl-dev:i386 (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libegl-dev:i386 : Depends: libegl1:i386 (= 1.7.0-2101~22.04) but 1.4.0-1 is installed
                   Breaks: libegl-dev (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libegl1 : Depends: libglvnd0 (= 1.7.0-2101~22.04) but 1.4.0-1 is installed
           Breaks: libegl1:i386 (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libegl1:i386 : Depends: libglvnd0:i386 (= 1.4.0-1) but 1.7.0-2101~22.04 is installed
                Breaks: libegl1 (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libgl-dev : Depends: libgl1 (= 1.7.0-2101~22.04) but 1.4.0-1 is installed
             Breaks: libgl-dev:i386 (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libgl-dev:i386 : Depends: libgl1:i386 (= 1.4.0-1) but 1.7.0-2101~22.04 is installed
                  Breaks: libgl-dev (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libgl1 : Depends: libglx0 (= 1.4.0-1) but 1.7.0-2101~22.04 is installed
          Breaks: libgl1:i386 (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libgl1:i386 : Depends: libglx0:i386 (= 1.7.0-2101~22.04) but 1.4.0-1 is installed
               Breaks: libgl1 (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libgles-dev : Breaks: libgles-dev:i386 (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libgles-dev:i386 : Breaks: libgles-dev (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libgles1 : Depends: libglvnd0 (= 1.7.0-2101~22.04) but 1.4.0-1 is installed
            Breaks: libgles1:i386 (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libgles1:i386 : Depends: libglvnd0:i386 (= 1.4.0-1) but 1.7.0-2101~22.04 is installed
                 Breaks: libgles1 (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libgles2 : Depends: libglvnd0 (= 1.7.0-2101~22.04) but 1.4.0-1 is installed
            Breaks: libgles2:i386 (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libgles2:i386 : Depends: libglvnd0:i386 (= 1.4.0-1) but 1.7.0-2101~22.04 is installed
                 Breaks: libgles2 (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libglvnd-core-dev : Breaks: libglvnd-core-dev:i386 (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libglvnd-core-dev:i386 : Breaks: libglvnd-core-dev (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libglvnd-dev : Depends: libglvnd-core-dev (= 1.4.0-1) but 1.7.0-2101~22.04 is installed
                Breaks: libglvnd-dev:i386 (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libglvnd-dev:i386 : Depends: libglvnd-core-dev:i386 (= 1.7.0-2101~22.04) but 1.4.0-1 is installed
                     Breaks: libglvnd-dev (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libglvnd0 : Breaks: libglvnd0:i386 (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libglvnd0:i386 : Breaks: libglvnd0 (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libglx-dev : Breaks: libglx-dev:i386 (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libglx-dev:i386 : Breaks: libglx-dev (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libglx0 : Depends: libglvnd0 (= 1.7.0-2101~22.04) but 1.4.0-1 is installed
           Breaks: libglx0:i386 (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libglx0:i386 : Depends: libglvnd0:i386 (= 1.4.0-1) but 1.7.0-2101~22.04 is installed
                Breaks: libglx0 (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libopengl-dev : Depends: libopengl0 (= 1.4.0-1) but 1.7.0-2101~22.04 is installed
                 Breaks: libopengl-dev:i386 (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
 libopengl-dev:i386 : Depends: libopengl0:i386 (= 1.7.0-2101~22.04) but 1.4.0-1 is installed
                      Breaks: libopengl-dev (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libopengl0 : Depends: libglvnd0 (= 1.7.0-2101~22.04) but 1.4.0-1 is installed
              Breaks: libopengl0:i386 (!= 1.7.0-2101~22.04) but 1.4.0-1 is installed
 libopengl0:i386 : Depends: libglvnd0:i386 (= 1.4.0-1) but 1.7.0-2101~22.04 is installed
                   Breaks: libopengl0 (!= 1.4.0-1) but 1.7.0-2101~22.04 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
abrown@abrown-MS-7B86:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  openttd-data openttd-opengfx openttd-openmsx
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libegl-dev libegl1:i386 libgl-dev:i386 libgl1 libgles-dev:i386 libgles1:i386 libgles2:i386 libglvnd-core-dev:i386 libglvnd-dev libglvnd0
  libglx-dev:i386 libglx0:i386 libopengl-dev libopengl0:i386
The following packages will be upgraded:
  libegl-dev libegl1:i386 libgl-dev:i386 libgl1 libgles-dev:i386 libgles1:i386 libgles2:i386 libglvnd-core-dev:i386 libglvnd-dev libglvnd0
  libglx-dev:i386 libglx0:i386 libopengl-dev libopengl0:i386
14 upgraded, 0 newly installed, 0 to remove and 50 not upgraded.
22 not fully installed or removed.
Need to get 0 B/580 kB of archives.
After this operation, 15.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up util-linux (2.37.2-4ubuntu3.4) ...
fstrim.service is a disabled or a static unit not running, not starting it.
(Reading database ... 355105 files and directories currently installed.)
Preparing to unpack .../00-libopengl-dev_1.7.0-2101~22.04_amd64.deb ...
Unpacking libopengl-dev:amd64 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/00-libopengl-dev_1.7.0-2101~22.04_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libopengl-dev/changelog.Debian.gz', which is different from other instances of package libopengl-dev:amd64
Preparing to unpack .../01-libopengl0_1.7.0-2101~22.04_i386.deb ...
Unpacking libopengl0:i386 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/01-libopengl0_1.7.0-2101~22.04_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libopengl0/changelog.Debian.gz', which is different from other instances of package libopengl0:i386
Preparing to unpack .../02-libgl1_1.7.0-2101~22.04_amd64.deb ...
Unpacking libgl1:amd64 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/02-libgl1_1.7.0-2101~22.04_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libgl1/changelog.Debian.gz', which is different from other instances of package libgl1:amd64
Preparing to unpack .../03-libglx-dev_1.7.0-2101~22.04_i386.deb ...
Unpacking libglx-dev:i386 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/03-libglx-dev_1.7.0-2101~22.04_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libglx-dev/changelog.Debian.gz', which is different from other instances of package libglx-dev:i386
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../04-libgl-dev_1.7.0-2101~22.04_i386.deb ...
Unpacking libgl-dev:i386 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/04-libgl-dev_1.7.0-2101~22.04_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libgl-dev/changelog.Debian.gz', which is different from other instances of package libgl-dev:i386
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../05-libglx0_1.7.0-2101~22.04_i386.deb ...
Unpacking libglx0:i386 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/05-libglx0_1.7.0-2101~22.04_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libglx0/changelog.Debian.gz', which is different from other instances of package libglx0:i386
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../06-libegl-dev_1.7.0-2101~22.04_amd64.deb ...
Unpacking libegl-dev:amd64 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/06-libegl-dev_1.7.0-2101~22.04_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libegl-dev/changelog.Debian.gz', which is different from other instances of package libegl-dev:amd64
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../07-libgles-dev_1.7.0-2101~22.04_i386.deb ...
Unpacking libgles-dev:i386 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/07-libgles-dev_1.7.0-2101~22.04_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libgles-dev/changelog.Debian.gz', which is different from other instances of package libgles-dev:i386
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../08-libglvnd-dev_1.7.0-2101~22.04_amd64.deb ...
Unpacking libglvnd-dev:amd64 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/08-libglvnd-dev_1.7.0-2101~22.04_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libglvnd-dev/changelog.Debian.gz', which is different from other instances of package libglvnd-dev:amd64
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../09-libglvnd-core-dev_1.7.0-2101~22.04_i386.deb ...
Unpacking libglvnd-core-dev:i386 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/09-libglvnd-core-dev_1.7.0-2101~22.04_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libglvnd-core-dev/changelog.Debian.gz', which is different from other instances of package libglvnd-core-dev:
i386
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../10-libgles1_1.7.0-2101~22.04_i386.deb ...
Unpacking libgles1:i386 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/10-libgles1_1.7.0-2101~22.04_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libgles1/changelog.Debian.gz', which is different from other instances of package libgles1:i386
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../11-libgles2_1.7.0-2101~22.04_i386.deb ...
Unpacking libgles2:i386 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/11-libgles2_1.7.0-2101~22.04_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libgles2/changelog.Debian.gz', which is different from other instances of package libgles2:i386
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../12-libegl1_1.7.0-2101~22.04_i386.deb ...
Unpacking libegl1:i386 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/12-libegl1_1.7.0-2101~22.04_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libegl1/changelog.Debian.gz', which is different from other instances of package libegl1:i386
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../13-libglvnd0_1.7.0-2101~22.04_amd64.deb ...
Unpacking libglvnd0:amd64 (1.7.0-2101~22.04) over (1.4.0-1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dJ3tMu/13-libglvnd0_1.7.0-2101~22.04_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libglvnd0/changelog.Debian.gz', which is different from other instances of package libglvnd0:amd64
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /tmp/apt-dpkg-install-dJ3tMu/00-libopengl-dev_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-dJ3tMu/01-libopengl0_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-dJ3tMu/02-libgl1_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-dJ3tMu/03-libglx-dev_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-dJ3tMu/04-libgl-dev_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-dJ3tMu/05-libglx0_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-dJ3tMu/06-libegl-dev_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-dJ3tMu/07-libgles-dev_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-dJ3tMu/08-libglvnd-dev_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-dJ3tMu/09-libglvnd-core-dev_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-dJ3tMu/10-libgles1_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-dJ3tMu/11-libgles2_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-dJ3tMu/12-libegl1_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-dJ3tMu/13-libglvnd0_1.7.0-2101~22.04_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```[/CODE]

---

### Post by MAFoElffen on 2024-04-13
Go to the Intel Support Forum- Graphics Section, and fill out a support request.

I have dealt with and actively working with two Upstream Intel Graphics Support Engineer Teams. They do take it seriously and are trying. I am currently working with them on their extended graphics driver issues with Jammy and kernel 6.5. That's with the HWE stack. 

My one question is, from your output, why do you have i386 packages? For what goals?

---

### Post by chamcham48 on 2024-04-14
Please post your findings and what you did to fix them, I have a very similar issue and can't do any updates.  I get this error which is similar to yours, I also installed the Intel Arc drivers per those directions.

                                                              Errors were encountered while processing:
 /tmp/apt-dpkg-install-ABe7w4/00-libglx-dev_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-ABe7w4/01-libgl-dev_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-ABe7w4/02-libgl1_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-ABe7w4/03-libglx0_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-ABe7w4/04-libgles1_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-ABe7w4/05-libgles-dev_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-ABe7w4/06-libgles2_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-ABe7w4/07-libegl-dev_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-ABe7w4/08-libegl1_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-ABe7w4/09-libopengl-dev_1.7.0-2101~22.04_i386.deb
 /tmp/apt-dpkg-install-ABe7w4/10-libopengl0_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-ABe7w4/11-libglvnd-core-dev_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-ABe7w4/12-libglvnd-dev_1.7.0-2101~22.04_amd64.deb
 /tmp/apt-dpkg-install-ABe7w4/13-libglvnd0_1.7.0-2101~22.04_i386.deb

---

### Post by captain062 on 2024-04-17
I'm facing the same issue. I'll turn to Intel forum to check if there's a solution...

---

### Post by chamcham48 on 2024-04-17
I ended up taking the Intel repos out of APT and was able to update.  However, now I don't think the intel driver is working, even though it says it's being used.  Plex, won't use it for hardware decoding at least...  Anyway, I was able to update by taking the intel repo out, but now wondering if I need to add it back in and try updating now to get the intel driver to work again?  I'm kind of scared doing that and mucking something else up.

---

### Post by torenrob on 2024-04-23
I had the same issue with many of the same packages and found a solution. 

Run apt --fix-broken install again. 
Make sure all of the 'error processing' messages contain a 'trying to overwrite ../changelog.Debian.gz' error. 
I had to delete all of the changelog files mentioned in the error. 
Then I reran apt --fix-broken install. 

I was able to successfully run apt update/apt upgrade after that. 

I'm guessing that something in the changelog was stopping the upgrade. Hope this helps.

---

### Post by MAFoElffen on 2024-04-23
Hmmmm. That is still something to look into.

Please post a link the URL of the thread you started there here, in this thread, so I can follow it there.

---

### Post by esavior on 2024-05-06
Thanks, torenrob. Deleting the changelog files displayed in the error allowed me to move past this problem. Your post definitely helped. God bless!

---

### Post by aaronabrown on 2024-07-11
I started having unrelated thermal stability problems so have rebuilt the system entirely, so for me it is moot, I hope someone finds a good answer as the Arc A750 has been a solid card for me.

---

