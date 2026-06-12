---
title: "Problems updating intramfs-tools"
date: 2013-10-15
forum: Installation &amp; Upgrades
---

### Post by agentjwall on 2013-10-15
Hello,
I was updating my software but for some reason I've hit a snag. upon updating intramfs-tools I get an error message saying:
 
"The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"

I've checked and I'm not using any third party repositories currently. I've also used 'sudo apt-get -f install' and get more errors:

```
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.2.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of udev:
 udev depends on initramfs-tools (>= 0.92bubuntu63); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 initramfs-tools
 apparmor
 udev
 network-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any Ideas?

EDIT:
Ok after a bit more searching I discovered that my /boot is out of space. The general solution seems to be temporarily uninstalling linux-server, but for whatever reason, It wasn't installed in the first place. 'sudo dpkg --configure -a' and 'sudo apt-get update' also have no effect.

---

### Post by varunendra on 2013-10-17
> **agentjwall said:**
> **Ok after a bit more searching I discovered that my /boot is out of space. The general solution seems to be temporarily uninstalling linux-server**, but for whatever reason, It wasn't installed in the first place. 'sudo dpkg --configure -a' and 'sudo apt-get update' also have no effect.

Regarding the linux-server suggestion, I suspect if you hit any of my posts where I suggested that. Remember - different reasons, different solutions.

So.. did you try to empty the /boot partition? You are on the right track with this, the initramfs problems occur almost always due to no space being left on the partition. Accordingly, please post back the outputs of -
```
df -h
dpkg -l | grep linux-image
```

---

### Post by agentjwall on 2013-10-21
Here you go, Sorry about the delay!

```
Filesystem                    Size  Used Avail Use% Mounted on/dev/mapper/ProjectMICA-root  148G   25G  116G  18% /
udev                          1.6G  4.0K  1.6G   1% /dev
tmpfs                         656M  312K  655M   1% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          1.6G  208K  1.6G   1% /run/shm
/dev/sda1                     228M  219M     0 100% /boot
/dev/sdc2                     930G  269M  930G   1% /media/Data disk
/dev/sdc1                     1.7G   10M  1.7G   1% /media/DellUtility
```
```
ii  linux-image-3.5.0-23-generic           3.5.0-23.35~precise1                    Linux kernel image for version 3.5.0 on 32 bit x86 SMPii  linux-image-3.5.0-30-generic           3.5.0-30.51~precise1                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-31-generic           3.5.0-31.52~precise1                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-32-generic           3.5.0-32.53~precise1                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-34-generic           3.5.0-34.55~precise1                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-37-generic           3.5.0-37.58~precise1                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-39-generic           3.5.0-39.60~precise1                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-40-generic           3.5.0-40.62~precise1                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-41-generic           3.5.0-41.64~precise1                    Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-quantal        3.5.0.41.47                             Generic Linux kernel image
```

---

### Post by Bashing-om on 2013-10-21
agentjwall; Hi !

"apt-get" can now remove the kernels from the /boot partition in newer installs, I am not sure where that break between older kernels and the newer kernels occurred. I spent a small amount of time seeking the documentation. I got impatient. Try the easy way that may work with the 3.5 series kernels.
```

sudo apt-get autoremove

```
If "autoremove" is applicable in this case, will remove all but the current booting kernel and the one under it. Cool, real cool.

Else there are other command line tools to remove the old kernels and config files.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by agentjwall on 2013-10-21
Thank for the tip! Unfortunately, I've already tried auto-remove and, ironically enough, it seems to be dependent on the one tool I cannot update...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.2 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by Bashing-om on 2013-10-21
agentjwall; Well,

As you are at 100% capacity on that "/boot" partition, may not have the headroom to operate. But, try:
```

sudo dpkg -P linux-image-3.5.0-{23,31,32,34,37,39}-generic
sudo dpkg -P linux-headers-3.5.0-{23,31,32,34,37,39}-generic

```
I have been pleasantly surprised before.

[INDENT][INDENT]maybe yes, maybe not so yes
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-21
agentjwall; Hey,

I am sorry if I am leaving you in  a learch, if that last is ineffective there are other means we can employ. However, it is past my time, and my mind is beginning to pumpkinize.
I will check your status in my AM.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by agentjwall on 2013-10-22
well those commands brought my /boot down to 36% but I'm still having trouble installing that same tool, along with a few others...

```
dpkg: dependency problems prevent configuration of initramfs-tools: initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.2.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of udev:
 udev depends on initramfs-tools (>= 0.92bubuntu63); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on udev; however:
  Package udev is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on udev (>= 149); however:
  Package udev is not configured yet.
dpkg: error processing xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 initramfs-tools
 apparmor
 udev
 network-manager
 xserver-xorg-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2013-10-22
agentjwall; Yuk !

This may be a real challenge :
> 
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.2.

the "(<< 0.99ubuntu13.1.1~)" says strictly this version, and nothing other will do.
However, at some point you have installed something that also installed version  0.99ubuntu13.2.
I would think the better solution here is to determine what was installed that also installed that later version of initramfs-tools-bin. Remove it from the system and (re-)install the required version. I bet right now you can not use the package manager to download anything(??). So what to do what to do ?

Do you have by chance or foresight "aptitude" installed ?
```

dpkg -l aptitude

``` as "aptitude" might be able to tell us or at least help us.

What does the package manager have to relate ?
```

dpkg -s initramfs-tools-bin
apt-cache policy initramfs-tools-bin

```

wget and dpkg -i to our rescue ??

[INDENT][INDENT]A process of learning
[/INDENT][/INDENT]

---

### Post by agentjwall on 2013-10-22
I do have aptitude:

```
Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  aptitude                  0.6.6-1ubuntu1.2          terminal-based package manager (terminal interface only)
```

The data on initramfs-tools-bin:

```
Package: initramfs-tools-bin
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 118
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: initramfs-tools
Version: 0.99ubuntu13.2
Depends: libc6 (>= 2.4), libudev0 (>= 147)
Description: binaries used by initramfs-tools
 This package contains binaries used inside the initramfs images generated
 by initramfs-tools.
Original-Maintainer: Debian kernel team <debian-kernel@lists.debian.org>
```
```
initramfs-tools-bin:
  Installed: 0.99ubuntu13.2
  Candidate: 0.99ubuntu13.2
  Version table:
 *** 0.99ubuntu13.2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     0.99ubuntu13 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages
```

---

### Post by Bashing-om on 2013-10-23
agentjwall; Well !

Are you in fact running a 32 bit operating system ?
and what does "aptitude" report from:
```

aptitude why initramfs-tools-bin_0.99ubuntu13.2

```
and confirm what version you are running
```

uname -a

``` as and because:
[http://packages.ubuntu.com/search?suite=precise-updates&searchon=names&keywords=initramfs-tools-bin](http://packages.ubuntu.com/search?suite=precise-updates&searchon=names&keywords=initramfs-tools-bin)
says that :
> 
precise-updates (utils): binaries used by initramfs-tools 
0.99ubuntu13.2
should be the correct version of initramfs-tools-bin !

//
I am done for my eve, brain is not engaging further.

[INDENT][INDENT]will see where this leads us
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-23
agentjwall; Hey,

Depending on the response, I do have a procedure to restore in mind !

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by agentjwall on 2013-10-25
Sorry for the delay, I've been busy non-stop the last couple days...

The first command claims that initramfs doesn't exist...
```
No package named "initramfs-tools-bin_0.99ubuntu13.2" exists.
```

and here's the second:
```
Linux ProjectMICA 3.5.0-41-generic #64~precise1-Ubuntu SMP Thu Sep 12 17:01:55 UTC 2013 i686 i686 i386 GNU/Linux
```

---

### Post by Bashing-om on 2013-10-25
agentjwall;
Well that sure blows a couple of theories away.
Try this before I go looking at what might be pinned, so as not to update.
Let's see what the package manager relates from:
```

sudo dpkg -C
sudo apt-get install -f

```

Not updating to the current version,
[INDENT][INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT][/INDENT]

---

