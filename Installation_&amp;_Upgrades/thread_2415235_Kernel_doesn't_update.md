---
title: "Kernel doesn't update"
date: 2019-03-22
forum: Installation &amp; Upgrades
---

### Post by cackerso on 2019-03-22
Several months ago I installed Kubuntu 18.04.  I get regular upgrades but the kernel is stuck at 4.15.0.32-generic.  When I do updates I can see newer kernels download but they never install. I think the current one should be 4.15.0.46-generic.

From a suggestion from another forum someone suggested I run the following:

```

uname -r

apt search linux-image | grep installed


``` 
I get:

```

4.15.0-32-generic

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

alsa-base/bionic,bionic,now 1.0.25+dfsg-0ubuntu5 all [installed]
linux-image-4.15.0-31-generic/now 4.15.0-31.33 amd64 [installed,local]
linux-image-4.15.0-32-generic/bionic-updates,bionic-security,now 4.15.0-32.35 amd64 [installed,automatic]

```

From a suggestion I tried a couple of other things:
```

sudo apt update
sudo apt full-upgrade

sudo apt install --reinstall linux-image-generic

```
I got
```

l-k@l-k1804:~$ sudo apt install --reinstall linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
linux-image-generic : Depends: linux-image-4.15.0-47-generic but it is not installable
                      Recommends: thermald but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
l-k@l-k1804:~$

```

The last update Kubuntu installed gave the following output when it ran.
```


Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
 linux-headers-4.15.0-46 linux-headers-4.15.0-46-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
 linux-headers-4.15.0-47 linux-headers-4.15.0-47-generic
The following packages will be upgraded:
 apt apt-utils libapt-inst2.0 libapt-pkg5.0 libnss-systemd libpam-systemd libsystemd0 libsystemd0:i386
 libudev1 libudev1:i386 linux-headers-generic linux-libc-dev opera-stable systemd systemd-sysv udev
16 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/90.7 MB of archives.
After this operation, 90.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 288176 files and directories currently installed.)
Preparing to unpack .../libsystemd0_237-3ubuntu10.16_i386.deb ...
De-configuring libsystemd0:amd64 (237-3ubuntu10.15) ...
Unpacking libsystemd0:i386 (237-3ubuntu10.16) over (237-3ubuntu10.15) ...
Preparing to unpack .../libsystemd0_237-3ubuntu10.16_amd64.deb ...
Unpacking libsystemd0:amd64 (237-3ubuntu10.16) over (237-3ubuntu10.15) ...
Setting up libsystemd0:amd64 (237-3ubuntu10.16) ...
Setting up libsystemd0:i386 (237-3ubuntu10.16) ...
(Reading database ... 288176 files and directories currently installed.)
Preparing to unpack .../0-libnss-systemd_237-3ubuntu10.16_amd64.deb ...
Unpacking libnss-systemd:amd64 (237-3ubuntu10.16) over (237-3ubuntu10.15) ...
Preparing to unpack .../1-libpam-systemd_237-3ubuntu10.16_amd64.deb ...
Unpacking libpam-systemd:amd64 (237-3ubuntu10.16) over (237-3ubuntu10.15) ...
Preparing to unpack .../2-systemd_237-3ubuntu10.16_amd64.deb ...
Unpacking systemd (237-3ubuntu10.16) over (237-3ubuntu10.15) ...
Preparing to unpack .../3-udev_237-3ubuntu10.16_amd64.deb ...
Unpacking udev (237-3ubuntu10.16) over (237-3ubuntu10.15) ...
Preparing to unpack .../4-libudev1_237-3ubuntu10.16_amd64.deb ...
De-configuring libudev1:i386 (237-3ubuntu10.15) ...
Unpacking libudev1:amd64 (237-3ubuntu10.16) over (237-3ubuntu10.15) ...
Preparing to unpack .../5-libudev1_237-3ubuntu10.16_i386.deb ...
Unpacking libudev1:i386 (237-3ubuntu10.16) over (237-3ubuntu10.15) ...
Setting up systemd (237-3ubuntu10.16) ...
(Reading database ... 288176 files and directories currently installed.)
Preparing to unpack .../systemd-sysv_237-3ubuntu10.16_amd64.deb ...
Unpacking systemd-sysv (237-3ubuntu10.16) over (237-3ubuntu10.15) ...
Preparing to unpack .../libapt-pkg5.0_1.6.10_amd64.deb ...
Unpacking libapt-pkg5.0:amd64 (1.6.10) over (1.6.9) ...
Setting up libudev1:amd64 (237-3ubuntu10.16) ...
Setting up libudev1:i386 (237-3ubuntu10.16) ...
Setting up libapt-pkg5.0:amd64 (1.6.10) ...
(Reading database ... 288176 files and directories currently installed.)
Preparing to unpack .../libapt-inst2.0_1.6.10_amd64.deb ...
Unpacking libapt-inst2.0:amd64 (1.6.10) over (1.6.9) ...
Preparing to unpack .../archives/apt_1.6.10_amd64.deb ...
Unpacking apt (1.6.10) over (1.6.9) ...
Setting up apt (1.6.10) ...
(Reading database ...

288177 files and directories currently installed.)
Preparing to unpack .../0-apt-utils_1.6.10_amd64.deb ...
Unpacking apt-utils (1.6.10) over (1.6.9) ...
Preparing to unpack .../1-opera-stable_58.0.3135.107_amd64.deb ...
Unpacking opera-stable (58.0.3135.107) over (58.0.3135.90) ...
Selecting previously unselected package linux-headers-4.15.0-47.
Preparing to unpack .../2-linux-headers-4.15.0-47_4.15.0-47.50_all.deb ...
Unpacking linux-headers-4.15.0-47 (4.15.0-47.50) ...
Selecting previously unselected package linux-headers-4.15.0-47-generic.
Preparing to unpack .../3-linux-headers-4.15.0-47-generic_4.15.0-47.50_amd64.deb ...
Unpacking linux-headers-4.15.0-47-generic (4.15.0-47.50) ...
Preparing to unpack .../4-linux-headers-generic_4.15.0.47.49_amd64.deb ...
Unpacking linux-headers-generic (4.15.0.47.49) over (4.15.0.46.48) ...
Preparing to unpack .../5-linux-libc-dev_4.15.0-47.50_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.15.0-47.50) over (4.15.0-46.49) ...
Setting up libapt-inst2.0:amd64 (1.6.10) ...
Setting up libnss-systemd:amd64 (237-3ubuntu10.16) ...
Setting up linux-headers-4.15.0-47 (4.15.0-47.50) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for ureadahead (0.100.0-20) ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Setting up apt-utils (1.6.10) ...
Setting up systemd-sysv (237-3ubuntu10.16) ...
Setting up linux-libc-dev:amd64 (4.15.0-47.50) ...
Processing triggers for menu (2.1.47ubuntu2.1) ...
Setting up opera-stable (58.0.3135.107) ...
Setting up linux-headers-4.15.0-47-generic (4.15.0-47.50) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up udev (237-3ubuntu10.16) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for shared-mime-info (1.9-2) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for dbus (1.12.2-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Setting up linux-headers-generic (4.15.0.47.49) ...
Setting up libpam-systemd:amd64 (237-3ubuntu10.16) ...
Processing triggers for menu (2.1.47ubuntu2.1) ...
Processing triggers for initramfs-tools (0.130ubuntu3.7) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-32-generic

```

I'm not completely new to Linux but I have no idea how to proceed from here:  And given my level of ignorance I surely don't want to just start messing around and break my installation.

---

### Post by Bashing-om on 2019-03-22
cackerso; Humm ,,,

> 
Package linux-image-generic
bionic-updates (kernel): Generic Linux kernel image 
4.15.0.46.48: amd64 arm64 armhf i386 ppc64el s390x


As -46 is the latest kernel in the repo that begs the question of where you got that -47 (linux-image-generic : Depends: linux-image-4.15.0-47-generic ) version kernel.

[INDENT][INDENT]sometimes we do wonder
[/INDENT][/INDENT]

---

### Post by TheFu on 2019-03-22
Sometimes updates fail because storage is full.  There is 2 types of "full" - no more sectors and no more inodes.

```
df -Th
df -i
```

No need to show any "loop" devices, please remove those if you post the output. Also, please post using _code tags_, like I did the commands above. This makes the output line up and readable in colums by just copy/paste. Too hard to read otherwise.

Another issue is if some .deb files were manually loaded outside the normal repos, then it might be holding the kernels back.  You'll need to figure out which package is doing that and manually remove it, update the system, then find a new version of that troublesome package and install it. This assumes that an acceptable version of the package isn't in the repos now or you can't find a version in a reputable PPA.

But let's check the storage issue first.

I have a few more ideas to resolve dependency issues using aptitude. It is more flexible in solving them by allowing us to reject proposed solutions until the tool provides one that we like.

---

### Post by cackerso on 2019-03-25
Please explain a bit more what's wrong with my posts.  It wasn't clear to me from your explanation.  
Anyway the out put from df -Th
```

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     794M  1.6M  793M   1% /run
/dev/sda6      ext4       29G   12G   16G  44% /
tmpfs          tmpfs     3.9G  183M  3.7G   5% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda9      ext3      210G   38G  162G  19% /mnt/117b8581-f098-4e61-bed9-80573d26f67d
/dev/sda7      ext4      258G   55G  190G  23% /home
/dev/sda5      fuseblk    51G   19G   33G  38% /mnt/72A536C3661B4582
/dev/sda4      fuseblk   244G   79G  166G  33% /mnt/6CC48633C4860016
/dev/sda2      vfat       96M   27M   70M  28% /boot/efi
tmpfs          tmpfs     794M     0  794M   0% /run/user/118
tmpfs          tmpfs     794M   20K  794M   1% /run/user/1000

```

and from df -i
```

Filesystem        Inodes  IUsed     IFree IUse% Mounted on
udev             1007728    583   1007145    1% /dev
tmpfs            1016151    979   1015172    1% /run
/dev/sda6        1921360 330053   1591307   18% /
tmpfs            1016151     92   1016059    1% /dev/shm
tmpfs            1016151      5   1016146    1% /run/lock
tmpfs            1016151     18   1016133    1% /sys/fs/cgroup
/dev/sda9       14032896 281705  13751191    3% /mnt/117b8581-f098-4e61-bed9-80573d26f67d
/dev/sda7       17195008 147892  17047116    1% /home
/dev/sda5       33641000   4377  33636623    1% /mnt/72A536C3661B4582
/dev/sda4      174075340 385236 173690104    1% /mnt/6CC48633C4860016
/dev/sda2              0      0         0     - /boot/efi
tmpfs            1016151     12   1016139    1% /run/user/118
tmpfs            1016151     24   1016127    1% /run/user/1000

```

---

### Post by jeremy31 on 2019-03-25
Is there another Linux distro installed since you installed 18.04?

---

### Post by Impavidus on 2019-03-25
Let's also have a look at```
dpkg --list | grep -v '^rc\|^ii'
```That will show all packages that have not been properly installed or removed. And show```
dpkg --list | grep linux- | grep -v '^rc'
```That will list all kernel and header packages, except those of which only the config files remain (which are, in fact, non-existent).

---

### Post by cackerso on 2019-03-25
In response to Jeremy31.  I have a triple boot set up.  Windows 10 Kubuntu 18.04 and a version of Mint that uses Ubuntu 16.04

In response to Impavidus,

dpkg --list | grep -v '^rc\|^ii'
 gives me
```

esired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                            Version                                     Architecture Description
+++-===============================================-===========================================-============-=====================================================================================================================================================================================================================

```
dpkg --list | grep linux- | grep -v '^rc'
 shows:
```

ii  binutils-x86-64-linux-gnu                       2.30-21ubuntu1~18.04                        amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                      4.5ubuntu1                                  all          Linux image base package
ii  linux-firmware                                  1.173.3                                     all          Firmware for Linux kernel drivers
ii  linux-headers-4.15.0-31                         4.15.0-31.33                                all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-31-generic                 4.15.0-31.33                                amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-32                         4.15.0-32.35                                all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-32-generic                 4.15.0-32.35                                amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-47                         4.15.0-47.50                                all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-47-generic                 4.15.0-47.50                                amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                           4.15.0.47.49                                amd64        Generic Linux kernel headers
ii  linux-image-4.15.0-31-generic                   4.15.0-31.33                                amd64        Signed kernel image generic
ii  linux-image-4.15.0-32-generic                   4.15.0-32.35                                amd64        Signed kernel image generic
ii  linux-libc-dev:amd64                            4.15.0-47.50                                amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-31-generic                 4.15.0-31.33                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-32-generic                 4.15.0-32.35                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-31-generic           4.15.0-31.33                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-32-generic           4.15.0-32.35                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-sound-base                                1.0.25+dfsg-0ubuntu5                        all          base package for ALSA and OSS sound systems

```

---

### Post by TheFu on 2019-03-25
There wasn't anything wrong with prior posts.  Last week I was helping some others who didn't use code tags for things in labels - and both df commands are basically unreadable without the columns lining up, as I asked specifically. Thanks.

The storage has plenty of room, so that ain't the issue.  Which is sorta good, because full storage can be difficult to fix. The other output isn't telling us much either.  Guess we get to do the harder stuff now.  It isn't something easy. ;(

[https://askubuntu.com/questions/772653/how-to-list-broken-packages-in-console](https://askubuntu.com/questions/772653/how-to-list-broken-packages-in-console) says to use :
```
dpkg -l | grep ^..r

dpkg-query -W -f='${db:Status-Abbrev} ${binary:Package}\n' | grep -E ^.[^nci] 

sudo apt-get check

```
You can check the manpages for what each does.  The 2nd one is an example in the dpkg-query manpage.

Any chance that package files were manually removed or the repositories have been removed?

---

### Post by Impavidus on 2019-03-26
As Bashing-om already remarked, the latest version of the header packages installed on your computer is version 4.15.0-47, whereas the latest in the repositories is version 4.15.0-46. Where did you get them? Did you enable the proposed repository? If so, disable it.

The meta-packages to pull in the new kernels are missing. To solve this, you have to install these meta-packages, currently at version 4.15.0.46.48, which, as you wrote in your first post, leads to a conflict.

First make sure the proposed repository is disabled. Then, to prevent any conflict, remove linux-headers-generic:```
sudo apt update
sudo apt remove linux-headers-generic
```It's a meta-package, so that won't harm.

Then install linux-generic:```
sudo apt install linux-generic
```That should pull in all other packages you need.

Post the output of those commands. Stop if you get any errors.

---

### Post by cackerso on 2019-03-27
To answer TheFu, I ran the commands and didn't get any output.

For Impavidus.  Using Muon I looked at the software sources.  I have "backports" enabled.  Also under Updates "pre-released" updates was checked as was "unsupported" updates.  So I disabled those.  
I don't know where I got the header packages.  I've just run regular updates using: 
```

sudo apt-get update && time sudo apt-get dist-upgrade

```
Anyway what proposed repository is listed that would be causing a problem?  How do I disable it?
If the wrong repositories were enabled I did it out of ignorance not knowing what complications they  would cause.

So I'll wait for a reply before proceeding with the rest of the proposal.

---

### Post by Impavidus on 2019-03-27
I don't use muon, but I think pre-released is the same as proposed. That's the repository with the upgrades that haven't been sufficiently tested. Only enable the proposed/pre-release repository if youre willing to help testing the upgrades or if you really can't wait for some critical bug fix. Upgrades from proposed often cause problems. Keep the other repositories enabled.

You got the headers package from the proposed repository. You most likely got a lot of other upgrades from the proposed repository, but if they don't cause problems, there's no need to revert them to the version of the regular repositories. It's just that one header metapackage causing a problem. Just proceed with the commands I suggested yesterday.

---

### Post by cackerso on 2019-03-29
Great! That worked. Thanks.

---

