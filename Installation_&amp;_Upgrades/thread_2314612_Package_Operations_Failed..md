---
title: "Package Operations Failed."
date: 2016-02-22
forum: Installation &amp; Upgrades
---

### Post by mateucciv on 2016-02-22
Tried having Ubuntu Software Center, repair some files for me. It didn't work and gave me this read out. 

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 369420 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-46-generic_3.13.0-46.79_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-46-generic (3.13.0-46.79) over (3.13.0-46.77) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-46-generic_3.13.0-46.79_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.13.0-46-generic' to '/boot/vmlinuz-3.13.0-46-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-46-generic_3.13.0-46.79_amd64.deb
Error in function: 
Setting up initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: deferring update (trigger activated)
dpkg: dependency problems prevent configuration of linux-signed-image-3.13.0-46-generic:
 linux-signed-image-3.13.0-46-generic depends on linux-image-3.13.0-46-generic (= 3.13.0-46.79); however:
  Version of linux-image-3.13.0-46-generic on system is 3.13.0-46.77.


dpkg: error processing package linux-signed-image-3.13.0-46-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-generic:
 linux-signed-image-generic depends on linux-signed-image-3.13.0-46-generic; however:
  Package linux-signed-image-3.13.0-46-generic is not configured yet.


dpkg: error processing package linux-signed-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic:
 linux-signed-generic depends on linux-signed-image-generic (= 3.13.0.46.53); however:
  Package linux-signed-image-generic is not configured yet.


dpkg: error processing package linux-signed-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-extra-3.13.0-46-generic (3.13.0-46.79) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic


gzip: stdout: No space left on device
cpio: write error: Broken pipe
E: mkinitramfs failure cpio 1 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-46-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-46-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-46-generic; however:
  Package linux-image-extra-3.13.0-46-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-39-generic


gzip: stdout: No space left on device
cpio: write error: Broken pipe
E: mkinitramfs failure cpio 1 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-39-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1



```

I saw the  No space left on device and ran 
```

Sudo apt-get autoclean

```

Also ran ```
df -h
```

```
/dev/mapper/ubuntu--vg-root  909G   54G  809G   7% /none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.9G  4.0K  3.9G   1% /dev
tmpfs                        787M  1.3M  786M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G   23M  3.9G   1% /run/shm
none                         100M   48K  100M   1% /run/user
/dev/sda2                    237M  229M     0 100% /boot
/dev/sda1                    511M  3.4M  508M   1% /boot/efi



```

And thats all i knew how to do so if anyone could give me some help i'd appreciate it. Also pretty new to ubuntu and linux in general, so talk slowly and clearly.

---

### Post by Bashing-om on 2016-02-22
mateuccivl Hello, Welcome to the forum.

You have done well to see and understand , and better to try and comprehend.

We are now at this point:
> 
/dev/sda2                    237M  229M     0 100% /boot


Which indicates that the partition is full, most likely due to old kernels still in residence .
It is unlikely that in this condition that the package manager can cope with removing those old kernels, but one can try this simpler approach before getting the more aggressive:
```

sudo apt-get autoremove

```
paying close attention to what the package manager thinks it is safe to remove. With the kernels broken, I doubt this command will be effective. In this event we manually address the issue.

When the 'autoremove' command fails we proceed as:
Need to KNOW what kernel is the present booted kernel, MUST not mess about with this kernel at this time.
```

uname -r

```
and now we need to know what kernels are installed :
```

dpkg -l | grep linux-

```

Once the targets are identified we can use the dpkg tools to effect the removal of these old kernels.

[INDENT][INDENT]ain't nothing to it
[INDENT][INDENT][INDENT]once you have done it a time or 3
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mateucciv on 2016-02-22
Hey!
So I ran

```
sudo apt-get autoremove
```

it gave me this
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-signed-image-3.13.0-46-generic : Depends: linux-image-3.13.0-46-generic (= 3.13.0-46.79) but 3.13.0-46.77 is installed
E: Unmet dependencies. Try using -f.
```
```
 uname -r 
gave me: 3.13.0-39-generic 
```
```
 ii  linux-firmware                                        1.127.11                                            all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-29                               3.13.0-29.53                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic                       3.13.0-29.53                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34                               3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                       3.13.0-34.60                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35                               3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                       3.13.0-35.62                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                               3.13.0-39.66                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                       3.13.0-39.66                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.46.53                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-29-generic                         3.13.0-29.53                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.77                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                   3.13.0.46.53                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-46.79                                        amd64        Linux Kernel Headers for development
iU  linux-signed-generic                                  3.13.0.46.53                                        amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-3.13.0-24-generic                  3.13.0-24.47                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-29-generic                  3.13.0-29.53                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-32-generic                  3.13.0-32.57                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-34-generic                  3.13.0-34.60                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-35-generic                  3.13.0-35.62                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-39-generic                  3.13.0-39.66                                        amd64        Signed kernel image generic
iU  linux-signed-image-3.13.0-46-generic                  3.13.0-46.79                                        amd64        Signed kernel image generic
iU  linux-signed-image-generic                            3.13.0.46.53                                        amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by ian-weisser on 2016-02-22
autoclean removed stored packages in /var/cache/apt/archives...which isn't on the full partition.
autoremove uninstalls package files, including stale kernels in /boot...which is exactly what you want to do on the full partition.

---

### Post by Bashing-om on 2016-02-22
mateucciv; Welp.

Was worth a shot to try ' autoremove' . Not surprised it did not complete 
a) no operating head room at the partition at 100% capacity;
b) have unmet dependencies:
c) partially installed control components:
> 
iU  linux-image-generic
iU  linux-signed-generic 


Let's take a gentle poke at this and see if we can get some operating head room:
```

sudo apt-get remove --purge linux-image-3.13.0-24-generic

```
Depending on how the system responds to this one poke, is what we do next . It is best to stay within the package managers realm of control when possible . IF and I do stress IF we have to go behind the package manager's back .. we can ... and fix all the damage later.

We are fortunate that Ian, the guru of package management, is looking over our shoulder .

When the going gets tough
[INDENT][INDENT]the tough get going
[/INDENT][/INDENT]

---

### Post by mateucciv on 2016-02-22
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-24-generic : Depends: linux-image-3.13.0-24-generic but it is not going to be installed
 linux-signed-image-3.13.0-24-generic : Depends: linux-image-3.13.0-24-generic (= 3.13.0-24.47) but it is not going to be installed
 linux-signed-image-3.13.0-46-generic : Depends: linux-image-3.13.0-46-generic (= 3.13.0-46.79) but 3.13.0-46.77 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

``` I'm assuming it poked me back, I'm really glad for all the help too.

---

### Post by Bashing-om on 2016-02-22
mateucciv; Ouch .

We poke and it did bite back !
Maybe I got the horse before the cart.

Another gentle poke:
```

sudo apt-get remove --purge linux-image-3.13.0-24-generic

```

As we try the easy ways 1st.

[INDENT][INDENT]happy
[INDENT][INDENT][INDENT]in a process of learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mateucciv on 2016-02-22
This computer's just being stubborn 

```
You might want to run 'apt-get -f install' to correct these:The following packages have unmet dependencies:
 linux-image-extra-3.13.0-24-generic : Depends: linux-image-3.13.0-24-generic but it is not going to be installed
 linux-signed-image-3.13.0-24-generic : Depends: linux-image-3.13.0-24-generic (= 3.13.0-24.47) but it is not going to be installed
 linux-signed-image-3.13.0-46-generic : Depends: linux-image-3.13.0-46-generic (= 3.13.0-46.79) but 3.13.0-46.77 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by ian-weisser on 2016-02-22
Try the following to remove your 3.13.0-24 series kernel and headers:
```
sudo dpkg --remove linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic linux-signed-image-3.13.0-24-generic
```

If that works, do the same for -29
Then test: See if apt-get upgrade works.

If you're still out of space, do the same for -32, then -34

When you have freed enough space using dpkg (apt-get upgrade works), then run apt-get autoremove to finish the job.

---

### Post by mateucciv on 2016-02-22
So I did what you said and it worked, or I think it worked. 

But when I read sudo apt-get upgrade I got this 
```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
vitor@vitor-SVF15218CXB:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-signed-image-3.13.0-46-generic : Depends: linux-image-3.13.0-46-generic (= 3.13.0-46.79) but 3.13.0-46.77 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by ian-weisser on 2016-02-22
Try apt-get autremove, then apt-get install -f

---

### Post by mateucciv on 2016-02-22
so autoremove gave me
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-signed-image-3.13.0-46-generic : Depends: linux-image-3.13.0-46-generic (= 3.13.0-46.79) but 3.13.0-46.77 is installed
E: Unmet dependencies. Try using -f.

```
so apt-get install -f 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-engb libssl0.9.8 linux-image-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-46-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following packages will be upgraded:
  linux-image-3.13.0-46-generic
1 upgraded, 0 newly installed, 0 to remove and 564 not upgraded.
6 not fully installed or removed.
Need to get 0 B/15.1 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 310253 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-46-generic_3.13.0-46.79_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-46-generic (3.13.0-46.79) over (3.13.0-46.77) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
Setting up initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.13.0-46-generic (3.13.0-46.79) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating image symbolic links since we are being updated/reinstalled 
(3.13.0-46.77 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-extra-3.13.0-46-generic (3.13.0-46.79) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-generic (3.13.0.46.53) ...
Setting up linux-signed-image-3.13.0-46-generic (3.13.0-46.79) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-signed-image-generic (3.13.0.46.53) ...
Setting up linux-signed-generic (3.13.0.46.53) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic

```

if you don't mind taking the time, what is -f ?

---

### Post by Bashing-om on 2016-02-22
mateucciv; Ho Kay !

Making progress, and now let's see what we can do to deal with that originating issue of the -46 kernel.
As we do not need it, and we will eventually remove it anyway; how bout we try and remove it now ?
verify once more the booting kernel, that it has not changed:
```

uname -r

```
now with Ian's command sequence:
```

sudo dpkg --remove linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic linux-image-3.13.0-46-generic linux-image-extra-3.13.0-46-generic linux-signed-image-3.13.0-46-generic

```

I can accept that the package manager may balk, depending on the advisory is what we do next .

[INDENT][INDENT]what does it take
[INDENT][INDENT][INDENT]to keep the package manager, satisfied
 [/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mateucciv on 2016-02-22
Alright here we go !

```
 uname -r3.13.0-39-generic

```

oh uh, I don't think it liked that I ran that .
```
 sudo dpkg --remove linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic linux-image-3.13.0-46-generic linux-image-extra-3.13.0-46-generic linux-signed-image-3.13.0-46-genericdpkg: dependency problems prevent removal of linux-headers-3.13.0-46-generic:
 linux-headers-generic depends on linux-headers-3.13.0-46-generic.


dpkg: error processing package linux-headers-3.13.0-46-generic (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-46-generic:
 linux-image-generic depends on linux-image-3.13.0-46-generic.


dpkg: error processing package linux-image-3.13.0-46-generic (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-extra-3.13.0-46-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-46-generic.


dpkg: error processing package linux-image-extra-3.13.0-46-generic (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-signed-image-3.13.0-46-generic:
 linux-signed-image-generic depends on linux-signed-image-3.13.0-46-generic.


dpkg: error processing package linux-signed-image-3.13.0-46-generic (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.13.0-46:
 linux-headers-3.13.0-46-generic depends on linux-headers-3.13.0-46.


dpkg: error processing package linux-headers-3.13.0-46 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.13.0-46-generic
 linux-image-3.13.0-46-generic
 linux-image-extra-3.13.0-46-generic
 linux-signed-image-3.13.0-46-generic
 linux-headers-3.13.0-46

```

---

### Post by Bashing-om on 2016-02-22
mateucciv; Hey !

Disregard my last, as we posted at the same time. Looks like we are in business now .. that -f switch is "fix" .

Now let's look at the status of the installed kernels:
```

dpkg -l | grep linux-

```
to insure that all that is installed, is fully installed .
And, See now what else maybe left to do.

[INDENT][INDENT]things coming to an end
[/INDENT][/INDENT]

---

### Post by mateucciv on 2016-02-22
slow and steady wins, the race right? 

```
 ii  linux-firmware                                        1.127.11                                            all          Firmware for Linux kernel driversii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34                               3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                       3.13.0-34.60                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35                               3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                       3.13.0-35.62                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                               3.13.0-39.66                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                       3.13.0-39.66                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ri  linux-headers-3.13.0-46                               3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ri  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.46.53                                        amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-29-generic                         3.13.0-29.53                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ri  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ri  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.46.53                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-46.79                                        amd64        Linux Kernel Headers for development
ii  linux-signed-generic                                  3.13.0.46.53                                        amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-3.13.0-24-generic                  3.13.0-24.47                                        amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-29-generic                  3.13.0-29.53                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-32-generic                  3.13.0-32.57                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-34-generic                  3.13.0-34.60                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-35-generic                  3.13.0-35.62                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-39-generic                  3.13.0-39.66                                        amd64        Signed kernel image generic
ri  linux-signed-image-3.13.0-46-generic                  3.13.0-46.79                                        amd64        Signed kernel image generic
ii  linux-signed-image-generic                            3.13.0.46.53                                        amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2016-02-22
mateucciv; Uh Huh .

> 
slow and steady wins, the race right? 

We are making good progress.
Gone from " iU linux-image-generic
iU linux-signed-generic" to fully installed:
> 
ii  linux-image-generic 
ii  linux-signed-generic

Let's do a different order of operations
```

sudo apt-get purge linux-image-3.13.0-46-generic 
sudo apt-get purge linux-headers-3.13.0-46-generic
sudo apt-get purge linux-headers-3.13.0-46
sudo apt-get purge linux-image-extra-3.13.0-46-generic

```

Now, what we want to wind up with, when all is said and done is the current kernel installed:
mine:
```

sysop@1404mini:~$ uname -r
3.13.0-77-generic
sysop@1404mini:~$

```
which is the latest.

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by mateucciv on 2016-02-22
ok so ran the purge and everything got deleted but when i ran uname -r I got 
```
 SVF15218CXB:~$ uname -r3.13.0-39-generic 
```

---

### Post by Bashing-om on 2016-02-22
mateucciv; Hey ..

All fine .. we will not have the -77 kernel installed 'til we tell the system to install.
We are still doing the foundation stuff in preparation.
So now what is the status:
```

df -h
df -i
dpkg -l | grep linux-

```
look'n to see that we can wipe some of the sweat off and continue on our merry way.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by mateucciv on 2016-02-22
ok, I was thoroughly confused at one point. 

```
 df -h Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  909G   53G  810G   7% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.9G   12K  3.9G   1% /dev
tmpfs                        787M  1.3M  786M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G   55M  3.8G   2% /run/shm
none                         100M   40K  100M   1% /run/user
/dev/sda2                    237M  184M   41M  83% /boot
/dev/sda1                    511M  3.4M  508M   1% /boot/efi

``` 

```
  df -iFilesystem                    Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 60489728 387150 60102578    1% /
none                         1006578      2  1006576    1% /sys/fs/cgroup
udev                         1003786    524  1003262    1% /dev
tmpfs                        1006578    560  1006018    1% /run
none                         1006578      4  1006574    1% /run/lock
none                         1006578    228  1006350    1% /run/shm
none                         1006578     35  1006543    1% /run/user
/dev/sda2                      62496    317    62179    1% /boot
/dev/sda1                          0      0        0     - /boot/efi

``` 

```
 dpkg -l | grep linux-
ii  linux-firmware                                        1.127.11                                            all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34                               3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                       3.13.0-34.60                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35                               3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                       3.13.0-35.62                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                               3.13.0-39.66                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                       3.13.0-39.66                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-77                               3.13.0-77.121                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                       3.13.0-77.121                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.77.83                                        amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-29-generic                         3.13.0-29.53                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-77-generic                         3.13.0-77.121                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                   3.13.0-77.121                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.77.83                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-46.79                                        amd64        Linux Kernel Headers for development
ii  linux-signed-generic                                  3.13.0.77.83                                        amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-3.13.0-24-generic                  3.13.0-24.47                                        amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-29-generic                  3.13.0-29.53                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-32-generic                  3.13.0-32.57                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-34-generic                  3.13.0-34.60                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-35-generic                  3.13.0-35.62                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-39-generic                  3.13.0-39.66                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-77-generic                  3.13.0-77.121                                       amd64        Signed kernel image generic
ii  linux-signed-image-generic                            3.13.0.77.83                                        amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2016-02-22
mateucciv; Well !! well ,,

You did "something" as now the -77 kernel is installed.
> 
ii  linux-image-3.13.0-77-generic


But still real short on head room !
> 
/dev/sda2                    237M  184M   41M  83% /boot

with only 41M of overhead.

What are you presently booting ?
```

uname -r

```
and maybe now "autoremove" will be effective ?
try it :
```

sudo apt-get autoremove

```
knowing there is still a bit of cleanup yet to be done.

[INDENT][INDENT]more progress in the making
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-02-22
I don't mean to jump in here but I wonder if he has rebooted yet?
Kind regards

---

### Post by Bashing-om on 2016-02-22
@runrickus :)

Always good for you to poke your head in ! Reboot is a great thought !

[INDENT][INDENT]3 heads are better than one,
[INDENT][INDENT][INDENT]even if 1 is a goat head
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mateucciv on 2016-02-22
hey ok so uname r gave me, drum roll please

```
 3.13.0-77-generic
```

and autoremove  removed

```
  kde-l10n-engb libssl0.9.8 linux-image-generic

```

---

### Post by Bashing-om on 2016-02-22
mateuccivl Yuk (??);

I had expected that 'autoremove' to remove the old kernels, not to remove " linux-image-generic " !
We want to keep " linux-image-generic                   3.13.0.77.83 " .

Need to look again and see what is installed :
```

dpkg -l | grep linux-

```
also see about that final cleanup of 'rc' marked packages.

[INDENT][INDENT]not done 'til done
[/INDENT][/INDENT]

---

### Post by mateucciv on 2016-02-22
Maybe I got a bit ahead of myself here. 
```
dpkg -l | grep linux-ii  linux-firmware                                        1.127.11                                            all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34                               3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                       3.13.0-34.60                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35                               3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                       3.13.0-35.62                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                               3.13.0-39.66                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                       3.13.0-39.66                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-77                               3.13.0-77.121                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                       3.13.0-77.121                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.77.83                                        amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-29-generic                         3.13.0-29.53                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-77-generic                         3.13.0-77.121                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                   3.13.0-77.121                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                                  3.13.0-46.79                                        amd64        Linux Kernel Headers for development
ii  linux-signed-generic                                  3.13.0.77.83                                        amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-3.13.0-24-generic                  3.13.0-24.47                                        amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-29-generic                  3.13.0-29.53                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-32-generic                  3.13.0-32.57                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-34-generic                  3.13.0-34.60                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-35-generic                  3.13.0-35.62                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-39-generic                  3.13.0-39.66                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-77-generic                  3.13.0-77.121                                       amd64        Signed kernel image generic
ii  linux-signed-image-generic                            3.13.0.77.83                                        amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies



```

---

### Post by Bashing-om on 2016-02-22
mateucciv; Hummm ....

If it is all the same to you, I would like to pause here and wait for Ian to catch up with this thread. 'autoremove' should have removed those old kernels in my expectation, I would like to learn the whynot .
In this meantime post back the result:
```

sudo apt-get autoremove

```
And what is set in the control file?
post the output:
```

cat /etc/apt/apt.conf.d/01autoremove

```
It would be nice in the future to have this functionality.

else: If there is a push we can tackle the old kernels manually.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by mateucciv on 2016-02-22
I'm glad my problem can be used for science!!
```
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 555 not upgraded.

```

and 01autoremove gave me 

```

at /etc/apt/apt.conf.d/01autoremove
APT
{
  NeverAutoRemove
  {
	"^firmware-linux.*";
	"^linux-firmware$";
  };


  VersionedKernelPackages
  {
	# linux kernels
	"linux-image";
	"linux-headers";
	"linux-image-extra";
	"linux-signed-image";
	# kfreebsd kernels
	"kfreebsd-image";
	"kfreebsd-headers";
	# hurd kernels
	"gnumach-image";
	# (out-of-tree) modules
	".*-modules";
	".*-kernel";
	"linux-backports-modules-.*";
        # tools
        "linux-tools";
  };


  Never-MarkAuto-Sections
  {
	"metapackages";
	"restricted/metapackages";
	"universe/metapackages";
	"multiverse/metapackages";
	"oldlibs";
	"restricted/oldlibs";
	"universe/oldlibs";
	"multiverse/oldlibs";
  };
};

```

---

### Post by Bashing-om on 2016-02-22
mateucciv; Ouch !

> 
0 upgraded, 0 newly installed, 0 to remove and [color=red]555 not upgraded[/color].

while we are waiting, let's get this puppy updated !!!
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```

I see nothing amiss in the autoremove control file .  Let's await Ian for advise.

[INDENT][INDENT]what in the world - 555 not upgraded
[/INDENT][/INDENT]

---

### Post by mateucciv on 2016-02-22
What, I literally did a sudo upgrade a few hours ago! weird...very weird.

---

### Post by ian-weisser on 2016-02-22
Oh, that. Kernel headers are never autoremoved. The same kernel headers also rely upon the kernel-image packages, so those won't be eligible for autoremove either.

Try removing the obsolete kernel headers first, then autoremove then fix some of the other issues.
```
sudo apt remove linux-headers-3.13.0-2* linux-headers-3.13.0-3*
sudo apt-get autoremove
sudo apt install linux-image-generic
dpkg -l | grep linux
sudo apt full-upgrade
```

---

### Post by mateucciv on 2016-02-22
Still updating guys, this is taking alot longer then I thought it would. Will post results when available.

---

### Post by mateucciv on 2016-02-22
here we go:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt remove linux-headers-3.13.0-2* linux-headers-3.13.0-3*[/FONT][/COLOR]Package 'linux-headers-3.13.0-77-lowlatency' is not installed, so not removed
The following packages will be REMOVED:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-headers-3.13.0-34 linux-headers-3.13.0-34-generic
  linux-headers-3.13.0-35 linux-headers-3.13.0-35-generic
  linux-headers-3.13.0-39 linux-headers-3.13.0-39-generic
  linux-headers-3.13.0-77 linux-headers-3.13.0-77-generic
  linux-headers-generic linux-signed-generic
0 upgraded, 0 newly installed, 12 to remove and 555 not upgraded.
After this operation, 383 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 310771 files and directories currently installed.)
Removing linux-headers-3.13.0-32-generic (3.13.0-32.57) ...
^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[ARemoving linux-headers-3.13.0-32 (3.13.0-32.57) ...
^[[B^[[B^[[BRemoving linux-headers-3.13.0-34-generic (3.13.0-34.60) ...
Removing linux-headers-3.13.0-34 (3.13.0-34.60) ...
Removing linux-headers-3.13.0-35-generic (3.13.0-35.62) ...
Removing linux-headers-3.13.0-35 (3.13.0-35.62) ...
Removing linux-headers-3.13.0-39-generic (3.13.0-39.66) ...
Removing linux-headers-3.13.0-39 (3.13.0-39.66) ...
Removing linux-signed-generic (3.13.0.77.83) ...
Removing linux-headers-generic (3.13.0.77.83) ...
Removing linux-headers-3.13.0-77-generic (3.13.0-77.121) ...
Removing linux-headers-3.13.0-77 (3.13.0-77.121) ...

```

```
 autoremove gave out 
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 555 not upgraded.

```


```

sudo apt install linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-image-generic
0 upgraded, 1 newly installed, 0 to remove and 555 not upgraded.
Need to get 0 B/2,234 B of archives.
After this operation, 29.7 kB of additional disk space will be used.
Selecting previously unselected package linux-image-generic.
(Reading database ... 186739 files and directories currently installed.)
Preparing to unpack .../linux-image-generic_3.13.0.77.83_amd64.deb ...
Unpacking linux-image-generic (3.13.0.77.83) ...
Setting up linux-image-generic (3.13.0.77.83) ...

```
```

dpkg -l | grep linux
ii  libselinux1:amd64                                     2.2.2-1ubuntu0.1                                    amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                      2.2.2-1ubuntu0.1                                    i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                        1.0.1-1                                             amd64        Collection of video4linux support libraries
ii  libv4l-0:i386                                         1.0.1-1                                             i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                  1.0.1-1                                             amd64        Video4linux frame format conversion library
ii  libv4lconvert0:i386                                   1.0.1-1                                             i386         Video4linux frame format conversion library
ii  linux-firmware                                        1.127.11                                            all          Firmware for Linux kernel drivers
rc  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-29-generic                         3.13.0-29.53                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-77-generic                         3.13.0-77.121                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                   3.13.0-77.121                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.77.83                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-46.79                                        amd64        Linux Kernel Headers for development
rc  linux-signed-image-3.13.0-24-generic                  3.13.0-24.47                                        amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-29-generic                  3.13.0-29.53                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-32-generic                  3.13.0-32.57                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-34-generic                  3.13.0-34.60                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-35-generic                  3.13.0-35.62                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-39-generic                  3.13.0-39.66                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-77-generic                  3.13.0-77.121                                       amd64        Signed kernel image generic
ii  linux-signed-image-generic                            3.13.0.77.83                                        amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  pptp-linux                                            1.7.2-7                                             amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                              3:4.05+dfsg-6+deb8u1                                amd64        collection of boot loaders
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                            2.20.1-5.1ubuntu20.4                                amd64        Miscellaneous system utilities

```

and well full-upgrade did it's things haha

---

### Post by mateucciv on 2016-02-23
So just a quick update, I rebooted after running upgrade. and my wifi wasn't working (like it dissipated from my drivers so i ran

```
 sudo apt-get install linux-headers-generic 
``` 

you know what they say, two steps forward, one step back and then one to the side.

---

### Post by ian-weisser on 2016-02-23
Ah, so that is why you had headers? I was wondering...
If so, autoremove will likely never work removing old kernels. Headers prevent. Get used to removing by hand every few months.
```
uname -r                                     ## Identify the current kernel,
sudo apt-get remove linux-image-3.13.0-3*    ## Read the list of proposed removals carefully. DO NOT REMOVE THE CURRENT KERNEL.
```

---

### Post by mateucciv on 2016-02-24
sorry it took me so long to get back on, i've been having some problems with my wifi and fan drivers not being installed. (problems have been fixed.)

```
  uname -r3.13.0-77-generic

```

So I should run it as sudo apt-get remove linux-image-3.13.0-3* ? or change it?.

---

