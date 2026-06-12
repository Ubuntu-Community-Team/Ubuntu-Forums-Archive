---
title: "Broken dependencies 14.10--how to address?"
date: 2015-06-20
forum: Installation &amp; Upgrades
---

### Post by Haven_McClure on 2015-06-20
I have one of those icons resembling a "Do Not Enter" sign on the top of my screen and a note saying I have broken dependencies.  I am not able to update as a result.  I ran Package Manager per the instructions and it identified three broken dependencies.  But I'm not sure what to do with them from here.  The dependencies are in an attached screen shot.

---

### Post by brian80 on 2015-06-20
Run these commands
```
sudo apt-get update 
sudo apt-get install -f
```
Let us know if you encounter more problems.

---

### Post by Haven_McClure on 2015-06-22
> **brian80 said:**
> Run these commands
```
sudo apt-get update 
sudo apt-get install -f
```
Let us know if you encounter more problems.

Thanks for the response.  I did encounter a number of error messages.

```
haven@haven-Lenovo-Z40-70:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.16.0-37-lowlatency
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  linux-image-3.16.0-36-generic linux-image-3.16.0-41-lowlatency
Suggested packages:
  fdutils linux-doc-3.16.0 linux-source-3.16.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.16.0-36-generic linux-image-3.16.0-41-lowlatency
0 upgraded, 2 newly installed, 0 to remove and 87 not upgraded.
16 not fully installed or removed.
Need to get 0 B/70.3 MB of archives.
After this operation, 247 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 428212 files and directories currently installed.)
Preparing to unpack .../linux-image-3.16.0-36-generic_3.16.0-36.48_amd64.deb ...
Done.
Unpacking linux-image-3.16.0-36-generic (3.16.0-36.48) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.16.0-36-generic_3.16.0-36.48_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.16.0-36-generic' to '/boot/vmlinuz-3.16.0-36-generic.dpkg-new': unexpected end of file or stream
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-image-3.16.0-41-lowlatency_3.16.0-41.57_amd64.deb ...
Done.
Unpacking linux-image-3.16.0-41-lowlatency (3.16.0-41.57) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.16.0-41-lowlatency_3.16.0-41.57_amd64.deb (--unpack):
 cannot copy extracted data for './boot/abi-3.16.0-41-lowlatency' to '/boot/abi-3.16.0-41-lowlatency.dpkg-new': unexpected end of file or stream
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-41-lowlatency /boot/vmlinuz-3.16.0-41-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-41-lowlatency /boot/vmlinuz-3.16.0-41-lowlatency
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.16.0-36-generic_3.16.0-36.48_amd64.deb
 /var/cache/apt/archives/linux-image-3.16.0-41-lowlatency_3.16.0-41.57_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
haven@haven-Lenovo-Z40-70:~$ 
```

I did follow the system's advice and did a sudo apt-get autoremove, but got the following response:

```
haven@haven-Lenovo-Z40-70:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.16.0-36-generic : Depends: linux-image-3.16.0-36-generic but it is not installed
 linux-image-lowlatency : Depends: linux-image-3.16.0-41-lowlatency but it is not installed
 linux-signed-image-3.16.0-36-generic : Depends: linux-image-3.16.0-36-generic (= 3.16.0-36.48) but it is not installed
E: Unmet dependencies. Try using -f.
```

I assumed the system meant sudo apt-get install -f, so I ran that again, only to get the same error messages as listed in the first set of codes I posted.

---

### Post by MAFoElffen on 2015-06-23
He forgot one step with fixing unmet dependencies:
```

sudo dpkg --configure -a

```
... But before doing that, first check the space left on the system volume. Sometimes (rarely), users will get that error when the system volume does not have enough space left over to fully install the dependency packages.

---

### Post by Haven_McClure on 2015-06-23
Thanks for the tip.  Here's the output when I ran it.  Lots of errors.  

```
haven@haven-Lenovo-Z40-70:~$ sudo dpkg --configure -a
[sudo] password for haven: 
Setting up linux-image-3.16.0-34-lowlatency (3.16.0-34.47) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating image symbolic links since we are being updated/reinstalled 
(3.16.0-34.45 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-34-lowlatency /boot/vmlinuz-3.16.0-34-lowlatency
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-34-lowlatency /boot/vmlinuz-3.16.0-34-lowlatency
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-34-lowlatency (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.16.0-34-lowlatency (x86_64)
Consult /var/lib/dkms/r8168/8.038.00/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-34-lowlatency /boot/vmlinuz-3.16.0-34-lowlatency
update-initramfs: Generating /boot/initrd.img-3.16.0-34-lowlatency

gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.16.0-34-lowlatency with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.16.0-34-lowlatency.postinst line 1025.
dpkg: error processing package linux-image-3.16.0-34-lowlatency (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-signed-image-3.16.0-36-generic:
 linux-signed-image-3.16.0-36-generic depends on linux-image-3.16.0-36-generic (= 3.16.0-36.48); however:
  Package linux-image-3.16.0-36-generic is not installed.

dpkg: error processing package linux-signed-image-3.16.0-36-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-lowlatency:
 linux-image-lowlatency depends on linux-image-3.16.0-41-lowlatency; however:
  Package linux-image-3.16.0-41-lowlatency is not installed.

dpkg: error processing package linux-image-lowlatency (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.16.0-34-generic (3.16.0-34.47) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.16.0-34.45 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.16.0-34.45 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-34-generic (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.16.0-34-generic (x86_64)
Consult /var/lib/dkms/r8168/8.038.00/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-34-generic

gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.16.0-34-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.16.0-34-generic.postinst line 1025.
dpkg: error processing package linux-image-3.16.0-34-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-3.16.0-41 (3.16.0-41.57) ...
Setting up linux-image-3.16.0-37-generic (3.16.0-37.49) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
vmlinuz(/boot/vmlinuz-3.16.0-37-generic
) points to /boot/vmlinuz-3.16.0-37-generic
 (/boot/vmlinuz-3.16.0-37-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.16.0-37-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-37-generic (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.16.0-37-generic (x86_64)
Consult /var/lib/dkms/r8168/8.038.00/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-37-generic

gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.16.0-37-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.16.0-37-generic.postinst line 1025.
dpkg: error processing package linux-image-3.16.0-37-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-lowlatency:
 linux-lowlatency depends on linux-image-lowlatency (= 3.16.0.41.41); however:
  Package linux-image-lowlatency is not configured yet.

dpkg: error processing package linux-lowlatency (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.16.0-36-generic:
 linux-image-extra-3.16.0-36-generic depends on linux-image-3.16.0-36-generic; however:
  Package linux-image-3.16.0-36-generic is not installed.

dpkg: error processing package linux-image-extra-3.16.0-36-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.16.0-34-generic:
 linux-image-extra-3.16.0-34-generic depends on linux-image-3.16.0-34-generic; however:
  Package linux-image-3.16.0-34-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.16.0-34-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-3.16.0-34-generic:
 linux-signed-image-3.16.0-34-generic depends on linux-image-3.16.0-34-generic (= 3.16.0-34.47); however:
  Package linux-image-3.16.0-34-generic is not configured yet.
 linux-signed-image-3.16.0-34-generic depends on linux-image-extra-3.16.0-34-generic (= 3.16.0-34.47); however:
  Package linux-image-extra-3.16.0-34-generic is not configured yet.

dpkg: error processing package linux-signed-image-3.16.0-34-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.16.0-41-lowlatency (3.16.0-41.57) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.16.0-41-lowlatency /boot/vmlinuz-3.16.0-41-lowlatency
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-41-lowlatency (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.16.0-41-lowlatency (x86_64)
Consult /var/lib/dkms/r8168/8.038.00/build/make.log for more information.
dpkg: dependency problems prevent configuration of linux-signed-image-3.16.0-37-generic:
 linux-signed-image-3.16.0-37-generic depends on linux-image-3.16.0-37-generic (= 3.16.0-37.49); however:
  Package linux-image-3.16.0-37-generic is not configured yet.

dpkg: error processing package linux-signed-image-3.16.0-37-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.16.0-37-generic:
 linux-image-extra-3.16.0-37-generic depends on linux-image-3.16.0-37-generic; however:
  Package linux-image-3.16.0-37-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.16.0-37-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-lowlatency (3.16.0.41.41) ...
dpkg: dependency problems prevent configuration of linux-signed-image-generic:
 linux-signed-image-generic depends on linux-signed-image-3.16.0-37-generic; however:
  Package linux-signed-image-3.16.0-37-generic is not configured yet.

dpkg: error processing package linux-signed-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic:
 linux-signed-generic depends on linux-signed-image-generic (= 3.16.0.37.38); however:
  Package linux-signed-image-generic is not configured yet.

dpkg: error processing package linux-signed-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.16.0-34-lowlatency
 linux-signed-image-3.16.0-36-generic
 linux-image-lowlatency
 linux-image-3.16.0-34-generic
 linux-image-3.16.0-37-generic
 linux-lowlatency
 linux-image-extra-3.16.0-36-generic
 linux-image-extra-3.16.0-34-generic
 linux-signed-image-3.16.0-34-generic
 linux-signed-image-3.16.0-37-generic
 linux-image-extra-3.16.0-37-generic
 linux-signed-image-generic
 linux-signed-generic


```

Furthermore, while this command was running, I got a "system error" dialog box that came up two or three times. I kept hitting "Report Problem" and the error I got was related to a bug reported about [here]("http://bugs.launchpad.net/ubuntu/+source/r8168/+bug/1385640")

Not sure if this is relevant, but I will bring it up given that I saw a Realtek driver (r8168) was mentioned during some of the error output.  When installing 14.10 on a new laptop last January, I made the mistake of thinking that the wireless card was a Realtek 8168, when it was really a Broadcomm module--Realtek was the Ethernet port.  I was having a hard time getting a wireless internet connection, and, following other people's directions, kept on trying to install an updated driver r8169.  I was confused as to why I couldn't get wireless internet going, until I discovered my screw-up, and once I installed the Broadcomm fix per instructions, my wireless began to work like a charm.  But I've had occasional problems with updating since then.  Sometimes I've gotten an error message saying there's not enough volume in the sys folder, though this hasn't happened so much recently.  It seems that the problems have accumulated to the point that I have a consistent icon on the top of my screen that looks like a "Do Not Enter" sign. In any case, I wonder if the unmet dependencies errors I've gotten were due to my messing with the r8168 and r8169 drivers, or if that's a coincidence.

Thanks for everyone's help with this so far.

---

### Post by Bashing-om on 2015-06-23
Haven_McClure; Hello;

Allow me to point out:
MAFoElffen's intuition bears fruit.
This:
> 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-34-lowlatency /boot/vmlinuz-3.16.0-34-lowlatency
update-initramfs: Generating /boot/initrd.img-3.16.0-34-lowlatency

gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1


says that the system has no operating headroom and no can do.
Let's verify:
```

df -h
df -i

```

Now that comes back that the /boot partition is full. We can try the simpler method - that might work IF there is operating head room for the package manager to operate in:
```

sudo apt-get autoremove

```
But, probable we will have to get hands on with this, and maybe get down and dirty. We try the least invasive things 1st.

[INDENT][INDENT]never can get away from
[INDENT][INDENT][INDENT]system maintenance 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Haven_McClure on 2015-06-23
Hmm, can't quite tell if /boot is full, since it seems to show different things between -h and -i.  Also, I don't know difference between /boot and /boot/efi
```

haven@haven-Lenovo-Z40-70:~$ df -h
Filesystem                           Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--studio--vg-root  450G   92G  336G  22% /
none                                 4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                 3.9G  4.0K  3.9G   1% /dev
tmpfs                                788M  1.4M  787M   1% /run
none                                 5.0M  4.0K  5.0M   1% /run/lock
none                                 3.9G   84K  3.9G   1% /run/shm
none                                 100M   40K  100M   1% /run/user
/dev/sda2                            237M  233M     0 100% /boot
/dev/sda1                            511M  3.4M  508M   1% /boot/efi
haven@haven-Lenovo-Z40-70:~$ df -i
Filesystem                            Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/ubuntu--studio--vg-root 29958144 514239 29443905    2% /
none                                 1008250      4  1008246    1% /sys/fs/cgroup
udev                                 1004116    579  1003537    1% /dev
tmpfs                                1008250    695  1007555    1% /run
none                                 1008250      3  1008247    1% /run/lock
none                                 1008250      6  1008244    1% /run/shm
none                                 1008250     28  1008222    1% /run/user
/dev/sda2                              62496    317    62179    1% /boot
/dev/sda1                                  0      0        0     - /boot/efi
```

---

### Post by Bashing-om on 2015-06-23
Haven_McClure; Welp;

Not looking real good for the home team:
> 
/dev/sda2                            237M  233M     0 100% /boot

With no headroom (100% capacity).

'df -h' shows disk space management ; 'df -i' shows the inode allotments ( one inode per file, run out of inodes then can not create additional files).

Situation at hand - Try:
```

sudo apt-get autoremove

```
and I do mean try. Most likely will not have the room to operate in but worth a try.

Now if that fails we try and remove the old kernels using the package management system.
We need to know the kernel that is presently booted, and as well all the other kernels that are installed:
```

uname -r
dpkg -l | grep linux-

```
Once we have the operating head room, then we try and update/upgrade the system.

[INDENT][INDENT]maybe a long hard road
[/INDENT][/INDENT]

---

### Post by MAFoElffen on 2015-06-24
This will purge all old kernels except the current running kernel:
```

dpkg -l 'linux-*' | sed  '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]*  [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

```
You will recover approximately 122MB for each kernel purged.

---

### Post by Haven_McClure on 2015-06-24
Thanks for your continued help.  I've identified the current kernel and the other kernels installed.
```
haven@haven-Lenovo-Z40-70:~$ uname -r
3.16.0-34-lowlatency
haven@haven-Lenovo-Z40-70:~$ dpkg -l | grep linux-
ii  ladspa-sdk                                  1.13-2                                   amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-firmware                              1.138.1                                  all          Firmware for Linux kernel drivers
ii  linux-headers-3.16.0-29                     3.16.0-29.39                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-29-lowlatency          3.16.0-29.39                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-33                     3.16.0-33.44                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-33-generic             3.16.0-33.44                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-33-lowlatency          3.16.0-33.44                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-34                     3.16.0-34.47                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-34-generic             3.16.0-34.47                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-34-lowlatency          3.16.0-34.47                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-36                     3.16.0-36.48                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-36-generic             3.16.0-36.48                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-36-lowlatency          3.16.0-36.48                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-37                     3.16.0-37.49                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-37-generic             3.16.0-37.49                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-37-lowlatency          3.16.0-37.49                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-41                     3.16.0-41.57                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-41-lowlatency          3.16.0-41.57                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-generic                       3.16.0.37.38                             amd64        Generic Linux kernel headers
ii  linux-headers-lowlatency                    3.16.0.41.41                             amd64        lowlatency Linux kernel headers
rc  linux-image-3.16.0-23-lowlatency            3.16.0-23.31                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-29-generic               3.16.0-29.39                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-29-lowlatency            3.16.0-29.39                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-30-generic               3.16.0-30.40                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-30-lowlatency            3.16.0-30.40                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-33-generic               3.16.0-33.44                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-33-lowlatency            3.16.0-33.44                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
iF  linux-image-3.16.0-34-generic               3.16.0-34.47                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
iF  linux-image-3.16.0-34-lowlatency            3.16.0-34.47                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
iF  linux-image-3.16.0-37-generic               3.16.0-37.49                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-29-generic         3.16.0-29.39                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-30-generic         3.16.0-30.40                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-33-generic         3.16.0-33.44                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
iU  linux-image-extra-3.16.0-34-generic         3.16.0-34.47                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
iU  linux-image-extra-3.16.0-36-generic         3.16.0-36.48                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
iU  linux-image-extra-3.16.0-37-generic         3.16.0-37.49                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
iU  linux-image-lowlatency                      3.16.0.41.41                             amd64        lowlatency Linux kernel image
ii  linux-libc-dev:amd64                        3.16.0-37.49                             amd64        Linux Kernel Headers for development
iU  linux-lowlatency                            3.16.0.41.41                             amd64        Complete lowlatency Linux kernel
iU  linux-signed-generic                        3.16.0.37.38                             amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-3.16.0-29-generic        3.16.0-29.39                             amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-30-generic        3.16.0-30.40                             amd64        Signed kernel image generic
ii  linux-signed-image-3.16.0-33-generic        3.16.0-33.44                             amd64        Signed kernel image generic
iU  linux-signed-image-3.16.0-34-generic        3.16.0-34.47                             amd64        Signed kernel image generic
iU  linux-signed-image-3.16.0-36-generic        3.16.0-36.48                             amd64        Signed kernel image generic
iU  linux-signed-image-3.16.0-37-generic        3.16.0-37.49                             amd64        Signed kernel image generic
iU  linux-signed-image-generic                  3.16.0.37.38                             amd64        Signed Generic Linux kernel image
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                     all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03~pre18+dfsg-1ubuntu1               all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu5                     amd64        Bootloader for Linux/i386 using MS-DOS floppies
```
However, it doesn't appear that MaFoElfen's purge code worked--I copied and pasted as is.  I checked -h and -i and had the same as before.

```
@haven-Lenovo-Z40-70:~$ dpkg -l 'linux-*' | sed  '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]*  [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 3.16.0-33.44
E: Couldn't find any package by regex '3.16.0-33.44'
haven@haven-Lenovo-Z40-70:~$ sudo apt-get -y purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.16.0-36-generic : Depends: linux-image-3.16.0-36-generic but it is not installed
 linux-image-lowlatency : Depends: linux-image-3.16.0-41-lowlatency but it is not installed
 linux-signed-image-3.16.0-36-generic : Depends: linux-image-3.16.0-36-generic (= 3.16.0-36.48) but it is not installed
E: Unmet dependencies. Try using -f.
haven@haven-Lenovo-Z40-70:~$ dh -h
The program 'dh' is currently not installed. You can install it by typing:
sudo apt-get install debhelper
haven@haven-Lenovo-Z40-70:~$ df -h
Filesystem                           Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--studio--vg-root  450G   92G  336G  22% /
none                                 4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                 3.9G  4.0K  3.9G   1% /dev
tmpfs                                788M  1.3M  787M   1% /run
none                                 5.0M  4.0K  5.0M   1% /run/lock
none                                 3.9G   80K  3.9G   1% /run/shm
none                                 100M   36K  100M   1% /run/user
/dev/sda2                            237M  233M     0 100% /boot
/dev/sda1                            511M  3.4M  508M   1% /boot/efi
haven@haven-Lenovo-Z40-70:~$ df -i
Filesystem                            Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/ubuntu--studio--vg-root 29958144 510589 29447555    2% /
none                                 1008250      4  1008246    1% /sys/fs/cgroup
udev                                 1004116    579  1003537    1% /dev
tmpfs                                1008250    692  1007558    1% /run
none                                 1008250      3  1008247    1% /run/lock
none                                 1008250      5  1008245    1% /run/shm
none                                 1008250     27  1008223    1% /run/user
/dev/sda2                              62496    317    62179    1% /boot
/dev/sda1                                  0      0        0     - /boot/efi
haven@haven-Lenovo-Z40-70:~$ 

```

---

### Post by mörgæs on 2015-06-24
If you manage to get 14.10 running what are your plans for it? Support is running out in a month.

---

### Post by Haven_McClure on 2015-06-24
> **mörgæs said:**
> If you manage to get 14.10 running what are your plans for it? Support is running out in a month.

[ 						 							 						 					]("http://ubuntuforums.org/member.php?u=939075") 				 				 					 						 	[Mörgæs]("http://ubuntuforums.org/member.php?u=939075"), that's an excellent question.  I intend to upgrade to 15.04.  It would seem to me that having 14.10 running smoothly would be important in order to upgrade properly. At this point, I prefer not to do a clean install because it usually takes a considerable amount of work to re-download software and I have had difficulty in the past with losing metadata with a couple critical pieces of software despite my best efforts to preserve it.  However, if fixing these issues on 14.10 seems to be too difficult, I might consider a clean install.

---

### Post by Bashing-om on 2015-06-24
Haven_McClure; Yuk ; !

I do not know how you got into this situation with several kernels only now partially installed. But, lets drop down to a lower level and try this:
```

sudo dpkg -P linux-image-extra-3.16.0-{29,33,36,37}-generic
sudo dpkg -P linux-signed-image-3.16.0-{33,36,37}-generic
sudo dpkg -P linux-image-3.16.0-{29,33}-lowlatency
sudo dpkg -P linux-headers-3.16.0-{33,36,37}-generic
sudo dpkg -P linux-headers-3.16.0-{29,33,36,37}-lowlatency
sudo dpkg -P linux-headers-3.16.0-{29,33,36,37}

```

Hope this gets us some operating head room and then we can do some cleanup.

[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT][INDENT]try something else ( sky diving excepted)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Haven_McClure on 2015-06-24
Well, I have my theories about how I got several partially  installed kernels--it's several messages back. 

I've run the commands and it looks like I have gotten some headroom.

```
haven@haven-Lenovo-Z40-70:~$ df -h
Filesystem                           Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--studio--vg-root  450G   91G  337G  22% /
none                                 4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                 3.9G  4.0K  3.9G   1% /dev
tmpfs                                788M  1.2M  787M   1% /run
none                                 5.0M  4.0K  5.0M   1% /run/lock
none                                 3.9G   80K  3.9G   1% /run/shm
none                                 100M   36K  100M   1% /run/user
/dev/sda2                            237M  145M   81M  65% /boot
/dev/sda1                            511M  3.4M  508M   1% /boot/efi
haven@haven-Lenovo-Z40-70:~$ df -h
Filesystem                           Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--studio--vg-root  450G   91G  337G  22% /
none                                 4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                 3.9G  4.0K  3.9G   1% /dev
tmpfs                                788M  1.2M  787M   1% /run
none                                 5.0M  4.0K  5.0M   1% /run/lock
none                                 3.9G   80K  3.9G   1% /run/shm
none                                 100M   36K  100M   1% /run/user
/dev/sda2                            237M  145M   81M  65% /boot
/dev/sda1                            511M  3.4M  508M   1% /boot/efi
```

I don't know if you need the output below, but this does show which of those commands executed fine and which ones executed with errors or didn't execute at all.

```
haven@haven-Lenovo-Z40-70:~$ sudo dpkg -P linux-image-extra-3.16.0-{29,33,36,37}-generic
[sudo] password for haven: 
(Reading database ... 428211 files and directories currently installed.)
Removing linux-image-extra-3.16.0-29-generic (3.16.0-29.39) ...
Purging configuration files for linux-image-extra-3.16.0-29-generic (3.16.0-29.39) ...
dpkg: dependency problems prevent removal of linux-image-extra-3.16.0-33-generic:
 linux-signed-image-3.16.0-33-generic depends on linux-image-extra-3.16.0-33-generic (= 3.16.0-33.44).

dpkg: error processing package linux-image-extra-3.16.0-33-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-extra-3.16.0-36-generic:
 linux-signed-image-3.16.0-36-generic depends on linux-image-extra-3.16.0-36-generic (= 3.16.0-36.48); however:
  Package linux-image-extra-3.16.0-36-generic is to be removed.

dpkg: error processing package linux-image-extra-3.16.0-36-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-extra-3.16.0-37-generic:
 linux-signed-image-3.16.0-37-generic depends on linux-image-extra-3.16.0-37-generic (= 3.16.0-37.49); however:
  Package linux-image-extra-3.16.0-37-generic is to be removed.

dpkg: error processing package linux-image-extra-3.16.0-37-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-extra-3.16.0-33-generic
 linux-image-extra-3.16.0-36-generic
 linux-image-extra-3.16.0-37-generic
haven@haven-Lenovo-Z40-70:~$ sudo dpkg -P linux-signed-image-3.16.0-{33,36,37}-generic
(Reading database ... 428211 files and directories currently installed.)
Removing linux-signed-image-3.16.0-33-generic (3.16.0-33.44) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-33-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
Found linux image: /boot/vmlinuz-3.16.0-29-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-29-lowlatency
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-signed-image-3.16.0-33-generic (3.16.0-33.44) ...
Removing linux-signed-image-3.16.0-36-generic (3.16.0-36.48) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-33-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
Found linux image: /boot/vmlinuz-3.16.0-29-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-29-lowlatency
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-signed-image-3.16.0-36-generic (3.16.0-36.48) ...
dpkg: dependency problems prevent removal of linux-signed-image-3.16.0-37-generic:
 linux-signed-image-generic depends on linux-signed-image-3.16.0-37-generic.

dpkg: error processing package linux-signed-image-3.16.0-37-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-signed-image-3.16.0-37-generic
haven@haven-Lenovo-Z40-70:~$ sudo dpkg -P linux-image-3.16.0-{29,33}-lowlatency
(Reading database ... 428203 files and directories currently installed.)
Removing linux-image-3.16.0-29-lowlatency (3.16.0-29.39) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.16.0-29-lowlatency /boot/vmlinuz-3.16.0-29-lowlatency
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-29-lowlatency /boot/vmlinuz-3.16.0-29-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.16.0-29-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-29-lowlatency /boot/vmlinuz-3.16.0-29-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-33-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-3.16.0-29-lowlatency (3.16.0-29.39) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-29-lowlatency /boot/vmlinuz-3.16.0-29-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-29-lowlatency /boot/vmlinuz-3.16.0-29-lowlatency
Removing linux-image-3.16.0-33-lowlatency (3.16.0-33.44) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.16.0-33-lowlatency /boot/vmlinuz-3.16.0-33-lowlatency
dkms: removing: bcmwl 6.30.223.248+bdcom (3.16.0-33-lowlatency) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  3.16.0-33-lowlatency (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.16.0-33-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-33-lowlatency /boot/vmlinuz-3.16.0-33-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.16.0-33-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-33-lowlatency /boot/vmlinuz-3.16.0-33-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-3.16.0-33-lowlatency (3.16.0-33.44) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-33-lowlatency /boot/vmlinuz-3.16.0-33-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-33-lowlatency /boot/vmlinuz-3.16.0-33-lowlatency
haven@haven-Lenovo-Z40-70:~$ sudo dpkg -P linux-headers-3.16.0-{33,36,37}-generic
(Reading database ... 418119 files and directories currently installed.)
Removing linux-headers-3.16.0-33-generic (3.16.0-33.44) ...
Removing linux-headers-3.16.0-36-generic (3.16.0-36.48) ...
dpkg: dependency problems prevent removal of linux-headers-3.16.0-37-generic:
 linux-headers-generic depends on linux-headers-3.16.0-37-generic.

dpkg: error processing package linux-headers-3.16.0-37-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.16.0-37-generic
haven@haven-Lenovo-Z40-70:~$ sudo dpkg -P linux-headers-3.16.0-{29,33,36,37}-lowlatency
(Reading database ... 400506 files and directories currently installed.)
Removing linux-headers-3.16.0-29-lowlatency (3.16.0-29.39) ...
Removing linux-headers-3.16.0-33-lowlatency (3.16.0-33.44) ...
Removing linux-headers-3.16.0-36-lowlatency (3.16.0-36.48) ...
dpkg: warning: while removing linux-headers-3.16.0-36-lowlatency, directory '/lib/modules/3.16.0-36-lowlatency' not empty so not removed
Removing linux-headers-3.16.0-37-lowlatency (3.16.0-37.49) ...
dpkg: warning: while removing linux-headers-3.16.0-37-lowlatency, directory '/lib/modules/3.16.0-37-lowlatency' not empty so not removed
haven@haven-Lenovo-Z40-70:~$ sudo dpkg -P linux-headers-3.16.0-{29,33,36,37}
(Reading database ... 365315 files and directories currently installed.)
Removing linux-headers-3.16.0-29 (3.16.0-29.39) ...
Removing linux-headers-3.16.0-33 (3.16.0-33.44) ...
Removing linux-headers-3.16.0-36 (3.16.0-36.48) ...
dpkg: dependency problems prevent removal of linux-headers-3.16.0-37:
 linux-headers-3.16.0-37-generic depends on linux-headers-3.16.0-37.

dpkg: error processing package linux-headers-3.16.0-37 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.16.0-37
```



> **Bashing-om said:**
> Haven_McClure; Yuk ; !

I do not know how you got into this situation with several kernels only now partially installed. But, lets drop down to a lower level and try this:
```

sudo dpkg -P linux-image-extra-3.16.0-{29,33,36,37}-generic
sudo dpkg -P linux-signed-image-3.16.0-{33,36,37}-generic
sudo dpkg -P linux-image-3.16.0-{29,33}-lowlatency
sudo dpkg -P linux-headers-3.16.0-{33,36,37}-generic
sudo dpkg -P linux-headers-3.16.0-{29,33,36,37}-lowlatency
sudo dpkg -P linux-headers-3.16.0-{29,33,36,37}

```

Hope this gets us some operating head room and then we can do some cleanup.[INDENT][INDENT]if at 1st you do not succeed[INDENT][INDENT][INDENT]try something else ( sky diving excepted)
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2015-06-24
Haven_McClure; Humm .. Looks like

I got the cart before the horse, maybe should have removed "  linux-signed-image " 1st .
But we are making good progress.
Let's do a bit of cleanup:
Now let’s remove all the packages marked as rc.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
and now get a new look at things:
```

dpkg -l | grep linux-

``` and we see where we go from here .

[INDENT][INDENT]progress made, one step at a time
[/INDENT][/INDENT]

---

### Post by Haven_McClure on 2015-06-24
Looks like progress.  Here's the output.  

```
haven@haven-Lenovo-Z40-70:~$ dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
[sudo] password for haven: 
(Reading database ... 318666 files and directories currently installed.)
Removing linux-image-3.16.0-23-lowlatency (3.16.0-23.31) ...
Purging configuration files for linux-image-3.16.0-23-lowlatency (3.16.0-23.31) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-23-lowlatency /boot/vmlinuz-3.16.0-23-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-23-lowlatency /boot/vmlinuz-3.16.0-23-lowlatency
Removing linux-image-3.16.0-29-generic (3.16.0-29.39) ...
Purging configuration files for linux-image-3.16.0-29-generic (3.16.0-29.39) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
Removing linux-image-3.16.0-30-generic (3.16.0-30.40) ...
Purging configuration files for linux-image-3.16.0-30-generic (3.16.0-30.40) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic
Removing linux-image-3.16.0-30-lowlatency (3.16.0-30.40) ...
Purging configuration files for linux-image-3.16.0-30-lowlatency (3.16.0-30.40) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-30-lowlatency /boot/vmlinuz-3.16.0-30-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-30-lowlatency /boot/vmlinuz-3.16.0-30-lowlatency
Removing linux-image-extra-3.16.0-30-generic (3.16.0-30.40) ...
Purging configuration files for linux-image-extra-3.16.0-30-generic (3.16.0-30.40) ...
Removing linux-signed-image-3.16.0-29-generic (3.16.0-29.39) ...
Purging configuration files for linux-signed-image-3.16.0-29-generic (3.16.0-29.39) ...
Removing linux-signed-image-3.16.0-30-generic (3.16.0-30.40) ...
Purging configuration files for linux-signed-image-3.16.0-30-generic (3.16.0-30.40) ...
Removing python-twisted (14.0.2-1ubuntu1) ...
Purging configuration files for python-twisted (14.0.2-1ubuntu1) ...
Removing tor (0.2.4.23-1) ...
Purging configuration files for tor (0.2.4.23-1) ...
Removing torbrowser-launcher (0.1.2-1) ...
Purging configuration files for torbrowser-launcher (0.1.2-1) ...
Removing torchat (0.9.9.553-1) ...
Purging configuration files for torchat (0.9.9.553-1) ...
Removing torsocks (2.0.0-1) ...
Purging configuration files for torsocks (2.0.0-1) ...
Removing vidalia (0.2.21-3ubuntu1) ...
Purging configuration files for vidalia (0.2.21-3ubuntu1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
haven@haven-Lenovo-Z40-70:~$ dpkg -l | grep linux
ii  fonts-linuxlibertine                        5.3.0-2                                  all          Linux Libertine family of fonts
ii  ladspa-sdk                                  1.13-2                                   amd64        sample tools for linux-audio-dev plugin architecture
ii  libselinux1:amd64                           2.3-1build1                              amd64        SELinux runtime shared libraries
ii  libv4l-0:amd64                              1.2.1-2build1                            amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                        1.2.1-2build1                            amd64        Video4linux frame format conversion library
ii  linux-firmware                              1.138.1                                  all          Firmware for Linux kernel drivers
ii  linux-headers-3.16.0-34                     3.16.0-34.47                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-34-generic             3.16.0-34.47                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-34-lowlatency          3.16.0-34.47                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
pi  linux-headers-3.16.0-37                     3.16.0-37.49                             all          Header files related to Linux kernel version 3.16.0
pi  linux-headers-3.16.0-37-generic             3.16.0-37.49                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-41                     3.16.0-41.57                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-41-lowlatency          3.16.0-41.57                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-generic                       3.16.0.37.38                             amd64        Generic Linux kernel headers
ii  linux-headers-lowlatency                    3.16.0.41.41                             amd64        lowlatency Linux kernel headers
ii  linux-image-3.16.0-33-generic               3.16.0-33.44                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
iF  linux-image-3.16.0-34-generic               3.16.0-34.47                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
iF  linux-image-3.16.0-34-lowlatency            3.16.0-34.47                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
iF  linux-image-3.16.0-37-generic               3.16.0-37.49                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
pi  linux-image-extra-3.16.0-33-generic         3.16.0-33.44                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
iU  linux-image-extra-3.16.0-34-generic         3.16.0-34.47                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
pU  linux-image-extra-3.16.0-36-generic         3.16.0-36.48                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
pU  linux-image-extra-3.16.0-37-generic         3.16.0-37.49                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
iU  linux-image-lowlatency                      3.16.0.41.41                             amd64        lowlatency Linux kernel image
ii  linux-libc-dev:amd64                        3.16.0-37.49                             amd64        Linux Kernel Headers for development
iU  linux-lowlatency                            3.16.0.41.41                             amd64        Complete lowlatency Linux kernel
iU  linux-signed-generic                        3.16.0.37.38                             amd64        Complete Signed Generic Linux kernel and headers
iU  linux-signed-image-3.16.0-34-generic        3.16.0-34.47                             amd64        Signed kernel image generic
pU  linux-signed-image-3.16.0-37-generic        3.16.0-37.49                             amd64        Signed kernel image generic
iU  linux-signed-image-generic                  3.16.0.37.38                             amd64        Signed Generic Linux kernel image
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                     all          base package for ALSA and OSS sound systems
ii  pptp-linux                                  1.7.2-7                                  amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                    3:6.03~pre18+dfsg-1ubuntu1               amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                             3:6.03~pre18+dfsg-1ubuntu1               all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu5                     amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                  2.25.1-3ubuntu4.1                        amd64        Miscellaneous system utilities


```

---

### Post by Bashing-om on 2015-06-24
Haven_McClure; Yeah ..

Not to shabby:
Let's poke at it a bit see if it bites back:
```

sudo dpkg -P linux-signed-image-3.16.0-37-generic

```

If that flies we try to purge the remaining partials .

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by Haven_McClure on 2015-06-24
Eh, not foaming at the mouth, but not exactly friendly either...

```
haven@haven-Lenovo-Z40-70:~$ sudo dpkg -P linux-signed-image-3.16.0-37-generic
[sudo] password for haven: 
dpkg: dependency problems prevent removal of linux-signed-image-3.16.0-37-generic:
 linux-signed-image-generic depends on linux-signed-image-3.16.0-37-generic.

dpkg: error processing package linux-signed-image-3.16.0-37-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-signed-image-3.16.0-37-generic
haven@haven-Lenovo-Z40-70:~$ sudo dpkg -P linux-signed-image-3.16.0-37-genericsudo dpkg -P linux-signed-image-3.16.0-37-generic


```

---

### Post by Bashing-om on 2015-06-24
Haven_McClure; HoKay :

Well then !
```

sudo apt-get install --reinstall linux-signed-image-generic

```

as we have as status ' iU ' for  linux-signed-generic .

See if this makes the package manager happy .

[INDENT][INDENT]maybe yes
maybe not so yes
[/INDENT][/INDENT]

---

### Post by Haven_McClure on 2015-06-24
Not so yes, apparently, but I wonder if I made a mistake by taking the system's suggestion to apt-get -f intall because apparently I have memory issues again. Should I go through those six dpkg commands again that freed up some space?

```
haven@haven-Lenovo-Z40-70:~$ sudo apt-get install --reinstall linux-signed-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.16.0-36-generic : Depends: linux-image-3.16.0-36-generic but it is not going to be installed
 linux-image-lowlatency : Depends: linux-image-3.16.0-41-lowlatency but it is not going to be installed
 linux-signed-generic : Depends: linux-signed-image-generic (= 3.16.0.37.38) but 3.16.0.41.41 is to be installed
 linux-signed-image-generic : Depends: linux-signed-image-3.16.0-41-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
haven@haven-Lenovo-Z40-70:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
haven@haven-Lenovo-Z40-70:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.16.0-36-generic linux-image-3.16.0-41-lowlatency
Suggested packages:
  fdutils linux-doc-3.16.0 linux-source-3.16.0 linux-tools
  linux-headers-3.16.0-36-generic
The following NEW packages will be installed:
  linux-image-3.16.0-36-generic linux-image-3.16.0-41-lowlatency
0 upgraded, 2 newly installed, 0 to remove and 86 not upgraded.
12 not fully installed or removed.
Need to get 0 B/70.3 MB of archives.
After this operation, 247 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 318652 files and directories currently installed.)
Preparing to unpack .../linux-image-3.16.0-36-generic_3.16.0-36.48_amd64.deb ...
Done.
Unpacking linux-image-3.16.0-36-generic (3.16.0-36.48) ...
Preparing to unpack .../linux-image-3.16.0-41-lowlatency_3.16.0-41.57_amd64.deb ...
Done.
Unpacking linux-image-3.16.0-41-lowlatency (3.16.0-41.57) ...
Setting up linux-image-3.16.0-34-generic (3.16.0-34.47) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating image symbolic links since we are being updated/reinstalled 
(3.16.0-34.45 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-34-generic (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.16.0-34-generic (x86_64)
Consult /var/lib/dkms/r8168/8.038.00/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 23929: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 23929: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 24118: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 24118: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-36-generic
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 24945: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 24945: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on lvs invocation. Parent PID 25079: /bin/sh
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-3.16.0-34-lowlatency (3.16.0-34.47) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.16.0-34.45 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.16.0-34.45 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-34-lowlatency /boot/vmlinuz-3.16.0-34-lowlatency
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-34-lowlatency /boot/vmlinuz-3.16.0-34-lowlatency
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-34-lowlatency (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.16.0-34-lowlatency (x86_64)
Consult /var/lib/dkms/r8168/8.038.00/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-34-lowlatency /boot/vmlinuz-3.16.0-34-lowlatency
update-initramfs: Generating /boot/initrd.img-3.16.0-34-lowlatency
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-34-lowlatency /boot/vmlinuz-3.16.0-34-lowlatency
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-34-lowlatency /boot/vmlinuz-3.16.0-34-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 4405: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 4405: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 4594: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 4594: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-36-generic
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 5415: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 5415: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on lvs invocation. Parent PID 5549: /bin/sh
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-3.16.0-37-generic (3.16.0-37.49) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
vmlinuz(/boot/vmlinuz-3.16.0-37-generic
) points to /boot/vmlinuz-3.16.0-37-generic
 (/boot/vmlinuz-3.16.0-37-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.16.0-37-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-37-generic (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.16.0-37-generic (x86_64)
Consult /var/lib/dkms/r8168/8.038.00/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-37-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 17199: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 17199: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 17388: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 17388: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found initrd image: /boot/initrd.img-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-36-generic
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 18228: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 18228: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on lvs invocation. Parent PID 18362: /bin/sh
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-extra-3.16.0-34-generic (3.16.0-34.47) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
Error! Bad return status for module build on kernel: 3.16.0-34-generic (x86_64)
Consult /var/lib/dkms/r8168/8.038.00/build/make.log for more information.
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-34-generic (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-34-generic /boot/vmlinuz-3.16.0-34-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 29903: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 29903: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 30093: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 30093: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found initrd image: /boot/initrd.img-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-36-generic
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 30932: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 30932: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on lvs invocation. Parent PID 31066: /bin/sh
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-3.16.0-36-generic (3.16.0-36.48) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
Error! Your kernel headers for kernel 3.16.0-36-generic cannot be found.
Please install the linux-headers-3.16.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.16.0-36-generic cannot be found.
Please install the linux-headers-3.16.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 9213: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 9213: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 9402: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 9402: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found initrd image: /boot/initrd.img-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-36-generic
Found initrd image: /boot/initrd.img-3.16.0-36-generic
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 10258: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 10258: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on lvs invocation. Parent PID 10392: /bin/sh
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-extra-3.16.0-36-generic (3.16.0-36.48) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
Error! Your kernel headers for kernel 3.16.0-36-generic cannot be found.
Please install the linux-headers-3.16.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.16.0-36-generic cannot be found.
Please install the linux-headers-3.16.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-36-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.16.0-36-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.16.0-36-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-extra-3.16.0-37-generic (3.16.0-37.49) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-37-generic (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.16.0-37-generic (x86_64)
Consult /var/lib/dkms/r8168/8.038.00/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-37-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.16.0-37-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.16.0-37-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-3.16.0-41-lowlatency (3.16.0-41.57) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-41-lowlatency /boot/vmlinuz-3.16.0-41-lowlatency
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-41-lowlatency /boot/vmlinuz-3.16.0-41-lowlatency
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-41-lowlatency (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.16.0-41-lowlatency (x86_64)
Consult /var/lib/dkms/r8168/8.038.00/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-41-lowlatency /boot/vmlinuz-3.16.0-41-lowlatency
update-initramfs: Generating /boot/initrd.img-3.16.0-41-lowlatency

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.16.0-41-lowlatency with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.16.0-41-lowlatency.postinst line 1025.
dpkg: error processing package linux-image-3.16.0-41-lowlatency (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-lowlatency:
 linux-image-lowlatency depends on linux-image-3.16.0-41-lowlatency; however:
  Package linux-image-3.16.0-41-lowlatency is not configured yet.

dpkg: error processing package linux-image-lowlatency (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-lowlatency:
 linux-lowlatency depends on linux-image-lowlatency (= 3.16.0.41.41); however:
  Package linux-image-lowlatency is not configured yet.

dpkg: error processing package linux-lowlatency (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-3.16.0-37-generic:
 linux-signed-image-3.16.0-37-generic depends on linux-image-extra-3.16.0-37-generic (= 3.16.0-37.49); however:
  Package linux-image-extra-3.16.0-37-generic is not configured yet.

dpkg: error processing package linux-signed-image-3.16.0-37-generic (--configure):
 dependeNo apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              ncy problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-generic:
 linux-signed-image-generic depends on linux-signed-image-3.16.0-37-generic; however:
  Package linux-signed-image-3.16.0-37-generic is not configured yet.

dpkg: error processing package linux-signed-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic:
 linux-signed-generic depends on linux-signed-image-generic (= 3.16.0.37.38); however:
  Package linux-signed-image-generic is not configured yet.

dpkg: error processing package linux-signed-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-signed-image-3.16.0-34-generic (3.16.0-34.47) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 10778: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 10778: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 10967: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 10967: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-37-generic
Found initrd image: /boot/initrd.img-3.16.0-37-generic
Found linux image: /boot/vmlinuz-3.16.0-36-generic
Found initrd image: /boot/initrd.img-3.16.0-36-generic
Found linux image: /boot/vmlinuz-3.16.0-34-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-34-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found linux image: /boot/vmlinuz-3.16.0-33-generic
Found initrd image: /boot/initrd.img-3.16.0-33-generic
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 11943: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 11943: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on lvs invocation. Parent PID 12084: /bin/sh
Adding boot menu entry for EFI firmware configuration
done
Errors were encountered while processing:
 linux-image-extra-3.16.0-36-generic
 linux-image-extra-3.16.0-37-generic
 linux-image-3.16.0-41-lowlatency
 linux-image-lowlatency
 linux-lowlatency
 linux-signed-image-3.16.0-37-generic
 linux-signed-image-generic
 linux-signed-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Here's the df -h and df -i 
```
haven@haven-Lenovo-Z40-70:~$ df -h
Filesystem                           Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--studio--vg-root  450G   92G  336G  22% /
none                                 4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                 3.9G  4.0K  3.9G   1% /dev
tmpfs                                788M  1.2M  787M   1% /run
none                                 5.0M  4.0K  5.0M   1% /run/lock
none                                 3.9G   80K  3.9G   1% /run/shm
none                                 100M   44K  100M   1% /run/user
/dev/sda2                            237M  233M     0 100% /boot
/dev/sda1                            511M  3.4M  508M   1% /boot/efi
haven@haven-Lenovo-Z40-70:~$ df -i
Filesystem                            Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/ubuntu--studio--vg-root 29958144 410405 29547739    2% /
none                                 1008250      4  1008246    1% /sys/fs/cgroup
udev                                 1004116    530  1003586    1% /dev
tmpfs                                1008250    618  1007632    1% /run
none                                 1008250      3  1008247    1% /run/lock
none                                 1008250      5  1008245    1% /run/shm
none                                 1008250     29  1008221    1% /run/user
/dev/sda2                              62496    317    62179    1% /boot
/dev/sda1                                  0      0        0     - /boot/efi


```

---

### Post by Bashing-om on 2015-06-24
Haven_McClure; Welp;

One step forward and 3 steps back.
Back to 100% capacity - no operating head room.

Let's go back to 'dpkg -l ' and see how we can help the package manager.
```

dpkg -l | grep linux-

```

and we see what we can do next .

[INDENT][INDENT]round and round we go
[/INDENT][/INDENT]

---

### Post by Haven_McClure on 2015-06-24
where it all stops, nobody knows...Wheel! Of! Fortune!

```
haven@haven-Lenovo-Z40-70:~$ dpkg -l | grep linux-
ii  ladspa-sdk                                  1.13-2                                   amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-firmware                              1.138.1                                  all          Firmware for Linux kernel drivers
ii  linux-headers-3.16.0-34                     3.16.0-34.47                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-34-generic             3.16.0-34.47                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-34-lowlatency          3.16.0-34.47                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
pi  linux-headers-3.16.0-37                     3.16.0-37.49                             all          Header files related to Linux kernel version 3.16.0
pi  linux-headhaven@haven-Lenovo-Z40-70:~$ dpkg -l | grep linux-
ii  ladspa-sdk                                  1.13-2                                   amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-firmware                              1.138.1                                  all          Firmware for Linux kernel drivers
ii  linux-headers-3.16.0-34                     3.16.0-34.47                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-34-generic             3.16.0-34.47                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-34-lowlatency          3.16.0-34.47                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
pi  linux-headers-3.16.0-37                     3.16.0-37.49                             all          Header files related to Linux kernel version 3.16.0
pi  linux-headers-3.16.0-37-generic             3.16.0-37.49                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-41                     3.16.0-41.57                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-41-lowlatency          3.16.0-41.57                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-generic                       3.16.0.37.38                             amd64        Generic Linux kernel headers
ii  linux-headers-lowlatency                    3.16.0.41.41                             amd64        lowlatency Linux kernel headers
ii  linux-image-3.16.0-33-generic               3.16.0-33.44                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-34-generic               3.16.0-34.47                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-34-lowlatency            3.16.0-34.47                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-36-generic               3.16.0-36.48                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-37-generic               3.16.0-37.49                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
iF  linux-image-3.16.0-41-lowlatency            3.16.0-41.57                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
pi  linux-image-extra-3.16.0-33-generic         3.16.0-33.44                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-34-generic         3.16.0-34.47                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
pF  linux-image-extra-3.16.0-36-generic         3.16.0-36.48                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
pF  linux-image-extra-3.16.0-37-generic         3.16.0-37.49                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
iU  linux-image-lowlatency                      3.16.0.41.41                             amd64        lowlatency Linux kernel image
ii  linux-libc-dev:amd64                        3.16.0-37.49                             amd64        Linux Kernel Headers for development
iU  linux-lowlatency                            3.16.0.41.41                             amd64        Complete lowlatency Linux kernel
iU  linux-signed-generic                        3.16.0.37.38                             amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-3.16.0-34-generic        3.16.0-34.47                             amd64        Signed kernel image generic
pU  linux-signed-image-3.16.0-37-generic        3.16.0-37.49                             amd64        Signed kernel image generic
iU  linux-signed-image-generic                  3.16.0.37.38                             amd64        Signed Generic Linux kernel image
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                     all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03~pre18+dfsg-1ubuntu1               all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu5                     amd64        Bootloader for Linux/i386 using MS-DOS floppies
ers-3.16.0-37-generic             3.16.0-37.49                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-41                     3.16.0-41.57                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-41-lowlatency          3.16.0-41.57                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-generic                       3.16.0.37.38                             amd64        Generic Linux kernel headers
ii  linux-headers-lowlatency                    3.16.0.41.41                             amd64        lowlatency Linux kernel headers
ii  linux-image-3.16.0-33-generic               3.16.0-33.44                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-34-generic               3.16.0-34.47                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-34-lowlatency            3.16.0-34.47                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-36-generic               3.16.0-36.48                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-37-generic               3.16.0-37.49                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
iF  linux-image-3.16.0-41-lowlatency            3.16.0-41.57                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
pi  linux-image-extra-3.16.0-33-generic         3.16.0-33.44                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-34-generic         3.16.0-34.47                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
pF  linux-image-extra-3.16.0-36-generic         3.16.0-36.48                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
pF  linux-image-extra-3.16.0-37-generic         3.16.0-37.49                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
iU  linux-image-lowlatency                      3.16.0.41.41                             amd64        lowlatency Linux kernel image
ii  linux-libc-dev:amd64                        3.16.0-37.49                             amd64        Linux Kernel Headers for development
iU  linux-lowlatency                            3.16.0.41.41                             amd64        Complete lowlatency Linux kernel
iU  linux-signed-generic                        3.16.0.37.38                             amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-3.16.0-34-generic        3.16.0-34.47                             amd64        Signed kernel image generic
pU  linux-signed-image-3.16.0-37-generic        3.16.0-37.49                             amd64        Signed kernel image generic
iU  linux-signed-image-generic                  3.16.0.37.38                             amd64        Signed Generic Linux kernel image
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                     all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03~pre18+dfsg-1ubuntu1               all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu5                     amd64        Bootloader for Linux/i386 using MS-DOS floppies


```

---

### Post by Bashing-om on 2015-06-24
Haven_McClure; Yeah !

Let's give the -36 and and -37 kernels a whirl.
(bearing in mind that "Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information. " will have to be dealt with at some point)

Can we do:
```

sudo dpkg -P linux-image-extra-3.16.0-36-generic

```

And a after hand thought, is this a total LVM install where we can rob the space from the /efi partition and give it to /boot ? When we can get to this point. Got to get the package manager happy and get this sytem updated !
-----------------
I got chores to get done, so I be away from the keyboard for a couple of hours.

I will be back and we pick this back up.
-------------------------------------------------------


[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Haven_McClure on 2015-06-24
Error messages, space limits, not sure whether to cheer yet.  Funny thing happened, though--got a "software update" notice, which I haven't seen in a while.  Probably would give errors though as we still seems to have space issues. Not sure what you mean by a total LVM install. Ubuntu Studio 14.10 is the only system on this laptop. 

```
haven@haven-Lenovo-Z40-70:~$ sudo dpkg -P linux-image-extra-3.16.0-36-generic
[sudo] password for haven: 
(Reading database ... 324482 files and directories currently installed.)
Removing linux-image-extra-3.16.0-36-generic (3.16.0-36.48) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
Error! Your kernel headers for kernel 3.16.0-36-generic cannot be found.
Please install the linux-headers-3.16.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.16.0-36-generic cannot be found.
Please install the linux-headers-3.16.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-36-generic /boot/vmlinuz-3.16.0-36-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-36-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.16.0-36-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.16.0-36-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.16.0-36-generic


```

---

### Post by Bashing-om on 2015-06-24
Haven_McClure; Sheesshh ...

Twix a rock and a hard place . No room to install anything to help, with no operating head room the package manager can not operate. 
So we go behind the package manager's back, get us some room, and repair the damage later.
So, what does grub think about this sloppyation ? - as we prepare to get dirty:
```

uname -r
ls -al /vmlinuz*
ls -al /initrd*

```

we now look at removing the old kernels manually:
what have we installed:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/

```

Keep in mind everyone reading this thread, THIS is not a good thing to do ! A means of last resort when there is no other alternative.

[INDENT][INDENT]when we break it
[INDENT][INDENT][INDENT][INDENT][INDENT]we fix it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Haven_McClure on 2015-06-24
> **Bashing-om said:**
> Haven_McClure; Sheesshh ...

Twix a rock and a hard place . No room to install anything to help, with no operating head room the package manager can not operate. 
So we go behind the package manager's back, get us some room, and repair the damage later.
So, what does grub think about this sloppyation ? - as we prepare to get dirty:
```

uname -r
ls -al /vmlinuz*
ls -al /initrd*

```

we now look at removing the old kernels manually:
what have we installed:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/

```

Keep in mind everyone reading this thread, THIS is not a good thing to do ! A means of last resort when there is no other alternative.
[INDENT][INDENT]when we break it[INDENT][INDENT][INDENT][INDENT][INDENT]we fix it
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Okay, before I attempt this, some new things have emerged. I shut down my laptop so I could carry it home with me. Then when I started it up--initially just white screen.  Held down start button, started it again, got screen giving me several choices.  I tried to log into the normal Ubuntni Studio, and it got error messages.  Shut it down, started it up again.  This time I hit Ubuntu Studio Recovery mode.  It gave me a bunch of kernels from which to start up.  I started the first low latency kernel in recovery mode (ended with a 41) and it gave me error messages and threw me back to the screen.  Then I tried starting it up with the other low latency kernel in recovery mode (ended with a 34) and this time it took.  Logged in like normal and everything looks fine except the only screen option it's giving me is 1920x1080 or something like that.  

One thing, though:  the "do not enter" icon is now gone.

So the stuff is getting serious.  What do you think now?  Proceed as is?  I'm backing everything up just to play it safe.:shock:

---

### Post by Bashing-om on 2015-06-24
Haven_McClure; Yeah;

Proceed. As to booting the -41 kernel, we know it is "bad" from the error reports.
However, as you have rebooted, will not hurt to take a look and see if we still have that 100% capacity condition.
If we now have some head room we can try to straighten things up with the package manager.

I am done for this session, calling it a day. We pick this up again on the morrow after I finish my morning chores.

[INDENT][INDENT]not so amazing the bear talks so well
[INDENT][INDENT][INDENT]what's amazing is that the bear talks at all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Haven_McClure on 2015-06-25
Okay, this is the output I got. Not sure what's really happening...but I put in a df -h and df -i at the end just to see where we're at.  Doesn't appear to be any significant change in the memory.

```
haven@haven-Lenovo-Z40-70:~$ uname -r
3.16.0-34-lowlatency
haven@haven-Lenovo-Z40-70:~$ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 33 Jun 24 17:28 /vmlinuz -> boot/vmlinuz-3.16.0-41-lowlatency
lrwxrwxrwx 1 root root 30 Jun 24 17:27 /vmlinuz.old -> boot/vmlinuz-3.16.0-36-generic
haven@haven-Lenovo-Z40-70:~$ ls -al /initrd*
lrwxrwxrwx 1 root root 36 Jun 24 17:28 /initrd.img -> boot/initrd.img-3.16.0-41-lowlatency
lrwxrwxrwx 1 root root 33 Jun 24 17:27 /initrd.img.old -> boot/initrd.img-3.16.0-36-generic
haven@haven-Lenovo-Z40-70:~$ ls -al /usr/src
total 48
drwxr-xr-x 12 root  root  4096 Jun 24 15:33 .
drwxr-xr-x 10 root  root  4096 Oct 22  2014 ..
drwxr-xr-x  5 root  root  4096 Feb 12 21:18 bcmwl-6.30.223.248+bdcom
drwxr-xr-x 24 root  root  4096 Apr 15 08:08 linux-headers-3.16.0-34
drwxr-xr-x  7 root  root  4096 Apr 15 08:09 linux-headers-3.16.0-34-generic
drwxr-xr-x  7 root  root  4096 Apr 15 08:09 linux-headers-3.16.0-34-lowlatency
drwxr-xr-x 24 root  root  4096 May  5 17:01 linux-headers-3.16.0-37
drwxr-xr-x  7 root  root  4096 May  5 17:01 linux-headers-3.16.0-37-generic
drwxr-xr-x 24 root  root  4096 Jun 20 15:49 linux-headers-3.16.0-41
drwxr-xr-x  7 root  root  4096 Jun 20 15:49 linux-headers-3.16.0-41-lowlatency
drwxr-xr-x  2 root  root  4096 Feb  6 20:26 r8168-8.038.00
drwxrwxrwx  3 haven haven 4096 Apr 13  2014 r8168-dkms-8.038.00
haven@haven-Lenovo-Z40-70:~$ ls -al /lib/modules/
total 40
drwxr-xr-x 10 root root 4096 Jun 24 15:33 .
drwxr-xr-x 25 root root 4096 Jan 24 18:21 ..
drwxr-xr-x  6 root root 4096 Jun 24 15:32 3.16.0-33-generic
drwxr-xr-x  6 root root 4096 Jun 24 17:26 3.16.0-34-generic
drwxr-xr-x  6 root root 4096 Jun 24 17:24 3.16.0-34-lowlatency
drwxr-xr-x  6 root root 4096 Jun 24 18:33 3.16.0-36-generic
drwxr-xr-x  3 root root 4096 Jun 24 15:33 3.16.0-36-lowlatency
drwxr-xr-x  6 root root 4096 Jun 24 17:28 3.16.0-37-generic
drwxr-xr-x  3 root root 4096 Jun 24 15:33 3.16.0-37-lowlatency
drwxr-xr-x  6 root root 4096 Jun 24 17:28 3.16.0-41-lowlatency
haven@haven-Lenovo-Z40-70:~$ ls -al /boot/
total 228305
drwxr-xr-x  5 root root     3072 Jun 24 18:33 .
drwxr-xr-x 23 root root     4096 Jun 24 17:28 ..
-rw-r--r--  1 root root  1207327 Mar 12 08:19 abi-3.16.0-33-generic
-rw-r--r--  1 root root  1207327 Apr 10 14:03 abi-3.16.0-34-generic
-rw-r--r--  1 root root  1208091 Apr 10 14:47 abi-3.16.0-34-lowlatency
-rw-r--r--  1 root root  1206938 Apr 14 15:48 abi-3.16.0-36-generic
-rw-r--r--  1 root root  1206938 Apr 29 16:17 abi-3.16.0-37-generic
-rw-r--r--  1 root root  1208130 Jun 18 05:29 abi-3.16.0-41-lowlatency
-rw-r--r--  1 root root   171819 Mar 12 08:19 config-3.16.0-33-generic
-rw-r--r--  1 root root   171819 Apr 10 14:03 config-3.16.0-34-generic
-rw-r--r--  1 root root   171821 Apr 10 14:47 config-3.16.0-34-lowlatency
-rw-r--r--  1 root root   171808 Apr 14 15:48 config-3.16.0-36-generic
-rw-r--r--  1 root root   171808 Apr 29 16:17 config-3.16.0-37-generic
-rw-r--r--  1 root root   171811 Jun 18 05:29 config-3.16.0-41-lowlatency
drwxr-xr-x  3 root root     4096 Dec 31  1969 efi
drwxr-xr-x  5 root root     1024 Jun 24 17:29 grub
-rw-r--r--  1 root root 31627338 Apr  4 15:14 initrd.img-3.16.0-33-generic
-rw-r--r--  1 root root 31636370 Jun 24 17:27 initrd.img-3.16.0-34-generic
-rw-r--r--  1 root root 31557236 Jun 24 17:25 initrd.img-3.16.0-34-lowlatency
-rw-r--r--  1 root root 31635696 Jun 24 17:27 initrd.img-3.16.0-36-generic
-rw-r--r--  1 root root 31635998 Jun 24 17:26 initrd.img-3.16.0-37-generic
drwx------  2 root root    12288 Jan 24 18:02 lost+found
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3502105 Mar 12 08:19 System.map-3.16.0-33-generic
-rw-------  1 root root  3502413 Apr 10 14:03 System.map-3.16.0-34-generic
-rw-------  1 root root  3504468 Apr 10 14:47 System.map-3.16.0-34-lowlatency
-rw-------  1 root root  3502913 Apr 14 15:48 System.map-3.16.0-36-generic
-rw-------  1 root root  3502913 Apr 29 16:17 System.map-3.16.0-37-generic
-rw-------  1 root root  3506826 Jun 18 05:29 System.map-3.16.0-41-lowlatency
-rw-------  1 root root  6411712 Mar 12 08:19 vmlinuz-3.16.0-33-generic
-rw-------  1 root root  6412672 Apr 10 14:03 vmlinuz-3.16.0-34-generic
-rw-------  1 root root  6414584 Jun 24 17:29 vmlinuz-3.16.0-34-generic.efi.signed
-rw-------  1 root root  6400528 Apr 10 14:47 vmlinuz-3.16.0-34-lowlatency
-rw-------  1 root root  6414272 Apr 14 15:48 vmlinuz-3.16.0-36-generic
-rw-------  1 root root  6414336 Apr 29 16:17 vmlinuz-3.16.0-37-generic
-rw-------  1 root root  6404176 Jun 18 05:29 vmlinuz-3.16.0-41-lowlatency
haven@haven-Lenovo-Z40-70:~$ df -h
Filesystem                           Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--studio--vg-root  450G   91G  337G  22% /
none                                 4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                 3.9G  4.0K  3.9G   1% /dev
tmpfs                                788M  1.3M  787M   1% /run
none                                 5.0M  4.0K  5.0M   1% /run/lock
none                                 3.9G   80K  3.9G   1% /run/shm
none                                 100M   44K  100M   1% /run/user
/dev/sda2                            237M  233M     0 100% /boot
/dev/sda1                            511M  3.4M  508M   1% /boot/efi
/dev/sdb1                            932G  172G  760G  19% /media/haven/My Passport
haven@haven-Lenovo-Z40-70:~$ df -i
Filesystem                             Inodes  IUsed     IFree IUse% Mounted on
/dev/mapper/ubuntu--studio--vg-root  29958144 404520  29553624    2% /
none                                  1008250      4   1008246    1% /sys/fs/cgroup
udev                                  1004115    574   1003541    1% /dev
tmpfs                                 1008250    676   1007574    1% /run
none                                  1008250      2   1008248    1% /run/lock
none                                  1008250      5   1008245    1% /run/shm
none                                  1008250     29   1008221    1% /run/user
/dev/sda2                               62496    317     62179    1% /boot
/dev/sda1                                   0      0         0     - /boot/efi
/dev/sdb1                           796496216  70313 796425903    1% /media/haven/My Passport
haven@haven-Lenovo-Z40-70:~$ 


```

---

### Post by Bashing-om on 2015-06-25
Haven_McClure; OK;

Let's do this the dirty way.
Looking at the 3 directories we can see why the package manager is screaming and hollering. All three "should"  reflect all the same versions for the corresponding files.
In booting grub there is no longer "boot/vmlinuz-3.16.0-36-generic: to fall back to. So we do away with any of the related files. And fix the link at a later time if the package manager does not fix it for us.
We must keep the kernel you are booting, -34 , and you MUST insure that you do boot up with that -34 kernel !
So, let's get us some operating room:
in /usr/src/ directory remove;
```

sudo rm -rf /usr/src/linux-headers-3.16.0-37-generic
sudo rm -rf /usr/src/linux-headers-3.16.0-37

```

in /lib/modules directory remove ;
```

sudo rm -rf /lib/modules/3.16.0-{33,36,37}-generic
sudo rm -rf /lib/modules/3.16.0-{36,37}-lowlatency

```

And in /boot directory remove:
```

sudo rm /boot/*-3.16.0-{33,36,37}-generic

```

OK, now we have some operating head room, let's see if the package manager will now complete the install of the -41 kernel:
```

sudo apt-get -f install

```

And for this round, a bit of cleanup and insurance:
```

sudo apt-get purge linux-image-3.16.0-{33,36,37}*
sudo apt-get purge linux-headers-3.16.0-{33,36,37}*

```
Be alright when the package manager can not find files, just a shot gun approach here to make sure all is purged.


OK, now let's see what we have:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo update-grub

```

Hold your breath, cross your fingers and RE-boot. Let's see what we look like !

Did the system fix the symlink for the backup kernel ? Look :
```

ls -al /vmlinuz*
ls -al /initrd*

``` 
See if we have to take matters into our hands here and install a backup kernel IF we are clean at this point .

And is your WIFI now working ? Package manager is smart, real smart - but - as the case is here. sometimes needs a helping hand.

[INDENT][INDENT][INDENT]maybe YES
[/INDENT][/INDENT][/INDENT]

---

### Post by Haven_McClure on 2015-06-25
Okay, before rebooting I thought I'd post the output.  So I went through the directory removals but forgot to do the removal from the /boot/ directory before doing an apt-get install -f, so I initially got errors.  But once I ran the directory removal for /boot/ things began to run more smoothly.  I refrained from doing the second "cleanup for insurance" purge because when it was about to do so, it said that it was going to remove some things associated with kernel 34, so I didn't want to take that chance.  I went ahead and went through the updates.  They seem to have worked.  So I'm posting this mountain of output below in case it's informative.

```
Found initrd image: /boot/initrd.img-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-41-generic
Found initrd image: /boot/initrd.img-3.16.0-41-generic
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 20062: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 20062: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on lvs invocation. Parent PID 20168: /bin/sh
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-extra-3.16.0-41-generic (3.16.0-41.57) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-41-generic /boot/vmlinuz-3.16.0-41-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-41-generic /boot/vmlinuz-3.16.0-41-generic
Error! Bad return status for module build on kernel: 3.16.0-41-generic (x86_64)
Consult /var/lib/dkms/r8168/8.038.00/build/make.log for more information.
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-41-generic (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-41-generic /boot/vmlinuz-3.16.0-41-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-41-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-41-generic /boot/vmlinuz-3.16.0-41-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-41-generic /boot/vmlinuz-3.16.0-41-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 31463: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 31463: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-41-lowlatency
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 31647: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 31647: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-41-generic
Found initrd image: /boot/initrd.img-3.16.0-41-generic
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 32013: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 32013: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on lvs invocation. Parent PID 32119: /bin/sh
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-signed-image-3.16.0-41-generic (3.16.0-41.57) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 32588: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 32588: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-41-lowlatency
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 307: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 307: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-41-generic
Found initrd image: /boot/initrd.img-3.16.0-41-generic
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 717: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on vgs invocation. Parent PID 717: /usr/sbin/grub-probe
File descriptor 56 (/dev/pts/12) leaked on lvs invocation. Parent PID 830: /bin/sh
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-signed-image-generic (3.16.0.41.41) ...
Setting up linux-headers-generic (3.16.0.41.41) ...
Setting up linux-signed-generic (3.16.0.41.41) ...
haven@haven-Lenovo-Z40-70:~$ sudo apt-get purge linux-headers-3.16.0-{33,36,37}*Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-headers-3.16.0-38-generic' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-36-generic' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-37-lowlatency' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-30' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-31' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-33' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-34' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-36' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-37' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-38' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-39' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-34-generic' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-34-lowlatency' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-31-lowlatency' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-39-lowlatency' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-30-generic' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-39-generic' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-36-lowlatency' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-37-generic' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-33-lowlatency' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-30-lowlatency' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-33-generic' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-38-lowlatency' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-31-generic' for regex 'linux-headers-3.16.0-33*'
Note, selecting 'linux-headers-3.16.0-38-generic' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-36-generic' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-37-lowlatency' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-30' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-31' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-33' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-34' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-36' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-37' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-38' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-39' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-34-generic' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-34-lowlatency' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-31-lowlatency' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-39-lowlatency' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-30-generic' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-39-generic' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-36-lowlatency' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-37-generic' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-33-lowlatency' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-30-lowlatency' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-33-generic' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-38-lowlatency' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-31-generic' for regex 'linux-headers-3.16.0-36*'
Note, selecting 'linux-headers-3.16.0-38-generic' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-36-generic' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-37-lowlatency' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-30' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-31' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-33' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-34' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-36' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-37' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-38' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-39' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-34-generic' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-34-lowlatency' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-31-lowlatency' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-39-lowlatency' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-30-generic' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-39-generic' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-36-lowlatency' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-37-generic' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-33-lowlatency' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-30-lowlatency' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-33-generic' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-38-lowlatency' for regex 'linux-headers-3.16.0-37*'
Note, selecting 'linux-headers-3.16.0-31-generic' for regex 'linux-headers-3.16.0-37*'
Package 'linux-headers-3.16.0-30' is not installed, so not removed
Package 'linux-headers-3.16.0-30-generic' is not installed, so not removed
Package 'linux-headers-3.16.0-30-lowlatency' is not installed, so not removed
Package 'linux-headers-3.16.0-31' is not installed, so not removed
Package 'linux-headers-3.16.0-31-generic' is not installed, so not removed
Package 'linux-headers-3.16.0-31-lowlatency' is not installed, so not removed
Package 'linux-headers-3.16.0-33' is not installed, so not removed
Package 'linux-headers-3.16.0-33-generic' is not installed, so not removed
Package 'linux-headers-3.16.0-33-lowlatency' is not installed, so not removed
Package 'linux-headers-3.16.0-36' is not installed, so not removed
Package 'linux-headers-3.16.0-36-generic' is not installed, so not removed
Package 'linux-headers-3.16.0-36-lowlatency' is not installed, so not removed
Package 'linux-headers-3.16.0-37-lowlatency' is not installed, so not removed
Package 'linux-headers-3.16.0-38' is not installed, so not removed
Package 'linux-headers-3.16.0-38-generic' is not installed, so not removed
Package 'linux-headers-3.16.0-38-lowlatency' is not installed, so not removed
Package 'linux-headers-3.16.0-39' is not installed, so not removed
Package 'linux-headers-3.16.0-39-generic' is not installed, so not removed
Package 'linux-headers-3.16.0-39-lowlatency' is not installed, so not removed
The following packages will be REMOVED:
  linux-headers-3.16.0-34* linux-headers-3.16.0-34-generic*
  linux-headers-3.16.0-34-lowlatency* linux-headers-3.16.0-37*
  linux-headers-3.16.0-37-generic*
0 upgraded, 0 newly installed, 5 to remove and 91 not upgraded.
After this operation, 170 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
haven@haven-Lenovo-Z40-70:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com utopic InRelease                              
Ign http://us.archive.ubuntu.com utopic-updates InRelease                      
Ign http://security.ubuntu.com utopic-security InRelease
Ign http://us.archive.ubuntu.com utopic-backports InRelease
Ign http://ppa.launchpad.net utopic InRelease  
Hit http://us.archive.ubuntu.com utopic Release.gpg
Get:1 http://us.archive.ubuntu.com utopic-updates Release.gpg [933 B]
Get:2 http://security.ubuntu.com utopic-security Release.gpg [933 B]           
Hit http://us.archive.ubuntu.com utopic-backports Release.gpg                  
Ign http://ppa.launchpad.net utopic Release.gpg 
Hit http://us.archive.ubuntu.com utopic Release 
Get:3 http://security.ubuntu.com utopic-security Release [63.5 kB]             
Get:4 http://us.archive.ubuntu.com utopic-updates Release [63.5 kB]          
Ign http://ppa.launchpad.net utopic Release                                    
Hit http://us.archive.ubuntu.com utopic-backports Release                      
Get:5 http://security.ubuntu.com utopic-security/main Sources [61.6 kB]        
Get:6 http://security.ubuntu.com utopic-security/restricted Sources [2,107 B]  
Get:7 http://security.ubuntu.com utopic-security/universe Sources [15.4 kB]    
Get:8 http://security.ubuntu.com utopic-security/multiverse Sources [2,394 B]  
Get:9 http://security.ubuntu.com utopic-security/main amd64 Packages [206 kB]  
Get:10 http://us.archive.ubuntu.com utopic-updates/main Sources [105 kB]       
Get:11 http://us.archive.ubuntu.com utopic-updates/restricted Sources [3,033 B]
Get:12 http://us.archive.ubuntu.com utopic-updates/universe Sources [30.2 kB]  
Get:13 http://us.archive.ubuntu.com utopic-updates/multiverse Sources [2,394 B]
Get:14 http://us.archive.ubuntu.com utopic-updates/main amd64 Packages [295 kB]
Get:15 http://security.ubuntu.com utopic-security/restricted amd64 Packages [8,496 B]
Get:16 http://security.ubuntu.com utopic-security/universe amd64 Packages [77.5 kB]
Get:17 http://us.archive.ubuntu.com utopic-updates/restricted amd64 Packages [11.0 kB]
Get:18 http://us.archive.ubuntu.com utopic-updates/universe amd64 Packages [112 kB]
Get:19 http://security.ubuntu.com utopic-security/multiverse amd64 Packages [4,363 B]
Get:20 http://us.archive.ubuntu.com utopic-updates/multiverse amd64 Packages [4,363 B]
Get:21 http://us.archive.ubuntu.com utopic-updates/main i386 Packages [292 kB] 
Get:22 http://security.ubuntu.com utopic-security/main i386 Packages [204 kB]  
Get:23 http://us.archive.ubuntu.com utopic-updates/restricted i386 Packages [11.0 kB]
Get:24 http://security.ubuntu.com utopic-security/restricted i386 Packages [8,438 B]
Err http://ppa.launchpad.net utopic/main amd64 Packages                        
  404  Not Found
Get:25 http://security.ubuntu.com utopic-security/universe i386 Packages [77.5 kB]
Get:26 http://us.archive.ubuntu.com utopic-updates/universe i386 Packages [112 kB]
Err http://ppa.launchpad.net utopic/main i386 Packages                         
  404  Not Found
Get:27 http://us.archive.ubuntu.com utopic-updates/multiverse i386 Packages [4,494 B]
Ign http://ppa.launchpad.net utopic/main Translation-en_US                     
Get:28 http://us.archive.ubuntu.com utopic-updates/main Translation-en [138 kB]
Get:29 http://security.ubuntu.com utopic-security/multiverse i386 Packages [4,494 B]
Ign http://ppa.launchpad.net utopic/main Translation-en                        
Get:30 http://us.archive.ubuntu.com utopic-updates/universe Translation-en [62.7 kB]
Hit http://us.archive.ubuntu.com utopic-backports/restricted Sources           
Hit http://us.archive.ubuntu.com utopic-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com utopic-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com utopic-backports/multiverse amd64 Packages    
Hit http://security.ubuntu.com utopic-security/main Translation-en             
Hit http://us.archive.ubuntu.com utopic-backports/restricted i386 Packages     
Hit http://security.ubuntu.com utopic-security/multiverse Translation-en       
Hit http://security.ubuntu.com utopic-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com utopic-backports/multiverse i386 Packages     
Hit http://security.ubuntu.com utopic-security/universe Translation-en         
Hit http://us.archive.ubuntu.com utopic-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com utopic-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com utopic/main Sources                           
Hit http://us.archive.ubuntu.com utopic/restricted Sources                     
Hit http://us.archive.ubuntu.com utopic/universe Sources                       
Hit http://us.archive.ubuntu.com utopic/multiverse Sources                     
Hit http://us.archive.ubuntu.com utopic/main amd64 Packages                    
Hit http://us.archive.ubuntu.com utopic/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com utopic/universe amd64 Packages                
Hit http://us.archive.ubuntu.com utopic/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com utopic/main i386 Packages                     
Hit http://us.archive.ubuntu.com utopic/restricted i386 Packages               
Hit http://us.archive.ubuntu.com utopic/universe i386 Packages                 
Hit http://us.archive.ubuntu.com utopic/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com utopic/main Translation-en                    
Hit http://us.archive.ubuntu.com utopic/multiverse Translation-en              
Hit http://us.archive.ubuntu.com utopic/restricted Translation-en              
Hit http://us.archive.ubuntu.com utopic/universe Translation-en                
Hit http://us.archive.ubuntu.com utopic-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com utopic-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com utopic-backports/main Sources                 
Hit http://us.archive.ubuntu.com utopic-backports/universe Sources             
Hit http://us.archive.ubuntu.com utopic-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com utopic-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com utopic-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com utopic-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com utopic-backports/main Translation-en          
Hit http://us.archive.ubuntu.com utopic-backports/universe Translation-en      
Fetched 1,983 kB in 13s (147 kB/s)                                             
W: Failed to fetch http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/utopic/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/utopic/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
haven@haven-Lenovo-Z40-70:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-37 linux-headers-3.16.0-37-generic
Use 'apt-get autoremove' to remove them.
Done
The following packages will be upgraded:
  apport apport-gtk aptdaemon aptdaemon-data chromium-codecs-ffmpeg-extra cups
  cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-ppdc
  cups-server-common dnsmasq-base firefox firefox-locale-en
  flashplugin-installer fuse gdisk gir1.2-gtk-3.0 gvfs gvfs-backends gvfs-bin
  gvfs-common gvfs-daemons gvfs-fuse gvfs-libs isc-dhcp-client isc-dhcp-common
  libcups2 libcupscgi1 libcupsimage2 libcupsmime1 libcupsppdc1 libfuse2
  libgail-3-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libicu52 libldap-2.4-2
  libnuma1 libpython2.7 libpython2.7-minimal libpython2.7-stdlib libpython3.4
  libpython3.4-minimal libpython3.4-stdlib libqt4-dbus libqt4-declarative
  libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqtcore4 libqtdbus4 libqtgui4 libssl1.0.0 libtasn1-6
  linux-headers-3.16.0-37 linux-headers-3.16.0-37-generic linux-libc-dev
  openssl oxideqt-codecs-extra patch ppp python-aptdaemon
  python-aptdaemon.gtk3widgets python2.7 python2.7-minimal python3-apport
  python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat
  python3-problem-report python3.4 python3.4-minimal qdbus qtcore4-l10n
  t1utils thunderbird wpasupplicant xserver-xorg-video-intel
93 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 127 MB of archives.
After this operation, 859 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libpython3.4 amd64 3.4.2-1ubuntu0.1 [1,316 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main python3.4 amd64 3.4.2-1ubuntu0.1 [173 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libpython3.4-stdlib amd64 3.4.2-1ubuntu0.1 [2,088 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main python3.4-minimal amd64 3.4.2-1ubuntu0.1 [1,614 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libssl1.0.0 amd64 1.0.1f-1ubuntu9.8 [850 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libpython3.4-minimal amd64 3.4.2-1ubuntu0.1 [460 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libtasn1-6 amd64 4.0-2ubuntu0.2 [41.8 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main fuse amd64 2.9.2-4ubuntu4.14.10.1 [25.3 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libfuse2 amd64 2.9.2-4ubuntu4.14.10.1 [89.0 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libldap-2.4-2 amd64 2.4.31-1+nmu2ubuntu11.1 [154 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libnuma1 amd64 2.0.9~rc5-1ubuntu3.14.10.1 [20.8 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/universe chromium-codecs-ffmpeg-extra amd64 43.0.2357.81-0ubuntu0.14.10.1.1131 [862 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main cups-server-common all 1.7.5-3ubuntu3.2 [519 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libcupsmime1 amd64 1.7.5-3ubuntu3.2 [12.3 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main cups-core-drivers amd64 1.7.5-3ubuntu3.2 [25.8 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main cups-common all 1.7.5-3ubuntu3.2 [173 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main cups-daemon amd64 1.7.5-3ubuntu3.2 [277 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libcupsimage2 amd64 1.7.5-3ubuntu3.2 [15.2 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libcupsppdc1 amd64 1.7.5-3ubuntu3.2 [44.6 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libcupscgi1 amd64 1.7.5-3ubuntu3.2 [26.9 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main cups-client amd64 1.7.5-3ubuntu3.2 [198 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libcups2 amd64 1.7.5-3ubuntu3.2 [182 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main cups amd64 1.7.5-3ubuntu3.2 [190 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main cups-bsd amd64 1.7.5-3ubuntu3.2 [35.4 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main cups-ppdc amd64 1.7.5-3ubuntu3.2 [25.7 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libgtk-3-common all 3.12.2-0ubuntu15.3 [174 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libgail-3-0 amd64 3.12.2-0ubuntu15.3 [20.7 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libgtk-3-0 amd64 3.12.2-0ubuntu15.3 [2,073 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libicu52 amd64 52.1-6ubuntu0.3 [6,775 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main python2.7 amd64 2.7.8-10ubuntu1.1 [205 kB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main python2.7-minimal amd64 2.7.8-10ubuntu1.1 [1,357 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libpython2.7 amd64 2.7.8-10ubuntu1.1 [1,080 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libpython2.7-stdlib amd64 2.7.8-10ubuntu1.1 [1,840 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libpython2.7-minimal amd64 2.7.8-10ubuntu1.1 [331 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main qtcore4-l10n all 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [619 kB]
Get:36 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-scripttools amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [223 kB]
Get:37 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-svg amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [138 kB]
Get:38 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-qt3support amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [1,071 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-opengl amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [304 kB]
Get:40 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-help amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [205 kB]
Get:41 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-designer amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [3,642 kB]
Get:42 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqtgui4 amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [4,265 kB]
Get:43 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-declarative amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [1,098 kB]
Get:44 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-xmlpatterns amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [1,059 kB]
Get:45 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-sql-sqlite amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [23.5 kB]
Get:46 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-sql-mysql amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [30.6 kB]
Get:47 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-sql amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [100 kB]
Get:48 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-network amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [567 kB]
Get:49 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-script amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [811 kB]
Get:50 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqtdbus4 amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [183 kB]
Get:51 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-dbus amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [6,496 B]
Get:52 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main qdbus amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [29.0 kB]
Get:53 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-xml amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [97.4 kB]
Get:54 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqt4-test amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [61.7 kB]
Get:55 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libqtcore4 amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1 [1,569 kB]
Get:56 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main isc-dhcp-client amd64 4.2.4-7ubuntu14.1 [657 kB]
Get:57 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main isc-dhcp-common amd64 4.2.4-7ubuntu14.1 [723 kB]
Get:58 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main openssl amd64 1.0.1f-1ubuntu9.8 [492 kB]
Get:59 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main ppp amd64 2.4.5-5.1ubuntu3.2 [314 kB]
Get:60 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main python3-problem-report all 2.14.7-0ubuntu8.5 [9,248 B]
Get:61 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main python3-apport all 2.14.7-0ubuntu8.5 [75.6 kB]
Get:62 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main apport all 2.14.7-0ubuntu8.5 [184 kB]
Get:63 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main gir1.2-gtk-3.0 amd64 3.12.2-0ubuntu15.3 [177 kB]
Get:64 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main apport-gtk all 2.14.7-0ubuntu8.5 [9,574 B]
Get:65 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main dnsmasq-base amd64 2.71-1ubuntu0.1 [280 kB]
Get:66 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main firefox amd64 38.0+build3-0ubuntu0.14.10.1 [38.8 MB]
Get:67 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main firefox-locale-en amd64 38.0+build3-0ubuntu0.14.10.1 [642 kB]
Get:68 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/multiverse flashplugin-installer amd64 11.2.202.468ubuntu0.14.10.1 [7,210 B]
Get:69 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main gvfs-fuse amd64 1.20.2-1ubuntu3.1 [13.5 kB]
Get:70 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main gvfs-bin amd64 1.20.2-1ubuntu3.1 [50.6 kB]
Get:71 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main gvfs-backends amd64 1.20.2-1ubuntu3.1 [276 kB]
Get:72 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main gvfs-libs amd64 1.20.2-1ubuntu3.1 [106 kB]
Get:73 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main gvfs amd64 1.20.2-1ubuntu3.1 [91.5 kB]
Get:74 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main gvfs-daemons amd64 1.20.2-1ubuntu3.1 [110 kB]
Get:75 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main gvfs-common all 1.20.2-1ubuntu3.1 [41.8 kB]
Get:76 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libgtk-3-bin amd64 3.12.2-0ubuntu15.3 [18.3 kB]
Get:77 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main linux-headers-3.16.0-37 all 3.16.0-37.51 [9,117 kB]
Get:78 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main linux-headers-3.16.0-37-generic amd64 3.16.0-37.51 [721 kB]
Get:79 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main linux-libc-dev amd64 3.16.0-41.57 [777 kB]
Get:80 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main patch amd64 2.7.1-5ubuntu0.3 [87.0 kB]
Get:81 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main t1utils amd64 1.37-2.1ubuntu0.1 [51.7 kB]
Get:82 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main thunderbird amd64 1:31.7.0+build1-0ubuntu0.14.10.1 [30.8 MB]
Get:83 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main wpasupplicant amd64 2.1-0ubuntu4.2 [766 kB]
Get:84 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main xserver-xorg-video-intel amd64 2:2.99.914-1~exp1ubuntu4.4 [693 kB]
Get:85 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main python3-aptdaemon.pkcompat all 1.1.1+bzr980-0ubuntu1.1 [23.2 kB]
Get:86 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main aptdaemon-data all 1.1.1+bzr980-0ubuntu1.1 [161 kB]
Get:87 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main python3-aptdaemon.gtk3widgets all 1.1.1+bzr980-0ubuntu1.1 [13.9 kB]
Get:88 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main aptdaemon all 1.1.1+bzr980-0ubuntu1.1 [13.6 kB]
Get:89 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main python3-aptdaemon all 1.1.1+bzr980-0ubuntu1.1 [76.7 kB]
Get:90 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main gdisk amd64 0.8.8-1ubuntu0.1 [185 kB]
Get:91 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main oxideqt-codecs-extra amd64 1.7.8-0ubuntu0.14.10.1 [870 kB]
Get:92 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main python-aptdaemon.gtk3widgets all 1.1.1+bzr980-0ubuntu1.1 [13.9 kB]
Get:93 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main python-aptdaemon all 1.1.1+bzr980-0ubuntu1.1 [76.1 kB]
Fetched 127 MB in 3min 37s (584 kB/s)                                          
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 313099 files and directories currently installed.)
Preparing to unpack .../libpython3.4_3.4.2-1ubuntu0.1_amd64.deb ...
Unpacking libpython3.4:amd64 (3.4.2-1ubuntu0.1) over (3.4.2-1) ...
Preparing to unpack .../python3.4_3.4.2-1ubuntu0.1_amd64.deb ...
Unpacking python3.4 (3.4.2-1ubuntu0.1) over (3.4.2-1) ...
Preparing to unpack .../libpython3.4-stdlib_3.4.2-1ubuntu0.1_amd64.deb ...
Unpacking libpython3.4-stdlib:amd64 (3.4.2-1ubuntu0.1) over (3.4.2-1) ...
Preparing to unpack .../python3.4-minimal_3.4.2-1ubuntu0.1_amd64.deb ...
Unpacking python3.4-minimal (3.4.2-1ubuntu0.1) over (3.4.2-1) ...
Preparing to unpack .../libssl1.0.0_1.0.1f-1ubuntu9.8_amd64.deb ...
Unpacking libssl1.0.0:amd64 (1.0.1f-1ubuntu9.8) over (1.0.1f-1ubuntu9.4) ...
Preparing to unpack .../libpython3.4-minimal_3.4.2-1ubuntu0.1_amd64.deb ...
Unpacking libpython3.4-minimal:amd64 (3.4.2-1ubuntu0.1) over (3.4.2-1) ...
Preparing to unpack .../libtasn1-6_4.0-2ubuntu0.2_amd64.deb ...
Unpacking libtasn1-6:amd64 (4.0-2ubuntu0.2) over (4.0-2ubuntu0.1) ...
Preparing to unpack .../fuse_2.9.2-4ubuntu4.14.10.1_amd64.deb ...
Unpacking fuse (2.9.2-4ubuntu4.14.10.1) over (2.9.2-4ubuntu4) ...
Preparing to unpack .../libfuse2_2.9.2-4ubuntu4.14.10.1_amd64.deb ...
Unpacking libfuse2:amd64 (2.9.2-4ubuntu4.14.10.1) over (2.9.2-4ubuntu4) ...
Preparing to unpack .../libldap-2.4-2_2.4.31-1+nmu2ubuntu11.1_amd64.deb ...
Unpacking libldap-2.4-2:amd64 (2.4.31-1+nmu2ubuntu11.1) over (2.4.31-1+nmu2ubuntu11) ...
Preparing to unpack .../libnuma1_2.0.9~rc5-1ubuntu3.14.10.1_amd64.deb ...
Unpacking libnuma1:amd64 (2.0.9~rc5-1ubuntu3.14.10.1) over (2.0.9~rc5-1ubuntu2) ...
Preparing to unpack .../chromium-codecs-ffmpeg-extra_43.0.2357.81-0ubuntu0.14.10.1.1131_amd64.deb ...
Unpacking chromium-codecs-ffmpeg-extra (43.0.2357.81-0ubuntu0.14.10.1.1131) over (41.0.2272.76-0ubuntu0.14.10.1.1118) ...
Preparing to unpack .../cups-server-common_1.7.5-3ubuntu3.2_all.deb ...
Unpacking cups-server-common (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../libcupsmime1_1.7.5-3ubuntu3.2_amd64.deb ...
Unpacking libcupsmime1:amd64 (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../cups-core-drivers_1.7.5-3ubuntu3.2_amd64.deb ...
Unpacking cups-core-drivers (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../cups-common_1.7.5-3ubuntu3.2_all.deb ...
Unpacking cups-common (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../cups-daemon_1.7.5-3ubuntu3.2_amd64.deb ...
cups stop/waiting
Unpacking cups-daemon (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../libcupsimage2_1.7.5-3ubuntu3.2_amd64.deb ...
Unpacking libcupsimage2:amd64 (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../libcupsppdc1_1.7.5-3ubuntu3.2_amd64.deb ...
Unpacking libcupsppdc1:amd64 (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../libcupscgi1_1.7.5-3ubuntu3.2_amd64.deb ...
Unpacking libcupscgi1:amd64 (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../cups-client_1.7.5-3ubuntu3.2_amd64.deb ...
Unpacking cups-client (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../libcups2_1.7.5-3ubuntu3.2_amd64.deb ...
Unpacking libcups2:amd64 (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../cups_1.7.5-3ubuntu3.2_amd64.deb ...
Unpacking cups (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../cups-bsd_1.7.5-3ubuntu3.2_amd64.deb ...
Unpacking cups-bsd (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../cups-ppdc_1.7.5-3ubuntu3.2_amd64.deb ...
Unpacking cups-ppdc (1.7.5-3ubuntu3.2) over (1.7.5-3ubuntu3.1) ...
Preparing to unpack .../libgtk-3-common_3.12.2-0ubuntu15.3_all.deb ...
Unpacking libgtk-3-common (3.12.2-0ubuntu15.3) over (3.12.2-0ubuntu15.2) ...
Preparing to unpack .../libgail-3-0_3.12.2-0ubuntu15.3_amd64.deb ...
Unpacking libgail-3-0:amd64 (3.12.2-0ubuntu15.3) over (3.12.2-0ubuntu15.2) ...
Preparing to unpack .../libgtk-3-0_3.12.2-0ubuntu15.3_amd64.deb ...
Unpacking libgtk-3-0:amd64 (3.12.2-0ubuntu15.3) over (3.12.2-0ubuntu15.2) ...
Preparing to unpack .../libicu52_52.1-6ubuntu0.3_amd64.deb ...
Unpacking libicu52:amd64 (52.1-6ubuntu0.3) over (52.1-6ubuntu0.2) ...
Preparing to unpack .../python2.7_2.7.8-10ubuntu1.1_amd64.deb ...
Unpacking python2.7 (2.7.8-10ubuntu1.1) over (2.7.8-10ubuntu1) ...
Preparing to unpack .../python2.7-minimal_2.7.8-10ubuntu1.1_amd64.deb ...
Unpacking python2.7-minimal (2.7.8-10ubuntu1.1) over (2.7.8-10ubuntu1) ...
Preparing to unpack .../libpython2.7_2.7.8-10ubuntu1.1_amd64.deb ...
Unpacking libpython2.7:amd64 (2.7.8-10ubuntu1.1) over (2.7.8-10ubuntu1) ...
Preparing to unpack .../libpython2.7-stdlib_2.7.8-10ubuntu1.1_amd64.deb ...
Unpacking libpython2.7-stdlib:amd64 (2.7.8-10ubuntu1.1) over (2.7.8-10ubuntu1) ...
Preparing to unpack .../libpython2.7-minimal_2.7.8-10ubuntu1.1_amd64.deb ...
Unpacking libpython2.7-minimal:amd64 (2.7.8-10ubuntu1.1) over (2.7.8-10ubuntu1) ...
Preparing to unpack .../qtcore4-l10n_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_all.deb ...
Unpacking qtcore4-l10n (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-scripttools_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-scripttools:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-svg_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-svg:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-qt3support_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-qt3support:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-opengl_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-opengl:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-help_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-help:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-designer_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-designer:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqtgui4_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqtgui4:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-declarative_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-declarative:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-xmlpatterns_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-xmlpatterns:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-sql-sqlite_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-sql-sqlite:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-sql-mysql_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-sql-mysql:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-sql_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-sql:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-network_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-network:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-script_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-script:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqtdbus4_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqtdbus4:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-dbus_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-dbus:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../qdbus_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking qdbus (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-xml_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-xml:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqt4-test_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqt4-test:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../libqtcore4_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1.1_amd64.deb ...
Unpacking libqtcore4:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) over (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Preparing to unpack .../isc-dhcp-client_4.2.4-7ubuntu14.1_amd64.deb ...
Unpacking isc-dhcp-client (4.2.4-7ubuntu14.1) over (4.2.4-7ubuntu14) ...
Preparing to unpack .../isc-dhcp-common_4.2.4-7ubuntu14.1_amd64.deb ...
Unpacking isc-dhcp-common (4.2.4-7ubuntu14.1) over (4.2.4-7ubuntu14) ...
Preparing to unpack .../openssl_1.0.1f-1ubuntu9.8_amd64.deb ...
Unpacking openssl (1.0.1f-1ubuntu9.8) over (1.0.1f-1ubuntu9.4) ...
Preparing to unpack .../ppp_2.4.5-5.1ubuntu3.2_amd64.deb ...
Unpacking ppp (2.4.5-5.1ubuntu3.2) over (2.4.5-5.1ubuntu3.1) ...
Preparing to unpack .../python3-problem-report_2.14.7-0ubuntu8.5_all.deb ...
Unpacking python3-problem-report (2.14.7-0ubuntu8.5) over (2.14.7-0ubuntu8.4) ...
Preparing to unpack .../python3-apport_2.14.7-0ubuntu8.5_all.deb ...
Unpacking python3-apport (2.14.7-0ubuntu8.5) over (2.14.7-0ubuntu8.4) ...
Preparing to unpack .../apport_2.14.7-0ubuntu8.5_all.deb ...
apport stop/waiting
Unpacking apport (2.14.7-0ubuntu8.5) over (2.14.7-0ubuntu8.4) ...
Preparing to unpack .../gir1.2-gtk-3.0_3.12.2-0ubuntu15.3_amd64.deb ...
Unpacking gir1.2-gtk-3.0 (3.12.2-0ubuntu15.3) over (3.12.2-0ubuntu15.2) ...
Preparing to unpack .../apport-gtk_2.14.7-0ubuntu8.5_all.deb ...
Unpacking apport-gtk (2.14.7-0ubuntu8.5) over (2.14.7-0ubuntu8.4) ...
Preparing to unpack .../dnsmasq-base_2.71-1ubuntu0.1_amd64.deb ...
Unpacking dnsmasq-base (2.71-1ubuntu0.1) over (2.71-1) ...
Preparing to unpack .../firefox_38.0+build3-0ubuntu0.14.10.1_amd64.deb ...
Unpacking firefox (38.0+build3-0ubuntu0.14.10.1) over (37.0.2+build1-0ubuntu0.14.10.1) ...
Preparing to unpack .../firefox-locale-en_38.0+build3-0ubuntu0.14.10.1_amd64.deb ...
Unpacking firefox-locale-en (38.0+build3-0ubuntu0.14.10.1) over (37.0.2+build1-0ubuntu0.14.10.1) ...
Preparing to unpack .../flashplugin-installer_11.2.202.468ubuntu0.14.10.1_amd64.deb ...
Unpacking flashplugin-installer (11.2.202.468ubuntu0.14.10.1) over (11.2.202.457ubuntu0.14.10.1) ...
Preparing to unpack .../gvfs-fuse_1.20.2-1ubuntu3.1_amd64.deb ...
Unpacking gvfs-fuse (1.20.2-1ubuntu3.1) over (1.20.2-1ubuntu3) ...
Preparing to unpack .../gvfs-bin_1.20.2-1ubuntu3.1_amd64.deb ...
Unpacking gvfs-bin (1.20.2-1ubuntu3.1) over (1.20.2-1ubuntu3) ...
Preparing to unpack .../gvfs-backends_1.20.2-1ubuntu3.1_amd64.deb ...
Unpacking gvfs-backends (1.20.2-1ubuntu3.1) over (1.20.2-1ubuntu3) ...
Preparing to unpack .../gvfs-libs_1.20.2-1ubuntu3.1_amd64.deb ...
Unpacking gvfs-libs:amd64 (1.20.2-1ubuntu3.1) over (1.20.2-1ubuntu3) ...
Preparing to unpack .../gvfs_1.20.2-1ubuntu3.1_amd64.deb ...
Unpacking gvfs:amd64 (1.20.2-1ubuntu3.1) over (1.20.2-1ubuntu3) ...
Preparing to unpack .../gvfs-daemons_1.20.2-1ubuntu3.1_amd64.deb ...
Unpacking gvfs-daemons (1.20.2-1ubuntu3.1) over (1.20.2-1ubuntu3) ...
Preparing to unpack .../gvfs-common_1.20.2-1ubuntu3.1_all.deb ...
Unpacking gvfs-common (1.20.2-1ubuntu3.1) over (1.20.2-1ubuntu3) ...
Preparing to unpack .../libgtk-3-bin_3.12.2-0ubuntu15.3_amd64.deb ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking libgtk-3-bin (3.12.2-0ubuntu15.3) over (3.12.2-0ubuntu15.2) ...
Selecting previously unselected package linux-headers-3.16.0-37.
Preparing to unpack .../linux-headers-3.16.0-37_3.16.0-37.51_all.deb ...
Unpacking linux-headers-3.16.0-37 (3.16.0-37.51) over (3.16.0-37.49) ...
Selecting previously unselected package linux-headers-3.16.0-37-generic.
Preparing to unpack .../linux-headers-3.16.0-37-generic_3.16.0-37.51_amd64.deb ...
Unpacking linux-headers-3.16.0-37-generic (3.16.0-37.51) over (3.16.0-37.49) ...
Preparing to unpack .../linux-libc-dev_3.16.0-41.57_amd64.deb ...
Unpacking linux-libc-dev:amd64 (3.16.0-41.57) over (3.16.0-37.49) ...
Preparing to unpack .../patch_2.7.1-5ubuntu0.3_amd64.deb ...
Unpacking patch (2.7.1-5ubuntu0.3) over (2.7.1-5) ...
Preparing to unpack .../t1utils_1.37-2.1ubuntu0.1_amd64.deb ...
Unpacking t1utils (1.37-2.1ubuntu0.1) over (1.37-2.1) ...
Preparing to unpack .../thunderbird_1%3a31.7.0+build1-0ubuntu0.14.10.1_amd64.deb ...
Unpacking thunderbird (1:31.7.0+build1-0ubuntu0.14.10.1) over (1:31.6.0+build1-0ubuntu0.14.10.1) ...
Preparing to unpack .../wpasupplicant_2.1-0ubuntu4.2_amd64.deb ...
Unpacking wpasupplicant (2.1-0ubuntu4.2) over (2.1-0ubuntu4.1) ...
Preparing to unpack .../xserver-xorg-video-intel_2%3a2.99.914-1~exp1ubuntu4.4_amd64.deb ...
Unpacking xserver-xorg-video-intel (2:2.99.914-1~exp1ubuntu4.4) over (2:2.99.914-1~exp1ubuntu4.2) ...
Preparing to unpack .../python3-aptdaemon.pkcompat_1.1.1+bzr980-0ubuntu1.1_all.deb ...
Unpacking python3-aptdaemon.pkcompat (1.1.1+bzr980-0ubuntu1.1) over (1.1.1+bzr980-0ubuntu1) ...
Preparing to unpack .../aptdaemon-data_1.1.1+bzr980-0ubuntu1.1_all.deb ...
Unpacking aptdaemon-data (1.1.1+bzr980-0ubuntu1.1) over (1.1.1+bzr980-0ubuntu1) ...
Preparing to unpack .../python3-aptdaemon.gtk3widgets_1.1.1+bzr980-0ubuntu1.1_all.deb ...
Unpacking python3-aptdaemon.gtk3widgets (1.1.1+bzr980-0ubuntu1.1) over (1.1.1+bzr980-0ubuntu1) ...
Preparing to unpack .../aptdaemon_1.1.1+bzr980-0ubuntu1.1_all.deb ...
Unpacking aptdaemon (1.1.1+bzr980-0ubuntu1.1) over (1.1.1+bzr980-0ubuntu1) ...
Preparing to unpack .../python3-aptdaemon_1.1.1+bzr980-0ubuntu1.1_all.deb ...
Unpacking python3-aptdaemon (1.1.1+bzr980-0ubuntu1.1) over (1.1.1+bzr980-0ubuntu1) ...
Preparing to unpack .../gdisk_0.8.8-1ubuntu0.1_amd64.deb ...
Unpacking gdisk (0.8.8-1ubuntu0.1) over (0.8.8-1build1) ...
Preparing to unpack .../oxideqt-codecs-extra_1.7.8-0ubuntu0.14.10.1_amd64.deb ...
Unpacking oxideqt-codecs-extra:amd64 (1.7.8-0ubuntu0.14.10.1) over (1.6.5-0ubuntu0.14.10.1) ...
Preparing to unpack .../python-aptdaemon.gtk3widgets_1.1.1+bzr980-0ubuntu1.1_all.deb ...
Unpacking python-aptdaemon.gtk3widgets (1.1.1+bzr980-0ubuntu1.1) over (1.1.1+bzr980-0ubuntu1) ...
Preparing to unpack .../python-aptdaemon_1.1.1+bzr980-0ubuntu1.1_all.deb ...
Unpacking python-aptdaemon (1.1.1+bzr980-0ubuntu1.1) over (1.1.1+bzr980-0ubuntu1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for man-db (2.7.0.2-2) ...
Processing triggers for mime-support (3.55ubuntu1.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for doc-base (0.10.6) ...
Processing 2 changed doc-base files...
Registering documents with scrollkeeper...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw (0.34~rc-0ubuntu4) ...
Processing triggers for libglib2.0-0:amd64 (2.42.1-1~ubuntu1) ...
No such key 'auto-launch' in schema 'com.ubuntu.update-notifier' as specified in override file '/usr/share/glib-2.0/schemas/20_ubuntustudio-default-settings.gschema.override'; ignoring override for this key.
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for dbus (1.8.8-1ubuntu2.1) ...
Processing triggers for update-notifier-common (3.157) ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20150623.1.orig.tar.gz
Get:1 http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20150623.1.orig.tar.gz [26.4 MB]
Fetched 26.4 MB in 1min 1s (431 kB/s)                                          
Installing from local file /var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20150623.1.orig.tar.gz
Flash Plugin installed.
Processing triggers for gconf2 (3.2.6-2ubuntu1) ...
Setting up libssl1.0.0:amd64 (1.0.1f-1ubuntu9.8) ...
Setting up libpython3.4-minimal:amd64 (3.4.2-1ubuntu0.1) ...
Setting up libpython3.4-stdlib:amd64 (3.4.2-1ubuntu0.1) ...
Setting up libpython3.4:amd64 (3.4.2-1ubuntu0.1) ...
Setting up python3.4-minimal (3.4.2-1ubuntu0.1) ...
Setting up python3.4 (3.4.2-1ubuntu0.1) ...
Setting up libtasn1-6:amd64 (4.0-2ubuntu0.2) ...
Setting up libfuse2:amd64 (2.9.2-4ubuntu4.14.10.1) ...
Setting up fuse (2.9.2-4ubuntu4.14.10.1) ...
update-initramfs: deferring update (trigger activated)
Setting up libldap-2.4-2:amd64 (2.4.31-1+nmu2ubuntu11.1) ...
Setting up libnuma1:amd64 (2.0.9~rc5-1ubuntu3.14.10.1) ...
Setting up chromium-codecs-ffmpeg-extra (43.0.2357.81-0ubuntu0.14.10.1.1131) ...
Setting up cups-server-common (1.7.5-3ubuntu3.2) ...
Setting up libcups2:amd64 (1.7.5-3ubuntu3.2) ...
Setting up libcupsmime1:amd64 (1.7.5-3ubuntu3.2) ...
Setting up cups-daemon (1.7.5-3ubuntu3.2) ...
cups start/running, process 4824
Setting up cups-core-drivers (1.7.5-3ubuntu3.2) ...
Setting up cups-common (1.7.5-3ubuntu3.2) ...
Setting up libcupsimage2:amd64 (1.7.5-3ubuntu3.2) ...
Setting up libcupsppdc1:amd64 (1.7.5-3ubuntu3.2) ...
Setting up libcupscgi1:amd64 (1.7.5-3ubuntu3.2) ...
Setting up cups-client (1.7.5-3ubuntu3.2) ...
Setting up cups-ppdc (1.7.5-3ubuntu3.2) ...
Setting up cups (1.7.5-3ubuntu3.2) ...
Updating PPD files for cups ...
Setting up cups-bsd (1.7.5-3ubuntu3.2) ...
Setting up libgtk-3-common (3.12.2-0ubuntu15.3) ...
Setting up libgtk-3-0:amd64 (3.12.2-0ubuntu15.3) ...
Setting up libgail-3-0:amd64 (3.12.2-0ubuntu15.3) ...
Setting up libicu52:amd64 (52.1-6ubuntu0.3) ...
Setting up libpython2.7-minimal:amd64 (2.7.8-10ubuntu1.1) ...
Setting up python2.7-minimal (2.7.8-10ubuntu1.1) ...
Setting up libpython2.7-stdlib:amd64 (2.7.8-10ubuntu1.1) ...
Setting up python2.7 (2.7.8-10ubuntu1.1) ...
Setting up libpython2.7:amd64 (2.7.8-10ubuntu1.1) ...
Setting up qtcore4-l10n (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqtcore4:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-xml:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqtdbus4:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-script:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-network:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-sql:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-xmlpatterns:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-sql-sqlite:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-sql-mysql:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up qdbus (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-dbus:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-test:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up isc-dhcp-common (4.2.4-7ubuntu14.1) ...
Setting up isc-dhcp-client (4.2.4-7ubuntu14.1) ...
Setting up openssl (1.0.1f-1ubuntu9.8) ...
Setting up ppp (2.4.5-5.1ubuntu3.2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up python3-problem-report (2.14.7-0ubuntu8.5) ...
Setting up python3-apport (2.14.7-0ubuntu8.5) ...
Setting up apport (2.14.7-0ubuntu8.5) ...
apport start/running
Setting up gir1.2-gtk-3.0 (3.12.2-0ubuntu15.3) ...
Setting up apport-gtk (2.14.7-0ubuntu8.5) ...
Setting up dnsmasq-base (2.71-1ubuntu0.1) ...
Setting up firefox (38.0+build3-0ubuntu0.14.10.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (38.0+build3-0ubuntu0.14.10.1) ...
Setting up flashplugin-installer (11.2.202.468ubuntu0.14.10.1) ...
Setting up gvfs-common (1.20.2-1ubuntu3.1) ...
Setting up gvfs-libs:amd64 (1.20.2-1ubuntu3.1) ...
Setting up gvfs-daemons (1.20.2-1ubuntu3.1) ...
Setting up gvfs:amd64 (1.20.2-1ubuntu3.1) ...
Setting up gvfs-fuse (1.20.2-1ubuntu3.1) ...
Setting up gvfs-bin (1.20.2-1ubuntu3.1) ...
Setting up gvfs-backends (1.20.2-1ubuntu3.1) ...
Setting up libgtk-3-bin (3.12.2-0ubuntu15.3) ...
Setting up linux-headers-3.16.0-37 (3.16.0-37.51) ...
Setting up linux-headers-3.16.0-37-generic (3.16.0-37.51) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.16.0-37-generic /boot/vmlinuz-3.16.0-37-generic
ERROR (dkms apport): binary package for r8168-dkms: 8.038.00 not found
Error! Bad return status for module build on kernel: 3.16.0-37-generic (x86_64)
Consult /var/lib/dkms/r8168-dkms/8.038.00/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.16.0-37-generic (x86_64)
Consult /var/lib/dkms/r8168/8.038.00/build/make.log for more information.
Setting up linux-libc-dev:amd64 (3.16.0-41.57) ...
Setting up patch (2.7.1-5ubuntu0.3) ...
Setting up t1utils (1.37-2.1ubuntu0.1) ...
Setting up thunderbird (1:31.7.0+build1-0ubuntu0.14.10.1) ...
Setting up wpasupplicant (2.1-0ubuntu4.2) ...
Setting up xserver-xorg-video-intel (2:2.99.914-1~exp1ubuntu4.4) ...
Setting up python3-aptdaemon (1.1.1+bzr980-0ubuntu1.1) ...
Setting up python3-aptdaemon.pkcompat (1.1.1+bzr980-0ubuntu1.1) ...
Setting up aptdaemon-data (1.1.1+bzr980-0ubuntu1.1) ...
Setting up python3-aptdaemon.gtk3widgets (1.1.1+bzr980-0ubuntu1.1) ...
Setting up aptdaemon (1.1.1+bzr980-0ubuntu1.1) ...
Setting up gdisk (0.8.8-1ubuntu0.1) ...
Setting up oxideqt-codecs-extra:amd64 (1.7.8-0ubuntu0.14.10.1) ...
Setting up python-aptdaemon (1.1.1+bzr980-0ubuntu1.1) ...
Setting up python-aptdaemon.gtk3widgets (1.1.1+bzr980-0ubuntu1.1) ...
Setting up libqtgui4:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-declarative:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-scripttools:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-svg:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-designer:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-qt3support:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-opengl:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Setting up libqt4-help:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1.1) ...
Processing triggers for libc-bin (2.19-10ubuntu2.3) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-41-lowlatency
haven@haven-Lenovo-Z40-70:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-37 linux-headers-3.16.0-37-generic
Use 'apt-get autoremove' to remove them.
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
haven@haven-Lenovo-Z40-70:~$ sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-41-lowlatency
Found initrd image: /boot/initrd.img-3.16.0-41-lowlatency
Found linux image: /boot/vmlinuz-3.16.0-41-generic
Found initrd image: /boot/initrd.img-3.16.0-41-generic
Adding boot menu entry for EFI firmware configuration
done
haven@haven-Lenovo-Z40-70:~$ 


```

Now for the reboot. Stay tuned. [-o

---

### Post by Haven_McClure on 2015-06-25
Okay, it rebooted, and better yet, it restored my previously set monitor settings so I won't need glasses after all. 

But several system error boxes flashed at me.  When I hit report, it linked me with this bug already reportedly reported.  [https://bugs.launchpad.net/ubuntu/+source/r8168/+bug/1385640](https://bugs.launchpad.net/ubuntu/+source/r8168/+bug/1385640)

Now as for those last two commands: 

```
haven@haven-Lenovo-Z40-70:~$ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 30 Jun 25 12:56 /vmlinuz -> boot/vmlinuz-3.16.0-41-generic
lrwxrwxrwx 1 root root 33 Jun 24 17:28 /vmlinuz.old -> boot/vmlinuz-3.16.0-41-lowlatency
haven@haven-Lenovo-Z40-70:~$ ls -al /initrd*
lrwxrwxrwx 1 root root 33 Jun 25 12:56 /initrd.img -> boot/initrd.img-3.16.0-41-generic
lrwxrwxrwx 1 root root 36 Jun 25 12:52 /initrd.img.old -> boot/initrd.img-3.16.0-41-lowlatency
haven@haven-Lenovo-Z40-70:~$ 

``` 

Wifi has been working the entire time.  Firefox is upgraded too.

---

### Post by Bashing-om on 2015-06-25
Haven_McClure; Hey hey !

Wonders never cease ... look'n good !
A small amount of adjustment:
> 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages                         
  404  Not Found

In your browser:
[http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/](http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/)
You see that utopic is not supported. Disable this PPA and maybe the developers will catch up (??) [kinda doubtful, but ]

Now can you boot up with both the generic and the low latency Kernels ? If you are able, we will not be concerned with installing a back up kernel !

And as in my prior concern about r8168-dkms; I will leave it alone and we let the big boys sort it out. I do appreciate that you caught it and did the homework and passed it along .

Now then once the PPAs are disabled ->
[INDENT][INDENT][INDENT]are you finer than a frog's hair ?
[/INDENT][/INDENT][/INDENT]

There remains then just a tad bit of final cleanup .

---

### Post by Haven_McClure on 2015-06-25
Well, the system is operating pretty smoothly.  How do I disable the PPA on Mixxx?  I participate in the community forums there a lot so I can communicate with them directly.  Maybe they're just sticking with the LTS versions now. 

When booting up, how do I get to the screen where it gives me a choice as to which kernels to boot from? 

Okay and yeah, looks like there's some cleaning up to do.

> **Bashing-om said:**
> Haven_McClure; Hey hey !

Wonders never cease ... look'n good !
A small amount of adjustment:

In your browser:
[http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/](http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/)
You see that utopic is not supported. Disable this PPA and maybe the developers will catch up (??) [kinda doubtful, but ]

Now can you boot up with both the generic and the low latency Kernels ? If you are able, we will not be concerned with installing a back up kernel !

And as in my prior concern about r8168-dkms; I will leave it alone and we let the big boys sort it out. I do appreciate that you caught it and did the homework and passed it along .

Now then once the PPAs are disabled ->[INDENT][INDENT][INDENT]are you finer than a frog's hair ?
[/INDENT]
[/INDENT]
[/INDENT]

There remains then just a tad bit of final cleanup .

---

### Post by Haven_McClure on 2015-06-25
Actually I figured out how to disable the PPA and the yellow triangle with the exclamation point is gone on reboot.  

> **Haven_McClure said:**
> Well, the system is operating pretty smoothly.  How do I disable the PPA on Mixxx?  I participate in the community forums there a lot so I can communicate with them directly.  Maybe they're just sticking with the LTS versions now. 

When booting up, how do I get to the screen where it gives me a choice as to which kernels to boot from? 

Okay and yeah, looks like there's some cleaning up to do.

---

### Post by Bashing-om on 2015-06-25
Haven_McClure; Grub'n

To see the grub boot menu in a single ubuntu install install condition:
legacy partitioning (MBR) when booting up as soon as the bios screen clears, depress and hold the right -shift- key;
EFI system as soon as the firmware screen clears repeatedly depress/release the escape key ( 3 second window of oportunity) .

Once we know that both boot up, we do the clean up.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Haven_McClure on 2015-06-25
Okay, that has been done.  Went about it a different way through trial and error.  As was true of my Asus, Lenovo's BIOS screen is accessible via F2 when the laptop logo is showing.  Once in the BIOS  fscreen, hit escape key once to get out of the bios screen, hit the escape key a second time (just once, not repeatedly) as soon as the BIOS screen clears, select "Advanced Options" and that gives the boot choices.  Found both the low-latency and generic versions of 41 and a safe mode start for each.

Both the low-latency and generic versions boot up.  Grabbing my broom to do some sweeping...


> **Bashing-om said:**
> Haven_McClure; Grub'n

To see the grub boot menu in a single ubuntu install install condition:
legacy partitioning (MBR) when booting up as soon as the bios screen clears, depress and hold the right -shift- key;
EFI system as soon as the firmware screen clears repeatedly depress/release the escape key ( 3 second window of oportunity) .

Once we know that both boot up, we do the clean up.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2015-06-25
Haven_McClure; Ho Kay !

Lets clean this up .
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get -f install
sudo dpkg -C

```
If "-f install" comes back all 0's and "dpkg" returns only to prompt.
We call this good, and you are good to go.

[INDENT][INDENT]fat lady is singing
[/INDENT][/INDENT]

---

### Post by Haven_McClure on 2015-06-25
-f install was zero, and dpkg returned to prompt. And it was good.
Loud soprano singing voice heard in background--don't know where that came from.
This thread is now marked solved.

Thanks, Bashing--om for untying this thorny knot.  Thirty-seven messages and we're done!

> **Bashing-om said:**
> Haven_McClure; Ho Kay !

Lets clean this up .
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get -f install
sudo dpkg -C

```
If "-f install" comes back all 0's and "dpkg" returns only to prompt.
We call this good, and you are good to go.
[INDENT][INDENT]fat lady is singing
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2015-06-25
Haven_McClure; YeaH !

You do good work . Hope the experience in retrospect is pleasant.

Morale of the story: Keep an eye on /boot !

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

