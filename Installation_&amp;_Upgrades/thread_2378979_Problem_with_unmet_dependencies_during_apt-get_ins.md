---
title: "Problem with unmet dependencies during apt-get install on 16.04"
date: 2017-11-29
forum: Installation &amp; Upgrades
---

### Post by giorgio-rome on 2017-11-29
Hi,
during an upgrade I noticed my PC (Toshiba X40) hang and the only way to restart was to powering-off and powering-on.
So I tried again to run sudo apt-get install and had this error

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic-hwe-16.04 : Depends: linux-headers-generic-hwe-16.04 (= 4.10.0.40.42) but 4.10.0.38.40 is installed
 linux-signed-generic-hwe-16.04 : Depends: linux-headers-generic-hwe-16.04 (= 4.10.0.40.42) but 4.10.0.38.40 is installed
E: Unmet dependencies. Try using -f.

Tried again several times with -f but every time the PC completely hangs.

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

$ uname -a
Linux fachiro 4.10.0-40-generic #44~16.04.1-Ubuntu SMP Thu Nov 9 15:37:44 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

$ pwd
/boot
$ df -h .
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p2   92G   65G   22G  75% /


Please help me to find a solution otherwise I need to reinstall the whole OS.
I'm posting additional info below, please don't hesitate to ask for additional info if needed

Many thanks

ciao

giorgio

############### ADDITIONAL INFO ##########################
Additional info:

$ sudo dpkg --audit
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 linux-headers-4.10.0-40 (no description available)

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-generic-hwe-16.04 Complete Generic Linux kernel and headers
 linux-signed-generic-hwe-16.04 Complete Signed Generic Linux kernel and header

The following packages are missing the list control file in the
database, they need to be reinstalled:
 linux-headers-4.10.0-40 (no description available)

The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 linux-headers-4.10.0-40 (no description available)

$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-generic-hwe-16.04:
 linux-generic-hwe-16.04 depends on linux-headers-generic-hwe-16.04 (= 4.10.0.40.42); however:
  Version of linux-headers-generic-hwe-16.04 on system is 4.10.0.38.40.

dpkg: error processing package linux-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic-hwe-16.04:
 linux-signed-generic-hwe-16.04 depends on linux-headers-generic-hwe-16.04 (= 4.10.0.40.42); however:
  Version of linux-headers-generic-hwe-16.04 on system is 4.10.0.38.40.

dpkg: error processing package linux-signed-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-generic-hwe-16.04
 linux-signed-generic-hwe-16.04

---

### Post by ian-weisser on 2017-11-30
> **giorgio-rome said:**
> linux-generic-hwe-16.04 : Depends: linux-headers-generic-hwe-16.04 (= 4.10.0.40.42) but 4.10.0.38.40 is installed
 linux-signed-generic-hwe-16.04 : Depends: linux-headers-generic-hwe-16.04 (= 4.10.0.40.42) but 4.10.0.38.40 is installed

Random apt commands won't help.
You must *understand* and *solve* the problem that apt's logic cannot.
Based upon the information provided, your metapackages seem out of date. Clear the old version from your local cache, then reinstall them.

```
sudo apt clean linux-headers-generic-hwe-16.04 linux-signed-generic-hwe-16.04
sudo apt install --reinstall linux-headers-generic-hwe-16.04 linux-signed-generic-hwe-16.04
```

This sort of apt error often happens when kernel upgrades are blocked for a long time (like a full /boot).

---

### Post by giorgio-rome on 2017-12-01
Hi,
thanks for your reply and sorry for the delay in answering.
First of all I agree with you when you say
>You must *understand* and *solve* the problem that apt's logic cannot.
but the problem is that I don't understand the problem :-(
Below is what I've done, following your suggestion:

giorgio@fachiro:~$ sudo apt clean linux-headers-generic-hwe-16.04 linux-signed-generic-hwe-16.04
giorgio@fachiro:~$ sudo apt install --reinstall linux-headers-generic-hwe-16.04 linux-signed-generic-hwe-16.04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic-hwe-16.04 : Depends: linux-headers-4.10.0-40-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I can't run apt-get -f install because PC freezes while running "unpacking linux-headers-4.10.0-40-generic..." (the only way to provide a log is a picture of screen) , so I don't know how to solve this.

Please let me know if there's something else I can do.

Many thanks in advance

Ciao

giorgio

---

### Post by ian-weisser on 2017-12-01
> **giorgio-rome said:**
> but the problem is that I don't understand the problem :-(

The original problem was that your metapackages were not updated.
Metapackages are empty packages that depend upon real packages. We use generic 'kernel' and 'kernel-header' metapackages to depend upon the rapidly-changing kernel packages.
When a metapackage gets out of date, it depends upon a kernel (or header) package that is old, and already withdrawn from the Ubuntu repos.
This almost never happens by accident.
It's usually due to the package manager being blocked for a few weeks, so the packages on your system are significantly out of date.


> **giorgio-rome said:**
> I can't run apt-get -f install because PC freezes while running "unpacking linux-headers-4.10.0-40-generic..." (the only way to provide a log is a picture of screen) , so I don't know how to solve this.

Freezing during unpacking is very unusual.
Is your disk full?
Try using 'clean' on that package, too, so apt will download a fresh copy.
If those don't fix it, then seeing that output is the next step.

---

### Post by Bashing-om on 2017-12-01
giorgio-rome; Hello -

How about we take a look at what apt is so unhappy about . Then see what we can do to make apt happy.
Post back - Between code tags - the output of terminal commands:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

df -h
df -i
lsb_release -a
dpkg -l | grep linux-

```

Though we have no indication this is space related, let's do make sure (df) that we do have the operational head room .

[INDENT][INDENT]cause and effect
[/INDENT][/INDENT]

---

### Post by giorgio-rome on 2017-12-01
> **ian-weisser said:**
> The original problem was that your metapackages were not updated.
Metapackages are empty packages that depend upon real packages. We use generic 'kernel' and 'kernel-header' metapackages to depend upon the rapidly-changing kernel packages.
When a metapackage gets out of date, it depends upon a kernel (or header) package that is old, and already withdrawn from the Ubuntu repos.
This almost never happens by accident.
It's usually due to the package manager being blocked for a few weeks, so the packages on your system are significantly out of date.

System has been installed from scratch on the 19th of November, problem appeared on the 28th of November, when I used the Setting->Details->"Check for updates" button, instead of using standard apt-get.

> **ian-weisser said:**
> Freezing during unpacking is very unusual.
Is your disk full?

I had put a "df -k" output in the initial post, there are 21GB free, it should be enough

> **ian-weisser said:**
>  Try using 'clean' on that package, too, so apt will download a fresh copy.
If those don't fix it, then seeing that output is the next step.
I posted output from clean and reinstall, same result.

Which output do you want to see ?

Let me know and I will provide

Many thanks

giorgio

---

### Post by giorgio-rome on 2017-12-01
> **Bashing-om said:**
> giorgio-rome; Hello -

How about we take a look at what apt is so unhappy about . Then see what we can do to make apt happy.
Post back - Between code tags - the output of terminal commands:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

df -h
df -i
lsb_release -a
dpkg -l | grep linux-

```

Though we have no indication this is space related, let's do make sure (df) that we do have the operational head room .[INDENT][INDENT]cause and effect
[/INDENT]
[/INDENT]


Below requested command output, I had already inserted some of these info in the initial post.

Many thanks

giorgio

```

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7,8G     0  7,8G   0% /dev
tmpfs           1,6G  9,7M  1,6G   1% /run
/dev/nvme0n1p2   92G   67G   21G  77% /
tmpfs           7,8G   50M  7,8G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           7,8G     0  7,8G   0% /sys/fs/cgroup
/dev/nvme0n1p1  511M  3,4M  508M   1% /boot/efi
/dev/nvme0n1p4  142G   28G  114G  20% /media/DATI
tmpfs           1,6G     0  1,6G   0% /run/user/998
tmpfs           1,6G   36K  1,6G   1% /run/user/1000
giorgio@fachiro:~$ df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
udev             2036899    523   2036376    1% /dev
tmpfs            2042480    832   2041648    1% /run
/dev/nvme0n1p2   6111232 316983   5794249    6% /
tmpfs            2042480     47   2042433    1% /dev/shm
tmpfs            2042480      6   2042474    1% /run/lock
tmpfs            2042480     16   2042464    1% /sys/fs/cgroup
/dev/nvme0n1p1         0      0         0     - /boot/efi
/dev/nvme0n1p4 119333784 158306 119175478    1% /media/DATI
tmpfs            2042480      4   2042476    1% /run/user/998
tmpfs            2042480     26   2042454    1% /run/user/1000
giorgio@fachiro:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial
giorgio@fachiro:~$ dpkg -l | grep linux-
ii  linux-base                                  4.0ubuntu1                                   all          Linux image base package
ii  linux-firmware                              1.157.13                                     all          Firmware for Linux kernel drivers
ii  linux-gcp-tools-4.10.0-1009                 4.10.0-1009.9                                amd64        Linux kernel version specific tools for version 4.10.0-1009
iU  linux-generic-hwe-16.04                     4.10.0.40.42                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.10.0-28                     4.10.0-28.32~16.04.2                         all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-28-generic             4.10.0-28.32~16.04.2                         amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-4.10.0-38                     4.10.0-38.42~16.04.1                         all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-38-generic             4.10.0-38.42~16.04.1                         amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
iHR linux-headers-4.10.0-40                     4.10.0-40.44~16.04.1                         all          (no description available)
ii  linux-headers-generic-hwe-16.04             4.10.0.38.40                                 amd64        Generic Linux kernel headers
ii  linux-image-4.10.0-28-generic               4.10.0-28.32~16.04.2                         amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-38-generic               4.10.0-38.42~16.04.1                         amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-40-generic               4.10.0-40.44~16.04.1                         amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-28-generic         4.10.0-28.32~16.04.2                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-38-generic         4.10.0-38.42~16.04.1                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-40-generic         4.10.0-40.44~16.04.1                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-generic-hwe-16.04               4.10.0.40.42                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        4.4.0-101.124                                amd64        Linux Kernel Headers for development
iU  linux-signed-generic-hwe-16.04              4.10.0.40.42                                 amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-4.10.0-38-generic        4.10.0-38.42~16.04.1                         amd64        Signed kernel image generic
ii  linux-signed-image-4.10.0-40-generic        4.10.0-40.44~16.04.1                         amd64        Signed kernel image generic
ii  linux-signed-image-generic-hwe-16.04        4.10.0.40.42                                 amd64        Signed Generic Linux kernel image
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  linux-tools-4.10.0-1009-gcp                 4.10.0-1009.9                                amd64        Linux kernel version specific tools for version 4.10.0-1009
ii  linux-tools-common                          4.4.0-101.124                                all          Linux kernel version specific tools for version 4.4.0
ii  linux-tools-gcp                             4.10.0.1009.11                               amd64        Google Cloud Platform (GCP) Linux kernel tools
ii  syslinux-common                             3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2017-12-01
giorgio-rome; K

Let's see if we can give apt a helping hand and tell it what to do:
```

sudo apt update
sudo apt install --reinstall linux-headers-4.10.0-40 linux-signed-generic-hwe-16.04 linux-generic-hwe-16.04

```

Examining your dpkg output, and comparing:
> 
sysop@x1604:~$ apt show linux-generic-hwe-16.04
<snip>
Depends: linux-image-generic-hwe-16.04 (= 4.10.0.40.42), linux-headers-generic-hwe-16.04 (= 4.10.0.40.42)
<snip>
Description: Complete Generic Linux kernel and headers
 This package will always depend on the latest complete generic Linux kernel
 and headers.


If the above --reinstall runs clean, then upgrade the system:
```

sudo apt update
sudo apt full-upgrade

```
the re-install I do expect to work wonders.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by giorgio-rome on 2017-12-02
It's not clear, at least to me, what to do.
the -reinstall gives error on unmet dependencies.

The upgrade again same error
> $ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic-hwe-16.04 : Depends: linux-headers-generic-hwe-16.04 (= 4.10.0.40.42) but 4.10.0.38.40 is installed
 linux-signed-generic-hwe-16.04 : Depends: linux-headers-generic-hwe-16.04 (= 4.10.0.40.42) but 4.10.0.38.40 is installed
E: Unmet dependencies. Try using -f.



Thanks

Giorgio

---

### Post by photonxp on 2017-12-02
First backup all your data and important files. 

Then we can try the following commands in order and see what happens:
```

sudo apt-get clean 
sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by giorgio-rome on 2017-12-02
> $ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic-hwe-16.04 : Depends: linux-headers-generic-hwe-16.04 (= 4.10.0.40.42) but 4.10.0.38.40 is installed
 linux-signed-generic-hwe-16.04 : Depends: linux-headers-generic-hwe-16.04 (= 4.10.0.40.42) but 4.10.0.38.40 is installed
E: Unmet dependencies. Try using -f.


I'm not an expert on Ubuntu but it should be clear that:
1) it's not a problem related to disk space
> 2) every apt "upgrade" command fails

Thanks

giorgio

---

### Post by Bashing-om on 2017-12-02
giorgio-rome; Yeah -

Agreed disk space is not an issue . But, I do not yet comprehend why apt is hollering about : 
> 
Depends: linux-headers-generic-hwe-16.04 (= 4.10.0.40.42) but 4.10.0.38.40 is installed


What kernel are you presently booting ? 
Post back:
```

uname -r
apt policy linux-generic-hwe-16.04

```

see what it takes
[INDENT][INDENT]to keep a package manager like that
[INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by giorgio-rome on 2017-12-03
Bashing-om and others who tried to help
thanks for your effort.
But I decided that it was faster to reinstall everything from scratch than proceed again with other attempts.
So last night I reinstalled everything and everything run fine, either upgrade and install.
I'm still puzzling on what has happened but I needed my PC ready and working for monday morning ;-)

Ciao

Giorgio

---

### Post by Bashing-om on 2017-12-03
giorgio-rome; Hey ..

Not a thing wrong with taking that nuclear solution when needed . It always works :)
Done that too several times in my excursions of learning .
However. we do not learn much from taking that option.

As this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

