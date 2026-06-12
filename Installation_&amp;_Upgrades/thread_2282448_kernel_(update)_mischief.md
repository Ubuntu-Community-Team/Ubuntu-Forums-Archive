---
title: "kernel (update) mischief"
date: 2015-06-14
forum: Installation &amp; Upgrades
---

### Post by maclenin on 2015-06-14
During a latest package update run...
```
$ sudo aptitude safe-upgrade
Resolving dependencies...                
The following NEW packages will be installed:
linux-headers-3.2.0-85{a} linux-headers-3.2.0-85-generic{a} 
The following partially installed packages will be configured:
linux-headers-generic 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/12.7 MB of archives. After unpacking 67.8 MB will be used.
Do you want to continue? [Y/n/?] Y
```
...I encountered the following (summary of) error(s):
```

Unpacking linux-headers-3.2.0-85 (from .../linux-headers-3.2.0-85_3.2.0-85.122_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-85_3.2.0-85.122_all.deb (--unpack):
error creating directory `./usr/src/linux-headers-3.2.0-85/arch/m68k/platform/528x': No space left on device
No apport report written because MaxReports has already been reached
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

...

Errors were encountered while processing:
/var/cache/apt/archives/linux-headers-3.2.0-85_3.2.0-85.122_all.deb
/var/cache/apt/archives/linux-headers-3.2.0-85-generic_3.2.0-85.122_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of linux-headers-generic:
linux-headers-generic depends on linux-headers-3.2.0-85-generic; however:
Package linux-headers-3.2.0-85-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
linux-headers-generic
                                         
$

```

At first, my speculation was that I had run out of space for additional kernels in /boot, however, a quick "df" shows:
```
Filesystem                  1K-blocks      Used Available Use% Mounted on
/dev/mapper/vgserver-lvroot  19223252   9300220   8946548  51% /
udev                          1536100         4   1536096   1% /dev
tmpfs                          308772       916    307856   1% /run
none                             5120         0      5120   0% /run/lock
none                          1543860     54012   1489848   4% /run/shm
/dev/mapper/vgserver-lvtmp    9611492    156660   8966592   2% /tmp
/dev/md127                  961431744 230624744 681969020  26% /shared
/dev/sda1                      472036    105779    341886  24% /boot
/dev/mapper/vgserver-lvvar    9611492   1405000   7718252  16% /var
/dev/mapper/vgserver-lvhome 187438988  39194016 138723616  23% /home
/dev/mapper/vgserver-lvopt    9615588    764716   8362424   9% /opt

```
An inspection of the contents of /usr/src reveals 2.9 GB of linux-headers / generic folders from version 3.2.0-23 to 3.2.0-**84**

Curiously, "uname -r", reports...
```
3.2.0-64-generic
```
...and not the 3.2.0-**84**-generic I might have expected.

An "ls" of /boot shows:
```
abi-3.2.0-60-generic
abi-3.2.0-61-generic
abi-3.2.0-63-generic
abi-3.2.0-64-generic
config-3.2.0-60-generic
config-3.2.0-61-generic
config-3.2.0-63-generic
config-3.2.0-64-generic
grub
initrd.img-3.2.0-60-generic
initrd.img-3.2.0-61-generic
initrd.img-3.2.0-63-generic
initrd.img-3.2.0-64-generic
lost+found
memtest86+.bin
memtest86+_multiboot.bin
System.map-3.2.0-60-generic
System.map-3.2.0-61-generic
System.map-3.2.0-63-generic
System.map-3.2.0-64-generic
vmlinuz-3.2.0-60-generic
vmlinuz-3.2.0-61-generic
vmlinuz-3.2.0-63-generic
vmlinuz-3.2.0-64-generic
```

Finally, a run of "sudo apt-get autoremove", yields the following:
```
$ sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
linux-headers-generic : Depends: linux-headers-3.2.0-85-generic but it is not installed
E: Unmet dependencies. Try using -f.
$ 
```

Essentially, the error messages and logical discrepancy between the "active" uname-r (**64**) and the kernel version to which I am attempting to upgrade (**85**) are causing a bit of confusion.

This doesn't strike me as a plain-vanilla autoremove old headers / image job....
 
Thanks for any guidance!

---

### Post by ian-weisser on 2015-06-14
It looks _exactly_ like the usual /boot-is-full situation to me...except for /boot running at 24%
Nevertheless, the no-space-left-on-device error is very specific, so I think that's the best path to try first.

Autoremove doesn't work *after* you run out of space; apt (understandably) can't autoremove until after the system has completed all pending package actions...which won't happen because you're out of space to execute those actions.
Yes, that's a bug. The exact nature of the bug is heavily debated on several relevant bug reports.

Workaround:
Use dpkg, not apt, to remove the -60 kernel. That should free up enough space for apt to complete installing -85, and then to autoremove -61 and -63.
Until the bug is fixed, I suggest running autoremove manually several times a year, or (if you have the 'unattended-upgrades' package installed) enabling autoremove in /etc/apt/apt.conf.d/50unattended-upgrades

---

### Post by bapoumba on 2015-06-14
Thing is, Ian, /boot is 24% full, so I'm not quite sure I understand or there is something very obvious I'm missing :)

@maclenin, do you have precise-updates enabled in your sources.list ?

---

### Post by maclenin on 2015-06-14
Thanks for the replies, folks....

@ian-weisser - indeed, /boot at "merely" 24% is one fact that gives me pause - to say nothing of the (egregiously) non-contiguous kernel upgrade path (i.e. from 64 to 85)....

@bapoumba - both of these "precise-updates" repositories are enabled in sources.list:
```
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
```

---

### Post by bapoumba on 2015-06-14
I'm not familiar with LVM mounts. Would you be running out of inodes ?
```
df -i
```

---

### Post by maclenin on 2015-06-15
...would I, bien sûr!
```
$ df -i
Filesystem                    Inodes   IUsed    IFree IUse% Mounted on
/dev/mapper/vgserver-lvroot  1220608 1213998     6610  100% /
udev                          211536     643   210893    1% /dev
tmpfs                         215416     596   214820    1% /run
none                          215416       3   215413    1% /run/lock
none                          215416     198   215218    1% /run/shm
/dev/mapper/vgserver-lvtmp    610800      72   610728    1% /tmp
/dev/md127                  61054976   89642 60965334    1% /shared
/dev/sda1                     121920     246   121674    1% /boot
/dev/mapper/vgserver-lvvar    610800   11088   599712    2% /var
/dev/mapper/vgserver-lvhome 11902976   86452 11816524    1% /home
/dev/mapper/vgserver-lvopt    610800    2779   608021    1% /opt
$ 
```
So, (as described [here]("http://stackoverflow.com/questions/653096/howto-free-inode-usage")) I've used this command (incrementally)...
```
sudo find . -xdev -type f | cut -d "/" -f 2 | sort | uniq -c | sort -n
```
...to determine that linux "headers" and "generic" folders 3.2.0-23 to 3.2.0-84 in the /usr/src/ folder consume ~86% of the "lvroot" or "/" volume.

The "lvroot" inodes used level (100%) seems to explain the "No space left on device" error.

However, does it help clarify why uname -r reports 3.2.0-64-generic and not 3.2.0-84-generic?

Somewhere at the "root" of this problem could be the fact that I use aptitude as my package update tool (and rarely apt-get), which does NOT incorporate the autoremove "feature" - leaving me (now) with a bloat of retired kernels!

This (referenced [here]("http://ubuntuforums.org/showthread.php?t=1961409&page=4&")) is one dpkg kernel removal solution I have looked at (to address the old kernels issue)...
```
$ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1
```
...however, when I run it (without the purge option) - these are the only two "image" references it lists: 
```
linux-image-3.2.0-60-generic
linux-image-3.2.0-61-generic
```
Shouldn't the dpkg script find associated "image" references for any and all kernel version content currently "present" on the machine (that would be roughly 45 versions, from "-23" to "-84")?

Thanks, again, for the guidance!

---

### Post by ian-weisser on 2015-06-15
> **maclenin said:**
> However, does it help clarify why uname -r reports 3.2.0-64-generic and not 3.2.0-84-generic?
Well, 'uname' reports the currently running kernel, not the newest.
For your kernel version, looks like you are running 12.04.

> **maclenin said:**
> Somewhere at the "root" of this problem could be the fact that I use aptitude as my package update tool (and rarely apt-get), which does NOT incorporate the autoremove "feature" - leaving me (now) with a bloat of retired kernels!
The exact nature of the kernels-don't-autoremove bug is in under debate in several of the relevant bug reports. It has nothing to do with apt-get vs. aptitude, systems using either/both have the bug.
There are several very easy workarounds to prevent the problem from recurring.
Interestingly, aptitude *does* have autoremove (--purge-unused/Aptitude:: Delete-unused) on by default according to the manpage, so I'm rather surprised your system ran into this bug.

> **maclenin said:**
> Shouldn't the dpkg script find associated "image" references for any and all kernel version content currently "present" on the machine (that would be roughly 45 versions, from "-23" to "-84")?

When I parse that dpkg script, seems like it deliberately excludes the current kernel and the newest kernel. Your results seem correct to me.
Do you really have 45 kernel images on your system? You would have quite an inode problem then!

Not every -xx increment gets released to 12.04. With LTS versions, kernel updates should only be semi-annually plus security patches. That's part of the LTS 'stability' concept.
For more frequent kernel updates, you would use 15.04 (current release), or 15.10 (development pre-release)...of course those have their own costs: Frequent upgrading to the next release and occasional reversions, all the costs you tried to avoid when you installed 12.04.

---

### Post by bapoumba on 2015-06-15
```
dpkg --list | grep linux-image
```
Will show you which kernels are installed.

One inode is used per file, one additional per hard link, have you looked at your /usr/src/ to see what is in there ? Running out of inodes usually means a large number (very large number) of files are present. May be some hiccup with one particular kernel ?

---

### Post by maclenin on 2015-06-17
**ian-weisser!**

**A.** > **ian-weisser said:**
> Well, 'uname' reports the currently running kernel, not the newest. For your kernel version, looks like you are running 12.04.
1. Why wouldn't / shouldn't "-84" (i.e. the kernel version just previous to the one being retrieved / downloaded) be the currently *running* kernel?
2. Shouldn't I assume the "12.04 LTS package manager" would allow only "12.04 LTS compatible" kernel versions to be retrieved / downloaded and installed? Is "-84", for example, not a "12.04 LTS compatible" kernel?
2.a. Relatedly - I am also having trouble understanding why kernel versions > "-64" are being downloaded and not installed - or downloaded, at all, if they are not "12.04 LTS compatible"....


**B.** > **ian-weisser said:**
> When I parse that dpkg script, seems like it deliberately excludes the current kernel and the newest kernel. Your results seem correct to me.
Given the results ("ii") in section **C.**, shouldn't the dpkg script...
```
$ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1
```
...display these 3 kernel images (assuming "-64" is the current and "-85" the newest):
```
linux-image-3.2.0-60-generic
linux-image-3.2.0-61-generic
linux-image-3.2.0-63-generic
```


I think I see the problem - inode bloat (e.g. in /usr/src/) - however, I am not yet certain of the cause - and I am trying to suss the most responsive solution.  Does a dpkg removal method still top your list?

Thanks for the explanations.

**bapoumba!**

**C.** 

As suggested:

```
$ dpkg --list | grep linux-image
rc  linux-image-3.2.0-23-generic           3.2.0-23.36                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-24-generic           3.2.0-24.39                             Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-25-generic           3.2.0-25.40                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-26-generic           3.2.0-26.41                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-27-generic           3.2.0-27.43                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-29-generic           3.2.0-29.46                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-30-generic           3.2.0-30.48                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-31-generic           3.2.0-31.50                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-32-generic           3.2.0-32.51                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-33-generic           3.2.0-33.52                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-34-generic           3.2.0-34.53                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-35-generic           3.2.0-35.55                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-36-generic           3.2.0-36.57                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-37-generic           3.2.0-37.58                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-38-generic           3.2.0-38.61                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-39-generic           3.2.0-39.62                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-60-generic           3.2.0-60.91                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-61-generic           3.2.0-61.93                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-63-generic           3.2.0-63.95                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-64-generic           3.2.0-64.97                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
$
```

**D.** 

...and I've used this command (incrementally)...

```
sudo find . -xdev -type f | cut -d "/" -f 2 | sort | uniq -c | sort -n
```
...to determine that linux "headers" and "generic" folders 3.2.0-23 to 3.2.0-84 in the /usr/src/ folder consume ~86% of the "lvroot" or "/" volume.

Thanks, as well, for sticking with this!

Looking forward to marking it all "solved"!

---

### Post by ian-weisser on 2015-06-17
> **maclenin said:**
> 1. Why wouldn't / shouldn't "-84" (i.e. the kernel version just previous to the one being retrieved / downloaded) be the currently *running* kernel?
The Ubuntu Kernel Team frequently updates the 12.04 kernel. They do this to ensure that some problem hasn't crept in. But they don't push every trivial update to LTS users - the entire point of an LTS is that you DON'T get spammed with trivial updates.

Instead, the kernel team only releases security updates. So -85 was a security update. It's likely that -84 and -83 and -82 etc. were not security updates. 
The -85/-84/-83 isn't just for you, it's a number they use internally, too.



> **maclenin said:**
> 2. Shouldn't I assume the "12.04 LTS package manager" would allow only "12.04 LTS compatible" kernel versions to be retrieved / downloaded and installed?
Apt in 12.04 (or any release of Ubuntu) uses a set of sources that will only install compatible packages. It can easily be overridden, but that's not relevant here.



> **maclenin said:**
> Does a dpkg removal method still top your list?
Apt removal tops the list, but you have already tried that.
dpkg removal is the next best option. The easiest way to properly uninstall a single package when apt is unavailable.

These two command should remove the -headers and -image packages of the oldest unused kernel (-60), freeing enough inodes for apt to take over:
```
sudo dpkg --remove linux-headers-3.2.0-60-generic   ## Uninstall old headers first
sudo dpkg --remove linux-image-3.2.0-60-generic     ## Uninstall the old kernel
sudo apt-get autoremove                             ## Install the new kernel, and autoremove the other old kernels
```

---

### Post by ubfan1 on 2015-06-17
> ...to determine that linux "headers" and "generic" folders 3.2.0-23 to  3.2.0-84 in the /usr/src/ folder consume ~86% of the "lvroot" or "/"  volume.
Try using the --purge switch on apt-get remove --purge or the purge argument sudo apt-get purge  on all the ...20s and ...30s version of the above files.  I just use something like:
> apt-cache pkgnames |fgrep "3.2.0-2"
sudo apt-get purge `!!`
To remove all the 20 versions of leftover files. You get a chance to confirm the purge.
repeat for the 30s.

---

### Post by ian-weisser on 2015-06-17
What's the benefit of 'purge' over 'remove' when uninstalling kernel packages?
Kernel package seem to have no files in /etc to purge....

All those -20s and -30s kernel packages are status 'rc' (already removed). They exist only as entries in the package database.

---

### Post by ubfan1 on 2015-06-17
I took the poster's statement to mean there was a lot of space taken with the old kernel directories under /usr/src.
A posting of     sudo du -s /usr/src/*    certainly would clarify how much space is there.  Some may only contain a dead link, some may contain a lot of files.  
I normally use purge, and don't get any leftover stuff under /usr/src.
If the purge does nothing, just manually remove the old directorys to free up space.

---

### Post by maclenin on 2015-06-18
**ian-weisser!**

Aptly enough, this might just do the purge trick for me, in lieu of dpkg - and in this order:

1. identify currently running kernel release
```
$ uname -r
```
2. identify currently installed linux-image releases (marked "ii") 
```
$ dpkg -l | grep linux-image
```
3. select kernel releases for purging (which are NOT identified in steps 1. and 2.) NOTE: Though release "-63" does appear in this list, which I think is an error, as "-63" is marked "ii" in step 2., it ("-63") should probably not be removed (as "-64" is the currently running kernel release).
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1
```
4. [purge]("http://ubuntuforums.org/showthread.php?t=2221389&p=13011472#post13011472") selected linux-image, linux-header and related configuration files (of releases "-25" through "-27", for example) 
```
sudo aptitude purge linux-image-3.2.0-{25..27}-generic
sudo aptitude purge linux-headers-3.2.0-{25..27}
```

ADDENDUM:

Still wondering why these two lists do not "match". Why are the **[COLOR="#FFA07A"]light salmon[/COLOR]** highlights in 1. "missing" their "headers" in 2. Were "-25", "-26", "-27" and "-29" not properly / thoroughly purged at some stage?

1. dpkg -l | grep linux-image
```
rc  **[COLOR="#FFA07A"]linux-image-3.2.0-25-generic[/COLOR]**           3.2.0-25.40                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  **[COLOR="#FFA07A"]linux-image-3.2.0-26-generic[/COLOR]**           3.2.0-26.41                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  **[COLOR="#FFA07A"]linux-image-3.2.0-27-generic[/COLOR]**           3.2.0-27.43                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  **[COLOR="#FFA07A"]linux-image-3.2.0-29-generic[/COLOR]**           3.2.0-29.46                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-30-generic           3.2.0-30.48                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-31-generic           3.2.0-31.50                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-32-generic           3.2.0-32.51                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-33-generic           3.2.0-33.52                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-34-generic           3.2.0-34.53                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-35-generic           3.2.0-35.55                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-36-generic           3.2.0-36.57                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-37-generic           3.2.0-37.58                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-38-generic           3.2.0-38.61                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-39-generic           3.2.0-39.62                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-60-generic           3.2.0-60.91                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-61-generic           3.2.0-61.93                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-63-generic           3.2.0-63.95                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-64-generic           3.2.0-64.97                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
$
```

2. $ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1
```
linux-headers-3.2.0-30
linux-headers-3.2.0-30-generic
linux-headers-3.2.0-31
linux-headers-3.2.0-31-generic
linux-headers-3.2.0-32
linux-headers-3.2.0-32-generic
linux-headers-3.2.0-33
linux-headers-3.2.0-33-generic
linux-headers-3.2.0-34
linux-headers-3.2.0-34-generic
linux-headers-3.2.0-35
linux-headers-3.2.0-35-generic
linux-headers-3.2.0-36
linux-headers-3.2.0-36-generic
linux-headers-3.2.0-37
linux-headers-3.2.0-37-generic
linux-headers-3.2.0-38
linux-headers-3.2.0-38-generic
linux-headers-3.2.0-39
linux-headers-3.2.0-39-generic
linux-headers-3.2.0-40
linux-headers-3.2.0-40-generic
linux-headers-3.2.0-41
linux-headers-3.2.0-41-generic
linux-headers-3.2.0-43
linux-headers-3.2.0-43-generic
linux-headers-3.2.0-44
linux-headers-3.2.0-44-generic
linux-headers-3.2.0-45
linux-headers-3.2.0-45-generic
linux-headers-3.2.0-48
linux-headers-3.2.0-48-generic
linux-headers-3.2.0-49
linux-headers-3.2.0-49-generic
linux-headers-3.2.0-51
linux-headers-3.2.0-51-generic
linux-headers-3.2.0-52
linux-headers-3.2.0-52-generic
linux-headers-3.2.0-53
linux-headers-3.2.0-53-generic
linux-headers-3.2.0-54
linux-headers-3.2.0-54-generic
linux-headers-3.2.0-55
linux-headers-3.2.0-55-generic
linux-headers-3.2.0-56
linux-headers-3.2.0-56-generic
linux-headers-3.2.0-57
linux-headers-3.2.0-57-generic
linux-headers-3.2.0-58
linux-headers-3.2.0-58-generic
linux-headers-3.2.0-59
linux-headers-3.2.0-59-generic
linux-headers-3.2.0-60
linux-headers-3.2.0-60-generic
linux-headers-3.2.0-61
linux-headers-3.2.0-61-generic
linux-headers-3.2.0-63
linux-headers-3.2.0-63-generic
linux-headers-3.2.0-65
linux-headers-3.2.0-65-generic
linux-headers-3.2.0-67
linux-headers-3.2.0-67-generic
linux-headers-3.2.0-68
linux-headers-3.2.0-68-generic
linux-headers-3.2.0-69
linux-headers-3.2.0-69-generic
linux-headers-3.2.0-70
linux-headers-3.2.0-70-generic
linux-headers-3.2.0-72
linux-headers-3.2.0-72-generic
linux-headers-3.2.0-74
linux-headers-3.2.0-74-generic
linux-headers-3.2.0-75
linux-headers-3.2.0-75-generic
linux-headers-3.2.0-76
linux-headers-3.2.0-76-generic
linux-headers-3.2.0-77
linux-headers-3.2.0-77-generic
linux-headers-3.2.0-79
linux-headers-3.2.0-79-generic
linux-headers-3.2.0-80
linux-headers-3.2.0-80-generic
linux-headers-3.2.0-82
linux-headers-3.2.0-82-generic
linux-headers-3.2.0-83
linux-headers-3.2.0-83-generic
linux-headers-3.2.0-84
linux-headers-3.2.0-84-generic
linux-headers-3.2.0-86
$ 
```

Finally, and again - because I am having difficulty grasping this - why would the latest release of the kernel I have downloaded (even for an LTS) not be the one I am running at next re-boot? Are the minor "security" releases simply "subsumed" by the major LTS releases - meaning "-64" (my current LTS release) could be comprised of minor (non-LTS) releases "-65" through "-86" - and would not change (as reported by uname -r) until another major LTS kernel "version", was "released" - say "-99"? At which stage - after downloading and re-boot, uname -r would report:
```
3.2.0-99-generic
```

**ubfan1!**

"I took the poster's statement to mean there was a lot of space taken with the old kernel directories under /usr/src." [Aside: sorry, not certain how to "multi-quote" from multiple posts / threads / etc - and the more so, after a reply has been started....]

...and you were absolutely spot on in your read of my statement. I have ~ 42 [old (< "-63") + new (> "-64")] kernel releases represented in my /usr/src/ directory.

...and I lean towards "purge", as well.

Thanks, again, for the comments.

---

### Post by ian-weisser on 2015-06-18
> **maclenin said:**
> Still wondering why these two lists do not "match". Why are the **[COLOR=#FFA07A]light salmon[/COLOR]** highlights in 1. "missing" their "headers" in 2. Were "-25", "-26", "-27" and "-29" not properly / thoroughly purged at some stage?

Generally, the lists should match.
On my system, they do match.




> **maclenin said:**
> why would the latest release of the kernel I have downloaded (even for an LTS) not be the one I am running at next re-boot?

The newer kernel should be started at next boot.
Part of the kernel post-install script includes a trigger to update the bootloader so your next boot is into the newly-installed kernel.
It's easy for users to override that selection, by manually selecting the kernel at GRUB. Several other ways, too.




 > **maclenin said:**
> Are the minor "security" releases simply "subsumed" by the major LTS releases - meaning "-64" (my current LTS release) could be comprised of minor (non-LTS) releases "-65" through "-86" - and would not change (as reported by uname -r) until another major LTS kernel "version", was "released" - say "-99"?

[EDIT]efflandt's answer below is better. Mine was flat wrong.

---

### Post by efflandt on 2015-06-20
Not sure why your update method choked back at -64 or if it was from failing to clean house of old kernels/headers or changed dependencies were skipped, but the normal update manager has been updating kernels all along. I still have 12.04 on SSD as a backup system (& grub boot drive) and need to remove a couple of old kernels, but it shows the progression of recent kernel versions in 12.04:```
efflandt@XPS-8100-1404:/media/efflandt/1b68a308-8400-41fc-a1f1-0197397f37b7/boot$ ls
abi-3.2.0-82-generic     config-3.2.0-84-generic      initrd.img-3.2.0-85-generic  System.map-3.2.0-85-generic
abi-3.2.0-83-generic     config-3.2.0-85-generic      initrd.img-3.2.0-86-generic  System.map-3.2.0-86-generic
abi-3.2.0-84-generic     config-3.2.0-86-generic      memtest86+.bin               vmlinuz-3.2.0-82-generic
abi-3.2.0-85-generic     grub                         memtest86+_multiboot.bin     vmlinuz-3.2.0-83-generic
abi-3.2.0-86-generic     initrd.img-3.2.0-82-generic  System.map-3.2.0-82-generic  vmlinuz-3.2.0-84-generic
config-3.2.0-82-generic  initrd.img-3.2.0-83-generic  System.map-3.2.0-83-generic  vmlinuz-3.2.0-85-generic
config-3.2.0-83-generic  initrd.img-3.2.0-84-generic  System.map-3.2.0-84-generic  vmlinuz-3.2.0-86-generic
```

---

### Post by maclenin on 2015-06-22
**ian-weisser / efflandt!**

I agree, I think this is the key issue: [QUOTE=efflandt]"Not sure why your update method choked back at -64...."[/QUOTE]

Re: clean-up - there are many ways to "purge" the old kernels - however, why updating "choked" at "-64"? This is the thing, methinks.

Thanks for the guidance!

---

### Post by ian-weisser on 2015-06-22
There are many possible causes.
Searching for a problem that no longer affects you may be difficult. No guarantee of success.

Look in /var/log/apt logs for errors. If the logs don't go back far enough, then I don't see a way forward on that path.

---

### Post by maclenin on 2015-06-23
**ian-weisser!**

Indeed.

PERHAPS, THE "CHOKE" ("-64" TO "-65") AS RECORDED IN HISTORY.LOG.12 - in /var/log/apt/history.log.12.gz - which I probably didn't pay much attention to as "inode drain" was not a problem then and subsequent updates (generally) seemed to proceed (until now) without issue
```
Start-Date: **2014**-06-26  09:41:35
Install: linux-image-3.2.0-65-generic:i386 (3.2.0-65.98, automatic), linux-image-generic:i386 (3.2.0.65.77), linux-generic:i386 (3.2.0.65.77)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: **2014**-06-26  09:41:39

Start-Date: **2014**-06-26  09:43:33
Commandline: apt-get -f install
Install: linux-image-3.2.0-65-generic:i386 (3.2.0-65.98)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: **2014**-06-26  09:43:36
```

CURRENT HISTORY.LOG - in /var/log/apt/history.log
```
Start-Date: **2015**-06-17  19:36:28
Install: linux-headers-3.2.0-86-generic:i386 (3.2.0-86.123, automatic), linux-headers-3.2.0-86:i386 (3.2.0-86.123, automatic)
Upgrade: linux-headers-generic:i386 (3.2.0.85.99, 3.2.0.86.100), inxi:i386 (2.2.21-0ubuntu1~12.04, 2.2.25-0ubuntu1~12.04)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: **2015**-06-17  19:36:45
```

CURRENT TERM.LOG - in /var/log/apt/term.log - this error appeared for "old" kernels {30..39} after running sudo aptitude purge linux-headers-3.2.0-{30..39} 
```
Removing linux-headers-3.2.0-30-generic ...
dpkg: warning: while removing linux-headers-3.2.0-30-generic, directory '/lib/modules/3.2.0-30-generic' not empty so not removed.
Log ended: **2015**-06-22  08:55:20
```

NOTE: /lib/modules/ contains ~ 200 MB in ~ 46 '3.2.0-{23..84}-generic' folders.... Might the larger issue lurk here?

---

### Post by ubfan1 on 2015-06-23
Take a look to see what's been left.  Third party driver's tend not be removed properly, so can cause the /lib/modules directory to be left for that kernel.  Just manually delete this sort of leftover.  If you ever get stuck unable to use the package manager to remove things because you have already removed parts (Why would that even be an error?), you can see what the package manager is complaining is missing, and create it yourself (even an empty file will satisfy a file delete, create directories as needed).  Then the package manager is happy to perform the requested action.

---

### Post by maclenin on 2015-06-25
**ubfan1!**

Thanks for the latest guidance. I guess this (still) leaves me with (at least) 2 questions:

1. Why the kernel upgrade "choke" from "-64" to "-65"? Running out of space - alone - shouldn't prevent the upgrade from completing - once the space issue is resolved? No?

2. Here's a representative sample of "leftovers" in the "not empty so not removed" /lib/module/3.2.0-*-generic folders. Why could these items not be removed using "sudo aptitude purge linux-headers-3.2.0-*"?
```
updates
modules.alias
modules.alias.bin
modules.ccwmap
modules.dep
modules.dep.bin
modules.devname
modules.ieee1394map
modules.inputmap
modules.isapnpmap
modules.ofmap
modules.pcimap
modules.seriomap
modules.softdep
modules.symbols
modules.symbols.bin
modules.usbmap
```

---

### Post by maclenin on 2015-07-29
...with regard to my latest (and still lingering) questions (see preceding post) - thanks to anyone who can help me mark this thread as [SOLVED]!

---

### Post by ubfan1 on 2015-07-29
Not sure about 1), but you seem to be missing linux-image-generic, which may cause the kernel updates.  You can always just install the kernel package you want, but it should be automatic.
2) use the apt-get instead of aptitude, and avoid the wildcards.  If the /lib/modules/... is not completely deleted, it's because of some third party leftover module, so just delete it yourself.

---

### Post by maclenin on 2015-07-30
**ubfan1!**

1. Therein is the thing: "If it broke, fix it...." I hear you re: installing the kernel package I want, however, I'd prefer that the automatic update process work...automatically....
2. I will give the apt-get / wildcard-free purge a go - and report back....

Thanks for the comments.

---

### Post by dino99 on 2015-07-30
The issue you hit:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1439769](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1439769)

please read that report to know why & how to work around it

---

