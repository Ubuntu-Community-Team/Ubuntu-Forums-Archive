---
title: "Removing old kernel issue's"
date: 2015-10-07
forum: Installation &amp; Upgrades
---

### Post by kevin134 on 2015-10-07
Hi all.
I'm a linux novice lately when i log into linux a pop up comes up saying 110% on boot.
I've tried to remove old kernel's through package manager which keep's failing.
Any help is appreciated

---

### Post by QDR06VV9 on 2015-10-07
Hi kevin134 there is a nice easy to follow guide here [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)
As suggested be sure to do the dry run first.

---

### Post by kevin134 on 2015-10-07
r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  jsvc libapache-pom-java libcommons-daemon-java libcommons-logging-java
  libcommons-parent-java libjetty-java libservlet2.5-java libslf4j-java
  thermald
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  linux-headers-3.19.0-16* linux-headers-3.19.0-16-generic*
  linux-headers-3.19.0-18* linux-headers-3.19.0-18-generic*
  linux-headers-3.19.0-20* linux-headers-3.19.0-20-generic*
  linux-headers-3.19.0-21* linux-headers-3.19.0-21-generic*
  linux-headers-3.19.0-26* linux-headers-3.19.0-26-generic*
  linux-headers-3.19.0-30* linux-headers-3.19.0-30-generic*
  linux-headers-generic* linux-image-3.13.0-43-generic*
  linux-image-3.16.0-37-generic* linux-image-3.19.0-16-generic*
  linux-image-3.19.0-18-generic* linux-image-3.19.0-20-generic*
  linux-image-3.19.0-21-generic* linux-image-extra-3.13.0-43-generic*
  linux-image-extra-3.16.0-37-generic* linux-image-extra-3.19.0-16-generic
  linux-image-extra-3.19.0-18-generic* linux-image-extra-3.19.0-20-generic*
  linux-image-extra-3.19.0-21-generic* linux-image-extra-3.19.0-30-generic
0 to upgrade, 0 to newly install, 26 to remove and 172 not to upgrade.
3 not fully installed or removed.
After this operation, 1,874 MB disk space will be freed.
(Reading database ... 385065 files and directories currently installed.)
Removing linux-image-extra-3.19.0-16-generic (3.19.0-16.16) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-16-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-16-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-16-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.19.0-30-generic (3.19.0-30.34) ...
depmod: FATAL: could not load /boot/System.map-3.19.0-30-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-30-generic
grep: /boot/config-3.19.0-30-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_UdCbpN/lib/modules/3.19.0-30-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_UdCbpN/lib/modules/3.19.0-30-generic/modules.builtin: No such file or directory

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-30-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.19.0-16-generic
 linux-image-extra-3.19.0-30-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
kevin@kombat87:~$ 
```

this is the output i got back. Can't really understand any of it to be fair.

---

### Post by QDR06VV9 on 2015-10-07
Run this in the terminal
```
sudo apt-get autoremove
```

Then paste back in code tags the results of 
```
[COLOR=#000000][FONT=courier bold]dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"`
[/FONT][/COLOR]
```

---

### Post by kevin134 on 2015-10-07
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

this is the result i'm getting back

Tried again realized software center was open 

here is the outcome

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 gstreamer1.0-libav : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                               libavcodec-extra-56 (>= 6:11.1) but it is not installed
 libav-tools : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                        libavcodec-extra-56 (>= 6:11.2) but it is not installed
 libavdevice55 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                          libavcodec-extra-56 (>= 6:11.2) but it is not installed
 libavfilter5 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                         libavcodec-extra-56 (>= 6:11.2) but it is not installed
 libavformat56 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                          libavcodec-extra-56 (>= 6:11.2) but it is not installed
 libchromaprint0 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                            libavcodec-extra-56 (>= 6:11) but it is not installed
 libmlt6 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                    libavcodec-extra-56 (>= 6:11) but it is not installed
 libopencv-highgui2.4 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                                 libavcodec-extra-56 (>= 6:11~beta1) but it is not installed
 libquicktime2 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                          libavcodec-extra-56 (>= 6:11) but it is not installed
 linux-image-extra-3.19.0-30-generic : Depends: linux-image-3.19.0-30-generic but it is not installed
 vlc : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                libavcodec-extra-56 (>= 6:11.2) but it is not installed
 vlc-nox : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                    libavcodec-extra-56 (>= 6:11.2) but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by QDR06VV9 on 2015-10-07
Do you have a package manager open like synaptic or software center?
if so close them. and try again.

---

### Post by QDR06VV9 on 2015-10-07
Ok it told you the error.
run this
```
sudo [COLOR=#000000]apt-get -f install[/COLOR]
```

---

### Post by kevin134 on 2015-10-07
ok ran it again and got the following

Do you want to continue? [Y/n] Y
(Reading database ... 385057 files and directories currently installed.)
Removing linux-image-extra-3.19.0-16-generic (3.19.0-16.16) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-16-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-16-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-16-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.19.0-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by QDR06VV9 on 2015-10-07
run the command in post #8
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo [/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]apt-get -f install[/FONT][/COLOR][/COLOR]
```

then run the autoremove command again

---

### Post by kevin134 on 2015-10-07
ok ran the commands seem to have same error
gstreamer1.0-libav : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                               libavcodec-extra-56 (>= 6:11.1) but it is not installed
 libav-tools : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                        libavcodec-extra-56 (>= 6:11.2) but it is not installed
 libavdevice55 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                          libavcodec-extra-56 (>= 6:11.2) but it is not installed
 libavfilter5 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                         libavcodec-extra-56 (>= 6:11.2) but it is not installed
 libavformat56 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                          libavcodec-extra-56 (>= 6:11.2) but it is not installed
 libchromaprint0 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                            libavcodec-extra-56 (>= 6:11) but it is not installed
 libmlt6 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                    libavcodec-extra-56 (>= 6:11) but it is not installed
 libopencv-highgui2.4 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                                 libavcodec-extra-56 (>= 6:11~beta1) but it is not installed
 libquicktime2 : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                          libavcodec-extra-56 (>= 6:11) but it is not installed
 linux-image-extra-3.19.0-30-generic : Depends: linux-image-3.19.0-30-generic but it is not installed
 vlc : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                libavcodec-extra-56 (>= 6:11.2) but it is not installed
 vlc-nox : Depends: libavcodec56 (>= 6:11~beta1) but it is not installed or
                    libavcodec-extra-56 (>= 6:11.2) but it is not installed
E: Unmet dependencies. Try using -f.

Would it be best to do a whole clean install?

---

### Post by QDR06VV9 on 2015-10-07
I rarely advise a reinstall but maybe that would be the best in this case.
The errors just seem to grow.
but before you do give the results of
```
df -h
```

---

### Post by kevin134 on 2015-10-07
Filesystem                   Size  Used Avail Use% Mounted on
udev                         1.9G     0  1.9G   0% /dev
tmpfs                        384M  6.0M  378M   2% /run
/dev/mapper/ubuntu--vg-root  455G  360G   73G  84% /
tmpfs                        1.9G  1.9M  1.9G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1                    236M  235M     0 100% /boot
tmpfs                        384M   84K  384M   1% /run/user/1000
/dev/sr0                     1.3G  1.3G     0 100% /media/kevin/Data disc (07 Oct 15)


these are the result's that came back

---

### Post by QDR06VV9 on 2015-10-07
For the most part it looks ok except
> [COLOR=#000000]/dev/mapper/ubuntu--vg-root 455G 360G 73G 84% /[/COLOR]
I have not seen that before personally.
Maybe for time sake here, back-up what you need from this install and do a fresh install
with the "format disk option" in the installer.

---

### Post by Bashing-om on 2015-10-07
kevin134; runrickus; Hey ;

What I see:
> 
/dev/sda1 236M 235M 0 100% /boot

A very small /boot partition that is filled to capacity. With no operating head room I can accept that 'autoremove' can not operate .
Maybe 'dpkg' with the P (Purge) option will work in this instance.
To see what we are going to sic 'dpkg' on, post back - Between code tags -  the outputs of terminal command:
```

dpkg -l | grep linux-

```

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-08
F```
ii  linux-firmware                                       1.143.3                                    all          Firmware for Linux kernel drivers
ii  linux-headers-3.19.0-16                              3.19.0-16.16                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-16-generic                      3.19.0-16.16                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-18                              3.19.0-18.18                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-18-generic                      3.19.0-18.18                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-20                              3.19.0-20.20                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-20-generic                      3.19.0-20.20                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-21                              3.19.0-21.21                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-21-generic                      3.19.0-21.21                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-22                              3.19.0-22.22                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-22-generic                      3.19.0-22.22                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-26                              3.19.0-26.28                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-26-generic                      3.19.0-26.28                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-30                              3.19.0-30.34                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic                      3.19.0-30.34                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                3.19.0.30.29                               amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-43-generic                        3.13.0-43.72                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-37-generic                        3.16.0-37.49                               amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-16-generic                        3.19.0-16.16                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-18-generic                        3.19.0-18.18                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-20-generic                        3.19.0-20.20                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-21-generic                        3.19.0-21.21                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-22-generic                        3.19.0-22.22                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                  3.13.0-43.72                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-37-generic                  3.16.0-37.49                               amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rH  linux-image-extra-3.19.0-16-generic                  3.19.0-16.16                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-18-generic                  3.19.0-18.18                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-20-generic                  3.19.0-20.20                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-21-generic                  3.19.0-21.21                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iF  linux-image-extra-3.19.0-22-generic                  3.19.0-22.22                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-26-generic                  3.19.0-26.28                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rH  linux-image-extra-3.19.0-30-generic                  3.19.0-30.34                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                                 3.19.0-22.22                               amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu4                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                                      3:6.03+dfsg-5ubuntu1                       all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu6                       amd64        Bootloader for Linux/i386 using MS-DOS floppies

```


This is my output, hopefully this is what you ment by using code tags

---

### Post by Bashing-om on 2015-10-08
kevin134; Yeah !

Now that is what I am talking about.
You have lots of old kernels that need to be removed.
We will try and do that with ' dpkg' . However, There exist a slight hitch in the plan:
> 
rH  linux-image-extra-3.19.0-16-generic
rH  linux-image-extra-3.19.0-30-generic
iF  linux-image-extra-3.19.0-22-generic
rc  linux-image-extra-3.19.0-26-generic
rH  linux-image-extra-3.19.0-30-generic

Where the status indicators ( 1st column ) :
r=removed
i=installed, but
F=halF configured 
H=Half installed
c=config files remain

Before we proceed and see what transpires. I need to know what we are working with and the kernel that is presently booted .
Post back - between code tags to maintain formatting and promote the readability - of terminal commands:
```


lsb_release -a
uname -r

```

Once I know these, we take a gentle poke at the situation and see how those partial kernels are going to effect the issue of removal  of all the old kernels.

[INDENT][INDENT]this could be a trying situation
[/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-08
ok so here is my results so far.
 ```

]No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

3.19.0-22-generic
  
```

---

### Post by Bashing-om on 2015-10-08
kevin134; K .........

Let's take that gentle poke at it and see what results:
```

sudo dpkg -P linux-image-3.13.0-43-generic

```

Depending on if it bites back is what we do.

[INDENT][INDENT]we see what it is
[/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-08
I've done the following command here is my outcome
 
```

dpkg: dependency problems prevent removal of linux-image-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic.

dpkg: error processing package linux-image-3.13.0-43-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.13.0-43-generic
 

 
```

---

### Post by Bashing-om on 2015-10-08
kevin134; oopppss ..

That one is my bad .. OK 
Let us do as the package manager advises:
```

sudo dpkg -P linux-image-extra-3.13.0-43-generic
sudo dpkg -P linux-image-3.13.0-43-generic

```

The good thing is those partial kernel installs are NOT noted to this time as a issue .

[INDENT][INDENT]still just a gentle poke
[/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-08
Ok so ran both and here is the outcome
```

(Reading database ... 384627 files and directories currently installed.)
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-43-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic

second outcome

(Reading database ... 380708 files and directories currently installed.)
Removing linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found initrd image: /boot/initrd.img-3.16.0-37-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic


 
```

---

### Post by Bashing-om on 2015-10-08
kevin134; Ouch !

This is really killing us .
> 
gzip: stdout: No space left on device
 absolutely no operating head room !

Let's try:
```

sudo dpkg -P linux-image-extra-3.19.0-16-generic
sudo dpkg -P linux-headers-3.19.0-16-generic
sudo dpkg -P linux-headers-3.19.0-16

```

Maybe we will have to get
[INDENT][INDENT][INDENT]real dirty
[/INDENT][/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-08
Isn't it just having a real bad headache from it haha.
ok i'll run these and copy the outcome 

So far all seem's to be well i think. Boot is now down to 96%

 ```

Reading database ... 380810 files and directories currently installed.)
Removing linux-image-extra-3.19.0-16-generic (3.19.0-16.16) ...
Purging configuration files for linux-image-extra-3.19.0-16-generic (3.19.0-16.16) ...

(Reading database ... 380810 files and directories currently installed.)
Removing linux-headers-3.19.0-16-generic (3.19.0-16.16) ...

(Reading database ... 371677 files and directories currently installed.)
Removing linux-headers-3.19.0-16 (3.19.0-16.16) ...


 
```

---

### Post by Bashing-om on 2015-10-08
kevin134; Yeah !

Looks like we pushed the right button.
Next let's finish off those partials:
```

sudo dpkg -P linux-image-extra-3.19.0-22-generic
sudo dpkg -P linux-headers-3.19.0-22-generic
sudo dpkg -P linux-headers-3.19.0-22

sudo dpkg -P linux-image-extra-3.19.0-26-generic
sudo dpkg -P linux-headers-3.19.0-26-generic
sudo dpkg -P linux-headers-3.19.0-26

sudo dpkg -P linux-image-extra-3.19.0-30-generic 
sudo dpkg -P linux-headers-3.19.0-30-generic
sudo dpkg -P linux-headers-3.19.0-30

```

[INDENT][INDENT]Maybe now we have
[INDENT][INDENT][INDENT]room to think about it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-08
I've come across a hiccup I can't seem to put those in at the moment as laptop restarted and when it booted up no connections was being detected too the internet. Hdmi is plugged into tv and laptop that's not being detected as well as usb. Any help would be greatly appreciated

---

### Post by Bashing-om on 2015-10-08
kevin134; Ouch !

Again my bad ! Removing the currently booting kernel ! Ouch again ouch ! .. the version 22 gave me tunnel vision as it only partially installed.
OK, we can fix !
Boot to the grub boot menu and boot the 3.19.0-21 kernel .

Do you now boot up to the GUI ? If so we continue to clean up and finish this up .

[INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-08
I actually have no idea :(

---

### Post by Bashing-om on 2015-10-08
kevin134; Hey;

Not to know is not a sin.
Panic not. Just proceed in a calm and orderly fashion.

Reboot the box and as soon as the bios screen clears depress and hold a shift key -> grub boot menu -> advanced options and select the -21 kernel to boot.

If this is a UEFI system it is the escape key that grub recognizes, there is but a 3 second window of opportunity so repeatedly depress/release the escape key.

Once you are booted up we continue.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2015-10-09
You know I do not want to come across Cheeky here, But I sure hope kevin134 comes back with a show of apreciation for the efforts Bashing-om displayed here, and hopefuly with a sucessful outcome. 
Trying hard not to sound harsh or even strong here.:D


;)@Bashing-om I know you don't like your own Horn tuted here so I will take the opertunity to say it** KUDO's to you**, Above the call of expections. **"Valueable Member".**
Albeit I think the time invested to do this was way longer than a freshly installed OS.(Just my 2 cents worth). 
Hopefuly the OP will come away with more knowledge of Ubuntu or even Linux.
Although wildcards tend to work well with apt-get, they don't work too well with dpkg directly (at least, not as far as I can tell).
Kind Regards

---

### Post by Bashing-om on 2015-10-09
@ runrickus; Blushing for sure.

But here I sure messed up, if it were not for my error the situation would likely be resolved at this point.
I am a firm believer in "fixing" as a primary means to become comfortable with this our operating system by choice.
I have ( and sometimes still do ) broke my system(s) many times in this learning process. The suburb documentation and support makes fixing any issue a real possibility. Fixing my issues was that means by which I have learned. I being a strong advocate of open source, I just pass it on .

However, with a good backup plan it only takes 30 minutes to (RE-)install and back up with no loss . But, but as we know ... re-installing we learn little.

Presently:
@ kevin134 . What is the status ? Can you boot an alternate kernel ? Or do we have to get the more aggressive ?

[INDENT][INDENT]it is 'buntu
[INDENT][INDENT][INDENT]together we do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-10-12
kevin134; Hello;

Request to know the status of the situation ?

Are you able to boot an older kernel ?

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-13
Hey sorry for the late reply was away throughout the weekend. So has been a really busy time. I am currently having problems with the laptop keyboard the keys won't work so this Friday I'll need to get myself a keyboard to continue fixing the issue. 
I am absolutely grateful for the help I have received and I am a firm beliver this will be resolved by end of this week :)

---

### Post by kevin134 on 2015-10-13
Ok I have managed to boot into a older kernel I believe so if you could kindly guide me from here that would be absolutely brilliant and of course all help is greatly appreciated

---

### Post by Bashing-om on 2015-10-13
kevin134; Outstanding ..

Let us continue on .. by some means.
OK, booting an older kernel .. need to know which kernel - so I do not remove it too ! -
```

uname -r

```

Let's look and see if there is any damage to repair:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```

I do not anticipate a problem .. but Prior Prudent Planning .. If I had exercised more we would be done by now .

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-13
ok so here is my current running kernel [URL="http://ubuntuforums.org/misc.php?do=bbcode#code"]```
[/URL]
3.19.0-22-generic

and the outcome from the following code's.
total 40
drwxr-xr-x 10 root root 4096 Oct  8 23:16 .
drwxr-xr-x 10 root root 4096 Jul 22  2014 ..
drwxr-xr-x 24 root root 4096 May 24 12:02 linux-headers-3.19.0-18
drwxr-xr-x  7 root root 4096 May 24 12:02 linux-headers-3.19.0-18-generic
drwxr-xr-x 24 root root 4096 Jul 12 11:52 linux-headers-3.19.0-22
drwxr-xr-x  7 root root 4096 Jul 12 11:52 linux-headers-3.19.0-22-generic
drwxr-xr-x 24 root root 4096 Sep  1 05:56 linux-headers-3.19.0-26
drwxr-xr-x  7 root root 4096 Sep  1 05:56 linux-headers-3.19.0-26-generic
drwxr-xr-x 24 root root 4096 Oct  7 14:32 linux-headers-3.19.0-30
drwxr-xr-x  7 root root 4096 Oct  7 14:32 linux-headers-3.19.0-30-generic

total 40
drwxr-xr-x 10 root root 4096 Oct  8 22:35 .
drwxr-xr-x 25 root root 4096 May  6 19:09 ..
drwxr-xr-x  5 root root 4096 May 24 12:00 3.16.0-37-generic
drwxr-xr-x  5 root root 4096 Oct  8 23:01 3.19.0-16-generic
drwxr-xr-x  5 root root 4096 Jul 20 21:58 3.19.0-18-generic
drwxr-xr-x  5 root root 4096 Oct  8 23:15 3.19.0-20-generic
drwxr-xr-x  5 root root 4096 Oct  8 23:16 3.19.0-21-generic
drwxr-xr-x  5 root root 4096 Oct  8 14:14 3.19.0-22-generic
drwxr-xr-x  2 root root 4096 Oct  7 15:29 3.19.0-26-generic
drwxr-xr-x  5 root root 4096 Oct  8 23:14 3.19.0-30-generic

total 210936
drwxr-xr-x  4 root root     3072 Oct  8 23:14 .
drwxr-xr-x 23 root root     4096 Oct  8 23:00 ..
-rw-r--r--  1 root root  1206938 Apr 29 22:17 abi-3.16.0-37-generic
-rw-r--r--  1 root root  1268815 Apr 30 18:23 abi-3.19.0-16-generic
-rw-r--r--  1 root root  1269284 May 19 20:45 abi-3.19.0-18-generic
-rw-r--r--  1 root root  1269462 May 29 12:02 abi-3.19.0-20-generic
-rw-r--r--  1 root root  1269462 Jun 14 20:44 abi-3.19.0-21-generic
-rw-r--r--  1 root root  1269462 Jun 16 19:30 abi-3.19.0-22-generic
-rw-r--r--  1 root root  1271518 Oct  3 01:04 abi-3.19.0-30-generic
-rw-r--r--  1 root root   171808 Apr 29 22:17 config-3.16.0-37-generic
-rw-r--r--  1 root root   177656 Apr 30 18:23 config-3.19.0-16-generic
-rw-r--r--  1 root root   177700 May 19 20:45 config-3.19.0-18-generic
-rw-r--r--  1 root root   177700 May 29 12:02 config-3.19.0-20-generic
-rw-r--r--  1 root root   177700 Jun 14 20:44 config-3.19.0-21-generic
-rw-r--r--  1 root root   177705 Jun 16 19:30 config-3.19.0-22-generic
-rw-r--r--  1 root root   177722 Oct  3 01:04 config-3.19.0-30-generic
drwxr-xr-x  5 root root     1024 Oct  8 23:15 grub
-rw-r--r--  1 root root  4459255 Oct  8 22:59 initrd.img-3.13.0-43-generic
-rw-r--r--  1 root root 21407121 May  6 18:28 initrd.img-3.16.0-37-generic
-rw-r--r--  1 root root  7888925 Oct  8 22:59 initrd.img-3.19.0-16-generic
-rw-r--r--  1 root root 21769704 May 28 12:26 initrd.img-3.19.0-18-generic
-rw-r--r--  1 root root 21773256 Jun 12 09:34 initrd.img-3.19.0-20-generic
-rw-r--r--  1 root root 21770960 Jun 28 14:17 initrd.img-3.19.0-21-generic
-rw-r--r--  1 root root 21769058 Jul 12 11:54 initrd.img-3.19.0-22-generic
-rw-r--r--  1 root root  4459322 Oct  7 15:29 initrd.img-3.19.0-26-generic
-rw-r--r--  1 root root  7892809 Oct  8 23:14 initrd.img-3.19.0-30-generic
drwx------  2 root root    12288 Dec 19  2014 lost+found
-rw-r--r--  1 root root   164216 Mar  6  2015 memtest86+.bin
-rw-r--r--  1 root root   165892 Mar  6  2015 memtest86+.elf
-rw-r--r--  1 root root   166396 Mar  6  2015 memtest86+_multiboot.bin
-rw-------  1 root root  3502913 Apr 29 22:17 System.map-3.16.0-37-generic
-rw-------  1 root root  3615358 Apr 30 18:23 System.map-3.19.0-16-generic
-rw-------  1 root root  3616263 May 19 20:45 System.map-3.19.0-18-generic
-rw-------  1 root root  3617303 May 29 12:02 System.map-3.19.0-20-generic
-rw-------  1 root root  3617303 Jun 14 20:44 System.map-3.19.0-21-generic
-rw-------  1 root root  3617446 Jun 16 19:30 System.map-3.19.0-22-generic
-rw-------  1 root root  3622042 Oct  3 01:04 System.map-3.19.0-30-generic
-rw-------  1 root root  6414336 Apr 29 22:17 vmlinuz-3.16.0-37-generic
-rw-------  1 root root  6611904 Apr 30 18:23 vmlinuz-3.19.0-16-generic
-rw-------  1 root root  6614144 May 19 20:45 vmlinuz-3.19.0-18-generic
-rw-------  1 root root  6616960 May 29 12:02 vmlinuz-3.19.0-20-generic
-rw-------  1 root root  6617408 Jun 14 20:44 vmlinuz-3.19.0-21-generic
-rw-------  1 root root  6616448 Jun 16 19:30 vmlinuz-3.19.0-22-generic
-rw-------  1 root root  6623936 Oct  3 01:04 vmlinuz-3.19.0-30-generic

ii  linux-firmware                                       1.143.3                                    all          Firmware for Linux kernel drivers
ii  linux-headers-3.19.0-18                              3.19.0-18.18                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-18-generic                      3.19.0-18.18                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-22                              3.19.0-22.22                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-22-generic                      3.19.0-22.22                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-26                              3.19.0-26.28                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-26-generic                      3.19.0-26.28                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-30                              3.19.0-30.34                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic                      3.19.0-30.34                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                3.19.0.30.29                               amd64        Generic Linux kernel headers
ii  linux-image-3.16.0-37-generic                        3.16.0-37.49                               amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-16-generic                        3.19.0-16.16                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-18-generic                        3.19.0-18.18                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-20-generic                        3.19.0-20.20                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-21-generic                        3.19.0-21.21                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-22-generic                        3.19.0-22.22                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic                        3.19.0-30.34                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-37-generic                  3.16.0-37.49                               amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-18-generic                  3.19.0-18.18                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-20-generic                  3.19.0-20.20                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-21-generic                  3.19.0-21.21                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-22-generic                  3.19.0-22.22                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-26-generic                  3.19.0-26.28                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-30-generic                  3.19.0-30.34                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                                 3.19.0-22.22                               amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu4                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                                      3:6.03+dfsg-5ubuntu1                       all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu6                       amd64        Bootloader for Linux/i386 using MS-DOS floppies


[URL="http://ubuntuforums.org/misc.php?do=bbcode#code"]
```[/URL]

---

### Post by Bashing-om on 2015-10-13
kevin134; OK;


Continue to always boot the -22 version kernel, so I do not loose track of what we can remove.

As we look we can see several disparities within the directories.
Let's see what the package manager can do to set things aright, or give us some hints what the package manager needs.
Run terminal commands:
```

sudo dpkg -P linux-image-3.13.0-43-generic

sudo dpkg -P linux-image-3.16.0-37-generic
sudo dpkg -P linux-image-extra-3.16.0-37-generic

sudo dpkg _P linux-image-3.19.0-16-generic

sudo dpkg -P linux-headers-3.19.0-26-generic 
sudo dpkg -P linux-headers-3.19.0-26
sudo dpkg -P linux-image-extra-3.19.0-26-generic

```
Where 'P' is Purge -- remove the <package> and all it's config files.
Let us not get dirty with this unless we absolutely must; hoping the package manager will do our work for us. If not, we do get dirty.
We must get all the directories to match. This is the 1st step in trying to get them all consistent. If the package manager works for us in this one instance, we may be able to continue within the graces of the package management system.

How much head room do we now have ?
Please show:
```

df -h

``` see if now we can (RE-)install our working -22 version kernel .


[INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-14
Ok so i've enetered the first few and seem to encounter error's

```
 dpkg: warning: ignoring request to remove linux-image-3.13.0-43-generic which isn't installed

dpkg: dependency problems prevent removal of linux-image-3.16.0-37-generic:
 linux-image-extra-3.16.0-37-generic depends on linux-image-3.16.0-37-generic.

dpkg: error processing package linux-image-3.16.0-37-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.16.0-37-generic

so i went and did df -h
which came out with




Filesystem                   Size  Used Avail Use% Mounted on
udev                         1.9G     0  1.9G   0% /dev
tmpfs                        384M  6.0M  378M   2% /run
/dev/mapper/ubuntu--vg-root  455G  329G  103G  77% /
tmpfs                        1.9G  1.5M  1.9G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1                    236M  215M  8.5M  97% /boot
tmpfs                        384M   76K  384M   1% /run/user/1000
/dev/sr0                     3.9G  3.9G     0 100% /media/kevin/ON_DISC


```

Would synaptic package manager be best too remove the remaining kernel's if so which one's would i be able to get rid of?

---

### Post by Bashing-om on 2015-10-14
kevin134; Welp;

Some what disappointed. but not at all surprised.
As to synaptic .. yeah quite possible, but has been some time since I have used the utility . and am not comfortable offering advise in that respect. Synaptic is a graphical front end for what we are doing in terminal. With the terminal interface we get a much better, clearer dialog as to what is going on.

As we do not have the operating head room to this time. let's get down and dirty. We manually jerk the rug out from under the package manger by removing the kernel support files, have the package manager heal it's self, and then clean up the mess.

Post back a freshened "look" at what we are working with :
```

uname -r
ls -al /usr/src/
ls -al /lib/modules/ 
ls -al /boot
dpkg -l | grep linux-

```

And we roll our sleeves up and go to work.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT][INDENT]more than 1 way to one end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-15
ok so here goes

```

3.19.0-22-generic

total 36
drwxr-xr-x  9 root root 4096 Oct 14 10:27 .
drwxr-xr-x 10 root root 4096 Jul 22  2014 ..
drwxr-xr-x 24 root root 4096 May 24 12:02 linux-headers-3.19.0-18
drwxr-xr-x  7 root root 4096 May 24 12:02 linux-headers-3.19.0-18-generic
drwxr-xr-x 24 root root 4096 Jul 12 11:52 linux-headers-3.19.0-22
drwxr-xr-x  7 root root 4096 Jul 12 11:52 linux-headers-3.19.0-22-generic
drwxr-xr-x 24 root root 4096 Sep  1 05:56 linux-headers-3.19.0-26
drwxr-xr-x 24 root root 4096 Oct  7 14:32 linux-headers-3.19.0-30
drwxr-xr-x  7 root root 4096 Oct  7 14:32 linux-headers-3.19.0-30-generic


total 40
drwxr-xr-x 10 root root 4096 Oct  8 22:35 .
drwxr-xr-x 25 root root 4096 May  6 19:09 ..
drwxr-xr-x  5 root root 4096 May 24 12:00 3.16.0-37-generic
drwxr-xr-x  5 root root 4096 Oct  8 23:01 3.19.0-16-generic
drwxr-xr-x  5 root root 4096 Jul 20 21:58 3.19.0-18-generic
drwxr-xr-x  5 root root 4096 Oct  8 23:15 3.19.0-20-generic
drwxr-xr-x  5 root root 4096 Oct  8 23:16 3.19.0-21-generic
drwxr-xr-x  5 root root 4096 Oct  8 14:14 3.19.0-22-generic
drwxr-xr-x  2 root root 4096 Oct 14 10:27 3.19.0-26-generic
drwxr-xr-x  5 root root 4096 Oct  8 23:14 3.19.0-30-generic

total 210936
drwxr-xr-x  4 root root     3072 Oct  8 23:14 .
drwxr-xr-x 23 root root     4096 Oct  8 23:00 ..
-rw-r--r--  1 root root  1206938 Apr 29 22:17 abi-3.16.0-37-generic
-rw-r--r--  1 root root  1268815 Apr 30 18:23 abi-3.19.0-16-generic
-rw-r--r--  1 root root  1269284 May 19 20:45 abi-3.19.0-18-generic
-rw-r--r--  1 root root  1269462 May 29 12:02 abi-3.19.0-20-generic
-rw-r--r--  1 root root  1269462 Jun 14 20:44 abi-3.19.0-21-generic
-rw-r--r--  1 root root  1269462 Jun 16 19:30 abi-3.19.0-22-generic
-rw-r--r--  1 root root  1271518 Oct  3 01:04 abi-3.19.0-30-generic
-rw-r--r--  1 root root   171808 Apr 29 22:17 config-3.16.0-37-generic
-rw-r--r--  1 root root   177656 Apr 30 18:23 config-3.19.0-16-generic
-rw-r--r--  1 root root   177700 May 19 20:45 config-3.19.0-18-generic
-rw-r--r--  1 root root   177700 May 29 12:02 config-3.19.0-20-generic
-rw-r--r--  1 root root   177700 Jun 14 20:44 config-3.19.0-21-generic
-rw-r--r--  1 root root   177705 Jun 16 19:30 config-3.19.0-22-generic
-rw-r--r--  1 root root   177722 Oct  3 01:04 config-3.19.0-30-generic
drwxr-xr-x  5 root root     1024 Oct  8 23:15 grub
-rw-r--r--  1 root root  4459255 Oct  8 22:59 initrd.img-3.13.0-43-generic
-rw-r--r--  1 root root 21407121 May  6 18:28 initrd.img-3.16.0-37-generic
-rw-r--r--  1 root root  7888925 Oct  8 22:59 initrd.img-3.19.0-16-generic
-rw-r--r--  1 root root 21769704 May 28 12:26 initrd.img-3.19.0-18-generic
-rw-r--r--  1 root root 21773256 Jun 12 09:34 initrd.img-3.19.0-20-generic
-rw-r--r--  1 root root 21770960 Jun 28 14:17 initrd.img-3.19.0-21-generic
-rw-r--r--  1 root root 21769058 Jul 12 11:54 initrd.img-3.19.0-22-generic
-rw-r--r--  1 root root  4459322 Oct  7 15:29 initrd.img-3.19.0-26-generic
-rw-r--r--  1 root root  7892809 Oct  8 23:14 initrd.img-3.19.0-30-generic
drwx------  2 root root    12288 Dec 19  2014 lost+found
-rw-r--r--  1 root root   164216 Mar  6  2015 memtest86+.bin
-rw-r--r--  1 root root   165892 Mar  6  2015 memtest86+.elf
-rw-r--r--  1 root root   166396 Mar  6  2015 memtest86+_multiboot.bin
-rw-------  1 root root  3502913 Apr 29 22:17 System.map-3.16.0-37-generic
-rw-------  1 root root  3615358 Apr 30 18:23 System.map-3.19.0-16-generic
-rw-------  1 root root  3616263 May 19 20:45 System.map-3.19.0-18-generic
-rw-------  1 root root  3617303 May 29 12:02 System.map-3.19.0-20-generic
-rw-------  1 root root  3617303 Jun 14 20:44 System.map-3.19.0-21-generic
-rw-------  1 root root  3617446 Jun 16 19:30 System.map-3.19.0-22-generic
-rw-------  1 root root  3622042 Oct  3 01:04 System.map-3.19.0-30-generic
-rw-------  1 root root  6414336 Apr 29 22:17 vmlinuz-3.16.0-37-generic
-rw-------  1 root root  6611904 Apr 30 18:23 vmlinuz-3.19.0-16-generic
-rw-------  1 root root  6614144 May 19 20:45 vmlinuz-3.19.0-18-generic
-rw-------  1 root root  6616960 May 29 12:02 vmlinuz-3.19.0-20-generic
-rw-------  1 root root  6617408 Jun 14 20:44 vmlinuz-3.19.0-21-generic
-rw-------  1 root root  6616448 Jun 16 19:30 vmlinuz-3.19.0-22-generic
-rw-------  1 root root  6623936 Oct  3 01:04 vmlinuz-3.19.0-30-generic

ii  linux-firmware                                       1.143.3                                    all          Firmware for Linux kernel drivers
ii  linux-headers-3.19.0-18                              3.19.0-18.18                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-18-generic                      3.19.0-18.18                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-22                              3.19.0-22.22                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-22-generic                      3.19.0-22.22                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-26                              3.19.0-26.28                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30                              3.19.0-30.34                               all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic                      3.19.0-30.34                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                3.19.0.30.29                               amd64        Generic Linux kernel headers
pi  linux-image-3.16.0-37-generic                        3.16.0-37.49                               amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-16-generic                        3.19.0-16.16                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-18-generic                        3.19.0-18.18                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-20-generic                        3.19.0-20.20                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-21-generic                        3.19.0-21.21                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-22-generic                        3.19.0-22.22                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic                        3.19.0-30.34                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-37-generic                  3.16.0-37.49                               amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-18-generic                  3.19.0-18.18                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-20-generic                  3.19.0-20.20                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-21-generic                  3.19.0-21.21                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-22-generic                  3.19.0-22.22                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-30-generic                  3.19.0-30.34                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                                 3.19.0-22.22                               amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu4                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                                      3:6.03+dfsg-5ubuntu1                       all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu6                       amd64        Bootloader for Linux/i386 using MS-DOS floppies




```

---

### Post by Bashing-om on 2015-10-15
kevin134; Yeah ...

That is what we are going to do - get dirty ! - . as you can see there are disparities between the directories. All must match.
We roll our sleeves up and make it so. I think the less work is to match with /usr/src/.
To that end execute these terminal commands: *******booting the -22 kernel *********
```

sudo rm -rf /usr/src/linux-headers-3.19.26

sudo rm -rf /lib/modules/3.16.0-37
sudo rm -rf /lib/modules/3.19.0-{16,21,26}*


sudo rm /boot/*-3.13.0-43-generic
sudo rm /boot/*-3.16.0-37-generic
sudo rm /boot/*-3.19.0-{16,21,26}-generic


```

Now next is to fix the package manager; run:
```

sudo apt-get -f install

``` This output I must see to know what we are to do next.

Then all that is left is a bit of cleanup to  properly uninstall the kernels and headers whose files we already deleted. Pending what we need to do from 'apt-get -f' output .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-15
Entered the command's with no output it asked for password which i entered than it went onto a new line apart from last command
 as for the other command this is what i got which point's
out nothing need's to be installed quite confused.



```


rm: cannot remove &#8216;/boot/*-3.19.0-16-generic&#8217;: No such file or directory
rm: cannot remove &#8216;/boot/*-3.19.0-21-generic&#8217;: No such file or directory
rm: cannot remove &#8216;/boot/*-3.19.0-26-generic&#8217;: No such file or directory




Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 172 not to upgrade.

```

---

### Post by Bashing-om on 2015-10-15
kevin134; Hummm ... 

I just do not see a fault (??) ..
Post back once more with the command:
```

ls -al /boot/

``` and I will re-examine my logic.
Looks to me that those files do exist per that last output and I see no error in my logic.
The expression *-3.19.0- using the wildcard character ' * ' should remove the abi, config, initrd.img, System.map, and vmlinuz files all at one fell swoop.

[INDENT][INDENT]I have made errors, maybe again[/INDENT][/INDENT]

---

### Post by kevin134 on 2015-10-15
Here is the result i'm so clueless with what's happening

```

total 118128
drwxr-xr-x  4 root root     3072 Oct 15 23:27 .
drwxr-xr-x 23 root root     4096 Oct  8 23:00 ..
-rw-r--r--  1 root root  1269284 May 19 20:45 abi-3.19.0-18-generic
-rw-r--r--  1 root root  1269462 May 29 12:02 abi-3.19.0-20-generic
-rw-r--r--  1 root root  1269462 Jun 16 19:30 abi-3.19.0-22-generic
-rw-r--r--  1 root root  1271518 Oct  3 01:04 abi-3.19.0-30-generic
-rw-r--r--  1 root root   177700 May 19 20:45 config-3.19.0-18-generic
-rw-r--r--  1 root root   177700 May 29 12:02 config-3.19.0-20-generic
-rw-r--r--  1 root root   177705 Jun 16 19:30 config-3.19.0-22-generic
-rw-r--r--  1 root root   177722 Oct  3 01:04 config-3.19.0-30-generic
drwxr-xr-x  5 root root     1024 Oct  8 23:15 grub
-rw-r--r--  1 root root 21769704 May 28 12:26 initrd.img-3.19.0-18-generic
-rw-r--r--  1 root root 21773256 Jun 12 09:34 initrd.img-3.19.0-20-generic
-rw-r--r--  1 root root 21769058 Jul 12 11:54 initrd.img-3.19.0-22-generic
-rw-r--r--  1 root root  7892809 Oct  8 23:14 initrd.img-3.19.0-30-generic
drwx------  2 root root    12288 Dec 19  2014 lost+found
-rw-r--r--  1 root root   164216 Mar  6  2015 memtest86+.bin
-rw-r--r--  1 root root   165892 Mar  6  2015 memtest86+.elf
-rw-r--r--  1 root root   166396 Mar  6  2015 memtest86+_multiboot.bin
-rw-------  1 root root  3616263 May 19 20:45 System.map-3.19.0-18-generic
-rw-------  1 root root  3617303 May 29 12:02 System.map-3.19.0-20-generic
-rw-------  1 root root  3617446 Jun 16 19:30 System.map-3.19.0-22-generic
-rw-------  1 root root  3622042 Oct  3 01:04 System.map-3.19.0-30-generic
-rw-------  1 root root  6614144 May 19 20:45 vmlinuz-3.19.0-18-generic
-rw-------  1 root root  6616960 May 29 12:02 vmlinuz-3.19.0-20-generic
-rw-------  1 root root  6616448 Jun 16 19:30 vmlinuz-3.19.0-22-generic
-rw-------  1 root root  6623936 Oct  3 01:04 vmlinuz-3.19.0-30-generic


```

---

### Post by Bashing-om on 2015-10-15
kevin134; Yepper, 

Gone gone now .. must have entered the 'rm' command twice.
However, now that my confidence has been shaken, let's verify that all directories are now the same ..before invoking " package manager, heal thyself" .
Show :
```

ls -al /usr/src/
ls -al /lib/modules/ 

```

[INDENT][INDENT]and we go on our way
[INDENT][INDENT][INDENT]merrily
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-10-20
kevin134; Hello;

Are we alive and well ? Are we to the point of clean up ?

[INDENT][INDENT]a bit left to do yet
[/INDENT][/INDENT]

---

