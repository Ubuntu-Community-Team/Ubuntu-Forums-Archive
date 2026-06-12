---
title: "Could not install 'linux-image-5.8.0-50-generic'"
date: 2023-06-24
forum: Installation &amp; Upgrades
---

### Post by metalfever87 on 2023-06-24
When trying to upgrade I get the following error mesage:

Could not install 'linux-image-5.8.0-50-generic'
The upgrade will continue but the 'linux-image-5.8.0-50-generic' package may not be in a working state. Please consider submitting a bug report about it.
installed linux-image-5.8.0-50-generic package post-removal script subprocess returned error exit status 1

I cannot perform any updates either without a generic error message:
```

dpkg: error processing package linux-image-5.8.0-50-generic (--remove):
 installed linux-image-5.8.0-50-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.8.0-50-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by TheFu on 2023-06-24
Is there sufficient storage on all the involved partitions?
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
will show the relevant parts.

This is the most common issue.
BTW, 5.8 is pretty old.  My 20.04.6 installs are all running 5.15.x kernels.  And 18.04 HWE ran 5.4.x kernels, so it seems you are probably on an unsupported release.
**lsb_release -d** will show the exact release.

Please post the output from those commands.

---

### Post by metalfever87 on 2023-06-24
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb5      ext4  117G   16G   96G  14% /
/dev/sdb3      vfat  512M   32K  512M   1% /boot/efi



```

Looks like there is plenty of storage

```
$ lsb_release -d 
Description:	Ubuntu 22.04.2 LTS

```

I just upgraded to 22.04.2 LTS from an old version and I think the update had some errors.

---

### Post by TheFu on 2023-06-24
Please do the 
```
sudo apt update && sudo apt upgrade

```again and post the the full output wrapped in code tags. Show the commands too.

5.8.x kernels shouldn't be part of any 22.04.x install.  Do you have a list of installed kernels?
```
dpkg -l |grep linux-image
``` 
will show them.  I suspect 5.8.x kernels are left over cruft from prior upgrades and need to be removed/purged. Let's see the list first.

---

### Post by jeremy31 on 2023-06-24
Can you ```
sudo apt install inxi
```
And post results for ```
inxi -r
```

---

### Post by metalfever87 on 2023-06-24
```

$ sudo apt update && sudo apt upgrade[sudo] password for zac: 
Hit:1 http://us.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:3 https://brave-browser-apt-release.s3.brave.com stable InRelease          
Get:4 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease [108 kB]   
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease
Fetched 108 kB in 1s (171 kB/s)                         
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://brave-browser-apt-release.s3.brave.com stable InRelease' doesn't support architecture 'i386'
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libavcodec58 libavutil56 libswresample3 libavformat58
Learn more about Ubuntu Pro at https://ubuntu.com/pro
The following packages will be REMOVED:
  linux-image-5.8.0-50-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 9,818 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 175921 files and directories currently installed.)
Removing linux-image-5.8.0-50-generic (5.8.0-50.56~20.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.8.0-50-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.s
o.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.8.0-50-generic (--remove):
 installed linux-image-5.8.0-50-generic package post-removal script subprocess r
eturned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.8.0-50-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

$ dpkg -l |grep linux-image
ii  linux-image-5.15.0-75-generic              5.15.0-75.82                            amd64        Signed kernel image generic
ii  linux-image-5.19.0-45-generic              5.19.0-45.46~22.04.1                    amd64        Signed kernel image generic
rH  linux-image-5.8.0-50-generic               5.8.0-50.56~20.04.1                     amd64        Signed kernel image generic
ii  linux-image-generic                        5.15.0.75.73                            amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-20.04              5.15.0.75.82~20.04.36                   amd64        Generic Linux kernel image

```

```

$ sudo apt install inxi
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  lm-sensors mesa-utils mesa-utils-bin tree
Suggested packages:
  libxml-dumper-perl fancontrol read-edid i2c-tools
The following packages will be REMOVED:
  linux-image-5.8.0-50-generic
The following NEW packages will be installed:
  inxi lm-sensors mesa-utils mesa-utils-bin tree
0 upgraded, 5 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1,541 kB of archives.
After this operation, 5,540 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 mesa-utils-bin amd64 8.4.0-1ubuntu1 [53.8 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 tree amd64 2.0.2-1 [47.9 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 inxi all 3.3.13-1-1 [283 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 lm-sensors amd64 1:3.6.0-7ubuntu1 [91.0 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 mesa-utils amd64 8.4.0-1ubuntu1 [1,065 kB]
Fetched 1,541 kB in 1s (2,998 kB/s) 
(Reading database ... 175921 files and directories currently installed.)
Removing linux-image-5.8.0-50-generic (5.8.0-50.56~20.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.8.0-50-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.s
o.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.8.0-50-generic (--remove):
 installed linux-image-5.8.0-50-generic package post-removal script subprocess r
eturned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.8.0-50-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by metalfever87 on 2023-06-24
Pretty sure it has something to do with grub. I've tried to purge the old kernel but it wont let me

---

### Post by #&amp;thj^% on 2023-06-24
Not sure I'd look at grub, but more at this:
H - Half installed:
```
r**[COLOR="#FF0000"]H [/COLOR]** linux-image-5.8.0-50-generic               5.8.0-50.56~20.04.1   
```

---

### Post by TheFu on 2023-06-24
If you can, remove the 2 older kernels and all their dependencies.  Keep only the latest one.

You've come across one of the reasons why release upgrades can cause issues, especially with 3rd party DEB files and PPAs installed/enabled. If you know exactly which deb files were manually installed, you can remove them and some held packages will be allowed to update.

But for most people, by the time you figure all that out, you could have already done a fresh install and restored the files from your current backups into that fresh environment.

If you have any PPAs enabled, disable them, remove that software, then try the update/upgrade again.  If you recall doing direct .deb file installs, but don't remember exactly which ones, then I'd just do a fresh install and restore from backups.  For me, that's between 30 and 45 minutes of effort, so not worth trying to solve this issue.  Plus, you'll have a clean install going forward without the prior release cruft.

---

### Post by #&amp;thj^% on 2023-06-25
I'd be curious if it is fixable at this point. As pointed out PPA's must be either disabled or even better removed and then a "dist-upgrade" needs to be ran. (It helps smooth over all the changes coming in.)
BTW if your interested in fixing or at best trying to fix it show us:
```
find /boot -type f -regex "^.*-generic"

```
You need to free up that broken half installed kernel first though. This will be more or less a point to learn from.

---

### Post by Impavidus on 2023-06-25
```
Generating grub configuration file ...
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
```
No such thing as /etc/grub.d/bin/grubcfg_proxy that I can find in the official repos. /etc/grub.d normally only has some scripts with names starting with two digits followed by an underscore. libcrypto.so.1.1 could be part of libssl1.1, which comes from an older Ubuntu release, but on my laptop it was left behind as a dependency of a printer driver package. It shouldn't really be part of an Ubuntu 22.04 system.

---

### Post by deadflowr on 2023-06-25
Title is backwards as this issue is about removing the package and not installing it.
try
```
sudo mv /var/lib/dpkg/info/linux-image-5.8.0-50-generic.postrm /tmp/
sudo dpkg --remove --force-remove-reinstreq linux-image-5.8.0-50-generic
```

---

### Post by metalfever87 on 2023-06-29
> **deadflowr said:**
> Title is backwards as this issue is about removing the package and not installing it.
try
```
sudo mv /var/lib/dpkg/info/linux-image-5.8.0-50-generic.postrm /tmp/
sudo dpkg --remove --force-remove-reinstreq linux-image-5.8.0-50-generic
```

I ran these commands and this seems to have fixed a portion of the errors but i still seem to have old kernels that cannot be removed in the upgrade process. See below after running sudo apt upgrade:

```

dpkg: error processing package linux-image-5.15.0-76-generic (--configure):
 installed linux-image-5.15.0-76-generic package post-installation script subpro
cess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.19.0-46-generic
 linux-image-5.15.0-76-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I appear to still have the following kernel images:

```

$ dpkg -l |grep linux-image
ii  linux-image-5.15.0-75-generic              5.15.0-75.82                            amd64        Signed kernel image generic
iF  linux-image-5.15.0-76-generic              5.15.0-76.83                            amd64        Signed kernel image generic
ii  linux-image-5.19.0-45-generic              5.19.0-45.46~22.04.1                    amd64        Signed kernel image generic
iF  linux-image-5.19.0-46-generic              5.19.0-46.47~22.04.1                    amd64        Signed kernel image generic
ii  linux-image-generic                        5.15.0.76.74                            amd64        Generic Linux kernel image
ii  linux-image-generic-hwe-20.04              5.15.0.76.74                            amd64        Generic Linux kernel image (dummy transitional package)
ii  linux-image-generic-hwe-22.04              5.19.0.46.47~22.04.21                   amd64        Generic Linux kernel image

```

Which should i remove?

---

### Post by deadflowr on 2023-06-30
Try
```
sudo dpkg --configure -a

or

sudo apt install -f
sudo dpkg --configure -a
```
see if that helps.

> I ran these commands and this seems to have fixed a portion of the errors but i still seem to have old kernels that cannot be removed in the upgrade process. See below after running sudo apt upgrade:


The commands i posted earlier fixed the initial problem.
These are new errors related to new kernels.

Both
```
linux-image-5.15.0-76-generic              5.15.0-76.83    
and 
linux-image-5.19.0-46-generic              5.19.0-46.47~22.04.1 
```
are the newest kernels Ubuntu has released.


Sidenote,
for the record you only need one of these packages
```
linux-image-generic                        
linux-image-generic-hwe-20.04              
linux-image-generic-hwe-22.04 
``` 
and
these two 
```
linux-image-generic                        
linux-image-generic-hwe-20.04
```

provide the exact same kernel.

But I guess deal with that issue when you can actually cross that bridge.

---

### Post by metalfever87 on 2023-06-30
```
$ sudo apt install -f[sudo] password for zac: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  linux-image-5.15.0-75-generic
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
3 not fully installed or removed.
After this operation, 11.6 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 212285 files and directories currently installed.)
Removing linux-image-5.15.0-75-generic (5.15.0-75.82) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-75-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.15.0-75-generic (--remove):
 installed linux-image-5.15.0-75-generic package post-removal script subprocess 
returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.15.0-75-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

$ sudo dpkg --configure -a
Setting up linux-image-5.15.0-76-generic (5.15.0-76.83) ...
Setting up linux-image-5.19.0-46-generic (5.19.0-46.47~22.04.1) ...
Processing triggers for linux-image-5.15.0-76-generic (5.15.0-76.83) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.15.0-76-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.15.0-76-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.15.0-76-generic (--configure):
 installed linux-image-5.15.0-76-generic package post-installation script subprocess returned error exit status 1
Processing triggers for linux-image-5.19.0-46-generic (5.19.0-46.47~22.04.1) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.19.0-46-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.19.0-46-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.19.0-46-generic (--configure):
 installed linux-image-5.19.0-46-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-5.15.0-76-generic
 linux-image-5.19.0-46-generic



```

---

### Post by MAFoElffen on 2023-06-30
Just an idea...

Fix it back to where you can install things again, then install package openssl. openssl provides libcryto.so.1, which should get it past that  error...

Then try to remove that kernel again.

---

### Post by metalfever87 on 2023-06-30
> **MAFoElffen said:**
> Just an idea...

Fix it back to where you can install things again, then install package openssl. openssl provides libcryto.so.1, which should get it past that  error...

Then try to remove that kernel again.


I don't know how to get it back to where I can install again...

---

### Post by TheFu on 2023-06-30
> **metalfever87 said:**
> I don't know how to get it back to where I can install again...

No versioned backups of the system?  Ouch.

---

### Post by MAFoElffen on 2023-06-30
Dang. Apt is locked up isn't it(?) I just thought of a way outside of dpkg and the APT system... Hehehe.

Just found something where that symlink is installed somewhere else (not where i originally thought)... Your error says it is from 'libcrypto.so.1.1' being missing... 

This is where I found that file on my 22.04.2 Server:
```

mafoelffen@Mikes-B460M:~$ find / -name libcrypto.so.1.1 2> /dev/null
/snap/core20/1950/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1
/snap/core20/1891/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1

mafoelffen@Mikes-B460M:~$ sudo snap list core20
Name    Version   Rev   Tracking       Publisher   Notes
core20  20230613  1950  latest/stable  canonical&#10003;  base

```
I haven't seen this problem, if it is really caused from a Snap... Usually you think of Snaps being sand-boxed. But they did strange things to integrate some things Sanp-wise into the system. So lets investigate this further, just to rule it out, for the just-in-cases. 

I have a plan. Since the only instance of 'libcryto.so.1.1' seems to be installed in that Snap, lets make sure that Snap gets replaced.
```

sudo snap refresh core20

``` 
If for some reason that goes south and it doesn't let you reinstall it, coming up with an error similar to this
```

snap "core20" has no updates available

```
Then there is a sneaky way to "trick" Snaps to force it to reinstall.
```

sudo snap refresh core20 --edge
sudo snap refresh core20 --stable

```
Then rerun
```

sudo apt install --fix-broken to see if it gets past that error.

```

---

### Post by MAFoElffen on 2023-06-30
On a sideline curiosity... In your output posted in Post #6, it mentioned that it wasn't going to list i386 packages from a certain repo. 
```

N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 
    'https://brave-browser-apt-release.s3.brave.com stable InRelease' 
    doesn't support architecture 'i386'

```
Thinking that it might only say that if i386 is added as an arch as multi-arch. Curious to see the output of
```

dpkg --print-foreign-architectures

```

---

### Post by metalfever87 on 2023-07-05
```

$ sudo snap refresh core20core20 20230622 from Canonical&#10003; refreshed

```

```

$ sudo apt install --fix-brokenReading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  linux-image-5.15.0-75-generic
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
3 not fully installed or removed.
After this operation, 11.6 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 212285 files and directories currently installed.)
Removing linux-image-5.15.0-75-generic (5.15.0-75.82) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-75-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.15.0-75-generic (--remove):
 installed linux-image-5.15.0-75-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.15.0-75-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

$ dpkg --print-foreign-architectures
i386

```

---

### Post by MAFoElffen on 2023-07-05
Have you tried installing and using 'aptitude'? I just ran onto this with another user on another package where it wouldn't reinstall something, to be able to remove it...

'aptitude' is more user friendly than dpkg and apt, and has more logic built into to it to try to resolve problems.

---

### Post by TheFu on 2023-07-06
**aptitude** can do some great things.  If the proposed solution isn't one that you like, tell it "n", and it will try to find a different solution.  I've had to say "n" 10+ times to get a solution presented that I wanted.  No harm in seeing all the proposed solutions from aptitude and rejecting them all.  Just keep track of the 1 you find that's best of the bad answers, run the command against and select that 1 solution.

BTW metalfever87, there's something odd about the pasted output.  newlines aren't getting pasted correctly or you are pasting lines at the end of others. 
```
$ sudo apt install --fix-brokenReading package lists... Done
```
is an example, it should probably be 
```
$ sudo apt install --fix-broken
Reading package lists... Done
```
Not a big deal for those lines, but with some of the others, it may lead to poor interpretation of the output.

---

### Post by metalfever87 on 2023-07-06
It isn't printing the line return after the initial command even though I have a line return in the copied text. I guess I need to manually add another one

---

### Post by metalfever87 on 2023-07-06
Here's what happens when I try to install aptitude:

```
$ sudo apt-get install aptitude
[sudo] password for zac: Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  aptitude-common libcwidget4 libxapian30
Suggested packages:
  apt-xapian-index aptitude-doc-en | aptitude-doc debtags tasksel
  libcwidget-dev xapian-tools
The following packages will be REMOVED:
  linux-image-5.15.0-75-generic
The following NEW packages will be installed:
  aptitude aptitude-common libcwidget4 libxapian30
0 upgraded, 4 newly installed, 1 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 3,826 kB of archives.
After this operation, 5,659 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 aptitude-common all 0.8.13-3ubuntu1 [1,719 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 libcwidget4 amd64 0.5.18-5build1 [306 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 libxapian30 amd64 1.4.18-4 [701 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 aptitude amd64 0.8.13-3ubuntu1 [1,100 kB]
Fetched 3,826 kB in 1s (6,405 kB/s) 
(Reading database ... 212285 files and directories currently installed.)
Removing linux-image-5.15.0-75-generic (5.15.0-75.82) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-75-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.15.0-75-generic (--remove):
 installed linux-image-5.15.0-75-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.15.0-75-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by TheFu on 2023-07-06
If this were me, I'd have wiped the system 5+ days ago, installed a fresh OS then restored my data, settings and packages from backups.  45 minutes and I'd have a fresh, new system, that had all my data, settings and programs.  Then I'd move on to life or other issues on other systems.  The life of an admin.

Next time around, I'd be 2x more careful loading PPAs and .deb files directly which can lead to "APT hell".  Also, I'd install aptitude BEFORE I need it on the new system. There are a few tools that are best to have pre-installed before they are needed. aptitude, lshw, inxi, ddrescue, testdisk, logwatch are off the top of my head.  I have a repeatable, standard set of things that I always install and configure on every system to deal with issues, monitoring, performance gathering, backup and recovery, and a bunch of aliases to make my life easier.

Is there any reason you aren't wiping the system and starting fresh?

---

### Post by MAFoElffen on 2023-07-07
This would circumvent apt to install aptitude:
Go to one of these mirrors in a browser or get from a terminal to directly download. This is current fro 22.04.2:
```

cd $HOME/Downloads/
wget -N -t 5 -T 10 http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/a/aptitude/aptitude_0.8.13-3ubuntu1_amd64.deb
sudo dpkg -i aptitude_0.8.13-3ubuntu1_amd64.deb

```
But, "We have a problem Houston...

Well... LOL. I have some "creative ideas". You have a recent backup right? If not, take one.

package linux-image-5.8.0-50 was a kernel from HWE 20.04. It doesn't even exist in 22.04.x... That package it orphaned. Since you upgraded to Jammy, it no longer has access to the focal repo's in it's source.list to be able to reinstall it. But it looks lie you need to reinstall it, because it is broken, to be able to remove it... You have to quite using apt for this, because it is spinning you around in circles... back to the same error.

Install that kernel directly, forcing the install, but in a dry run (simulated)...
```

mkdir $HOME/Downloads/kernel-5.8.0-50
cd $HOME/Downloads/kernel-5.8.0-50

# Get the deb packages from Focal
wget -N -t 5 -T 10 http://security.ubuntu.com/ubuntu/pool/main/l/linux-signed-hwe-5.8/linux-image-5.8.0-50-generic_5.8.0-50.56~20.04.1_amd64.deb
wget -N -t 5 -T 10 http://security.ubuntu.com/ubuntu/pool/main/l/linux-hwe-5.8/linux-modules-5.8.0-50-generic_5.8.0-50.56~20.04.1_amd64.deb
wget -N -t 5 -T 10 http://security.ubuntu.com/ubuntu/pool/main/l/linux-hwe-5.8/linux-headers-5.8.0-50-generic_5.8.0-50.56~20.04.1_amd64.deb

# Test it
sudo dpkg -i --dry-run --assert-multi-conrep --debug=2 --abort-after=100 linux-*-5.8.0-50-generic_5.8.0-50.56~20.04.1_amd64.deb | tee -a "./test01.log.txt"

# If all goes well above... Install them
sudo dpkg -i ./linux-*_5.8.0-50.56~20.04.1_amd64.deb

# Then remove
sudo dpkg -r -P linux-headers-5.8.0-50-generic
sudo dpkg -r -P linux-image-5.8.0-50-generic
sudo dpkg -r -P linux-module-5.8.0-50-generic

```
Let's see "how" that goes...

---

