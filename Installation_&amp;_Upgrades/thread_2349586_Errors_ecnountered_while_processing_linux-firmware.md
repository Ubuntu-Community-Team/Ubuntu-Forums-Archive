---
title: "Errors ecnountered while processing: linux-firmware"
date: 2017-01-16
forum: Installation &amp; Upgrades
---

### Post by vimothy on 2017-01-16
I'm getting an error whenever I try to upgrade my packages. For example:

```
&#10140;  ~ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  redis-server
The following packages will be upgraded:
  python-pymysql xdg-utils
2 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
1 not fully installed or removed.
Need to get 116 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python-pymysql all 0.7.2-1ubuntu1 [56.4 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 xdg-utils all 1.1.1-1ubuntu1.16.04.1 [59.7 kB]
Fetched 116 kB in 0s (1,027 kB/s)   
(Reading database ... 355894 files and directories currently installed.)
Preparing to unpack .../python-pymysql_0.7.2-1ubuntu1_all.deb ...
Unpacking python-pymysql (0.7.2-1ubuntu1) over (0.7.2-1) ...
Preparing to unpack .../xdg-utils_1.1.1-1ubuntu1.16.04.1_all.deb ...
Unpacking xdg-utils (1.1.1-1ubuntu1.16.04.1) over (1.1.1-1ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Ai2zHl/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Ai2zHl/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-36-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-pymysql (0.7.2-1ubuntu1) ...
Setting up xdg-utils (1.1.1-1ubuntu1.16.04.1) ...
Errors were encountered while processing:
 linux-firmware
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm on 16.04. Thanks.

---

### Post by howefield on 2017-01-16
Can you post the output of..

```
df -i
```
```
df -h
```
```
ls -l /boot
```

---

### Post by vimothy on 2017-01-16
Thanks, howefield.

```
&#10140;  ~ df -i      
Filesystem                    Inodes   IUsed    IFree IUse% Mounted on
udev                         2036766     612  2036154    1% /dev
tmpfs                        2041668     934  2040734    1% /run
/dev/mapper/ubuntu--vg-root 30171136 1757573 28413563    6% /
tmpfs                        2041668     161  2041507    1% /dev/shm
tmpfs                        2041668       7  2041661    1% /run/lock
tmpfs                        2041668      18  2041650    1% /sys/fs/cgroup
/dev/sda1                          0       0        0     - /mnt/4AB4-3F10
/dev/sda2                      62496     305    62191    1% /boot
cgmfs                        2041668      14  2041654    1% /run/cgmanager/fs
tmpfs                        2041668      26  2041642    1% /run/user/1001

```

```
&#10140;  ~ df -h      
Filesystem                   Size  Used Avail Use% Mounted on
udev                         7.8G     0  7.8G   0% /dev
tmpfs                        1.6G  9.8M  1.6G   1% /run
/dev/mapper/ubuntu--vg-root  453G  185G  246G  43% /
tmpfs                        7.8G  373M  7.5G   5% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda1                    511M  3.4M  508M   1% /mnt/4AB4-3F10
/dev/sda2                    237M  197M   28M  88% /boot
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        1.6G   40K  1.6G   1% /run/user/1001

```

```
&#10140;  ~ ls -l /boot
total 191254
-rw-r--r-- 1 root root  1241960 Aug 11 20:58 abi-4.4.0-36-generic
-rw-r--r-- 1 root root   189696 Aug 11 20:58 config-4.4.0-36-generic
drwxrwxr-x 3 root root     1024 Jun 25  2016 efi
drwxr-xr-x 5 root root     1024 Jan 15 13:07 grub
-rw-r--r-- 1 root root 12757799 Jul 17  2016 initrd.img-4.4.0-24-generic.old-dkms
-rw-r--r-- 1 root root 12759993 Aug  9 13:19 initrd.img-4.4.0-28-generic.old-dkms
-rw-r--r-- 1 root root 12735125 Aug 31 09:35 initrd.img-4.4.0-31-generic.old-dkms
-rw-r--r-- 1 root root  9161591 Sep 23 09:19 initrd.img-4.4.0-34-generic
-rw-r--r-- 1 root root  7417856 Sep 23 09:17 initrd.img-4.4.0-34-generic.old-dkms
-rw-r--r-- 1 root root 36611239 Sep 18 12:58 initrd.img-4.4.0-36-generic
-rw-r--r-- 1 root root 36611736 Sep  1 09:26 initrd.img-4.4.0-36-generic.old-dkms
-rw-r--r-- 1 root root 10425682 Jan 16 13:36 initrd.img-4.4.0-38-generic
-rw-r--r-- 1 root root 36615822 Sep 23 09:17 initrd.img-4.4.0-38-generic.old-dkms
drwx------ 2 root root    12288 Sep 15  2015 lost+found
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  3867829 Aug 11 20:58 System.map-4.4.0-36-generic
-rw------- 1 root root  7045472 Aug 11 20:58 vmlinuz-4.4.0-36-generic
-rw------- 1 root root  7047384 Sep  1 09:26 vmlinuz-4.4.0-36-generic.efi.signed

```

---

### Post by howefield on 2017-01-16
Is this an encrypted installation ?

I'd try the easy..

```
sudo apt autoremove
```

in an attempt to clear some space in /boot, if that doesn't work then a manual removal of some of the older kernels/images can be done. Let's see what autoremove can do first though.

---

### Post by vimothy on 2017-01-16
Output from autoremove:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_OxCzJ9/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_OxCzJ9/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-36-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-firmware
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ajgreeny on 2017-01-16
```
-rw-r--r-- 1 root root 12757799 Jul 17  2016 initrd.img-4.4.0-24-generic.old-dkms
-rw-r--r-- 1 root root 12759993 Aug  9 13:19 initrd.img-4.4.0-28-generic.old-dkms
-rw-r--r-- 1 root root 12735125 Aug 31 09:35 initrd.img-4.4.0-31-generic.old-dkms
-rw-r--r-- 1 root root  9161591 Sep 23 09:19 initrd.img-4.4.0-34-generic
-rw-r--r-- 1 root root  7417856 Sep 23 09:17 initrd.img-4.4.0-34-generic.old-dkms
-rw-r--r-- 1 root root 36611239 Sep 18 12:58 initrd.img-4.4.0-36-generic
-rw-r--r-- 1 root root 36611736 Sep  1 09:26 initrd.img-4.4.0-36-generic.old-dkms
-rw-r--r-- 1 root root 10425682 Jan 16 13:36 initrd.img-4.4.0-38-generic
-rw-r--r-- 1 root root 36615822 Sep 23 09:17 initrd.img-4.4.0-38-generic.old-dkms
```
I have never seen a listing like that before with those old.dkms files which are taking a lot of space but mostly do not relate to installed kernels.
You appear to have only kernel 4.4.0-36 installed, and 4.4.0-38 which is not yet fully installed and configured, hence it does not show in your listing.  Have you ever manually removed any system files from /boot using either the file manager or a **sudo rm** command?

It would be very helpful to also see the output of command ```
dpkg -l linux-image*
``` which will tell us the state of all the kernels installed, removed, and unconfigured on your machine, and will help us sort out what needs removing.

---

### Post by vimothy on 2017-01-16
Thanks, ajgreeny. I seem to have to manually remove old kernel images periodically to free up space on /boot (using commands described [here]("http://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot")). I've never had this error before though.

```
&#10140;  ~ dpkg -l linux-image*
zsh: no matches found: linux-image*

```

---

### Post by ajgreeny on 2017-01-16
You do not tell us which of the multitude of commands on that linked askubuntu thread you used so it is difficult to know if you have done something you ought to have avoided.

What are the "&#10140;  ~ " characters doing in your shown command?
They should not be there, unless that is something to do with terminal prompts when using **zsh** which I don't know at all. However I can not understand why the dpkg command shows no matches as you obviously must have at least one linux-image installed in order for Ubuntu to run.

---

### Post by vimothy on 2017-01-16
ajgreeny: 

"[COLOR=#000000]&#10140; ~"[/COLOR] is my terminal prompt (the prompt shows my current directory -- it's the default oh-my-zsh prompt). The second line I posted is the output of the command.

The command I've used previously is this one: [COLOR=#111111][FONT=Consolas]dpkg -l linux-{image,headers}-"[0-9]*" | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e '[0-9]' | xargs sudo apt-get -y purge[/FONT][/COLOR]

---

### Post by vimothy on 2017-01-16
BTW, a similar command *does* produce output:

```
&#10140;  ~ dpkg -l linux-image-\*           
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                      Version                   Architecture              Description
+++-=========================================-=========================-=========================-========================================================================================
un  linux-image-3.0                           <none>                    <none>                    (no description available)
rc  linux-image-3.19.0-15-generic             3.19.0-15.15              amd64                     Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-30-generic             3.19.0-30.34              amd64                     Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-31-generic             3.19.0-31.36              amd64                     Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-32-generic             3.19.0-32.37              amd64                     Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-33-generic             3.19.0-33.38              amd64                     Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-34-generic              4.2.0-34.39               amd64                     Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-35-generic              4.2.0-35.40               amd64                     Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-36-generic              4.2.0-36.42               amd64                     Linux kernel image for version 4.2.0 on 64 bit x86 SMP
un  linux-image-4.4.0-34-generic              <none>                    <none>                    (no description available)
ii  linux-image-4.4.0-36-generic              4.4.0-36.55               amd64                     Linux kernel image for version 4.4.0 on 64 bit x86 SMP
un  linux-image-4.4.0-38-generic              <none>                    <none>                    (no description available)
rc  linux-image-extra-3.19.0-15-generic       3.19.0-15.15              amd64                     Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-30-generic       3.19.0-30.34              amd64                     Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-31-generic       3.19.0-31.36              amd64                     Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-32-generic       3.19.0-32.37              amd64                     Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-33-generic       3.19.0-33.38              amd64                     Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-34-generic        4.2.0-34.39               amd64                     Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-35-generic        4.2.0-35.40               amd64                     Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-36-generic        4.2.0-36.42               amd64                     Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-generic        4.4.0-34.53               amd64                     Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-36-generic        4.4.0-36.55               amd64                     Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic        4.4.0-38.57               amd64                     Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP



```

---

### Post by ajgreeny on 2017-01-16
OK, thanks for that; it must be one of the differences between **bash** and **zsh** that caused that lack of output.
You certainly have a lot of kernel configuration still in place by the look of it, but I am still baffled by your original output with all those **initrd.img-4.4.0-##-generic.old-dkms** files which I assume are doing nothing, apart from using about half of the total space available in /boot.

Do not, however just remove them until we have figured out why they are there and what is the best way to get rid of them.
Normally using an **rm** command in such system files is a non-starter so as to keep the filesystem and package management running smoothly, but in this case there may be no other way to deal with it all.
Let's see if anyone else can come up with ideas.
```
-rw-r--r-- 1 root root 12757799 Jul 17  2016 initrd.img-4.4.0-24-generic.old-dkms
-rw-r--r-- 1 root root 12759993 Aug  9 13:19 initrd.img-4.4.0-28-generic.old-dkms
-rw-r--r-- 1 root root 12735125 Aug 31 09:35 initrd.img-4.4.0-31-generic.old-dkms
-rw-r--r-- 1 root root  9161591 Sep 23 09:19 initrd.img-4.4.0-34-generic
-rw-r--r-- 1 root root  7417856 Sep 23 09:17 initrd.img-4.4.0-34-generic.old-dkms
-rw-r--r-- 1 root root 36611239 Sep 18 12:58 initrd.img-4.4.0-36-generic
-rw-r--r-- 1 root root 36611736 Sep  1 09:26 initrd.img-4.4.0-36-generic.old-dkms
-rw-r--r-- 1 root root 10425682 Jan 16 13:36 initrd.img-4.4.0-38-generic
-rw-r--r-- 1 root root 36615822 Sep 23 09:17 initrd.img-4.4.0-38-generic.old-dkms
```

---

### Post by vimothy on 2017-01-16
Thanks. One thing that had been puzzling me was the need to periodically (and reasonably frequently) free up space in /boot. I've not had to do this when I've used Ubuntu in the past.

---

### Post by ajgreeny on 2017-01-17
> **vimothy said:**
> Thanks. One thing that had been puzzling me was the need to periodically (and reasonably frequently) free up space in /boot. I've not had to do this when I've used Ubuntu in the past.
It is a problem that many have found with the newer versions of Ubuntu if using either LVM or encryption, both of which automatically create a separate /boot partition.
Unfortunately the developers did not make that partition large enough for more than approximately 3 kernels to be installed, so it quite quickly becomes overfilled and does not allow further kernels to be installed properly if older kernels are not removed.

If you did not use either LVM or encryption in the past this will not have been a problem as there will not have been a separate /boot partition.

---

### Post by vimothy on 2017-01-17
Ah. It's quite possible I'm using both. It's a work laptop, so I think it's certainly encrypted (I didn't set it up).

---

### Post by ajgreeny on 2017-01-17
Further searching suggests that it is OK to remove the *generic.old-dkms files from boot with an rm command as they are put there not by the package manager but by dkms as a backup when dkms builds modules in your kernel at installation.
See [http://askubuntu.com/questions/863380/can-i-remove-old-dkms-files](http://askubuntu.com/questions/863380/can-i-remove-old-dkms-files)
and [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=717584](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=717584)

You can therefore run command ```
sudo rm /boot/*.old-dkms
``` which will remove just those old and useless files but leave the "real" initrd.img-4.4.0-##-generic files which are needed and created when kernels are installed by the package manager.

---

### Post by vimothy on 2017-01-17
Many thanks for your help. I'm now able to upgrade my packages (although there was some strange output, which I'll post below). Do you think it's likely that I'll have to do this again, at some point?

The output (edited for brevity):

```

...
Setting up linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
WARNING: missing /lib/modules/4.4.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_OyJ9lr/lib/modules/4.4.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_OyJ9lr/lib/modules/4.4.0-38-generic/modules.builtin: No such file or directory
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-34-generic
WARNING: missing /lib/modules/4.4.0-34-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-34-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_wRNXwR/lib/modules/4.4.0-34-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_wRNXwR/lib/modules/4.4.0-34-generic/modules.builtin: No such file or directory
Setting up virtualbox-5.1 (5.1.14-112924~Ubuntu~xenial) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Setting up libdbus-1-3:amd64 (1.10.6-1ubuntu3.3) ...
...
```

I've only run the upgrade once, so I suppose it's possible that this warnings will not appear after the next upgrade.

---

### Post by howefield on 2017-01-18
Looks like you're still way behind on your kernel, I think the current version would be 4.4.0-59

With an encrypted installation as ajgreeny said,  /boot is smaller than it otherwise would be so you'll most likely need to run sudo apt autoremove regularly, diary it every quarter or so.

Alternatively get unattended-upgrades to take care of it, eg [https://ubuntuforums.org/showthread.php?t=2311001&p=13427857&viewfull=1#post13427857](https://ubuntuforums.org/showthread.php?t=2311001&p=13427857&viewfull=1#post13427857)

---

### Post by ajgreeny on 2017-01-18
What does command ```
sudo update-initramfs -u -k all
``` show you as output?

From the dpkg output it should only be giving you an update to the 4.4.0-36 kernel which seems to be the only one fully and properly installed at present.
If it throws errors about 4.4.0-34 it is possibly because there are unnecessary files remaining in /var/lib/initramfs-tools for that kernel version which is no longer fully installed.

I have found suggestions at [http://askubuntu.com/questions/809947/update-initramfs-missing-lib-modules-4-4-0-13-generic](http://askubuntu.com/questions/809947/update-initramfs-missing-lib-modules-4-4-0-13-generic) to remove these extraneous files ```
sudo rm /var/lib/initramfs-tools/4.4.0-34-generic
``` but I am not totally certain what the **un** at the start of the **dpkg -l** output means for that kernel version so hang around for a while yet before going ahead and also show us the output of ```
dpkg -s linux-image-4.4.0-34-generic
``` which ought to give more info on its status in your system. You can the retry that command for the 4.4.0-38 version to see what appears there.

---

