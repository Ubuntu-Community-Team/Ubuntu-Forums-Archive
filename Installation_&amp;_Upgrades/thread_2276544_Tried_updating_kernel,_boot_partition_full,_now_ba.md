---
title: "Tried updating kernel, boot partition full, now badly stuck - HELP!"
date: 2015-05-03
forum: Installation &amp; Upgrades
---

### Post by skyemoor on 2015-05-03
During a kernel update, I received the notice that it failed before completing. Checking the forums, I found various threads on how to solve this. I walked through;

```
sudo apt-get autoremove
```

which returned;

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-lowlatency : Depends: linux-image-3.13.0-51-lowlatency but it is not installed
E: Unmet dependencies. Try using -f.
```

So then I found other hints that started me down this path;

```
df -i
```

which output;

```
df: &#8216;/run/user/1001/gvfs&#8217;: Permission denied
Filesystem                           Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--studio--vg-root  213G  144G   58G  72% /
none                                 4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                 7.7G   12K  7.7G   1% /dev
tmpfs                                1.6G  1.7M  1.6G   1% /run
none                                 5.0M  4.0K  5.0M   1% /run/lock
none                                 7.7G   60M  7.7G   1% /run/shm
none                                 100M   40K  100M   1% /run/user
/dev/sda1                            236M  236M     0 100% /boot
/home/will/.Private                  213G  144G   58G  72% /home/will
```

```
uname -r
```

which outputed;

```
3.13.0-48-lowlatency
```

so then I ran;

```
dpkg -l | grep linux-
```

which gave me;

```
ii  ladspa-sdk                                                  1.13-2                                     amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-firmware                                              1.127.11                                   all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-40                                     3.13.0-40.69                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-lowlatency                          3.13.0-40.69                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-43                                     3.13.0-43.72                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-lowlatency                          3.13.0-43.72                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44                                     3.13.0-44.73                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-lowlatency                          3.13.0-44.73                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-45                                     3.13.0-45.74                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-lowlatency                          3.13.0-45.74                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                                     3.13.0-46.79                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-lowlatency                          3.13.0-46.79                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-48                                     3.13.0-48.80                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-lowlatency                          3.13.0-48.80                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                                     3.13.0-49.81                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-lowlatency                          3.13.0-49.81                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-51                                     3.13.0-51.84                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-lowlatency                          3.13.0-51.84                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-lowlatency                                    3.13.0.51.58                               amd64        lowlatency Linux kernel headers
ii  linux-image-3.13.0-40-lowlatency                            3.13.0-40.69                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-lowlatency                            3.13.0-43.72                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-lowlatency                            3.13.0-44.73                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-lowlatency                            3.13.0-45.74                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-lowlatency                            3.13.0-46.79                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-48-lowlatency                            3.13.0-48.80                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-lowlatency                                      3.13.0.51.58                               amd64        lowlatency Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-49.81                               amd64        Linux Kernel Headers for development
iU  linux-lowlatency                                            3.13.0.51.58                               amd64        Complete lowlatency Linux kernel
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                       all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

I then ran;

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

which returned;

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6-dev : Depends: linux-libc-dev but it is not going to be installed
 linux-headers-lowlatency : Depends: linux-headers-3.13.0-51-lowlatency but it is not going to be installed
 linux-image-lowlatency : Depends: linux-image-3.13.0-51-lowlatency but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

apt-get -f install did now work, then I found a thread that seemed to solve this;

[Try 'apt-get -f install' not working]("http://ubuntuforums.org/showthread.php?t=2273512")

The next step I tried was;

```
sudo dpkg -P linux-headers-3.13.0-{40,43,44,45,46}

```

which resulted in;

```
dpkg: dependency problems prevent removal of linux-headers-3.13.0-40:
 linux-headers-3.13.0-40-lowlatency depends on linux-headers-3.13.0-40.

dpkg: error processing package linux-headers-3.13.0-40 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-43:
 linux-headers-3.13.0-43-lowlatency depends on linux-headers-3.13.0-43.

dpkg: error processing package linux-headers-3.13.0-43 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-44:
 linux-headers-3.13.0-44-lowlatency depends on linux-headers-3.13.0-44.

dpkg: error processing package linux-headers-3.13.0-44 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-45:
 linux-headers-3.13.0-45-lowlatency depends on linux-headers-3.13.0-45.

dpkg: error processing package linux-headers-3.13.0-45 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-46:
 linux-headers-3.13.0-46-lowlatency depends on linux-headers-3.13.0-46.

dpkg: error processing package linux-headers-3.13.0-46 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.13.0-40
 linux-headers-3.13.0-43
 linux-headers-3.13.0-44
 linux-headers-3.13.0-45
 linux-headers-3.13.0-46

```

Then on to the next step in the post, where I inserted the values for my system;

```
sudo dpkg -P linux-headers-3.13.0-{40,43,44,45,46}-lowlatency

```

```
(Reading database ... 534364 files and directories currently installed.)
Removing linux-headers-3.13.0-40-lowlatency (3.13.0-40.69) ...
Removing linux-headers-3.13.0-43-lowlatency (3.13.0-43.72) ...
Removing linux-headers-3.13.0-44-lowlatency (3.13.0-44.73) ...
Removing linux-headers-3.13.0-45-lowlatency (3.13.0-45.74) ...
Removing linux-headers-3.13.0-46-lowlatency (3.13.0-46.79) ...
```

then ran apt-get autoremove again due to the freed-up space, but;

```
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-lowlatency : Depends: linux-image-3.13.0-51-lowlatency but it is not installed
E: Unmet dependencies. Try using -f.
```

so tried apt-get -f install again, and here's where it gets scary;

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  hyphen-en-us libconfig-inifiles-perl libmosquitto0 libnx-x11 libnx-xorg
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-l10n-en-gb
  libreoffice-l10n-en-za mythes-en-au openoffice.org-hyphenation
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-51-lowlatency
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-51-lowlatency
0 upgraded, 1 newly installed, 0 to remove and 119 not upgraded.
2 not fully installed or removed.
Need to get 0 B/51.8 MB of archives.
After this operation, 194 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 486615 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-51-lowlatency_3.13.0-51.84_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-51-lowlatency (3.13.0-51.84) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-51-lowlatency_3.13.0-51.84_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-3.13.0-51-lowlatency' to '/boot/System.map-3.13.0-51-lowlatency.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-51-lowlatency /boot/vmlinuz-3.13.0-51-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-51-lowlatency /boot/vmlinuz-3.13.0-51-lowlatency
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-51-lowlatency_3.13.0-51.84_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

now df -h shows the same thing and I'm back to square one.

**What should I do??**

---

### Post by TheFu on 2015-05-03
Only kernels are placed into /boot/ - that is where the out-of-storage problem lies.

You need to remove old kernels, since /boot is full.  I find that retaining 3 kernels to be the best option and remove all those that are older manually.  Then the extra dependences can be autoremoved - like the headers that were installed as part of the older kernels, now removed.

Is there a specific reason to have all those low-latency kernels?  Looks like you get 2x the kernels because linux-image-lowlatency metapackage is installed. If you don't need it, purge that package too. That would be the fastest way to free up storage in /boot.

---

### Post by skyemoor on 2015-05-03
I've tried more than one way to remove the old kernels, perhaps the ways I tried were not the best due to the unmet dependencies (especially with the hanging new kernel not yet installed). Are there better ways?

---

### Post by Dik_Allison on 2015-05-03
I use bleachbit as root (in the repositories) to remove old kernels, although whether it will work when things have got this upset I don't know.

---

### Post by TheFu on 2015-05-03
> **skyemoor said:**
> I've tried more than one way to remove the old kernels, perhaps the ways I tried were not the best due to the unmet dependencies (especially with the hanging new kernel not yet installed). Are there better ways?

```
sudo apt-get -f purge linux-image-lowlatency
```
doesn't work?
Please post that command with the exact results.  Then you might have to manually remove all the specific lowlatency kernels.
```

sudo apt-get -f purge linux-image-3.13.0-40-lowlatency linux-image-3.13.0-43-lowlatency linux-image-3.13.0-44-lowlatency linux-image-3.13.0-45-lowlatency linux-image-3.13.0-46-lowlatency
```

---

### Post by skyemoor on 2015-05-03
> **TheFu said:**
> ```
sudo apt-get -f purge linux-image-lowlatency
```
doesn't work?
Please post that command with the exact results.  Then you might have to manually remove all the specific lowlatency kernels. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-lowlatency : Depends: linux-image-lowlatency (= 3.13.0.51.58) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

> **TheFu said:**
> 
```

sudo apt-get -f purge linux-image-3.13.0-40-lowlatency linux-image-3.13.0-43-lowlatency linux-image-3.13.0-44-lowlatency linux-image-3.13.0-45-lowlatency linux-image-3.13.0-46-lowlatency
```

```
$sudo apt-get -f purge linux-image-3.13.0-40-lowlatency linux-image-3.13.0-43-lowlatency linux-image-3.13.0-44-lowlatency linux-image-3.13.0-45-lowlatency linux-image-3.13.0-46-lowlatency

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-lowlatency : Depends: linux-image-3.13.0-51-lowlatency but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

So the unmet dependency still seems to be the hanging point.

---

### Post by TheFu on 2015-05-04
> **TheFu said:**
> Is there a specific reason to have all those low-latency kernels?  Looks like you get 2x the kernels because linux-image-lowlatency metapackage is installed. If you don't need it, purge that package too. That would be the fastest way to free up storage in /boot.

???? Do you need the lowlatency kernels?

Put all the lowlatency kernels into the same -purge command so the metapackage AND all individual lowlatency kernels are in the list.

Ref last post here: [https://askubuntu.com/questions/261230/unmet-dependencies-linux-generic](https://askubuntu.com/questions/261230/unmet-dependencies-linux-generic)

---

### Post by matt_symes on 2015-05-04
Hi

AS TheFU pointed out, your *boot* partition is full so deleting the headers that are stored in ```
/usr/src
``` on your *root* partition will not help.

```
sudo dpkg -P linux-image-3.13.0-{40,43}-lowlatency
```

That should delete 2 kernels from your boot partition without using apt. You cannot use apt due to the dependency problems.

If the above command returns successfully then post back.

If it fails then post back the errors.

Kind regards

---

### Post by skyemoor on 2015-05-04
That did the trick;

```
$ sudo dpkg -P linux-image-3.13.0-{40,43}-lowlatency
(Reading database ... 486614 files and directories currently installed.)
Removing linux-image-3.13.0-40-lowlatency (3.13.0-40.69) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-40-lowlatency /boot/vmlinuz-3.13.0-40-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.13.0-40-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-40-lowlatency /boot/vmlinuz-3.13.0-40-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-48-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-48-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-48-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-48-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-46-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-46-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-45-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-45-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-44-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-44-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-43-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-43-lowlatency
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-40-lowlatency (3.13.0-40.69) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-40-lowlatency /boot/vmlinuz-3.13.0-40-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-40-lowlatency /boot/vmlinuz-3.13.0-40-lowlatency
Removing linux-image-3.13.0-43-lowlatency (3.13.0-43.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-lowlatency /boot/vmlinuz-3.13.0-43-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.13.0-43-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-lowlatency /boot/vmlinuz-3.13.0-43-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-48-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-48-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-48-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-48-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-46-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-46-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-45-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-45-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-44-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-44-lowlatency
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-43-lowlatency (3.13.0-43.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-lowlatency /boot/vmlinuz-3.13.0-43-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-lowlatency /boot/vmlinuz-3.13.0-43-lowlatency
dpkg: warning: while removing linux-image-3.13.0-43-lowlatency, directory '/lib/modules/3.13.0-43-lowlatency' not empty so not removed
```

now;

```
$ df -h
df: ‘/run/user/1001/gvfs’: Permission denied
Filesystem                           Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--studio--vg-root  213G  148G   55G  74% /
none                                 4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                 7.7G   12K  7.7G   1% /dev
tmpfs                                1.6G  1.7M  1.6G   1% /run
none                                 5.0M  4.0K  5.0M   1% /run/lock
none                                 7.7G  102M  7.6G   2% /run/shm
none                                 100M   44K  100M   1% /run/user
/dev/sda1                            236M  160M   65M  72% /boot
/home/will/.Private                  213G  148G   55G  74% /home/will

```

Solved! Thanks to everyone for their kind help!

---

### Post by skyemoor on 2015-05-04
Solved!

---

### Post by TheFu on 2015-05-04
This will happen again, if you don't clean up kernels.  Keeping 3 is reasonable.  Now that you ahve working room, do the apt-get update/dist-upgrade cycle, then clean up all the kernels you don't need and set a reminder to do that after every kernel update in the future.  And if you aren't using the low-latency kernels for a specific reason - purge the metapackage AND all those kernels too.

---

### Post by skyemoor on 2015-05-04
Thanks, TheFu, your housecleaning suggestions ring true. The low-latency kernels are for multi-track audio processing with [Ardour]("http://ardour.org/"), to avoid dropouts.

---

