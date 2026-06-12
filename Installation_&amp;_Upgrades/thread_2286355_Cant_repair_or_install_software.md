---
title: "Cant repair or install software"
date: 2015-07-11
forum: Installation &amp; Upgrades
---

### Post by Melotron07 on 2015-07-11
Help :)  Im new to ubuntu and dont know how to fix this.
Herer are the log on my problem :

```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 444629 files and directories currently installed.) 
Preparing to unpack .../linux-image-3.13.0-57-generic_3.13.0-57.95_amd64.deb ... 
Done. 
Unpacking linux-image-3.13.0-57-generic (3.13.0-57.95) ... 
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-57-generic_3.13.0-57.95_amd64.deb (--unpack): 
 cannot copy extracted data for './boot/vmlinuz-3.13.0-57-generic' to '/boot/vmlinuz-3.13.0-57-generic.dpkg-new': failed to write (No space left on device) 
No apport report written because the error message indicates a disk full error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic 
Preparing to unpack .../linux-image-3.13.0-52-generic_3.13.0-52.86_amd64.deb ... 
Done. 
Unpacking linux-image-3.13.0-52-generic (3.13.0-52.86) ... 
No apport report written because the error message indicates a disk full error
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-52-generic_3.13.0-52.86_amd64.deb (--unpack): 
 cannot copy extracted data for './boot/vmlinuz-3.13.0-52-generic' to '/boot/vmlinuz-3.13.0-52-generic.dpkg-new': failed to write (No space left on device) 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-52-generic /boot/vmlinuz-3.13.0-52-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-52-generic /boot/vmlinuz-3.13.0-52-generic 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-image-3.13.0-57-generic_3.13.0-57.95_amd64.deb 
 /var/cache/apt/archives/linux-image-3.13.0-52-generic_3.13.0-52.86_amd64.deb 
Error in function:  
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-57-generic: 
 linux-image-extra-3.13.0-57-generic depends on linux-image-3.13.0-57-generic; however: 
  Package linux-image-3.13.0-57-generic is not installed. 
 
dpkg: error processing package linux-image-extra-3.13.0-57-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-52-generic: 
 linux-image-extra-3.13.0-52-generic depends on linux-image-3.13.0-52-generic; however: 
  Package linux-image-3.13.0-52-generic is not installed. 
 
dpkg: error processing package linux-image-extra-3.13.0-52-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up linux-image-extra-3.13.0-51-generic (3.13.0-51.84) ... 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic 
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic 
update-initramfs: Generating /boot/initrd.img-3.13.0-51-generic 
 
gzip: stdout: No space left on device 
cpio: write error: Broken pipe 
E: mkinitramfs failure cpio 1 gzip 1 
update-initramfs: failed for /boot/initrd.img-3.13.0-51-generic with 1. 
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1 
dpkg: error processing package linux-image-extra-3.13.0-51-generic (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-3.13.0-57-generic; however: 
  Package linux-image-3.13.0-57-generic is not installed. 
 linux-image-generic depends on linux-image-extra-3.13.0-57-generic; however: 
  Package linux-image-extra-3.13.0-57-generic is not configured yet. 
 
dpkg: error processing package linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 3.13.0.57.64); however: 
  Package linux-image-generic is not configured yet. 
 
dpkg: error processing package linux-generic (--configure): 
 dependency problems - leaving unconfigured
```

I tryed to update Plex today but my ubuntu said that its something wrong with a package.
Ive tryed with gui and following commands :
sudo apt-get update -f
sudo apt-get install

But its the same error thats poping up.

Please can anyone tell me whats wrong ??


//Magnus Svensson

---

### Post by oldos2er on 2015-07-11
> gzip: stdout: No space left on device is what's wrong. Can you post the output of ```
df -h
```? Also see [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by Melotron07 on 2015-07-11
```
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  286G  141G  131G  52% /
none                         4,0K     0  4,0K   0% /sys/fs/cgroup
udev                         1,9G  8,0K  1,9G   1% /dev
tmpfs                        387M  1,5M  386M   1% /run
none                         5,0M     0  5,0M   0% /run/lock
none                         1,9G  152K  1,9G   1% /run/shm
none                         100M   48K  100M   1% /run/user
/dev/sda1                    236M  231M     0 100% /boot
/dev/sdb1                     26T   12T   13T  48% /media/magnus/Share
```

Looks as boot are full, how do i increase it ??

---

### Post by Bashing-om on 2015-07-11
Melotron07; Hello;

With a full LVM install it is possible, 
> 
Looks as boot are full, how do i increase it ??

but beyond my experience level to advise the how.
There is a bug open in this respect of /boot partition creation size:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)
You are encouraged to add your voice .

What one can do is practice a tighter house keeping routine and keep the old kernels removed from the boot partition.
Try:
```

sudo apt-get autoremove

```
at this time, and see if apt-get will work. At 100% capacity odds are will not; as there may be no operating head room.

[INDENT][INDENT]easily worth a shot
[/INDENT][/INDENT]

---

### Post by Melotron07 on 2015-07-11
Ive made my voice heard on the bug report.
I have tryed the autoremove but im still standing on the same square.
Herer are the log on the autoremove.

```
magnus@EXXON-SKYNET:~$ sudo apt-get autoremove
[sudo] password for magnus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-52-generic : Depends: linux-image-3.13.0-52-generic but it is not installed
 linux-image-extra-3.13.0-57-generic : Depends: linux-image-3.13.0-57-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-57-generic but it is not installed
E: Unmet dependencies. Try using -f.
magnus@EXXON-SKYNET:~$ 
```

Are there any way to clear out the info manualy and what should i delete??

//Magnus

---

### Post by Bashing-om on 2015-07-11
Melotron07; Hey ;

Yes we can do this manually and get really dirty in that process, let's "try" a cleaner way 1st .
Show us what is presently installed, and the kernel you are booting up with ( we MUST not mess around with this one).
```

uname -r
dpkg -l | grep linux

```
and we see if 'dpkg' will handle this for us.

[INDENT][INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT][INDENT][INDENT]try something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Melotron07 on 2015-07-12
Thanks.

Here are the output : 

```
magnus@EXXON-SKYNET:~$ uname -r
3.13.0-51-generic
magnus@EXXON-SKYNET:~$ dpkg -l | grep linux
ii  libselinux1:amd64                                     2.2.2-1ubuntu0.1                                    amd64        SELinux runtime shared libraries
ii  libv4l-0:amd64                                        1.0.1-1                                             amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                  1.0.1-1                                             amd64        Video4linux frame format conversion library
ii  linux-firmware                                        1.127.13                                            all          Firmware for Linux kernel drivers
iU  linux-generic                                         3.13.0.57.64                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-43                               3.13.0-43.72                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                       3.13.0-43.72                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44                               3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                       3.13.0-44.73                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.83                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.83                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-51                               3.13.0-51.84                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                       3.13.0-51.84                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-52                               3.13.0-52.85                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.85                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-57                               3.13.0-57.95                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                       3.13.0-57.95                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.57.64                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-51-generic                         3.13.0-51.84                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-extra-3.13.0-51-generic                   3.13.0-51.84                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                   3.13.0.57.64                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-52.85                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  pptp-linux                                            1.7.2-7                                             amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                              3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                            2.20.1-5.1ubuntu20.4                                amd64        Miscellaneous system utilities
magnus@EXXON-SKYNET:~$
```

---

### Post by QIII on 2015-07-12
Melotron07:

Please use code tags around any text copied from the terminal.  It makes your posts easier to read and preserves formatting.

To use code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by Melotron07 on 2015-07-12
Thanks :-)
I'm going to do that so it's easier to read. 

//Magnus

---

### Post by dino99 on 2015-07-12
from 'synaptic' select 'installed' on the left pane, to search both 'linux-image' & 'linux-headers' (in 2 steps); and purge (full removal) all the installed found packages but the 2 last kernels. That will make room as expected.

---

### Post by Bashing-om on 2015-07-12
Melotron07; Hey ;

As much as I admire and appreciate 'synaptic' ; I am the more a proponent of the command line. I do assure you that the procedure as outlined by dino99 will be effective.

Do keep in mind the kernel you are booting - 3.13.0-51-generic - and do not remove it .

If you want to proceed with the terminal removal method, well we can.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]more than 1 path to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Melotron07 on 2015-07-13
Thanks :)
But I don't have synaptic installed and cant install any programs.
So I are more or less "forced" to take it in terminal :)

//Magnus Svensson

---

### Post by Bashing-om on 2015-07-13
Melotron07; Hey;

We can do that, Like I say I prefer the command line.

Let's run these commands, see what results. -in the order of operations -

```

sudo dpkg -P linux-image-extra-3.13.0-{32,43,44,46,48}-generic
sudo dpkg -P linux-image-3.13.0-{32,43,44,46,48}-generic
sudo dpkg -P linux-headers-3.13.0-{32,43,44,46,48}-generic
sudo dpkg -P linux-headers-3.13.0-{32,43,44,46,48}

```

Once these run, we get an updated status and see where we stand.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Melotron07 on 2015-07-15
Bashing-om Thanks!

It cleared up alot of space on /boot
```
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  286G  139G  133G  52% /
none                         4,0K     0  4,0K   0% /sys/fs/cgroup
udev                         1,9G   12K  1,9G   1% /dev
tmpfs                        387M  1,5M  385M   1% /run
none                         5,0M     0  5,0M   0% /run/lock
none                         1,9G  152K  1,9G   1% /run/shm
none                         100M   52K  100M   1% /run/user
/dev/sda1                    236M  110M  114M  50% /boot
/dev/sdb1                     26T   12T   13T  48% /media/magnus/Share
```

The repair took some time to repair it all.
But it looks as its working now :))

Thanks alot for the help.

---

### Post by Bashing-om on 2015-07-15
Melotron07; Yeah !


Looks good. Should be good to go.

Are the symlinks (4) re-established for the current booting kernel and the backup ?
Check:
```

ls -al /

```

As you now know you will have to keep an eye on /boot ( df -h ) and remove old kernels ( sudo apt-get autoremove ) as new kernels are installed.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

