---
title: "problem with dependencies with updating"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by bphillips2 on 2014-08-04
I tried updating my system using "apt-get upgrade" but received an error.  I'm not sure how to fix it.  Any help would be greatly appreciated.

```
justin@ubuntu:/var/www/owncloud$ sudo apt-get upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
**The following packages have unmet dependencies:**
** libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14) but 1.0.1-4ubuntu5.16 is installed**
E: Unmet dependencies. Try using -f.
```

I then tried using the "apt-get -f install" command and it still didn't work

```
justin@ubuntu:/var/www/owncloud$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl-dev
The following packages will be upgraded:
  libssl-dev
1 upgraded, 0 newly installed, 0 to remove and **88 not upgraded**.
6 not fully installed or removed.
Need to get 0 B/1,575 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up initramfs-tools (0.99ubuntu13.5) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.8.0-37-generic (3.8.0-37.53~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-38-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-37-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.8.0-37-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-37-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-37-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.8.0-38-generic (3.8.0-38.56~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-37-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-38-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.8.0-38-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-38-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-38-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.14); however:
  Version of libssl1.0.0 on system is 1.0.1-4ubuntu5.16.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-raring:
 linux-image-generic-lts-raring depends on linux-image-3.8.0-37-generic; however:
  Package linux-image-3.8.0-37-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-raring (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-raring:
 linux-generic-lts-raring depends on linux-image-generic-lts-raring; however:
  Package linux-image-generic-lts-raring is not configured yet.
dpkg: error processing linux-generic-lts-raring (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                                                                                                                                                        No apport report written because MaxReports is reached already
                                                                                                                                                                                                                                      update-initramfs: Generating /boot/initrd.img-3.8.0-36-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.8.0-36-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.8.0-37-generic
 linux-image-3.8.0-38-generic
 libssl-dev
 linux-image-generic-lts-raring
 linux-generic-lts-raring
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Anyone have any idea how to fix this?

---

### Post by Bucky Ball on 2014-08-04
Might be a silly questions, but you did do 'sudo apt-get update' before 'sudo apt-get upgrade'? Might not solve your issue, but just checking.

---

### Post by bphillips2 on 2014-08-04
> **Bucky Ball said:**
> Might be a silly questions, but you did do 'sudo apt-get update' before 'sudo apt-get upgrade'? Might not solve your issue, but just checking.

Yes, I used sudo before the commands.

---

### Post by Bucky Ball on 2014-08-04
This is the error you're repeatedly getting:

```
gzip: stdout: No space left on device
```

... which appears as if you are out of space on whatever physical device is getting updated at that stage. Do you have a separate /boot partition which might be full? You could try deleting any old, unused or obsolete kernel images.

BTW: the kernel that is attempting to install is old. Which release are you using? 12.04 and 14.04 are the currently supported releases. If you are not using one of them, please consider upgrading and please read this:

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

Thanks.

PS: I have added [code] tags to your first post rather than [quote] tags. Edit to see how. ;)

---

### Post by bphillips2 on 2014-08-04
> **Bucky Ball said:**
> This is the error you're repeatedly getting:

```
gzip: stdout: No space left on device
```

... which appears as if you are out of space on whatever physical device is getting updated at that stage. Do you have a separate /boot partition which might be full? You could try deleting any old, unused or obsolete kernel images.

BTW: the kernel that is attempting to install is old. Which release are you using? 12.04 and 14.04 are the currently supported releases. If you are not using one of them, please consider upgrading and please read this:

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

Thanks.

PS: I have added ```
 tags to your first post rather than [quote] tags. Edit to see how. ;)

Thanks for the replies.  You are right about the boot drive being full.

[CODE][COLOR=#000000]justin@ubuntu:~$ df -h[/COLOR]Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  1.8T  100G  1.6T   6% /
udev                         3.8G  4.0K  3.8G   1% /dev
tmpfs                        1.6G  380K  1.6G   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.8G     0  3.8G   0% /run/shm [COLOR=#000000]
/dev/sda1                    228M  226M     0 100% /boot[/COLOR]
```

I attempted to remove old kernels using instructions I found [here]("http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu") but it didn't do anything.  It still gave me the dependencies error.  Here is my output

```
[COLOR=#000000]justin@ubuntu:~$ sudo apt-get remove --purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d')[/COLOR][sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14) but 1.0.1-4ubuntu5.16 is to be installed
 linux-headers-generic-lts-raring : Depends: linux-headers-3.8.0-41-generic but it is not going to be installed [COLOR=#000000]E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/COLOR]
```

I am using ubuntu 12.04 LTS

---

### Post by Bashing-om on 2014-08-04
bphillips2; Hi !

At 100% capacity, may not have any headroom to operate in, but, I have an idea to try that 'might' remove the kernels.
Post back the outputs of terminal commands:
```

uname -r
dpkg -l | grep linux-

``` and will see if a direct application of 'dpkg' will handle this situation.
If the application of 'dpkg' in the manner I have in mind fails, well ;
There are dirtier ways to get the job done.

[INDENT][INDENT]don't hurt to try
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-05
Here is my output

```
[COLOR=#000000]justin@ubuntu:~$ uname -r
[/COLOR]3.8.0-36-generic
justin@ubuntu:~$ dpkg -l | grep linux-
ii  linux-firmware                   1.79.14                           Firmware for Linux kernel drivers
iU  linux-generic-lts-raring         3.8.0.37.37                       Generic Linux kernel image and headers
ii  linux-headers-3.8.0-29           3.8.0-29.42~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-29-generic   3.8.0-29.42~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-30           3.8.0-30.44~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-30-generic   3.8.0-30.44~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-31           3.8.0-31.46~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-31-generic   3.8.0-31.46~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-32           3.8.0-32.47~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-32-generic   3.8.0-32.47~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-33           3.8.0-33.48~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-33-generic   3.8.0-33.48~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-34           3.8.0-34.49~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-34-generic   3.8.0-34.49~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-35           3.8.0-35.52~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-35-generic   3.8.0-35.52~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-36           3.8.0-36.52~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-36-generic   3.8.0-36.52~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-37           3.8.0-37.53~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-37-generic   3.8.0-37.53~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-38           3.8.0-38.56~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-38-generic   3.8.0-38.56~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-39           3.8.0-39.58~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-39-generic   3.8.0-39.58~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-41           3.8.0-41.60~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-41-generic   3.8.0-41.60~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-42           3.8.0-42.62~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-42-generic   3.8.0-42.62~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-raring 3.8.0.41.41                       Generic Linux kernel headers
ii  linux-image-3.8.0-29-generic     3.8.0-29.42~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-30-generic     3.8.0-30.44~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-31-generic     3.8.0-31.46~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-32-generic     3.8.0-32.47~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-33-generic     3.8.0-33.48~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-34-generic     3.8.0-34.49~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-35-generic     3.8.0-35.52~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-36-generic     3.8.0-36.52~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
iF  linux-image-3.8.0-37-generic     3.8.0-37.53~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
iF  linux-image-3.8.0-38-generic     3.8.0-38.56~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
iU  linux-image-generic-lts-raring   3.8.0.37.37                       Generic Linux kernel image
ii  linux-libc-dev                   3.2.0-63.95                       Linux Kernel Headers for development [COLOR=#000000]justin@ubuntu:~$ [/COLOR]
```

---

### Post by Bashing-om on 2014-08-05
bphillips2; Morning !

Let's give this one a whirl :
```

sudo dpkg -P linux-image-3.8.0-{29,30,31,32,33,34,35}-generic
sudo dpkg -P linux-headers-3.8.0-{29,30,31,32,33,34,35}-generic
sudo dpkg -P linux-headers-3.8.0-{29,30,31,32,33,34,35}

```

Now, if these do indeed run .. let's look at what else 'might' remain to clean up:
Verify that the directory 
```

ls -la /lib/modules

```
does not contain any unused kernel entries. In our next steps we will deal with 37, 38, 39, 41 and 42 ( and what ever else may get installed in the update process).

Once all the old no-longer-needed kernels are removed we then do some final clean-up of the system.

[INDENT][INDENT]small steps.
[INDENT][INDENT][INDENT][INDENT]but we will get there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-05
Awesome! This is working! My boot drive is down to 23% now!

Here is my output after those steps.

```
[COLOR=#000000]justin@ubuntu:~$ ls -la /lib/modules[/COLOR]total 32
drwxr-xr-x  8 root root 4096 Aug  5 10:13 .
drwxr-xr-x 17 root root 4096 Jan 28  2014 ..
drwxr-xr-x  4 root root 4096 Feb 19 06:45 3.8.0-36-generic
drwxr-xr-x  4 root root 4096 Aug  4 17:11 3.8.0-37-generic
drwxr-xr-x  4 root root 4096 Aug  4 17:11 3.8.0-38-generic
drwxr-xr-x  2 root root 4096 May  5 06:28 3.8.0-39-generic
drwxr-xr-x  2 root root 4096 Jun  5 06:53 3.8.0-41-generic
drwxr-xr-x  2 root root 4096 Jun  6 06:37 3.8.0-42-generic [COLOR=#000000]justin@ubuntu:~$ [/COLOR]
```

---

### Post by Bashing-om on 2014-08-05
bphillips2; Great !

Let's wipe the sweat off and see where we stand:
What results:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade ##does a bit of clean up and tries to install held kernels##

```

[INDENT][INDENT]we be cooking with
[INDENT][INDENT][INDENT]Crisco now
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-05
The first command worked, but not the second.  Here is my output:

```
...
[COLOR=#000000]Hit http://security.ubuntu.com precise-security/universe TranslationIndex
[/COLOR]Hit http://security.ubuntu.com precise-security/main Translation-en                                                                                                    
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                                                              
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                                                              
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                                                                
Fetched 4,195 kB in 12s (323 kB/s)                                                                                                                                     
Reading package lists... Done
W: GPG error: http://php53.dotdeb.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E9C74FEEA2098A6E
W: GPG error: http://packages.dotdeb.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E9C74FEEA2098A6E
justin@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14) but 1.0.1-4ubuntu5.16 is installed
E: Unmet dependencies. Try using -f. [COLOR=#000000]justin@ubuntu:~$ [/COLOR]
```

---

### Post by Bashing-om on 2014-08-05
bphillips2; Welp.

A different set of issues, but need addressing now. We will return to the kernels later.
One at a time, let's deal with the dependency issue, 1st:
Try taking the package manager's advise, see what now comes of terminal command:
```

sudo apt-get -f install

```

[INDENT][INDENT]more fun
[INDENT][INDENT][INDENT]than a basket full of speckled puppies
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-05
Here is my output.

```
justin@ubuntu:~$ sudo apt-get -f install
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl-dev
The following packages will be upgraded:
  libssl-dev
1 upgraded, 0 newly installed, 0 to remove and 88 not upgraded.
6 not fully installed or removed.
Need to get 0 B/1,575 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up initramfs-tools (0.99ubuntu13.5) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.8.0-37-generic (3.8.0-37.53~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-37-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-37-generic
Found initrd image: /boot/initrd.img-3.8.0-37-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-3.8.0-38-generic (3.8.0-38.56~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-37-generic
Found initrd image: /boot/initrd.img-3.8.0-37-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found memtest86+ image: /memtest86+.bin
done
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.14); however:
  Version of libssl1.0.0 on system is 1.0.1-4ubuntu5.16.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-generic-lts-raring (3.8.0.37.37) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up linux-generic-lts-raring (3.8.0.37.37) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-38-generic
Errors were encountered while processing:
 libssl-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
justin@ubuntu:~$ 
```

---

### Post by Bashing-om on 2014-08-05
bphillips2; Welp'

Let's see what we can do to help things along:
> 
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.14); however:
  Version of libssl1.0.0 on system is 1.0.1-4ubuntu5.16.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured

Says you have installed something that the package manager can not cope with.
1) What release are you running ?
```

lsb_release -a
cat /etc/issue

```

2) What 3rd party stuff have you installed ?
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT][INDENT]all in the care and feeding
[INDENT][INDENT][INDENT]of your 'buntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-05
Here is my release info

```
justin@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:        12.04
Codename:       precise

justin@ubuntu:~$ cat /etc/issue
Ubuntu 12.04.4 LTS \n \l


justin@ubuntu:~$ 
```

And my third party info.  That last line of command gave me an error as you will see.

```
justin@ubuntu:~$ cat -n /etc/apt/sources.list     
1  # 
     2
     3  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
     4  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
     5  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted
     6
     7  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
     8  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
     9  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted
    10
    11  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    12  # newer versions of the distribution.
    13  deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    14  deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    15
    16  ## Major bug fix updates produced after the final release of the
    17  ## distribution.
    18  deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    19  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    20
    21  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    22  ## team. Also, please note that software in universe WILL NOT receive any
    23  ## review or updates from the Ubuntu security team.
    24  deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    25  deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    26  deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    27  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    28
    29  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    30  ## team, and may not be under a free licence. Please satisfy yourself as to 
    31  ## your rights to use the software. Also, please note that software in 
    32  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    33  ## security team.
    34  deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    35  deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    36  deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    37  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    38
    39  ## N.B. software from this repository may not have been tested as
    40  ## extensively as that contained in the main release, although it includes
    41  ## newer versions of some applications which may provide useful features.
    42  ## Also, please note that software in backports WILL NOT receive any review
    43  ## or updates from the Ubuntu security team.
    44  deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    45  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    46
    47  deb http://security.ubuntu.com/ubuntu precise-security main restricted
    48  deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    49  deb http://security.ubuntu.com/ubuntu precise-security universe
    50  deb-src http://security.ubuntu.com/ubuntu precise-security universe
    51  deb http://security.ubuntu.com/ubuntu precise-security multiverse
    52  deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    53
    54  ## Uncomment the following two lines to add software from Canonical's
    55  ## 'partner' repository.
    56  ## This software is not part of Ubuntu, but is offered by Canonical and the
    57  ## respective vendors as a service to Ubuntu users.
    58  # deb http://archive.canonical.com/ubuntu precise partner
    59  # deb-src http://archive.canonical.com/ubuntu precise partner
    60
    61  ## Uncomment the following two lines to add software from Ubuntu's
    62  ## 'extras' repository.
    63  ## This software is not part of Ubuntu, but is offered by third-party
    64  ## developers who want to ship their latest software.
    65  # deb http://extras.ubuntu.com/ubuntu precise main
    66  # deb-src http://extras.ubuntu.com/ubuntu precise main
    67
    68  deb http://php53.dotdeb.org stable all
    69  deb-src http://php53.dotdeb.org stable all
    70
    71  deb http://packages.dotdeb.org stable all
    72  deb-src http://packages.dotdeb.org stable all

justin@ubuntu:~$ tail -v -n +1 /etc/apt/sources.list.d/*
tail: cannot open `/etc/apt/sources.list.d/*' for reading: No such file or directory
justin@ubuntu:~$ 
```

---

### Post by Bashing-om on 2014-08-05
bphillips2; Well, well -

I am not familiar enough with debian to really say, but; Let's do a bit of fault isolation thus:
disable ( comment out) the lines:
> 
68  deb [http://php53.dotdeb.org](http://php53.dotdeb.org) stable all
    69  deb-src [http://php53.dotdeb.org](http://php53.dotdeb.org) stable all
    70
    71  deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
    72  deb-src [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all

in "/etc/apt/sources.list" file with your favorite text editor ( make a back up 1st, strange things can and do happen) .

No output from "tail -v -n +1 /etc/apt/sources.list.d/*" is a good thing, just means there is nothing there ( no 3rd party fetches are indexed here).

Now run the update/upgrade routines and see what results:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-gt dist-upgrade

```

[INDENT][INDENT]maybe now yes
[INDENT][INDENT][INDENT]but maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-05
The first command worked but the second gave me that same error.  I tried running the requested command "apt-get -f install" with no luck.  Here's my output.

```
justin@ubuntu:/etc/apt$ sudo apt-get upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14) but 1.0.1-4ubuntu5.16 is installed
E: Unmet dependencies. Try using -f.


justin@ubuntu:/etc/apt$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl-dev
The following packages will be upgraded:
  libssl-dev
1 upgraded, 0 newly installed, 0 to remove and 82 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,575 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.14); however:
  Version of libssl1.0.0 on system is 1.0.1-4ubuntu5.16.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 libssl-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)


justin@ubuntu:/etc/apt$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14) but 1.0.1-4ubuntu5.16 is installed
E: Unmet dependencies. Try using -f.


justin@ubuntu:/etc/apt$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14) but 1.0.1-4ubuntu5.16 is installed
E: Unmet dependencies. Try using -f.
justin@ubuntu:/etc/apt$ 
```

---

### Post by Bashing-om on 2014-08-05
bphillips2; Think'n

This:
> 
libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14) but 1.0.1-4ubuntu5.16 is installed

make me look at this:
> 
You have searched for packages that names contain libssl1.0.0 in suite(s) precise-updates, all sections, and all architectures. Found 3 matching packages.

Exact hits

Package libssl1.0.0

precise-updates (libs): SSL shared libraries 
1.0.1-4ubuntu5.16: amd64 i386


So we know that the correct version of the library is installed for ubuntu .

Let us see what we can do to find out what is using that old version of the library, such that the package manager is screaming and hollering .
```

dpkg -L libssl1.0.0 ##what is actually installed dependencies
dpkg -s libssl1.0.0
apt-cache policy libssl1.0.0

```

Looks like it may be real tough to isolate to what package 'rdepends' on libssl1.0.0.

maybe we can get some hints, I keep plugging away at it.

[INDENT][INDENT][INDENT]there are those times I just do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-05
I appreciate your continued help with this.  Here are my outputs for each one

```
justin@ubuntu:/etc/apt$ dpkg -L libssl1.0.0/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libssl1.0.0
/usr/share/doc/libssl1.0.0/copyright
/usr/share/doc/libssl1.0.0/changelog.Debian.gz
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/openssl-1.0.0
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/libnuron.so
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/libcswift.so
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/libgmp.so
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/libpadlock.so
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/lib4758cca.so
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/libaep.so
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/libsureware.so
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/libchil.so
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/libcapi.so
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/libubsec.so
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/libgost.so
/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/libatalla.so
/lib
/lib/x86_64-linux-gnu
/lib/x86_64-linux-gnu/libssl.so.1.0.0
/lib/x86_64-linux-gnu/libcrypto.so.1.0.0
```

```
justin@ubuntu:/etc/apt$ dpkg -s libssl1.0.0Package: libssl1.0.0
Status: install ok installed
Multi-Arch: same
Priority: important
Section: libs
Installed-Size: 2922
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: openssl
Version: 1.0.1-4ubuntu5.16
Depends: libc6 (>= 2.14), zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0
Pre-Depends: multiarch-support
Breaks: openssh-client (<< 1:5.9p1-4), openssh-server (<< 1:5.9p1-4)
Description: SSL shared libraries
 libssl and libcrypto shared libraries needed by programs like
 apache-ssl, telnet-ssl and openssh.
 .
 It is part of the OpenSSL implementation of SSL.
Original-Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
```

```
justin@ubuntu:/etc/apt$ apt-cache policy libssl1.0.0libssl1.0.0:
  Installed: 1.0.1-4ubuntu5.16
  Candidate: 1.0.1-4ubuntu5.16
  Version table:
 *** 1.0.1-4ubuntu5.16 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1.0.1-4ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```

---

### Post by Bashing-om on 2014-08-05
bphillips2; Well ! That ain't much help .

And it just gets stranger . Where in the world does does/why another old version crop up <- I ask myself.
> 
Version table:
 1.0.1-4ubuntu3 0

Before we go hunting in the status file directly, what returns from:
```

dpkg-query -s libssl1.0.0
dpkg-query -S '/lib/x86_64-linux-gnu/libssl.so.1.0.0' ## a reverse lookup, maybe##
sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade ##Maybe find out what's keeping or removing a package##
ls -la /var/lib/dpkg/info/libss*.list

```

[INDENT][INDENT]still do not know
[INDENT][INDENT][INDENT][INDENT]still, want to find out
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-05
Here are the outputs for each.

```
justin@ubuntu:/etc/apt$ dpkg-query -s libssl1.0.0Package: libssl1.0.0
Status: install ok installed
Multi-Arch: same
Priority: important
Section: libs
Installed-Size: 2922
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: openssl
Version: 1.0.1-4ubuntu5.16
Depends: libc6 (>= 2.14), zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0
Pre-Depends: multiarch-support
Breaks: openssh-client (<< 1:5.9p1-4), openssh-server (<< 1:5.9p1-4)
Description: SSL shared libraries
 libssl and libcrypto shared libraries needed by programs like
 apache-ssl, telnet-ssl and openssh.
 .
 It is part of the OpenSSL implementation of SSL.
Original-Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
```

```
justin@ubuntu:/etc/apt$ dpkg-query -S '/lib/x86_64-linux-gnu/libssl.so.1.0.0'
libssl1.0.0: /lib/x86_64-linux-gnu/libssl.so.1.0.0
```

```
justin@ubuntu:/etc/apt$ apt-get -o Debug::pkgProblemResolver=yes dist-upgradeE: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


justin@ubuntu:/etc/apt$ sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14) but 1.0.1-4ubuntu5.16 is installed
E: Unmet dependencies. Try using -f.
```

```


justin@ubuntu:/etc/apt$ ls -la /var/lib/dpkg/info/libss*.list
-rw-r--r-- 1 root root   225 Aug 26  2013 /var/lib/dpkg/info/libss2:amd64.list
-rw-r--r-- 1 root root  9499 Jan 22  2014 /var/lib/dpkg/info/libssh2-1-dev.list
-rw-r--r-- 1 root root   229 Jan 22  2014 /var/lib/dpkg/info/libssh2-1.list
-rw-r--r-- 1 root root   278 Jan 22  2014 /var/lib/dpkg/info/libssh2-php.list
-rw-r--r-- 1 root root  1096 Aug  4 13:55 /var/lib/dpkg/info/libssl1.0.0:amd64.list
-rw-r--r-- 1 root root  2686 Jun  6 06:37 /var/lib/dpkg/info/libssl-dev.list
-rw-r--r-- 1 root root 61186 Jun  6 06:37 /var/lib/dpkg/info/libssl-doc.list
```

---

### Post by Bashing-om on 2014-08-05
bphillips2; Hummm...

I am confused, and stumped presently,

Going to go take a needed nap ( lack of sleep last night !) .. and maybe something else will occur to me .
Else we going to look into the status file " /var/lib/dpkg/status" see if we can find what/where that older version  of 'libssl1.0.0' is installed.
(and what it is going to take to remove it )

[INDENT][INDENT]I hate when this happens
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-05
Thanks for the help thus far and the reply.  Hopefully something comes to you in a dream! ;)

---

### Post by Bashing-om on 2014-08-05
bphillips2; Yeah, thin'n better.

The problem install is 'libssl-dev', and low and behold:
> 
 Secure Sockets Layer toolkit - development files
It contains development libraries, header files, and manpages for libssl
 and libcrypto.


NOT a system file, I think we can be safe in removing it.
Let's try and see if the package manager will allow it.
```

sudo apt-get remove libssl-dev

```
And, if that package is removed, once more let's see what the package manager relates:
```

sudo apt-get update
sudo apt-get -f install
sudo dpkg --configure -a

```
It will be nice
[INDENT][INDENT][INDENT]if it is this simple
[/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-08-06
You're a legend, Bashing. We'll get to the bottom of this eventually! I's a watchin' and a waitin'. ;)

---

### Post by bphillips2 on 2014-08-06
Hmm, that doesn't seem to have fixed it.  Here are my outputs

```
justin@ubuntu:~$ sudo apt-get remove libssl-dev
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 php5-dev : Depends: libssl-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

```
justin@ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise Release.gpg      
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise-backports Release.gpg
Get:3 http://security.ubuntu.com precise-security Release [50.7 kB]
Hit http://us.archive.ubuntu.com precise Release       
Get:4 http://us.archive.ubuntu.com precise-updates Release [98.7 kB]
Get:5 http://security.ubuntu.com precise-security/main Sources [108 kB]                  
Hit http://us.archive.ubuntu.com precise-backports Release       
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main amd64 Packages
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Get:6 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:7 http://security.ubuntu.com precise-security/universe Sources [32.3 kB]
Get:8 http://security.ubuntu.com precise-security/multiverse Sources [1,795 B]
Get:9 http://security.ubuntu.com precise-security/main amd64 Packages [414 kB]   
Hit http://us.archive.ubuntu.com precise/universe i386 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:10 http://us.archive.ubuntu.com precise-updates/main Sources [476 kB]
Get:11 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:12 http://security.ubuntu.com precise-security/universe amd64 Packages [96.5 kB]  
Get:13 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,442 B]      
Get:14 http://security.ubuntu.com precise-security/main i386 Packages [442 kB]            
Get:15 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]          
Get:16 http://us.archive.ubuntu.com precise-updates/universe Sources [109 kB]              
Get:17 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,893 B]          
Get:18 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [823 kB]           
Get:19 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]     
Get:20 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]           
Get:21 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,650 B]      
Get:22 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]               
Get:23 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]           
Get:24 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:25 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:26 http://security.ubuntu.com precise-security/main Translation-en [189 kB]  
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Get:27 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [13.7 kB]
Get:28 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [246 kB]
Get:29 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]
Get:30 http://us.archive.ubuntu.com precise-updates/main i386 Packages [854 kB]
Get:31 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]                                                                                 
Get:32 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [252 kB]                                                                                    
Get:33 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]                                                                                 
Get:34 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]                                                                                    
Get:35 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]                                                                              
Get:36 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]                                                                              
Get:37 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]                                                                                
Hit http://us.archive.ubuntu.com precise-backports/main Sources                                                                                                        
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources                                                                                                  
Hit http://us.archive.ubuntu.com precise-backports/universe Sources                                                                                                    
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources                                                                                                  
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages                                                                                                 
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages                                                                                           
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages                                                                                             
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages                                                                                           
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages                                                                                                  
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages                                                                                            
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages                                                                                              
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages                                                                                            
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex                                                                                               
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex                                                                                         
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex                                                                                         
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex                                                                                           
Hit http://us.archive.ubuntu.com precise/main Translation-en                                                                                                           
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                                                                                                     
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                                                                                                     
Hit http://us.archive.ubuntu.com precise/universe Translation-en                                                                                                       
Get:38 http://us.archive.ubuntu.com precise-updates/main Translation-en [361 kB]                                                                                       
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                                                                                             
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                                                                                             
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                                                                                               
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en                                                                                                 
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en                                                                                           
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en                                                                                           
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en                                                                                             
Fetched 4,761 kB in 7s (621 kB/s)                                                                                                                                      
Reading package lists... Done



```

```
justin@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl-dev
The following packages will be upgraded:
  libssl-dev
1 upgraded, 0 newly installed, 0 to remove and 85 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,575 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.14); however:
  Version of libssl1.0.0 on system is 1.0.1-4ubuntu5.16.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libssl-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This seems to be the incorrect command, did you mean "--configure" instead of "--reconfigure"?
```
justin@ubuntu:~$ dpkg --reconfigure -a
dpkg: error: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
```

---

### Post by Bashing-om on 2014-08-06
bphillips2; OK,

Following the 'tree' //let's remove:
```

sudo apt-get remove php5-dev

```

If/when we mess something up you do want/need, we go back when all is straight and stable and put things back in place.

An yeah, boo-boo on my part " dpkg --reconfigure -a" ; correct it to be:
```

sudo dpkg --configure -a

``` let's see how that runs.

[INDENT][INDENT]as we work hard
[INDENT][INDENT][INDENT]to get to the bottom of things
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
hmmm, still running into same issues

```
justin@ubuntu:~$ sudo apt-get remove php5-dev
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14) but 1.0.1-4ubuntu5.16 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

```
justin@ubuntu:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.14); however:
  Version of libssl1.0.0 on system is 1.0.1-4ubuntu5.16.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libssl-dev



```

---

### Post by Bashing-om on 2014-08-06
bphillips2; Humm ....

Not sure what is going on here ??

OK, let's check the source once more.
```

cat -n /etc/apt/sources.list

```

and then approach this from the other end.

[INDENT][INDENT][INDENT]where there is a will there is away
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
Here it is

```
justin@ubuntu:~$ cat -n /etc/apt/sources.list
     1  # 
     2
     3  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
     4  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
     5  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted
     6
     7  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
     8  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
     9  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted
    10
    11  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    12  # newer versions of the distribution.
    13  deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    14  deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    15
    16  ## Major bug fix updates produced after the final release of the
    17  ## distribution.
    18  deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    19  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    20
    21  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    22  ## team. Also, please note that software in universe WILL NOT receive any
    23  ## review or updates from the Ubuntu security team.
    24  deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    25  deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    26  deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    27  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    28
    29  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    30  ## team, and may not be under a free licence. Please satisfy yourself as to 
    31  ## your rights to use the software. Also, please note that software in 
    32  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    33  ## security team.
    34  deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    35  deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    36  deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    37  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    38
    39  ## N.B. software from this repository may not have been tested as
    40  ## extensively as that contained in the main release, although it includes
    41  ## newer versions of some applications which may provide useful features.
    42  ## Also, please note that software in backports WILL NOT receive any review
    43  ## or updates from the Ubuntu security team.
    44  deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    45  deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    46
    47  deb http://security.ubuntu.com/ubuntu precise-security main restricted
    48  deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    49  deb http://security.ubuntu.com/ubuntu precise-security universe
    50  deb-src http://security.ubuntu.com/ubuntu precise-security universe
    51  deb http://security.ubuntu.com/ubuntu precise-security multiverse
    52  deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    53
    54  ## Uncomment the following two lines to add software from Canonical's
    55  ## 'partner' repository.
    56  ## This software is not part of Ubuntu, but is offered by Canonical and the
    57  ## respective vendors as a service to Ubuntu users.
    58  # deb http://archive.canonical.com/ubuntu precise partner
    59  # deb-src http://archive.canonical.com/ubuntu precise partner
    60
    61  ## Uncomment the following two lines to add software from Ubuntu's
    62  ## 'extras' repository.
    63  ## This software is not part of Ubuntu, but is offered by third-party
    64  ## developers who want to ship their latest software.
    65  # deb http://extras.ubuntu.com/ubuntu precise main
    66  # deb-src http://extras.ubuntu.com/ubuntu precise main
    67
    68  #These lines commented out while troubleshooting upgrade issue
    69  #deb http://php53.dotdeb.org stable all
    70  #deb-src http://php53.dotdeb.org stable all
    71  #
    72  #deb http://packages.dotdeb.org stable all
    73  #deb-src http://packages.dotdeb.org stable all
```

---

### Post by Bashing-om on 2014-08-06
bphillips2; Well.

I find no fault with that sources.list file:
Here goes from that other end:
```

sudo apt-get remove libssl1.0.0

```
and let's see what the package manager screams and hollers about now .

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
Here's what I get

```
justin@ubuntu:~$ sudo apt-get remove libssl1.0.0
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apache2-utils : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 apache2.2-bin : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 bacula-common : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 iputils-ping : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 libapache2-mod-php5 : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 libc-client2007e : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 libcurl3 : Depends: libssl1.0.0 (>= 1.0.1) but it is not going to be installed
 libdns81 : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 libpython2.7 : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 libsasl2-modules : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14) but it is not going to be installed
 nginx-full : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 ntpdate : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 openssh-client : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 openssh-server : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 openssl : Depends: libssl1.0.0 (>= 1.0.1) but it is not going to be installed
 php5-cgi : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 php5-cli : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 php5-fpm : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 postfix : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 python-openssl : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 python2.7-minimal : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 tcpdump : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 w3m : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 wget : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
 wpasupplicant : Depends: libssl1.0.0 (>= 1.0.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by Bashing-om on 2014-08-06
bphillips2; Well !

Why am I not surprised ! // ( I did look to see what 'might and most likely' occur/s). Webbed in tight, huh !

So much for that thought.
Back to plan a:
What is holding "php5-dev" ?
```

apt-cache rdepends php5-dev

```

[INDENT][INDENT]sometimes I do not know
[INDENT][INDENT][INDENT][INDENT]othertimes I wonder
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
```
[COLOR=#000000]justin@ubuntu:~$ apt-cache rdepends php5-dev[/COLOR]php5-dev
Reverse Depends:
  php-pear
  php5-dev:i386
  php-pear
  php5-dev:i386 [COLOR=#000000]  php-pear[/COLOR]
```

---

### Post by Bashing-om on 2014-08-06
bphillips2; HEY,

I do appreciate your patience as we work through this.

Now that last output makes me question that 2 instances of "php-pear" ( what ever in the world that is !) is installed;
what results:
```

apt-cache policy php-pear

```

getting prepared to remove these !

[INDENT][INDENT] What does it take
[INDENT][INDENT][INDENT]to keep
[INDENT][INDENT][INDENT][INDENT]an application like you
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
I appreciate your patience and help with this!

Here is the output

```
[COLOR=#000000]justin@ubuntu:~$ apt-cache policy php-pear[/COLOR]php-pear:
  Installed: 5.3.10-1ubuntu3.11
  Candidate: 5.3.10-1ubuntu3.13
  Version table:
     5.3.10-1ubuntu3.13 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
 *** 5.3.10-1ubuntu3.11 0
        100 /var/lib/dpkg/status
     5.3.10-1ubuntu3 0 [COLOR=#000000]        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages[/COLOR]
```

---

### Post by Bashing-om on 2014-08-06
bphillips2; Shucks,

Do not know what to make of it besides that an old version of " php-pear " is installed.
Let's poke at it a bit and see what  stirs:
```

sudo dpkg-reconfigure php-pear

``` just because I am not ready to "wholesale" remove things (YET);
as maybe a shortcut to find out what is not taking place.

[INDENT]think thrice 
[INDENT][INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
No output on that one

```
justin@ubuntu:~$ sudo dpkg-reconfigure php-pear
[sudo] password for justin: 
justin@ubuntu:~$ 
```

---

### Post by Bashing-om on 2014-08-06
bphillips2; Surprised .

Expected the package manager to scream and holler ! .. let's look and see what is now:
```

apt-cache policy php-pear

``` 'cause a no output to a command -> no sass, no back talk, NO COMPLAINTS -> system doing as told.

[INDENT][INDENT]humm, we be look'n
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
Here it is

```
justin@ubuntu:~$ apt-cache policy php-pear
php-pear:
  Installed: 5.3.10-1ubuntu3.11
  Candidate: 5.3.10-1ubuntu3.13
  Version table:
     5.3.10-1ubuntu3.13 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
 *** 5.3.10-1ubuntu3.11 0
        100 /var/lib/dpkg/status
     5.3.10-1ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```

---

### Post by Bashing-om on 2014-08-06
bphillips2; Curious !

No change from that old version, the command did not complain ( package manager happy at that point ); What gives ?

Let's make another step up on this tree and look:
```

apt-cache rdepends php-pear

```

Looking for that duplication.

[INDENT][INDENT]an effectation, somewhere, somehow
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
```
[COLOR=#000000]justin@ubuntu:~$ apt-cache rdpends php-pear
[/COLOR][COLOR=#000000]E: Invalid operation rdpends[/COLOR]
```

---

### Post by Bashing-om on 2014-08-06
bphillips2; Sorry 'bout that ->
typo !

correct to be:
```

apt-cache rdepends php-pear

```
And away 
[INDENT][INDENT]we go
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
```
justin@ubuntu:~$ apt-cache rdepends php-pear
php-pear
Reverse Depends:
  libapache2-mod-php5
  php5-cli
  php5-fpm
  php5-cgi
  php5-fpm
  php-letodms-lucene
  libapache2-mod-php5filter
  php5-cli
  php5-cgi
  libapache2-mod-php5
  zoph
  squirrelmail
  smbind
  serendipity
  poker-web
  pkg-php-tools
  phpunit
  phpreports
  php5-fpm
  php-xml-serializer
  php-xml-rss
  php-xml-rpc2
  php-xml-rpc
  php-xml-parser
  php-xml-htmlsax3
  php-text-wiki
  php-text-password
  php-text-figlet
  php-text-captcha
  php-soap
  php-services-weather
  php-services-json
  php-pager
  php-numbers-words
  php-net-whois
  php-net-url
  php-net-socket
  php-net-smtp
  php-net-smartirc
  php-net-sieve
  php-net-portscan
  php-net-ping
  php-net-nntp
  php-net-lmtp
  php-net-ldap2
  php-net-ldap
  php-net-ipv6
  php-net-ipv4
  php-net-imap
  php-net-ftp
  php-net-dnsbl
  php-net-dime
  php-net-checkip
  php-mime-type
  php-mdb2-driver-sqlite
  php-mdb2-driver-pgsql
  php-mdb2-driver-mysql
  php-mdb2
  php-mail-mimedecode
  php-mail-mime
  php-mail
  php-log
  php-letodms-lucene
  php-letodms-core
  php-kolab-freebusy
  php-kolab-filter
  php-image-text
  php-http-webdav-server
  php-http-upload
  php-http-request
  php-http
  php-html-template-it
  php-html-common
  php-file
  php-event-dispatcher
  php-db
  php-date
  php-crypt-gpg
  php-crypt-cbc
  php-crypt-blowfish
  php-console-table
  php-config
  php-compat
  php-codesniffer
  php-cache
  php-benchmark
  php-auth-sasl
  php-auth-http
  php-auth
  owncloud
  mahara
  ltsp-cluster-control
  libapache2-mod-php5filter
  fusionforge-plugin-oslc
  fossology-common
  extplorer
  dh-make-php
  d-push
  php5-cli
  php5-cgi
  libapache2-mod-php5
```

---

### Post by Bashing-om on 2014-08-06
bphillips2; again, unexpected.

Cogitating soon as I have my "mind right" - am looking - we will make another move.
see:
```
 
apt-cache depends php5

```


[INDENT][INDENT]which way did he go George
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
```
[COLOR=#000000]justin@ubuntu:~$ apt-cache depends php5
[/COLOR]php5
 |Depends: libapache2-mod-php5
 |Depends: libapache2-mod-php5filter
 |Depends: php5-cgi
  Depends: php5-fpm
  Depends: php5-common [COLOR=#000000]justin@ubuntu:~$ [/COLOR]
```

---

### Post by Bashing-om on 2014-08-06
bphillips2; Sorta stuck again:
> 
php5:

Description-en: server-side, HTML-embedded scripting language (metapackage)
 This package is a metapackage that, when installed, guarantees that you
 have at least one of the four server-side versions of the PHP5 interpreter
 installed. Removing this package won't remove PHP5 from your system, however
 it may remove other packages that depend on this one.


I ain't got any idea what might result "IF" we remove php5. Let's take a poke at it, gently, and see what it will do if we tell it to remove php5.
-that to me is the way the tree leads from libssl-dev -
```

sudo apt-get remove -s php5

```
[INDENT][INDENT]maybe yes,
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
```
[COLOR=#000000]justin@ubuntu:~$ sudo apt-get remove -s php5
[/COLOR][sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 drupal7 : Depends: php5 but it is not going to be installed
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14) but 1.0.1-4ubuntu5.16 is to be installed 
[COLOR=#000000]E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/COLOR]
```

If it matters, we don't use Drupal7 anymore. It could be removed if needed.

---

### Post by Bashing-om on 2014-08-06
bphillips2; Welp;

I am all in favor of keeping a clean system, getting rid of things not needed. Removing "drupal7" ,as it is in the tree path , might even lead to something constructive !

Do it !
```

sudo apt-get --purge remove drupal7

```

hey,
[INDENT][INDENT]it's a thought
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
Getting the similar error

```
[COLOR=#000000]justin@ubuntu:~$ sudo apt-get --purge remove drupal7
[/COLOR][sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14) but 1.0.1-4ubuntu5.16 is to be installed 
[COLOR=#000000]E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/COLOR]
```

---

### Post by Bashing-om on 2014-08-06
bphillips2; Well,

Got me wonding some more, and think'n heavy ...

We are going to do something, I just do not know what yet.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-06
bphillips2; Welp;

In this 'round robin' once more let's see what the package manager advises:
```

sudo dpkg --audit

```
as I struggle to see where to go to.

[INDENT][INDENT]give the package manager a helping hand
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
Oh, this output looks promising! 

```
justin@ubuntu:~$ sudo dpkg --audit
[sudo] password for justin: 
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libssl-dev           SSL development libraries, header files and documentation
```

---

### Post by Bashing-om on 2014-08-06
bphillips2; Yeah;

We did that once, but wont hurt to run it again.
```

sudo dpkg --configure libssl-dev

```

Also worth investigating is an architecture mismatch:
```

dpkg -l libssl1.0.0:i386
dpkg -l libssl1.0.0
dpkg -l libssl-dev:i386
dpkg -l libssl-dev

```

Then I am also debating on getting direct with the versions .. but, but, messing about with libssl, I am exercising extreme caution.
I do not want to do anything harmful that we can not back out of or easily correct.

[INDENT][INDENT]just so you know
[INDENT][INDENT][INDENT][INDENT]I am thinking
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-06
```
justin@ubuntu:~$ sudo dpkg --configure libssl-dev
[sudo] password for justin: 
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.14); however:
  Version of libssl1.0.0 on system is 1.0.1-4ubuntu5.16.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libssl-dev

```
```

justin@ubuntu:~$ dpkg -l libssl1.0.0:i386
No packages found matching libssl1.0.0:i386.

```
```

justin@ubuntu:~$ dpkg -l libssl1.0.0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                              Description
+++-====================================-====================================-========================================================================================
ii  libssl1.0.0                          1.0.1-4ubuntu5.16                    SSL shared libraries

```
```

justin@ubuntu:~$ dpkg -l libssl-dev:i386
No packages found matching libssl-dev:i386.

```
```

justin@ubuntu:~$ dpkg -l libssl-dev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                              Description
+++-====================================-====================================-========================================================================================
iU  libssl-dev                           1.0.1-4ubuntu5.14                    SSL development libraries, header files and documentation
justin@ubuntu:~$ 
```

---

### Post by murp32 on 2014-08-06
Hi folks...

Sorry to hijack this thread but I think I may have the same issue. I'm getting dependency errors when installing openssl and php5-dev together:

```
root@e21a7926dc28:/# apt-get install openssl php5-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 php5-dev : Depends: libssl-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

As far as I can see, the issue is that openssl depends on libssl1.0.0 (>= 1.0.1), whereas php5-dev depends on libssl-dev [1], which in turn depends on libssl1.0.0 (= 1.0.1f-1ubuntu2.4) [2]. My limited knowledge tells me that effectively those two packages can not be installed on the same system. Am I correct?

[0] [http://packages.ubuntu.com/trusty/openssl](http://packages.ubuntu.com/trusty/openssl)
[1] [http://packages.ubuntu.com/trusty/php5-dev](http://packages.ubuntu.com/trusty/php5-dev)
[2] [http://packages.ubuntu.com/trusty/libssl-dev](http://packages.ubuntu.com/trusty/libssl-dev)

I'm testing this on a fresh trusty install (actually a Docker image) but I've noticed the same problem on saucy, albeit with slightly different version numbers.

Thanks,

Matt

---

### Post by Bashing-om on 2014-08-06
@ murp32; Hello,

Yeah, only 1 version of libssl1.0.0 can be installed, so ya need to look at what packages need to be upgraded( or down graded !) to match the libssl1.0.0 version that is installed.
check with:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
and make sure of the versions for the release installed ( and updated !) .

@ bphillips2; Now why am I not surprised ?

Grasping a bit here, but :
Architecture ?
```

dpkg -l php5-dev
dpkg -l php5-dev:i386

``` There is something somewhere somehow requiring the older version of libssl1.0.0 // how to find it ?

Maybe we should consider the explicit removal of 'libssl-dev=1.0.1-4ubuntu5.14" and trying to install the correct version "1.0.1-4ubuntu5.16" ?? BUT, sure would behoove us to know what is holding it to that lower version ! .. Doing the removal/reinstall might tell us what gets broke in the process, and maybe we can fix it (??).

[INDENT][INDENT]as around and round we go
[/INDENT][/INDENT]

---

### Post by murp32 on 2014-08-06
So it sounds like it's not the same issue... right?

Can you give me a quick hint on what to try next? I've never had to deal with a conflict like this before.

Thanks!

---

### Post by bphillips2 on 2014-08-06
Here is my output

```
justin@ubuntu:~$ dpkg -l php5-dev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                              Description
+++-====================================-====================================-========================================================================================
ii  php5-dev                             5.3.10-1ubuntu3.11                   Files for PHP5 module development

```
```



justin@ubuntu:~$ dpkg -l php5-dev:i386
No packages found matching php5-dev:i386.
```

---

### Post by Bashing-om on 2014-08-06
murp32; Welcome to our boat !

1st, ya got any 3rd party PPAs ? .. If so disable them, and also make sure that trusty-updates is enabled in your software sources.
update/upgrade -> see what the package manager relates .. 
Then the hunt is on - so far as I know . I have a whole page flow charting this dependency issue, trying to understand what/where/why.

Try and see what results:
```

sudo apt-get install libssl-dev

``` as the place to start.

@ bphillips2; sheesshh,

Looks like I do not comprehend all I do not know.
> 
justin@ubuntu:~$ apt-cache rdepends php5-devphp5-dev
Reverse Depends:
  php-pear
  php5-dev:i386
  php-pear
  php5-dev:i386   php-pear
 why do I add 2 + 2 and get a result of 2 ?
I may not understand the rdepend output (??) but I would think it is telling us that 'php5-dev:i386' is installed, correct ? .. then "dpkg" tells us it is not installed .
I do not have php5 installed onto my system so can not test or verify .

Let's sleep on this, look at it with a fresh mind, and then force the issue ! See what breaks .


[INDENT][INDENT]why, oh why ! ( when this is over we will be a lot smarter )
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-07
Bashing-om, I can't tell you how much I appreciate your help on this.  You have been phenomenal! 

I'm actually out of town with limited internet availability starting tomorrow morning until Monday.  Can we take the weekend to think about it and I'll bump the thread when I get back to continue?

If it helps the thought process, I tried the command '[COLOR=#000000]*apt-cache rdepends php5-dev'*[/COLOR] on my other server that has php and received the same output.  Pasted below.
```
brad@ubuntu:~$ apt-cache rdepends php5-dev
php5-dev
Reverse Depends:
  php5-dev:i386
  php-pear
  php5-dev:i386
  php-pear
```

Thanks again for all of your help!

---

### Post by murp32 on 2014-08-07
You the man! (I assume...)

Enabling trusty-updates did the trick. If you're ever in New Zealand I will definitely buy you a beer or two.

Again, sorry for hijacking the thread, hope you can figure out the original problem.

Matt

---

### Post by murp32 on 2014-08-07
-

---

### Post by Bashing-om on 2014-08-07
murp32; Great !

Pleased that one was easy, glad ya got it sorted out.

now you can just keep on keep'n on.

@bphillips2; sheesshh ..

Yeah, we can pick this up at a later date.
 If what we are working on is a production server, it deserves a lot of careful thought. ( but hey, look how far we have come from that 1st post !).
I would much prefer to know where the problem is than to take a sledge hammer approach - but we can and see what breaks !

[INDENT][INDENT]mean while
[INDENT][INDENT][INDENT]back at the ranch
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-12
> **Bashing-om said:**
> murp32; Great !

Pleased that one was easy, glad ya got it sorted out.

now you can just keep on keep'n on.

@bphillips2; sheesshh ..

Yeah, we can pick this up at a later date.
 If what we are working on is a production server, it deserves a lot of careful thought. ( but hey, look how far we have come from that 1st post !).
I would much prefer to know where the problem is than to take a sledge hammer approach - but we can and see what breaks !
[INDENT][INDENT]mean while[INDENT][INDENT][INDENT]back at the ranch
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hi Bashing-om, I'm back! Any epiphanies on the problem over the weekend? :)

---

### Post by Bashing-om on 2014-08-12
bphillips2; Hey !

Yeah, I been doing a bit of homework on this.
How 'bout we take this approach:
```

sudo apt-get remove libssl1.0.0=1.0.1-4ubuntu5.14
sudo apt-get  install --reinstall libssl1.0.0=1.0.1-40ubuntu5.16

```
Hopefully will get some idea of what is holding "ibssl1.0.0=1.0.1-4ubuntu5.14" at that old version, and maybe the updated version will complete.

[INDENT][INDENT]worth a shot
[INDENT][INDENT][INDENT]and take it from there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-12
Thanks for re-engaging the problem!

Here is my output from those two commands

```
justin@ubuntu:~$ sudo apt-get remove libssl1.0.0=1.0.1-4ubuntu5.14
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '1.0.1-4ubuntu5.14' for 'libssl1.0.0' was not found
```

```
justin@ubuntu:~$ sudo apt-get  install --reinstall libssl1.0.0=1.0.1-40ubuntu5.16
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '1.0.1-40ubuntu5.16' for 'libssl1.0.0' was not found
```

---

### Post by Bashing-om on 2014-08-12
bphillips2; What  ! ??

Now that is completely unexpected outputs. Are my wires crossed ?
what returns from:
```

dpkg -l libssl1.0.0
apt-cache policy libssl1.0.0

```
As I fall back, regroup ->

[INDENT][INDENT][INDENT]look'n for a way to punt
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-12
Here is the output

```
justin@ubuntu:~$ dpkg -l libssl1.0.0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                              Description
+++-====================================-====================================-========================================================================================
ii  libssl1.0.0                          1.0.1-4ubuntu5.16                    SSL shared libraries

```
```



justin@ubuntu:~$ apt-cache policy libssl1.0.0
libssl1.0.0:
  Installed: 1.0.1-4ubuntu5.16
  Candidate: 1.0.1-4ubuntu5.17
  Version table:
     1.0.1-4ubuntu5.17 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
 *** 1.0.1-4ubuntu5.16 0
        100 /var/lib/dpkg/status
     1.0.1-4ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```

---

### Post by Bashing-om on 2014-08-12
bphillips2; Humm ..

With that, I must ask, "Who is lying to who" ?; And why !

I must be away from the keyboard for a bit .. will re/examine what I do not know, and take this matter up once more; when I return.

[INDENT][INDENT]no such thing as quit
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-12
Sounds good.  Thanks for the help thus far!

---

### Post by Bashing-om on 2014-08-12
bphillips2; Welp.

Still stuck.
What does the system say is installed ? :
```

ls -la /var/lib/dpkg/info/libssl*

```

And in the file ( huge, to big to post ):
Looking at it in your favorite text editor;
```

/var/lib/dpkg/status

```
how many entries is there for the search term: " Package: libssl1.0.0 " ?
What version does the file(s) advise is installed within the stanza(s)?

[INDENT][INDENT]understanding sometimes
[INDENT][INDENT][INDENT][INDENT]be a struggle
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-12
```
justin@ubuntu:~$ ls -la /var/lib/dpkg/info/libssl*
-rw-r--r-- 1 root root   1096 Aug  4 13:55 /var/lib/dpkg/info/libssl1.0.0:amd64.list
-rw-r--r-- 1 root root   1413 Jun 20 13:58 /var/lib/dpkg/info/libssl1.0.0:amd64.md5sums
-rwxr-xr-x 1 root root   5878 Jun 20 13:57 /var/lib/dpkg/info/libssl1.0.0:amd64.postinst
-rwxr-xr-x 1 root root    321 Jun 20 13:57 /var/lib/dpkg/info/libssl1.0.0:amd64.postrm
-rw-r--r-- 1 root root    175 Jun 20 13:57 /var/lib/dpkg/info/libssl1.0.0:amd64.shlibs
-rw-r--r-- 1 root root 155562 Jun 20 13:57 /var/lib/dpkg/info/libssl1.0.0:amd64.symbols
-rw-r--r-- 1 root root  29037 Jun 20 13:57 /var/lib/dpkg/info/libssl1.0.0:amd64.templates
-rw-r--r-- 1 root root   2686 Jun  6 06:37 /var/lib/dpkg/info/libssl-dev.list
-rw-r--r-- 1 root root   4899 Jun  2 14:41 /var/lib/dpkg/info/libssl-dev.md5sums
-rw-r--r-- 1 root root  61186 Jun  6 06:37 /var/lib/dpkg/info/libssl-doc.list
-rw-r--r-- 1 root root  33160 Jun  2 14:40 /var/lib/dpkg/info/libssl-doc.md5sums
```

Only one occurrence in /var/lib/dpkg/status for "[COLOR=#000000]Package: libssl1.0.0"

[/COLOR]```
Package: libssl1.0.0Status: install ok installed
Multi-Arch: same
Priority: important
Section: libs
Installed-Size: 2922
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: openssl
Version: 1.0.1-4ubuntu5.16
Depends: libc6 (>= 2.14), zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0
Pre-Depends: multiarch-support
Breaks: openssh-client (<< 1:5.9p1-4), openssh-server (<< 1:5.9p1-4)
Description: SSL shared libraries
 libssl and libcrypto shared libraries needed by programs like
 apache-ssl, telnet-ssl and openssh.



```[COLOR=#000000]
[/COLOR]

---

### Post by Bashing-om on 2014-08-12
bphillips2; Yikes !


OK, I am still floundering here: ->
Once more there is no hint that version libssl1.0.0 (= 1.0.1-4ubuntu5.14) is installed !

But, the package manager insist that it is.
> 
libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.14); however:
  Version of libssl1.0.0 on system is 1.0.1-4ubuntu5.16.

How does "  libssl1.0.0 (= 1.0.1-4ubuntu5.14) " come into play here ?

Let's repeat the procedure and this time look at libssl-dev.

We keep coming back to look from "libssl-dev" that is holding " libssl1.0.0 " to the lower version.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-12
Here is the output

```
justin@ubuntu:~$ ls -la /var/lib/dpkg/info/libssl-dev*
-rw-r--r-- 1 root root 2686 Jun  6 06:37 /var/lib/dpkg/info/libssl-dev.list
-rw-r--r-- 1 root root 4899 Jun  2 14:41 /var/lib/dpkg/info/libssl-dev.md5sums
```


I tried searching for "package:libssl-dev" in 
```
[COLOR=#000000][FONT=Ubuntu Mono]/var/lib/dpkg/status[/FONT][/COLOR]
```

But didn't find it anywhere.  Maybe i misunderstood that part

---

### Post by Bashing-om on 2014-08-12
bphillips2; Humm,

No misunderstanding on your part ( not so sure about mine !).

The package manager has no track on " libssl-dev " !
What in the world can that mean ?
Maybe look in
```

/var/lib/dpkg/status-old

```
see if it exist there.

and what are we working with, what returns:
```

dpkg -l libssl-dev
apt-cache policy libssl-dev

``` what to do ? can't move forward, can't move back ( no install, no remove anything)// same ole question - what is holding "libssl1.0.0 " to the lower version ?

how to find it !

[INDENT][INDENT][INDENT]back to the drawing board
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-12
> **Bashing-om said:**
> bphillips2; Humm,

No misunderstanding on your part ( not so sure about mine !).

The package manager has no track on " libssl-dev " !
What in the world can that mean ?
Maybe look in
```

/var/lib/dpkg/status-old

```
see if it exist there.

Doesn't exist there either

```
justin@ubuntu:~$ dpkg -l libssl-dev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                              Description
+++-====================================-====================================-========================================================================================
iU  libssl-dev                           1.0.1-4ubuntu5.14                    SSL development libraries, header files and documentation

```
```



justin@ubuntu:~$ apt-cache policy libssl-dev
libssl-dev:
  Installed: 1.0.1-4ubuntu5.14
  Candidate: 1.0.1-4ubuntu5.17
  Version table:
     1.0.1-4ubuntu5.17 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
 *** 1.0.1-4ubuntu5.14 0
        100 /var/lib/dpkg/status
     1.0.1-4ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```

---

### Post by Bashing-om on 2014-08-12
bphillips2; YUK;....

The plot thickens:
> 
*** 1.0.1-4ubuntu5.14 0
        100 /var/lib/dpkg/status
     1.0.1-4ubuntu3 0

apt-cache policy says the entry exist in /var/lib/dpkg/status, but we looked and it does not exist.
As that file contains all the data dpkg requires to update and uninstall packages; With out that entry seems not much we can do. So now that begs the question, how to restore/rebuild '/var/lib/dpkg/status' ?
Might be worth considering; remove all these files listed in:"/var/lib/dpkg/info/libssl-dev.list" manually and then clean/update/reinstall ' libssl-dev '. 
compare to the output of:
```

dpkg --listfiles libssl-dev

```
and as well the file " /var/lib/dpkg/available " 
Could be 1 way to do this.
Is it worth while to look in the archives, see if there is a copy with the missing stanza present ?
```

ls -al /var/backups/dpkg.status*

```

I got my home work cut out for me.
and
I have a doctor's appointment tomorrow ( out of town) so will be amiss here tomorrow. I will get back on this soonest.

[INDENT][INDENT][INDENT]there is a reason
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-12
I'm a little confused by this, but here are the outputs of the commands you gave me

```
justin@ubuntu:~$ dpkg --listfiles libssl-dev/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libssl-dev
/usr/include
/usr/include/openssl
/usr/include/openssl/asn1t.h
/usr/include/openssl/rc2.h
/usr/include/openssl/ocsp.h
/usr/include/openssl/conf_api.h
/usr/include/openssl/srp.h
/usr/include/openssl/x509.h
/usr/include/openssl/cms.h
/usr/include/openssl/safestack.h
/usr/include/openssl/ec.h
/usr/include/openssl/sha.h
/usr/include/openssl/dh.h
/usr/include/openssl/aes.h
/usr/include/openssl/ecdh.h
/usr/include/openssl/obj_mac.h
/usr/include/openssl/ossl_typ.h
/usr/include/openssl/des_old.h
/usr/include/openssl/md5.h
/usr/include/openssl/symhacks.h
/usr/include/openssl/stack.h
/usr/include/openssl/rand.h
/usr/include/openssl/hmac.h
/usr/include/openssl/objects.h
/usr/include/openssl/lhash.h
/usr/include/openssl/whrlpool.h
/usr/include/openssl/rsa.h
/usr/include/openssl/bn.h
/usr/include/openssl/srtp.h
/usr/include/openssl/buffer.h
/usr/include/openssl/engine.h
/usr/include/openssl/ui_compat.h
/usr/include/openssl/pkcs7.h
/usr/include/openssl/ssl23.h
/usr/include/openssl/md4.h
/usr/include/openssl/ssl3.h
/usr/include/openssl/asn1.h
/usr/include/openssl/ssl2.h
/usr/include/openssl/ecdsa.h
/usr/include/openssl/bio.h
/usr/include/openssl/evp.h
/usr/include/openssl/krb5_asn.h
/usr/include/openssl/kssl.h
/usr/include/openssl/crypto.h
/usr/include/openssl/dso.h
/usr/include/openssl/des.h
/usr/include/openssl/opensslconf.h
/usr/include/openssl/err.h
/usr/include/openssl/pem2.h
/usr/include/openssl/ssl.h
/usr/include/openssl/x509_vfy.h
/usr/include/openssl/pkcs12.h
/usr/include/openssl/comp.h
/usr/include/openssl/camellia.h
/usr/include/openssl/ts.h
/usr/include/openssl/cast.h
/usr/include/openssl/x509v3.h
/usr/include/openssl/cmac.h
/usr/include/openssl/dtls1.h
/usr/include/openssl/opensslv.h
/usr/include/openssl/conf.h
/usr/include/openssl/pqueue.h
/usr/include/openssl/asn1_mac.h
/usr/include/openssl/seed.h
/usr/include/openssl/tls1.h
/usr/include/openssl/ebcdic.h
/usr/include/openssl/txt_db.h
/usr/include/openssl/modes.h
/usr/include/openssl/blowfish.h
/usr/include/openssl/ui.h
/usr/include/openssl/ripemd.h
/usr/include/openssl/pem.h
/usr/include/openssl/rc4.h
/usr/include/openssl/e_os2.h
/usr/include/openssl/dsa.h
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/pkgconfig
/usr/lib/x86_64-linux-gnu/pkgconfig/libcrypto.pc
/usr/lib/x86_64-linux-gnu/pkgconfig/openssl.pc
/usr/lib/x86_64-linux-gnu/pkgconfig/libssl.pc
/usr/lib/x86_64-linux-gnu/libssl.a
/usr/lib/x86_64-linux-gnu/libcrypto.a
/usr/share/doc/libssl-dev/changelog.Debian.gz
/usr/share/doc/libssl-dev/copyright
/usr/share/doc/libssl-dev/changelog.gz
/usr/lib/x86_64-linux-gnu/libssl.so
/usr/lib/x86_64-linux-gnu/libcrypto.so
```

Do you want this compared to the file "var/lib/dpkg/available"?


```
justin@ubuntu:~$ ls -al /var/backups/dpkg.status*-rw-r--r-- 1 root root 537686 Aug  5 14:08 /var/backups/dpkg.status.0
-rw-r--r-- 1 root root 160581 Aug  4 17:11 /var/backups/dpkg.status.1.gz
-rw-r--r-- 1 root root 160581 Jun 13 15:19 /var/backups/dpkg.status.2.gz
-rw-r--r-- 1 root root 160646 Jun 13 06:38 /var/backups/dpkg.status.3.gz
-rw-r--r-- 1 root root 160654 Jun  6 06:38 /var/backups/dpkg.status.4.gz
-rw-r--r-- 1 root root 160507 Jun  3 06:55 /var/backups/dpkg.status.5.gz
-rw-r--r-- 1 root root 160495 May 27 06:52 /var/backups/dpkg.status.6.gz



```

Good luck at the doctors appt.  I'll await your reply!

---

### Post by Bashing-om on 2014-08-13
bphillips2; Hey, hey


Look once more just to be sure that there is no entry in /var/lib/dpkg/status for the control stanza
```

Package: libssl-dev

```

Then for safety sake, look in your other server, see if there, that stanza exists.

Then see if that stanza exist in a archive file within one of the files in  "var/lib/dpkg/available" . A archive manager (nautilus) will allow you to open and read the compressed file.

NOW, until I find that there is some other method to resolve this fact that the control file is not present, the only thing we can do is to manually remove all those many many files listed by " dpkg --listfiles libssl-dev", that should be the same same list as in " /var/lib/dpkg/info/libssl-dev ".
Re-install 'libssl-dev' and make sure then that the package manager is in a consistent state.

That stanza not present in the status file will answer all the questions of why not I have been going around and round with.

-----------------------
So, unless I find otherwise; either laboriously remove the files ( those who really know their stuff and comfortable with the command line would craft up a bash script to do the removing ); or, do a fresh clean install of the operating system.
I will do some more investigation and see if I can find a better alternative -> presently I am unaware of one.

[INDENT][INDENT]as we face the nuclear solution
[/INDENT][/INDENT]

Doctor's appointment went well, I rest fairly certain I will awaken on the morrow.

---

### Post by bphillips2 on 2014-08-13
Oops, I must have omitted the space after "package:" Found the entry in /var/lib/dpkg/status

```
Package: libssl-devStatus: install ok unpacked
Priority: optional
Section: libdevel
Installed-Size: 6150
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: openssl
Version: 1.0.1-4ubuntu5.14
Config-Version: 1.0.1-4ubuntu5.13
Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14), zlib1g-dev
Recommends: libssl-doc
Description: SSL development libraries, header files and documentation
 libssl and libcrypto development libraries, header files and manpages.
```

It is also in /var/lib/dpkg/available

```
Package: libssl-devPriority: optional
Section: libdevel
Installed-Size: 6150
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: openssl
Version: 1.0.1-4ubuntu5.14
Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14), zlib1g-dev
Recommends: libssl-doc
Size: 1573088
Description: SSL development libraries, header files and documentation
 libssl and libcrypto development libraries, header files and manpages.
 .
 It is part of the OpenSSL implementation of SSL.
Original-Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
```

Maybe this changes your plan of attack?

---

### Post by Bashing-om on 2014-08-13
bphillips2; Yeah !

That puts us back on a different track - Before I became all excited at "knowing" what the causation is.
Upfront, we could do a hack job and get back in business, but I am not fond of hacking things up at all.
As we now know the source - if not the cause - of where the older version is called from; IF I can not come up with a better alternative, as that stanza exist for only once instance of "libssl-dev", we could foreseeably edit the files to reflect the correct version, and It might even come to that. That course of action has been on my mind.

Lemme have a bit of time to do some checking/verifying; a bit more time to clear my head and see what there is we can do.

[INDENT][INDENT]2 steps forward, and
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-13
bphillips2; HEY !

I may be onto something - finally .
Check this out.
On your system is installed for libssl-dev:
> 
justin@ubuntu:~$ apt-cache policy libssl-dev
libssl-dev:
  Installed: 1.0.1-4ubuntu5.14
  Candidate: 1.0.1-4ubuntu5.17

Looking from:
[http://packages.ubuntu.com/search?keywords=libssl-dev&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=libssl-dev&searchon=names&suite=precise&section=all)

Guess what // There is no such version as 1.0.1-4ubuntu5.14 in ubuntu packaging ! for any release.

Let's consider - will sleep on it - editing the "/var/lib/dpkg/status" file for that package "libssl-dev" and replace that invalid version number with the correct version number.
THEN lets see if we can remove it from the system
```

sudo apt-get remove libssl-dev

```
IF that runs, let's now put things back in place:
```

sudo apt-get install libssl1.0.0
sudo apt-get install libssl-dev

```
check:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

```

And remaining then to be dealt with is "drupal7" ( least should forget )

[INDENT][INDENT][INDENT]maybe finally yes 
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-13
Just to confirm, I need to change my file at /var/lib/dpkg/status

from this:
```
Package: libssl-devStatus: install ok unpacked
Priority: optional
Section: libdevel
Installed-Size: 6150
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: openssl
Version: 1.0.1-_**4ubuntu5.14**_
Config-Version: 1.0.1-4ubuntu5.13
Depends: libssl1.0.0 (=** _1.0.1-4ubuntu5.14_**), zlib1g-dev
Recommends: libssl-doc
Description: SSL development libraries, header files and documentation
 libssl and libcrypto development libraries, header files and manpages.
 .
 It is part of the OpenSSL implementation of SSL.
Original-Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
```

To this:
```
Package: libssl-devStatus: install ok unpacked
Priority: optional
Section: libdevel
Installed-Size: 6150
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: openssl
Version: _**1.0.1-4ubuntu5.16**_
Config-Version: 1.0.1-4ubuntu5.13
Depends: libssl1.0.0 (**= _1.0.1-4ubuntu5.16_**), zlib1g-dev
Recommends: libssl-doc
Description: SSL development libraries, header files and documentation
 libssl and libcrypto development libraries, header files and manpages.
 .
 It is part of the OpenSSL implementation of SSL.
Original-Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
```

And then run the commands you posted??

---

### Post by Bashing-om on 2014-08-13
bphillips2; Semi so;

You got it. That is what I think .. Be aware there is lots about the package manager I do not know but I do think the below should work.

Take notes of what/how you changed - or make a copy before doing the edits - so we can easily revert back if the change is problematic.

The line "Version: 1.0.1-4ubuntu5.14" /  change the version to "1.0.1-4ubuntu5.17: ;
The line "Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.14), zlib1g-dev" / change the version to "1.0.1-4ubuntu5.16"

the version number of what 'should be installed' for libssl-dev
the version number of what is 'actually installed', per all our request to know, for libssl1.0.0

And let's see what happens.
[INDENT][INDENT]make me real happy
[INDENT][INDENT][INDENT]you tell me we are on the tight track
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-13
Well, this looks promising.  I believe that worked!!!!

```
justin@ubuntu:/var/lib/dpkg$ sudo apt-get remove libssl-dev
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libssl-dev php5-dev
0 upgraded, 0 newly installed, 2 to remove and 92 not upgraded.
1 not fully installed or removed.
After this operation, 8,973 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 190339 files and directories currently installed.)
Removing php5-dev ...
dpkg: warning: while removing php5-dev, directory '/usr/include/php5/ext' not empty so not removed.
Removing libssl-dev ...
Processing triggers for man-db ...

```
```

justin@ubuntu:/var/lib/dpkg$ sudo apt-get install libssl1.0.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  shtool libssl-doc zlib1g-dev
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libssl1.0.0
1 upgraded, 0 newly installed, 0 to remove and 91 not upgraded.
Need to get 1,049 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libssl1.0.0 amd64 1.0.1-4ubuntu5.17 [1,049 kB]
Fetched 1,049 kB in 4s (227 kB/s)      
Preconfiguring packages ...
(Reading database ... 189954 files and directories currently installed.)
Preparing to replace libssl1.0.0 1.0.1-4ubuntu5.16 (using .../libssl1.0.0_1.0.1-4ubuntu5.17_amd64.deb) ...
Unpacking replacement libssl1.0.0 ...
Setting up libssl1.0.0 (1.0.1-4ubuntu5.17) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place



```
```



justin@ubuntu:/$ sudo apt-get install libssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  shtool
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libssl-dev
0 upgraded, 1 newly installed, 0 to remove and 91 not upgraded.
Need to get 1,574 kB of archives.
After this operation, 6,299 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libssl-dev amd64 1.0.1-4ubuntu5.17 [1,574 kB]
Fetched 1,574 kB in 0s (1,737 kB/s)   
Selecting previously unselected package libssl-dev.
(Reading database ... 189954 files and directories currently installed.)
Unpacking libssl-dev (from .../libssl-dev_1.0.1-4ubuntu5.17_amd64.deb) ...
Setting up libssl-dev (1.0.1-4ubuntu5.17) ...





```
```

justin@ubuntu:/$ sudo apt-get update
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise-backports Release.gpg
Hit http://us.archive.ubuntu.com precise Release
Get:2 http://us.archive.ubuntu.com precise-updates Release [98.7 kB]
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]         
Get:4 http://security.ubuntu.com precise-security Release [50.7 kB]
Hit http://us.archive.ubuntu.com precise-backports Release        
Hit http://us.archive.ubuntu.com precise/main Sources                             
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main amd64 Packages
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:5 http://us.archive.ubuntu.com precise-updates/main Sources [477 kB]
Get:6 http://security.ubuntu.com precise-security/main Sources [108 kB]
Get:7 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:8 http://us.archive.ubuntu.com precise-updates/universe Sources [110 kB]   
Get:9 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:10 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]          
Get:11 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B]        
Get:12 http://security.ubuntu.com precise-security/main amd64 Packages [416 kB]         
Get:13 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]       
Get:14 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [825 kB]           
Get:15 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]     
Get:16 http://security.ubuntu.com precise-security/universe amd64 Packages [96.8 kB]         
Get:17 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,451 B]    
Get:18 http://security.ubuntu.com precise-security/main i386 Packages [444 kB]             
Get:19 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]      
Get:20 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]        
Get:21 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [13.7 kB]     
Get:22 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]        
Get:23 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]            
Get:24 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]              
Get:25 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:26 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B] 
Get:27 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [247 kB]               
Get:28 http://security.ubuntu.com precise-security/main Translation-en [190 kB]  
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                        
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Get:29 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]
Get:30 http://us.archive.ubuntu.com precise-updates/main i386 Packages [855 kB]    
Hit http://security.ubuntu.com precise-security/universe Translation-en          
Get:31 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:32 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]
Get:33 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:34 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:35 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:36 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:37 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://us.archive.ubuntu.com precise-backports/main Sources  
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Get:38 http://us.archive.ubuntu.com precise-updates/main Translation-en [362 kB]
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 4,772 kB in 3s (1,444 kB/s)
Reading package lists... Done
```

```
justin@ubuntu:/$ sudo apt-get upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic-lts-raring linux-image-generic-lts-raring
The following packages will be upgraded:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common apparmor apt apt-transport-https apt-utils base-files bsdutils dbus dmidecode dpkg-dev file
  gnupg gpgv grub-common grub-pc grub-pc-bin grub2-common ifupdown iproute krb5-locales libapache2-mod-php5 libapt-inst1.4 libapt-pkg4.12 libblkid1 libc-bin
  libc-dev-bin libc6 libc6-dev libdbus-1-3 libdpkg-perl libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libgssapi-krb5-2 libjpeg-turbo8 libk5crypto3 libkrb5-3
  libkrb5support0 liblzo2-2 libmagic1 libmount1 libmysqlclient18 libparted0debian1 libssl-doc libtasn1-3 libuuid1 libwbclient0 libxml2 linux-firmware
  linux-generic-lts-raring linux-headers-3.8.0-42 linux-headers-3.8.0-42-generic linux-libc-dev mount multiarch-support mysql-client-5.5 mysql-client-core-5.5
  mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5 openssl parted php-pear php5 php5-cgi php5-cli php5-common php5-curl php5-dbg php5-fpm php5-gd
  php5-intl php5-mysql php5-sqlite samba-common samba-common-bin smbclient tzdata update-manager-core update-notifier-common util-linux uuid-runtime wget
89 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 145 MB of archives.
After this operation, 4,096 B disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main base-files amd64 6.5ubuntu6.8 [68.2 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main mount amd64 2.20.1-1ubuntu3.1 [166 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main tzdata all 2014e-0ubuntu0.12.04 [458 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main util-linux amd64 2.20.1-1ubuntu3.1 [596 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libc-dev-bin amd64 2.15-0ubuntu10.6 [85.1 kB]                                                          
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libc6-dev amd64 2.15-0ubuntu10.6 [2,946 kB]                                                            
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libc-bin amd64 2.15-0ubuntu10.6 [1,184 kB]                                                             
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libc6 amd64 2.15-0ubuntu10.6 [4,652 kB]                                                                
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-libc-dev amd64 3.2.0-67.101 [862 kB]                                                             
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main bsdutils amd64 1:2.20.1-1ubuntu3.1 [39.7 kB]                                                          
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libapt-pkg4.12 amd64 0.8.16~exp12ubuntu10.17 [940 kB]                                                 
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gpgv amd64 1.4.11-3ubuntu2.6 [185 kB]                                                                 
Get:13 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gnupg amd64 1.4.11-3ubuntu2.6 [808 kB]                                                                
Get:14 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apt amd64 0.8.16~exp12ubuntu10.17 [1,102 kB]                                                          
Get:15 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libuuid1 amd64 2.20.1-1ubuntu3.1 [12.8 kB]                                                            
Get:16 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libblkid1 amd64 2.20.1-1ubuntu3.1 [73.7 kB]                                                           
Get:17 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libmount1 amd64 2.20.1-1ubuntu3.1 [71.5 kB]                                                           
Get:18 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libapt-inst1.4 amd64 0.8.16~exp12ubuntu10.17 [102 kB]                                                 
Get:19 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdbus-1-3 amd64 1.4.18-1ubuntu1.5 [145 kB]                                                          
Get:20 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm2 amd64 2.4.52-1~precise1 [26.1 kB]                                                             
Get:21 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-intel1 amd64 2.4.52-1~precise1 [65.8 kB]                                                       
Get:22 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-nouveau1a amd64 2.4.52-1~precise1 [14.0 kB]                                                    
Get:23 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-radeon1 amd64 2.4.52-1~precise1 [27.9 kB]                                                      
Get:24 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apparmor amd64 2.7.102-0ubuntu3.10 [357 kB]                                                           
Get:25 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libk5crypto3 amd64 1.10+dfsg~beta1-2ubuntu0.5 [79.9 kB]                                               
Get:26 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgssapi-krb5-2 amd64 1.10+dfsg~beta1-2ubuntu0.5 [118 kB]                                            
Get:27 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libkrb5-3 amd64 1.10+dfsg~beta1-2ubuntu0.5 [354 kB]                                                   
Get:28 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libkrb5support0 amd64 1.10+dfsg~beta1-2ubuntu0.5 [24.2 kB]                                            
Get:29 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libparted0debian1 amd64 2.3-8ubuntu5.2 [240 kB]                                                       
Get:30 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libtasn1-3 amd64 2.10-1ubuntu1.2 [43.7 kB]                                                            
Get:31 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxml2 amd64 2.7.8.dfsg-5.1ubuntu4.9 [673 kB]                                                        
Get:32 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libjpeg-turbo8 amd64 1.1.90+svn733-0ubuntu4.4 [112 kB]                                                
Get:33 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main liblzo2-2 amd64 2.06-1ubuntu0.1 [52.5 kB]                                                             
Get:34 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main mysql-common all 5.5.38-0ubuntu0.12.04.1 [13.2 kB]                                                    
Get:35 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libmysqlclient18 amd64 5.5.38-0ubuntu0.12.04.1 [949 kB]                                               
Get:36 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libwbclient0 amd64 2:3.6.3-2ubuntu2.11 [29.8 kB]                                                      
Get:37 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main mysql-server all 5.5.38-0ubuntu0.12.04.1 [11.4 kB]                                                    
Get:38 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main mysql-server-5.5 amd64 5.5.38-0ubuntu0.12.04.1 [8,834 kB]                                             
Get:39 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main mysql-client-core-5.5 amd64 5.5.38-0ubuntu0.12.04.1 [1,941 kB]                                        
Get:40 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main mysql-client-5.5 amd64 5.5.38-0ubuntu0.12.04.1 [8,342 kB]                                             
Get:41 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main mysql-server-core-5.5 amd64 5.5.38-0ubuntu0.12.04.1 [6,090 kB]                                        
Get:42 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main file amd64 5.09-2ubuntu0.4 [19.7 kB]                                                                  
Get:43 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libmagic1 amd64 5.09-2ubuntu0.4 [217 kB]                                                              
Get:44 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main php5-dbg amd64 5.3.10-1ubuntu3.13 [13.3 MB]                                                           
Get:45 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main php5-cli amd64 5.3.10-1ubuntu3.13 [3,051 kB]                                                          
Get:46 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main php5-cgi amd64 5.3.10-1ubuntu3.13 [6,104 kB]                                                          
Get:47 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apache2 amd64 2.2.22-1ubuntu1.7 [1,494 B]                                                             
Get:48 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apache2-mpm-prefork amd64 2.2.22-1ubuntu1.7 [2,404 B]                                                 
Get:49 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apache2.2-common amd64 2.2.22-1ubuntu1.7 [226 kB]                                                     
Get:50 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apache2.2-bin amd64 2.2.22-1ubuntu1.7 [1,342 kB]                                                      
Get:51 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apache2-utils amd64 2.2.22-1ubuntu1.7 [89.3 kB]                                                       
Get:52 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libapache2-mod-php5 amd64 5.3.10-1ubuntu3.13 [3,137 kB]                                               
Get:53 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe php5-intl amd64 5.3.10-1ubuntu3.13 [60.5 kB]                                                      
Get:54 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main php5-mysql amd64 5.3.10-1ubuntu3.13 [76.6 kB]                                                         
Get:55 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main php5-curl amd64 5.3.10-1ubuntu3.13 [28.0 kB]                                                          
Get:56 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main php5-sqlite amd64 5.3.10-1ubuntu3.13 [27.6 kB]                                                        
Get:57 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main php5-gd amd64 5.3.10-1ubuntu3.13 [38.8 kB]                                                            
Get:58 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe php5-fpm amd64 5.3.10-1ubuntu3.13 [3,095 kB]                                                      
Get:59 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main php5-common amd64 5.3.10-1ubuntu3.13 [1,774 kB]                                                       
Get:60 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main update-manager-core amd64 1:0.156.14.17 [186 kB]                                                      
Get:61 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main update-notifier-common all 0.119ubuntu8.7 [222 kB]                                                    
Get:62 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main multiarch-support amd64 2.15-0ubuntu10.6 [4,476 B]                                                    
Get:63 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apt-utils amd64 0.8.16~exp12ubuntu10.17 [189 kB]                                                      
Get:64 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main iproute amd64 20111117-1ubuntu2.3 [444 kB]                                                            
Get:65 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main ifupdown amd64 0.7~beta2ubuntu11.1 [48.3 kB]                                                          
Get:66 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apt-transport-https amd64 0.8.16~exp12ubuntu10.17 [16.3 kB]                                           
Get:67 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main dbus amd64 1.4.18-1ubuntu1.5 [359 kB]                                                                 
Get:68 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main dmidecode amd64 2.11-4ubuntu0.1 [52.3 kB]                                                             
Get:69 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main krb5-locales all 1.10+dfsg~beta1-2ubuntu0.5 [9,558 B]                                                 
Get:70 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main openssl amd64 1.0.1-4ubuntu5.17 [523 kB]                                                              
Get:71 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main parted amd64 2.3-8ubuntu5.2 [52.4 kB]                                                                 
Get:72 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main uuid-runtime amd64 2.20.1-1ubuntu3.1 [14.1 kB]                                                        
Get:73 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main wget amd64 1.13.4-2ubuntu1.1 [279 kB]                                                                 
Get:74 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main dpkg-dev all 1.16.1.2ubuntu7.5 [468 kB]                                                               
Get:75 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdpkg-perl all 1.16.1.2ubuntu7.5 [182 kB]                                                           
Get:76 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-pc amd64 1.99-21ubuntu3.16 [140 kB]                                                              
Get:77 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-pc-bin amd64 1.99-21ubuntu3.16 [870 kB]                                                          
Get:78 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub2-common amd64 1.99-21ubuntu3.16 [95.1 kB]                                                        
Get:79 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.16 [2,072 kB]                                                        
Get:80 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libssl-doc all 1.0.1-4ubuntu5.17 [1,036 kB]                                                           
Get:81 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-firmware all 1.79.16 [27.7 MB]                                                                  
Get:82 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-generic-lts-raring amd64 3.8.0.44.44 [1,740 B]                                                  
Get:83 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.8.0-42 all 3.8.0-42.63~precise1 [12.2 MB]                                             
Get:84 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.8.0-42-generic amd64 3.8.0-42.63~precise1 [998 kB]                                    
Get:85 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main php-pear all 5.3.10-1ubuntu3.13 [371 kB]                                                              
Get:86 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main php5 all 5.3.10-1ubuntu3.13 [1,078 B]                                                                 
Get:87 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main smbclient amd64 2:3.6.3-2ubuntu2.11 [14.1 MB]                                                         
Get:88 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main samba-common all 2:3.6.3-2ubuntu2.11 [325 kB]                                                         
Get:89 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main samba-common-bin amd64 2:3.6.3-2ubuntu2.11 [6,175 kB]                                                 
Fetched 145 MB in 13min 32s (178 kB/s)                                                                                                                                 
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace base-files 6.5ubuntu6.7 (using .../base-files_6.5ubuntu6.8_amd64.deb) ...
Unpacking replacement base-files ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-38-generic
Setting up base-files (6.5ubuntu6.8) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
Installing new version of config file /etc/os-release ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-38-generic
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace mount 2.20.1-1ubuntu3 (using .../mount_2.20.1-1ubuntu3.1_amd64.deb) ...
Unpacking replacement mount ...
Processing triggers for man-db ...
Setting up mount (2.20.1-1ubuntu3.1) ...
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace tzdata 2014c-0ubuntu0.12.04 (using .../tzdata_2014e-0ubuntu0.12.04_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2014e-0ubuntu0.12.04) ...


Current default time zone: 'America/Chicago'
Local time is now:      Wed Aug 13 22:49:22 CDT 2014.
Universal Time is now:  Thu Aug 14 03:49:22 UTC 2014.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


(Reading database ... 190039 files and directories currently installed.)
Preparing to replace util-linux 2.20.1-1ubuntu3 (using .../util-linux_2.20.1-1ubuntu3.1_amd64.deb) ...
Unpacking replacement util-linux ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up util-linux (2.20.1-1ubuntu3.1) ...
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace libc-dev-bin 2.15-0ubuntu10.5 (using .../libc-dev-bin_2.15-0ubuntu10.6_amd64.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev 2.15-0ubuntu10.5 (using .../libc6-dev_2.15-0ubuntu10.6_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc-bin 2.15-0ubuntu10.5 (using .../libc-bin_2.15-0ubuntu10.6_amd64.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.15-0ubuntu10.6) ...
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.5 (using .../libc6_2.15-0ubuntu10.6_amd64.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.15-0ubuntu10.6) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace linux-libc-dev 3.2.0-63.95 (using .../linux-libc-dev_3.2.0-67.101_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace bsdutils 1:2.20.1-1ubuntu3 (using .../bsdutils_1%3a2.20.1-1ubuntu3.1_amd64.deb) ...
Unpacking replacement bsdutils ...
Processing triggers for man-db ...
Setting up bsdutils (1:2.20.1-1ubuntu3.1) ...
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.16 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.17_amd64.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.17) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace gpgv 1.4.11-3ubuntu2.5 (using .../gpgv_1.4.11-3ubuntu2.6_amd64.deb) ...
Unpacking replacement gpgv ...
Processing triggers for man-db ...
Setting up gpgv (1.4.11-3ubuntu2.6) ...
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace gnupg 1.4.11-3ubuntu2.5 (using .../gnupg_1.4.11-3ubuntu2.6_amd64.deb) ...
Unpacking replacement gnupg ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up gnupg (1.4.11-3ubuntu2.6) ...
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp12ubuntu10.16 (using .../apt_0.8.16~exp12ubuntu10.17_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
Setting up apt (0.8.16~exp12ubuntu10.17) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace libuuid1 2.20.1-1ubuntu3 (using .../libuuid1_2.20.1-1ubuntu3.1_amd64.deb) ...
Unpacking replacement libuuid1 ...
Setting up libuuid1 (2.20.1-1ubuntu3.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace libblkid1 2.20.1-1ubuntu3 (using .../libblkid1_2.20.1-1ubuntu3.1_amd64.deb) ...
Unpacking replacement libblkid1 ...
Setting up libblkid1 (2.20.1-1ubuntu3.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace libmount1 2.20.1-1ubuntu3 (using .../libmount1_2.20.1-1ubuntu3.1_amd64.deb) ...
Unpacking replacement libmount1 ...
Setting up libmount1 (2.20.1-1ubuntu3.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace libapt-inst1.4 0.8.16~exp12ubuntu10.16 (using .../libapt-inst1.4_0.8.16~exp12ubuntu10.17_amd64.deb) ...
Unpacking replacement libapt-inst1.4 ...
Preparing to replace libdbus-1-3 1.4.18-1ubuntu1.4 (using .../libdbus-1-3_1.4.18-1ubuntu1.5_amd64.deb) ...
Unpacking replacement libdbus-1-3 ...
Preparing to replace libdrm2 2.4.46-1ubuntu0.0.0.1 (using .../libdrm2_2.4.52-1~precise1_amd64.deb) ...
Unpacking replacement libdrm2 ...
Preparing to replace libdrm-intel1 2.4.46-1ubuntu0.0.0.1 (using .../libdrm-intel1_2.4.52-1~precise1_amd64.deb) ...
Unpacking replacement libdrm-intel1 ...
Preparing to replace libdrm-nouveau1a 2.4.46-1ubuntu0.0.0.1 (using .../libdrm-nouveau1a_2.4.52-1~precise1_amd64.deb) ...
Unpacking replacement libdrm-nouveau1a ...
Preparing to replace libdrm-radeon1 2.4.46-1ubuntu0.0.0.1 (using .../libdrm-radeon1_2.4.52-1~precise1_amd64.deb) ...
Unpacking replacement libdrm-radeon1 ...
Preparing to replace apparmor 2.7.102-0ubuntu3.9 (using .../apparmor_2.7.102-0ubuntu3.10_amd64.deb) ...
Unpacking replacement apparmor ...
Preparing to replace libk5crypto3 1.10+dfsg~beta1-2ubuntu0.3 (using .../libk5crypto3_1.10+dfsg~beta1-2ubuntu0.5_amd64.deb) ...
Unpacking replacement libk5crypto3 ...
Preparing to replace libgssapi-krb5-2 1.10+dfsg~beta1-2ubuntu0.3 (using .../libgssapi-krb5-2_1.10+dfsg~beta1-2ubuntu0.5_amd64.deb) ...
Unpacking replacement libgssapi-krb5-2 ...
Preparing to replace libkrb5-3 1.10+dfsg~beta1-2ubuntu0.3 (using .../libkrb5-3_1.10+dfsg~beta1-2ubuntu0.5_amd64.deb) ...
Unpacking replacement libkrb5-3 ...
Preparing to replace libkrb5support0 1.10+dfsg~beta1-2ubuntu0.3 (using .../libkrb5support0_1.10+dfsg~beta1-2ubuntu0.5_amd64.deb) ...
Unpacking replacement libkrb5support0 ...
Preparing to replace libparted0debian1 2.3-8ubuntu5.1 (using .../libparted0debian1_2.3-8ubuntu5.2_amd64.deb) ...
Unpacking replacement libparted0debian1 ...
Preparing to replace libtasn1-3 2.10-1ubuntu1.1 (using .../libtasn1-3_2.10-1ubuntu1.2_amd64.deb) ...
Unpacking replacement libtasn1-3 ...
Preparing to replace libxml2 2.7.8.dfsg-5.1ubuntu4.7 (using .../libxml2_2.7.8.dfsg-5.1ubuntu4.9_amd64.deb) ...
Unpacking replacement libxml2 ...
Preparing to replace libjpeg-turbo8 1.1.90+svn733-0ubuntu4.3 (using .../libjpeg-turbo8_1.1.90+svn733-0ubuntu4.4_amd64.deb) ...
Unpacking replacement libjpeg-turbo8 ...
Preparing to replace liblzo2-2 2.06-1 (using .../liblzo2-2_2.06-1ubuntu0.1_amd64.deb) ...
Unpacking replacement liblzo2-2 ...
Preparing to replace mysql-common 5.5.37-0ubuntu0.12.04.1 (using .../mysql-common_5.5.38-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement mysql-common ...
Preparing to replace libmysqlclient18 5.5.37-0ubuntu0.12.04.1 (using .../libmysqlclient18_5.5.38-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libmysqlclient18 ...
Preparing to replace libwbclient0 2:3.6.3-2ubuntu2.10 (using .../libwbclient0_2%3a3.6.3-2ubuntu2.11_amd64.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace mysql-server 5.5.37-0ubuntu0.12.04.1 (using .../mysql-server_5.5.38-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement mysql-server ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up mysql-common (5.5.38-0ubuntu0.12.04.1) ...
(Reading database ... 190039 files and directories currently installed.)
Preparing to replace mysql-server-5.5 5.5.37-0ubuntu0.12.04.1 (using .../mysql-server-5.5_5.5.38-0ubuntu0.12.04.1_amd64.deb) ...
mysql stop/waiting
Unpacking replacement mysql-server-5.5 ...
Preparing to replace mysql-client-core-5.5 5.5.37-0ubuntu0.12.04.1 (using .../mysql-client-core-5.5_5.5.38-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement mysql-client-core-5.5 ...
Preparing to replace mysql-client-5.5 5.5.37-0ubuntu0.12.04.1 (using .../mysql-client-5.5_5.5.38-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement mysql-client-5.5 ...
Preparing to replace mysql-server-core-5.5 5.5.37-0ubuntu0.12.04.1 (using .../mysql-server-core-5.5_5.5.38-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement mysql-server-core-5.5 ...
Preparing to replace file 5.09-2ubuntu0.3 (using .../file_5.09-2ubuntu0.4_amd64.deb) ...
Unpacking replacement file ...
Preparing to replace libmagic1 5.09-2ubuntu0.3 (using .../libmagic1_5.09-2ubuntu0.4_amd64.deb) ...
Unpacking replacement libmagic1 ...
Preparing to replace php5-dbg 5.3.10-1ubuntu3.11 (using .../php5-dbg_5.3.10-1ubuntu3.13_amd64.deb) ...
Unpacking replacement php5-dbg ...
Preparing to replace php5-cli 5.3.10-1ubuntu3.11 (using .../php5-cli_5.3.10-1ubuntu3.13_amd64.deb) ...
Unpacking replacement php5-cli ...
Preparing to replace php5-cgi 5.3.10-1ubuntu3.11 (using .../php5-cgi_5.3.10-1ubuntu3.13_amd64.deb) ...
Unpacking replacement php5-cgi ...
Preparing to replace apache2 2.2.22-1ubuntu1.6 (using .../apache2_2.2.22-1ubuntu1.7_amd64.deb) ...
Unpacking replacement apache2 ...
Preparing to replace apache2-mpm-prefork 2.2.22-1ubuntu1.6 (using .../apache2-mpm-prefork_2.2.22-1ubuntu1.7_amd64.deb) ...
 * Stopping web server apache2                                                                                                                                          [Wed Aug 13 22:50:41 2014] [warn] module deflate_module is already loaded, skipping
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting                                                                                                                                                     [ OK ]
Unpacking replacement apache2-mpm-prefork ...
Preparing to replace apache2.2-common 2.2.22-1ubuntu1.6 (using .../apache2.2-common_2.2.22-1ubuntu1.7_amd64.deb) ...
Unpacking replacement apache2.2-common ...
Preparing to replace apache2.2-bin 2.2.22-1ubuntu1.6 (using .../apache2.2-bin_2.2.22-1ubuntu1.7_amd64.deb) ...
Unpacking replacement apache2.2-bin ...
Preparing to replace apache2-utils 2.2.22-1ubuntu1.6 (using .../apache2-utils_2.2.22-1ubuntu1.7_amd64.deb) ...
Unpacking replacement apache2-utils ...
Preparing to replace libapache2-mod-php5 5.3.10-1ubuntu3.11 (using .../libapache2-mod-php5_5.3.10-1ubuntu3.13_amd64.deb) ...
Unpacking replacement libapache2-mod-php5 ...
Preparing to replace php5-intl 5.3.10-1ubuntu3.11 (using .../php5-intl_5.3.10-1ubuntu3.13_amd64.deb) ...
Unpacking replacement php5-intl ...
Preparing to replace php5-mysql 5.3.10-1ubuntu3.11 (using .../php5-mysql_5.3.10-1ubuntu3.13_amd64.deb) ...
Unpacking replacement php5-mysql ...
Preparing to replace php5-curl 5.3.10-1ubuntu3.11 (using .../php5-curl_5.3.10-1ubuntu3.13_amd64.deb) ...
Unpacking replacement php5-curl ...
Preparing to replace php5-sqlite 5.3.10-1ubuntu3.11 (using .../php5-sqlite_5.3.10-1ubuntu3.13_amd64.deb) ...
Unpacking replacement php5-sqlite ...
Preparing to replace php5-gd 5.3.10-1ubuntu3.11 (using .../php5-gd_5.3.10-1ubuntu3.13_amd64.deb) ...
Unpacking replacement php5-gd ...
Preparing to replace php5-fpm 5.3.10-1ubuntu3.11 (using .../php5-fpm_5.3.10-1ubuntu3.13_amd64.deb) ...
Unpacking replacement php5-fpm ...
Preparing to replace php5-common 5.3.10-1ubuntu3.11 (using .../php5-common_5.3.10-1ubuntu3.13_amd64.deb) ...
Unpacking replacement php5-common ...
Preparing to replace update-manager-core 1:0.156.14.13 (using .../update-manager-core_1%3a0.156.14.17_amd64.deb) ...
Unpacking replacement update-manager-core ...
Preparing to replace update-notifier-common 0.119ubuntu8.6 (using .../update-notifier-common_0.119ubuntu8.7_all.deb) ...
Unpacking replacement update-notifier-common ...
Preparing to replace multiarch-support 2.15-0ubuntu10.5 (using .../multiarch-support_2.15-0ubuntu10.6_amd64.deb) ...
Unpacking replacement multiarch-support ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Setting up multiarch-support (2.15-0ubuntu10.6) ...
(Reading database ... 190048 files and directories currently installed.)
Preparing to replace apt-utils 0.8.16~exp12ubuntu10.16 (using .../apt-utils_0.8.16~exp12ubuntu10.17_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace iproute 20111117-1ubuntu2.1 (using .../iproute_20111117-1ubuntu2.3_amd64.deb) ...
Unpacking replacement iproute ...
Preparing to replace ifupdown 0.7~beta2ubuntu11 (using .../ifupdown_0.7~beta2ubuntu11.1_amd64.deb) ...
Unpacking replacement ifupdown ...
Preparing to replace apt-transport-https 0.8.16~exp12ubuntu10.16 (using .../apt-transport-https_0.8.16~exp12ubuntu10.17_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace dbus 1.4.18-1ubuntu1.4 (using .../dbus_1.4.18-1ubuntu1.5_amd64.deb) ...
Unpacking replacement dbus ...
Preparing to replace dmidecode 2.11-4 (using .../dmidecode_2.11-4ubuntu0.1_amd64.deb) ...
Unpacking replacement dmidecode ...
Preparing to replace krb5-locales 1.10+dfsg~beta1-2ubuntu0.3 (using .../krb5-locales_1.10+dfsg~beta1-2ubuntu0.5_all.deb) ...
Unpacking replacement krb5-locales ...
Preparing to replace openssl 1.0.1-4ubuntu5.13 (using .../openssl_1.0.1-4ubuntu5.17_amd64.deb) ...
Unpacking replacement openssl ...
Preparing to replace parted 2.3-8ubuntu5.1 (using .../parted_2.3-8ubuntu5.2_amd64.deb) ...
Unpacking replacement parted ...
Preparing to replace uuid-runtime 2.20.1-1ubuntu3 (using .../uuid-runtime_2.20.1-1ubuntu3.1_amd64.deb) ...
Unpacking replacement uuid-runtime ...
Preparing to replace wget 1.13.4-2ubuntu1 (using .../wget_1.13.4-2ubuntu1.1_amd64.deb) ...
Unpacking replacement wget ...
Preparing to replace dpkg-dev 1.16.1.2ubuntu7.4 (using .../dpkg-dev_1.16.1.2ubuntu7.5_all.deb) ...
Unpacking replacement dpkg-dev ...
Preparing to replace libdpkg-perl 1.16.1.2ubuntu7.4 (using .../libdpkg-perl_1.16.1.2ubuntu7.5_all.deb) ...
Unpacking replacement libdpkg-perl ...
Preparing to replace grub-pc 1.99-21ubuntu3.14 (using .../grub-pc_1.99-21ubuntu3.16_amd64.deb) ...
Unpacking replacement grub-pc ...
Preparing to replace grub-pc-bin 1.99-21ubuntu3.14 (using .../grub-pc-bin_1.99-21ubuntu3.16_amd64.deb) ...
Unpacking replacement grub-pc-bin ...
Preparing to replace grub2-common 1.99-21ubuntu3.14 (using .../grub2-common_1.99-21ubuntu3.16_amd64.deb) ...
Unpacking replacement grub2-common ...
Preparing to replace grub-common 1.99-21ubuntu3.14 (using .../grub-common_1.99-21ubuntu3.16_amd64.deb) ...
Unpacking replacement grub-common ...
Preparing to replace libssl-doc 1.0.1-4ubuntu5.14 (using .../libssl-doc_1.0.1-4ubuntu5.17_all.deb) ...
Unpacking replacement libssl-doc ...
Preparing to replace linux-firmware 1.79.14 (using .../linux-firmware_1.79.16_all.deb) ...
Unpacking replacement linux-firmware ...
Preparing to replace linux-generic-lts-raring 3.8.0.37.37 (using .../linux-generic-lts-raring_3.8.0.44.44_amd64.deb) ...
Unpacking replacement linux-generic-lts-raring ...
Preparing to replace linux-headers-3.8.0-42 3.8.0-42.62~precise1 (using .../linux-headers-3.8.0-42_3.8.0-42.63~precise1_all.deb) ...
Unpacking replacement linux-headers-3.8.0-42 ...
Preparing to replace linux-headers-3.8.0-42-generic 3.8.0-42.62~precise1 (using .../linux-headers-3.8.0-42-generic_3.8.0-42.63~precise1_amd64.deb) ...
Unpacking replacement linux-headers-3.8.0-42-generic ...
Preparing to replace php-pear 5.3.10-1ubuntu3.11 (using .../php-pear_5.3.10-1ubuntu3.13_all.deb) ...
Unpacking replacement php-pear ...
Preparing to replace php5 5.3.10-1ubuntu3.11 (using .../php5_5.3.10-1ubuntu3.13_all.deb) ...
Unpacking replacement php5 ...
Preparing to replace smbclient 2:3.6.3-2ubuntu2.10 (using .../smbclient_2%3a3.6.3-2ubuntu2.11_amd64.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common 2:3.6.3-2ubuntu2.10 (using .../samba-common_2%3a3.6.3-2ubuntu2.11_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace samba-common-bin 2:3.6.3-2ubuntu2.10 (using .../samba-common-bin_2%3a3.6.3-2ubuntu2.11_amd64.deb) ...
Unpacking replacement samba-common-bin ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
Setting up libc-dev-bin (2.15-0ubuntu10.6) ...
Setting up linux-libc-dev (3.2.0-67.101) ...
Setting up libc6-dev (2.15-0ubuntu10.6) ...
Setting up libapt-inst1.4 (0.8.16~exp12ubuntu10.17) ...
Setting up libdbus-1-3 (1.4.18-1ubuntu1.5) ...
Setting up libdrm2 (2.4.52-1~precise1) ...
Setting up libdrm-intel1 (2.4.52-1~precise1) ...
Setting up libdrm-nouveau1a (2.4.52-1~precise1) ...
Setting up libdrm-radeon1 (2.4.52-1~precise1) ...
Setting up apparmor (2.7.102-0ubuntu3.10) ...
 * Starting AppArmor profiles                                                                                                                                           Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                                                                                                                 [ OK ]
 * Reloading AppArmor profiles                                                                                                                                          Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                                                                                                                 [ OK ]
Setting up libkrb5support0 (1.10+dfsg~beta1-2ubuntu0.5) ...
Setting up libk5crypto3 (1.10+dfsg~beta1-2ubuntu0.5) ...
Setting up libkrb5-3 (1.10+dfsg~beta1-2ubuntu0.5) ...
Setting up libgssapi-krb5-2 (1.10+dfsg~beta1-2ubuntu0.5) ...
Setting up libparted0debian1 (2.3-8ubuntu5.2) ...
Setting up libtasn1-3 (2.10-1ubuntu1.2) ...
Setting up libxml2 (2.7.8.dfsg-5.1ubuntu4.9) ...
Setting up libjpeg-turbo8 (1.1.90+svn733-0ubuntu4.4) ...
Setting up liblzo2-2 (2.06-1ubuntu0.1) ...
Setting up libmysqlclient18 (5.5.38-0ubuntu0.12.04.1) ...
Setting up libwbclient0 (2:3.6.3-2ubuntu2.11) ...
Setting up mysql-client-core-5.5 (5.5.38-0ubuntu0.12.04.1) ...
Setting up mysql-client-5.5 (5.5.38-0ubuntu0.12.04.1) ...
Setting up mysql-server-core-5.5 (5.5.38-0ubuntu0.12.04.1) ...
Setting up mysql-server-5.5 (5.5.38-0ubuntu0.12.04.1) ...
mysql start/running, process 18156
Setting up mysql-server (5.5.38-0ubuntu0.12.04.1) ...
Setting up libmagic1 (5.09-2ubuntu0.4) ...
Setting up file (5.09-2ubuntu0.4) ...
Setting up php5-common (5.3.10-1ubuntu3.13) ...
Setting up apache2.2-bin (2.2.22-1ubuntu1.7) ...
Setting up apache2-utils (2.2.22-1ubuntu1.7) ...
Setting up apache2.2-common (2.2.22-1ubuntu1.7) ...
Setting up apache2-mpm-prefork (2.2.22-1ubuntu1.7) ...
 * Starting web server apache2                                                                                                                                          [Wed Aug 13 22:53:16 2014] [warn] module deflate_module is already loaded, skipping
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                                                                                 [ OK ]
Setting up libapache2-mod-php5 (5.3.10-1ubuntu3.13) ...
 * Reloading web server config apache2                                                                                                                                  [Wed Aug 13 22:53:18 2014] [warn] module deflate_module is already loaded, skipping
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                                                                                 [ OK ]
Setting up php5-cgi (5.3.10-1ubuntu3.13) ...
Setting up php5-cli (5.3.10-1ubuntu3.13) ...
Setting up php5-fpm (5.3.10-1ubuntu3.13) ...
Installing new version of config file /etc/php5/fpm/pool.d/www.conf ...
update-rc.d: warning: php5-fpm stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)
Setting up php5-curl (5.3.10-1ubuntu3.13) ...
Setting up php5-gd (5.3.10-1ubuntu3.13) ...
Setting up php5-intl (5.3.10-1ubuntu3.13) ...
Setting up php5-mysql (5.3.10-1ubuntu3.13) ...
Setting up php5-sqlite (5.3.10-1ubuntu3.13) ...
Setting up php5-dbg (5.3.10-1ubuntu3.13) ...
Setting up apache2 (2.2.22-1ubuntu1.7) ...
Setting up update-manager-core (1:0.156.14.17) ...
Setting up update-notifier-common (0.119ubuntu8.7) ...
Setting up apt-utils (0.8.16~exp12ubuntu10.17) ...
Setting up iproute (20111117-1ubuntu2.3) ...
Setting up ifupdown (0.7~beta2ubuntu11.1) ...
Installing new version of config file /etc/init/network-interface.conf ...
Setting up apt-transport-https (0.8.16~exp12ubuntu10.17) ...
Setting up dbus (1.4.18-1ubuntu1.5) ...
Setting up dmidecode (2.11-4ubuntu0.1) ...
Setting up krb5-locales (1.10+dfsg~beta1-2ubuntu0.5) ...
Setting up openssl (1.0.1-4ubuntu5.17) ...
Setting up parted (2.3-8ubuntu5.2) ...
Setting up uuid-runtime (2.20.1-1ubuntu3.1) ...
Setting up wget (1.13.4-2ubuntu1.1) ...
Setting up libdpkg-perl (1.16.1.2ubuntu7.5) ...
Setting up dpkg-dev (1.16.1.2ubuntu7.5) ...
Setting up grub-common (1.99-21ubuntu3.16) ...
Setting up grub2-common (1.99-21ubuntu3.16) ...
Setting up grub-pc-bin (1.99-21ubuntu3.16) ...
Setting up grub-pc (1.99-21ubuntu3.16) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-37-generic
Found initrd image: /boot/initrd.img-3.8.0-37-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found memtest86+ image: /memtest86+.bin
done
Setting up libssl-doc (1.0.1-4ubuntu5.17) ...
Setting up linux-firmware (1.79.16) ...
Setting up linux-generic-lts-raring (3.8.0.44.44) ...
Setting up linux-headers-3.8.0-42 (3.8.0-42.63~precise1) ...
Setting up linux-headers-3.8.0-42-generic (3.8.0-42.63~precise1) ...
Setting up php-pear (5.3.10-1ubuntu3.13) ...
Setting up php5 (5.3.10-1ubuntu3.13) ...
Setting up samba-common (2:3.6.3-2ubuntu2.11) ...
Setting up smbclient (2:3.6.3-2ubuntu2.11) ...
Setting up samba-common-bin (2:3.6.3-2ubuntu2.11) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
justin@ubuntu:/$
```


```
justin@ubuntu:/$ sudo apt-get -f install[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  shtool
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
justin@ubuntu:/$ 
```


```
justin@ubuntu:/$ sudo dpkg -C
justin@ubuntu:/$ 
```

---

### Post by Bashing-om on 2014-08-14
bphillips2; By Golly !

That do look good ! " I think you dood it " ..

one other thing now - not last nor least but do:
```

sudo apt-get dist-upgrade

```
to pick up and install these:
> 
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

"2 not upgraded"

left remaining is drupal7. ya want to remove it or (re-)install ?

[INDENT][INDENT]what does it take to keep
[INDENT][INDENT][INDENT]a dependency like you
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-14
Here's the output.

```
justin@ubuntu:~$ sudo apt-get dist-upgrade
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.8.0-44 linux-headers-3.8.0-44-generic linux-image-3.8.0-44-generic
The following packages will be upgraded:
  linux-headers-generic-lts-raring linux-image-generic-lts-raring
2 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 64.1 MB of archives.
After this operation, 252 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.8.0-44-generic amd64 3.8.0-44.66~precise1 [50.9 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.8.0-44 all 3.8.0-44.66~precise1 [12.2 MB]                                              
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.8.0-44-generic amd64 3.8.0-44.66~precise1 [1,002 kB]                                   
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic-lts-raring amd64 3.8.0.44.44 [2,376 B]                                           
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-generic-lts-raring amd64 3.8.0.44.44 [2,380 B]                                             
Fetched 64.1 MB in 4min 31s (236 kB/s)                                                                                                                                 
Selecting previously unselected package linux-image-3.8.0-44-generic.
(Reading database ... 190041 files and directories currently installed.)
Unpacking linux-image-3.8.0-44-generic (from .../linux-image-3.8.0-44-generic_3.8.0-44.66~precise1_amd64.deb) ...
Done.
Selecting previously unselected package linux-headers-3.8.0-44.
Unpacking linux-headers-3.8.0-44 (from .../linux-headers-3.8.0-44_3.8.0-44.66~precise1_all.deb) ...
Selecting previously unselected package linux-headers-3.8.0-44-generic.
Unpacking linux-headers-3.8.0-44-generic (from .../linux-headers-3.8.0-44-generic_3.8.0-44.66~precise1_amd64.deb) ...
Preparing to replace linux-headers-generic-lts-raring 3.8.0.41.41 (using .../linux-headers-generic-lts-raring_3.8.0.44.44_amd64.deb) ...
Unpacking replacement linux-headers-generic-lts-raring ...
Preparing to replace linux-image-generic-lts-raring 3.8.0.37.37 (using .../linux-image-generic-lts-raring_3.8.0.44.44_amd64.deb) ...
Unpacking replacement linux-image-generic-lts-raring ...
Setting up linux-image-3.8.0-44-generic (3.8.0-44.66~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-44-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found initrd image: /boot/initrd.img-3.8.0-44-generic
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-37-generic
Found initrd image: /boot/initrd.img-3.8.0-37-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-headers-3.8.0-44 (3.8.0-44.66~precise1) ...
Setting up linux-headers-3.8.0-44-generic (3.8.0-44.66~precise1) ...
Setting up linux-headers-generic-lts-raring (3.8.0.44.44) ...
Setting up linux-image-generic-lts-raring (3.8.0.44.44) ...
justin@ubuntu:~$ 
```

I'm all for removing Drupal if it is fairly easy and you have the time to help.

---

### Post by Bashing-om on 2014-08-14
bphillips2; wiping the sweat off;

Yeah, we will attend to that (drupal7)..
Next though that requires attention is get you off that now End_Of_Life kernel and up on the current kernel.
I have reached the point of forced/unreliable thinking for this session. Will pick this up on our morrow,
as there are factors to clear up before making the attempt.


[INDENT][INDENT]but hey
[INDENT][INDENT][INDENT]look'n good
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-14
Sounds good.  Thanks so much for the help.  I can't begin to express how much I appreciate it!

---

### Post by Bashing-om on 2014-08-14
bphillips2; Morning,

And back to it ...
> 
 Thanks so much for the help. I can't begin to express how much I appreciate it!

I enjoy a good puzzle, and solving these puzzles sure beats doing jig-saw puzzles ! and besides - paying it forward, you too one day will do the same.

To our situation at hand, let's look now at what it will take to get you off the 3.8 kernel, maybe easy. maybe not:
As you are running release 12.04.4 and with kernel "linux-image-3.8.0-44-generic" I expect that the HardWare Enablement stack is in effect.
Look'n to see, post back:
```

hwe-support-status --verbose
ls -al /usr/bin/hwe-support-status
hwe-support-status --show-all-unsupported
hwe-support-status --show-replacements

```
so we do not do any
[INDENT][INDENT][INDENT]leaps of faith
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-14
```
justin@ubuntu:~$ hwe-support-status --verbose

Your current Hardware Enablement Stack (HWE) is no longer supported
since 2014-08-07.  Security updates for critical parts (kernel
and graphics stack) of your system are no longer available.


For more information, please see:
http://wiki.ubuntu.com/1204_HWE_EOL


To upgrade to a supported (or longer supported) configuration:


* Upgrade from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS by running:
sudo do-release-upgrade 


OR


* Install a newer HWE version by running:
sudo apt-get install linux-generic-lts-trusty linux-image-generic-lts-trusty


and reboot your system.
justin@ubuntu:~$ 

```
```



justin@ubuntu:~$ ls -al /usr/bin/hwe-support-status
-rwxr-xr-x 1 root root 9429 Jul 30 11:15 /usr/bin/hwe-support-status
justin@ubuntu:~$ 



```
```



justin@ubuntu:~$ hwe-support-status --show-all-unsupported
linux-headers-3.8.0-42 linux-headers-3.8.0-39-generic 
linux-image-3.8.0-36-generic linux-headers-3.8.0-36-generic 
linux-image-generic-lts-raring linux-headers-3.8.0-41 
linux-image-3.8.0-37-generic linux-headers-3.8.0-38 
linux-image-3.8.0-44-generic linux-generic-lts-raring 
linux-headers-3.8.0-39 linux-headers-3.8.0-37-generic 
linux-headers-3.8.0-44-generic linux-headers-3.8.0-42-generic 
linux-headers-3.8.0-41-generic linux-headers-3.8.0-38-generic 
linux-headers-3.8.0-44 linux-headers-3.8.0-37 
linux-headers-generic-lts-raring linux-image-3.8.0-38-generic 
linux-headers-3.8.0-36 


justin@ubuntu:~$ 



```
```



justin@ubuntu:~$ hwe-support-status --show-replacements
linux-generic-lts-trusty linux-image-generic-lts-trusty
justin@ubuntu:~$
```

---

### Post by Bashing-om on 2014-08-14
bphillips2; Great !

Looking good, should be a cinch to upgrade the kernel.
I prefer going a couple of steps further than that of the advisory, do:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty

``` to make sure that the xserver is compatible with that new kernel, and as well updated open source graphics drivers are available.
Yeah, do the update/upgrade routine again. Things change rapidly, and new updates may be available since last run. cheap insurance.

Reboot  and now show us what is:
```

lsb_release -a
uname -r
dpkg -l | grep linux-
sudo apt-get -f install

```

and hopefully
[INDENT][INDENT][INDENT]we proceed on our merry way -> drupal7 
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-14
Here are all the outputs

```
justin@ubuntu:~$ sudo apt-get update[sudo] password for justin: 
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]       
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                          
Hit http://us.archive.ubuntu.com precise Release                             
Get:2 http://us.archive.ubuntu.com precise-updates Release [98.7 kB]
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]         
Get:4 http://security.ubuntu.com precise-security Release [50.7 kB] 
Hit http://us.archive.ubuntu.com precise-backports Release        
Hit http://us.archive.ubuntu.com precise/main Sources                             
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main amd64 Packages
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:5 http://us.archive.ubuntu.com precise-updates/main Sources [477 kB]
Get:6 http://security.ubuntu.com precise-security/main Sources [108 kB]
Get:7 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:8 http://us.archive.ubuntu.com precise-updates/universe Sources [110 kB]
Get:9 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]        
Get:10 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [825 kB]     
Get:11 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]         
Get:12 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]   
Get:13 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B]           
Get:14 http://security.ubuntu.com precise-security/main amd64 Packages [416 kB]            
Get:15 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [13.7 kB]   
Get:16 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [247 kB]         
Get:17 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]    
Get:18 http://us.archive.ubuntu.com precise-updates/main i386 Packages [855 kB]              
Get:19 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]     
Get:20 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]          
Get:21 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]   
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex                       
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex     
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/main Sources                  
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources            
Hit http://us.archive.ubuntu.com precise-backports/universe Sources              
Get:22 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:23 http://security.ubuntu.com precise-security/universe amd64 Packages [96.7 kB]
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources             
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages            
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages       
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages         
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages       
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages              
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages        
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en                       
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                 
Get:24 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,451 B]
Get:25 http://security.ubuntu.com precise-security/main i386 Packages [444 kB]    
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en              
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en          
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en      
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en      
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en       
Get:26 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:27 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]
Get:28 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]
Get:29 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:30 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:31 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:32 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:33 http://security.ubuntu.com precise-security/main Translation-en [190 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 4,400 kB in 2s (1,491 kB/s)
Reading package lists... Done



```
```





justin@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```
```

justin@ubuntu:~$ sudo apt-get install linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  shtool
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdrm-nouveau2 libegl1-mesa-drivers-lts-trusty libegl1-mesa-lts-trusty libfontenc1 libgbm1-lts-trusty libgl1-mesa-dri-lts-trusty libglamor-ltst0
  libglapi-mesa-lts-trusty libice6 libllvm3.4 libmtdev1 libopenvg1-mesa-lts-trusty libpixman-1-0 libsm6 libtxc-dxtn-s2tc0 libwayland-egl1-mesa-lts-trusty
  libwayland-ltst-client0 libwayland-ltst-server0 libx11-xcb1 libxatracker2-lts-trusty libxaw7 libxcb-dri2-0 libxcb-glx0 libxcb-util0 libxcb-xfixes0 libxcursor1
  libxdamage1 libxfixes3 libxfont1 libxi6 libxinerama1 libxkbfile1 libxmu6 libxrandr-ltst2 libxrandr2 libxrender1 libxt6 libxv1 libxvmc1 libxxf86vm1
  linux-headers-3.13.0-34 linux-headers-3.13.0-34-generic linux-headers-generic-lts-trusty linux-image-3.13.0-34-generic x11-common x11-xkb-utils x11-xserver-utils
  x11-xserver-utils-lts-trusty xfonts-base xfonts-encodings xfonts-utils xserver-common xserver-common-lts-trusty xserver-xorg-core-lts-trusty
  xserver-xorg-input-all-lts-trusty xserver-xorg-input-evdev-lts-trusty xserver-xorg-input-mouse-lts-trusty xserver-xorg-input-synaptics-lts-trusty
  xserver-xorg-input-vmmouse-lts-trusty xserver-xorg-input-wacom-lts-trusty xserver-xorg-video-all-lts-trusty xserver-xorg-video-ati-lts-trusty
  xserver-xorg-video-cirrus-lts-trusty xserver-xorg-video-fbdev-lts-trusty xserver-xorg-video-glamoregl-lts-trusty xserver-xorg-video-intel-lts-trusty
  xserver-xorg-video-mach64-lts-trusty xserver-xorg-video-mga-lts-trusty xserver-xorg-video-modesetting-lts-trusty xserver-xorg-video-neomagic-lts-trusty
  xserver-xorg-video-nouveau-lts-trusty xserver-xorg-video-openchrome-lts-trusty xserver-xorg-video-r128-lts-trusty xserver-xorg-video-radeon-lts-trusty
  xserver-xorg-video-s3-lts-trusty xserver-xorg-video-savage-lts-trusty xserver-xorg-video-siliconmotion-lts-trusty xserver-xorg-video-sis-lts-trusty
  xserver-xorg-video-sisusb-lts-trusty xserver-xorg-video-tdfx-lts-trusty xserver-xorg-video-trident-lts-trusty xserver-xorg-video-vesa-lts-trusty
  xserver-xorg-video-vmware-lts-trusty
Suggested packages:
  libglide3 fdutils linux-lts-trusty-doc-3.13.0 linux-lts-trusty-source-3.13.0 linux-lts-trusty-tools nickle cairo-5c xorg-docs-core xfs xserver xfonts-100dpi
  xfonts-75dpi xfonts-scalable gpointing-device-settings touchfreeze xinput firmware-linux
The following NEW packages will be installed:
  libdrm-nouveau2 libegl1-mesa-drivers-lts-trusty libegl1-mesa-lts-trusty libfontenc1 libgbm1-lts-trusty libgl1-mesa-dri-lts-trusty libgl1-mesa-glx-lts-trusty
  libglamor-ltst0 libglapi-mesa-lts-trusty libice6 libllvm3.4 libmtdev1 libopenvg1-mesa-lts-trusty libpixman-1-0 libsm6 libtxc-dxtn-s2tc0
  libwayland-egl1-mesa-lts-trusty libwayland-ltst-client0 libwayland-ltst-server0 libx11-xcb1 libxatracker2-lts-trusty libxaw7 libxcb-dri2-0 libxcb-glx0 libxcb-util0
  libxcb-xfixes0 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxi6 libxinerama1 libxkbfile1 libxmu6 libxrandr-ltst2 libxrandr2 libxrender1 libxt6 libxv1 libxvmc1
  libxxf86vm1 linux-generic-lts-trusty linux-headers-3.13.0-34 linux-headers-3.13.0-34-generic linux-headers-generic-lts-trusty linux-image-3.13.0-34-generic
  linux-image-generic-lts-trusty x11-common x11-xkb-utils x11-xserver-utils x11-xserver-utils-lts-trusty xfonts-base xfonts-encodings xfonts-utils xserver-common
  xserver-common-lts-trusty xserver-xorg-core-lts-trusty xserver-xorg-input-all-lts-trusty xserver-xorg-input-evdev-lts-trusty xserver-xorg-input-mouse-lts-trusty
  xserver-xorg-input-synaptics-lts-trusty xserver-xorg-input-vmmouse-lts-trusty xserver-xorg-input-wacom-lts-trusty xserver-xorg-lts-trusty
  xserver-xorg-video-all-lts-trusty xserver-xorg-video-ati-lts-trusty xserver-xorg-video-cirrus-lts-trusty xserver-xorg-video-fbdev-lts-trusty
  xserver-xorg-video-glamoregl-lts-trusty xserver-xorg-video-intel-lts-trusty xserver-xorg-video-mach64-lts-trusty xserver-xorg-video-mga-lts-trusty
  xserver-xorg-video-modesetting-lts-trusty xserver-xorg-video-neomagic-lts-trusty xserver-xorg-video-nouveau-lts-trusty xserver-xorg-video-openchrome-lts-trusty
  xserver-xorg-video-r128-lts-trusty xserver-xorg-video-radeon-lts-trusty xserver-xorg-video-s3-lts-trusty xserver-xorg-video-savage-lts-trusty
  xserver-xorg-video-siliconmotion-lts-trusty xserver-xorg-video-sis-lts-trusty xserver-xorg-video-sisusb-lts-trusty xserver-xorg-video-tdfx-lts-trusty
  xserver-xorg-video-trident-lts-trusty xserver-xorg-video-vesa-lts-trusty xserver-xorg-video-vmware-lts-trusty
0 upgraded, 87 newly installed, 0 to remove and 0 not upgraded.
Need to get 96.2 MB of archives.
After this operation, 376 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-nouveau2 amd64 2.4.52-1~precise1 [15.3 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libllvm3.4 amd64 1:3.4-1ubuntu3~precise1 [9,667 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgl1-mesa-dri-lts-trusty amd64 10.1.3-0ubuntu0.1~precise1 [4,907 kB]                                 
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libwayland-ltst-client0 amd64 1.4.0-1ubuntu1~precise1 [25.3 kB]                                        
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libwayland-ltst-server0 amd64 1.4.0-1ubuntu1~precise1 [31.4 kB]                                        
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-dri2-0 amd64 1.8.1-1ubuntu0.2 [7,486 B]                                                         
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgbm1-lts-trusty amd64 10.1.3-0ubuntu0.1~precise1 [19.3 kB]                                          
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libx11-xcb1 amd64 2:1.4.99.1-0ubuntu2.2 [10.5 kB]                                                      
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-xfixes0 amd64 1.8.1-1ubuntu0.2 [9,524 B]                                                        
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libegl1-mesa-lts-trusty amd64 10.1.3-0ubuntu0.1~precise1 [58.6 kB]                                    
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libglapi-mesa-lts-trusty amd64 10.1.3-0ubuntu0.1~precise1 [21.4 kB]                                   
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libopenvg1-mesa-lts-trusty amd64 10.1.3-0ubuntu0.1~precise1 [13.0 kB]                                 
Get:13 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxfixes3 amd64 1:5.0-4ubuntu4.2 [12.5 kB]                                                           
Get:14 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libwayland-egl1-mesa-lts-trusty amd64 10.1.3-0ubuntu0.1~precise1 [6,506 B]                            
Get:15 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libegl1-mesa-drivers-lts-trusty amd64 10.1.3-0ubuntu0.1~precise1 [1,994 kB]                           
Get:16 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-glx0 amd64 1.8.1-1ubuntu0.2 [26.4 kB]                                                          
Get:17 http://us.archive.ubuntu.com/ubuntu/ precise/main libxdamage1 amd64 1:1.1.3-2build1 [7,560 B]                                                                   
Get:18 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxxf86vm1 amd64 1:1.1.1-2ubuntu0.1 [11.9 kB]                                                        
Get:19 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgl1-mesa-glx-lts-trusty amd64 10.1.3-0ubuntu0.1~precise1 [109 kB]                                  
Get:20 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libglamor-ltst0 amd64 0.6.0-0ubuntu4~precise1 [101 kB]                                                
Get:21 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main x11-common all 1:7.6+12ubuntu2 [52.0 kB]                                                              
Get:22 http://us.archive.ubuntu.com/ubuntu/ precise/main libice6 amd64 2:1.0.7-2build1 [46.1 kB]                                                                       
Get:23 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libpixman-1-0 amd64 0.30.2-1ubuntu0.0.0.0.1 [256 kB]                                                  
Get:24 http://us.archive.ubuntu.com/ubuntu/ precise/main libsm6 amd64 2:1.2.0-2build1 [18.1 kB]                                                                        
Get:25 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxatracker2-lts-trusty amd64 10.1.3-0ubuntu0.1~precise1 [157 kB]                                    
Get:26 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxt6 amd64 1:1.1.1-2ubuntu0.1 [186 kB]                                                              
Get:27 http://us.archive.ubuntu.com/ubuntu/ precise/main libxmu6 amd64 2:1.1.0-3 [52.7 kB]                                                                             
Get:28 http://us.archive.ubuntu.com/ubuntu/ precise/main libxaw7 amd64 2:1.0.9-3ubuntu1 [201 kB]                                                                       
Get:29 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxrender1 amd64 1:0.9.6-2ubuntu0.1 [20.6 kB]                                                        
Get:30 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcursor1 amd64 1:1.1.12-1ubuntu0.1 [22.7 kB]                                                       
Get:31 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxi6 amd64 2:1.7.1.901-1ubuntu1~precise1 [31.6 kB]                                                  
Get:32 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxinerama1 amd64 2:1.1.1-3ubuntu0.1 [8,072 B]                                                       
Get:33 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxkbfile1 amd64 1:1.0.7-1ubuntu0.1 [73.8 kB]                                                        
Get:34 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxrandr-ltst2 amd64 2:1.4.2-1~precise1 [19.2 kB]                                                    
Get:35 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxrandr2 amd64 2:1.3.2-2ubuntu0.2 [17.5 kB]                                                         
Get:36 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxv1 amd64 2:1.0.6-2ubuntu0.1 [12.4 kB]                                                             
Get:37 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.13.0-34-generic amd64 3.13.0-34.60~precise1 [52.4 MB]                                   
Get:38 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libtxc-dxtn-s2tc0 amd64 0~git20110809-2.1 [56.9 kB]                                                   
Get:39 http://us.archive.ubuntu.com/ubuntu/ precise/main libxcb-util0 amd64 0.3.8-2 [13.5 kB]                                                                          
Get:40 http://us.archive.ubuntu.com/ubuntu/ precise/main libfontenc1 amd64 1:1.1.0-1 [15.4 kB]                                                                         
Get:41 http://us.archive.ubuntu.com/ubuntu/ precise/main libmtdev1 amd64 1.1.0-2ubuntu1 [15.4 kB]                                                                      
Get:42 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxfont1 amd64 1:1.4.4-1ubuntu0.2 [134 kB]                                                           
Get:43 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxvmc1 amd64 2:1.0.6-1ubuntu2.1 [15.9 kB]                                                           
Get:44 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-generic-lts-trusty amd64 3.13.0.34.30 [2,502 B]                                           
Get:45 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.13.0-34 all 3.13.0-34.60~precise1 [12.9 MB]                                           
Get:46 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.13.0-34-generic amd64 3.13.0-34.60~precise1 [1,124 kB]                                
Get:47 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic-lts-trusty amd64 3.13.0.34.30 [2,492 B]                                         
Get:48 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-generic-lts-trusty amd64 3.13.0.34.30 [1,750 B]                                                 
Get:49 http://us.archive.ubuntu.com/ubuntu/ precise/main x11-xkb-utils amd64 7.6+4 [196 kB]                                                                            
Get:50 http://us.archive.ubuntu.com/ubuntu/ precise/main x11-xserver-utils amd64 7.6+3 [182 kB]                                                                        
Get:51 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main x11-xserver-utils-lts-trusty amd64 7.7+2ubuntu1~precise1 [33.5 kB]                                    
Get:52 http://us.archive.ubuntu.com/ubuntu/ precise/main xfonts-encodings all 1:1.0.4-1ubuntu1 [583 kB]                                                                
Get:53 http://us.archive.ubuntu.com/ubuntu/ precise/main xfonts-utils amd64 1:7.6+1 [96.4 kB]                                                                          
Get:54 http://us.archive.ubuntu.com/ubuntu/ precise/main xfonts-base all 1:1.0.3 [6,180 kB]                                                                            
Get:55 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-common all 2:1.11.4-0ubuntu10.14 [31.8 kB]                                                    
Get:56 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-common-lts-trusty all 2:1.15.1-0ubuntu2~precise2 [22.2 kB]                                    
Get:57 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-core-lts-trusty amd64 2:1.15.1-0ubuntu2~precise2 [1,560 kB]                              
Get:58 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-input-evdev-lts-trusty amd64 1:2.8.2-1ubuntu2~precise1 [34.3 kB]                         
Get:59 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-input-synaptics-lts-trusty amd64 1.7.4-0ubuntu1~precise2 [67.9 kB]                       
Get:60 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-input-mouse-lts-trusty amd64 1:1.9.0-1build1~precise1 [41.2 kB]                          
Get:61 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-input-vmmouse-lts-trusty amd64 1:13.0.0-1build1~precise1 [15.2 kB]                       
Get:62 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-input-wacom-lts-trusty amd64 1:0.23.0-0ubuntu2~precise1 [93.0 kB]                        
Get:63 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-input-all-lts-trusty amd64 1:7.7+1ubuntu8~precise1 [4,760 B]                             
Get:64 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-glamoregl-lts-trusty amd64 0.6.0-0ubuntu4~precise1 [9,670 B]                       
Get:65 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-r128-lts-trusty amd64 6.9.2-1build1~precise1 [56.6 kB]                             
Get:66 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-mach64-lts-trusty amd64 6.9.4-1build1~precise1 [78.8 kB]                           
Get:67 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-radeon-lts-trusty amd64 1:7.3.0-1ubuntu3.1~precise1 [165 kB]                       
Get:68 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-ati-lts-trusty amd64 1:7.3.0-1ubuntu3.1~precise1 [7,448 B]                         
Get:69 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-cirrus-lts-trusty amd64 1:1.5.2-1build1~precise1 [34.4 kB]                         
Get:70 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-fbdev-lts-trusty amd64 1:0.4.4-1build1~precise1 [13.5 kB]                          
Get:71 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-intel-lts-trusty amd64 2:2.99.910-0ubuntu1~precise1 [770 kB]                       
Get:72 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-mga-lts-trusty amd64 1:1.6.3-1build1~precise1 [73.5 kB]                            
Get:73 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-modesetting-lts-trusty amd64 0.8.1-1build1~precise1 [23.5 kB]                      
Get:74 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-neomagic-lts-trusty amd64 1:1.2.8-1build1~precise1 [33.5 kB]                       
Get:75 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-nouveau-lts-trusty amd64 1:1.0.10-1ubuntu2~precise1 [93.3 kB]                      
Get:76 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-openchrome-lts-trusty amd64 1:0.3.3-1build1~precise1 [177 kB]                      
Get:77 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-s3-lts-trusty amd64 1:0.6.5-0ubuntu4~precise1 [33.3 kB]                            
Get:78 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-savage-lts-trusty amd64 1:2.3.7-2ubuntu2~precise1 [69.7 kB]                        
Get:79 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-siliconmotion-lts-trusty amd64 1:1.7.7-2build1~precise1 [55.9 kB]                  
Get:80 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-sis-lts-trusty amd64 1:0.10.7-0ubuntu6~precise1 [263 kB]                           
Get:81 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-sisusb-lts-trusty amd64 1:0.9.6-2build1~precise1 [41.8 kB]                         
Get:82 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-tdfx-lts-trusty amd64 1:1.4.5-1build1~precise1 [33.5 kB]                           
Get:83 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-trident-lts-trusty amd64 1:1.3.6-0ubuntu5~precise1 [62.0 kB]                       
Get:84 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-vesa-lts-trusty amd64 1:2.3.3-1build1~precise1 [16.5 kB]                           
Get:85 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-vmware-lts-trusty amd64 1:13.0.2-2ubuntu1~precise1 [78.6 kB]                       
Get:86 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-all-lts-trusty amd64 1:7.7+1ubuntu8~precise1 [4,846 B]                             
Get:87 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-lts-trusty amd64 1:7.7+1ubuntu8~precise1 [17.4 kB]                                       
Fetched 96.2 MB in 2min 52s (557 kB/s)                                                                                                                                 
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously unselected package libdrm-nouveau2.
(Reading database ... 218297 files and directories currently installed.)
Unpacking libdrm-nouveau2 (from .../libdrm-nouveau2_2.4.52-1~precise1_amd64.deb) ...
Selecting previously unselected package libllvm3.4.
Unpacking libllvm3.4 (from .../libllvm3.4_1%3a3.4-1ubuntu3~precise1_amd64.deb) ...
Selecting previously unselected package libgl1-mesa-dri-lts-trusty.
Unpacking libgl1-mesa-dri-lts-trusty (from .../libgl1-mesa-dri-lts-trusty_10.1.3-0ubuntu0.1~precise1_amd64.deb) ...
Selecting previously unselected package libwayland-ltst-client0.
Unpacking libwayland-ltst-client0 (from .../libwayland-ltst-client0_1.4.0-1ubuntu1~precise1_amd64.deb) ...
Selecting previously unselected package libwayland-ltst-server0.
Unpacking libwayland-ltst-server0 (from .../libwayland-ltst-server0_1.4.0-1ubuntu1~precise1_amd64.deb) ...
Selecting previously unselected package libxcb-dri2-0.
Unpacking libxcb-dri2-0 (from .../libxcb-dri2-0_1.8.1-1ubuntu0.2_amd64.deb) ...
Selecting previously unselected package libgbm1-lts-trusty.
Unpacking libgbm1-lts-trusty (from .../libgbm1-lts-trusty_10.1.3-0ubuntu0.1~precise1_amd64.deb) ...
Selecting previously unselected package libx11-xcb1.
Unpacking libx11-xcb1 (from .../libx11-xcb1_2%3a1.4.99.1-0ubuntu2.2_amd64.deb) ...
Selecting previously unselected package libxcb-xfixes0.
Unpacking libxcb-xfixes0 (from .../libxcb-xfixes0_1.8.1-1ubuntu0.2_amd64.deb) ...
Selecting previously unselected package libegl1-mesa-lts-trusty.
Unpacking libegl1-mesa-lts-trusty (from .../libegl1-mesa-lts-trusty_10.1.3-0ubuntu0.1~precise1_amd64.deb) ...
Selecting previously unselected package libglapi-mesa-lts-trusty.
Unpacking libglapi-mesa-lts-trusty (from .../libglapi-mesa-lts-trusty_10.1.3-0ubuntu0.1~precise1_amd64.deb) ...
Selecting previously unselected package libopenvg1-mesa-lts-trusty.
Unpacking libopenvg1-mesa-lts-trusty (from .../libopenvg1-mesa-lts-trusty_10.1.3-0ubuntu0.1~precise1_amd64.deb) ...
Selecting previously unselected package libxfixes3.
Unpacking libxfixes3 (from .../libxfixes3_1%3a5.0-4ubuntu4.2_amd64.deb) ...
Selecting previously unselected package libwayland-egl1-mesa-lts-trusty.
Unpacking libwayland-egl1-mesa-lts-trusty (from .../libwayland-egl1-mesa-lts-trusty_10.1.3-0ubuntu0.1~precise1_amd64.deb) ...
Selecting previously unselected package libegl1-mesa-drivers-lts-trusty.
Unpacking libegl1-mesa-drivers-lts-trusty (from .../libegl1-mesa-drivers-lts-trusty_10.1.3-0ubuntu0.1~precise1_amd64.deb) ...
Selecting previously unselected package libxcb-glx0.
Unpacking libxcb-glx0 (from .../libxcb-glx0_1.8.1-1ubuntu0.2_amd64.deb) ...
Selecting previously unselected package libxdamage1.
Unpacking libxdamage1 (from .../libxdamage1_1%3a1.1.3-2build1_amd64.deb) ...
Selecting previously unselected package libxxf86vm1.
Unpacking libxxf86vm1 (from .../libxxf86vm1_1%3a1.1.1-2ubuntu0.1_amd64.deb) ...
Selecting previously unselected package libgl1-mesa-glx-lts-trusty.
Unpacking libgl1-mesa-glx-lts-trusty (from .../libgl1-mesa-glx-lts-trusty_10.1.3-0ubuntu0.1~precise1_amd64.deb) ...
Selecting previously unselected package libglamor-ltst0.
Unpacking libglamor-ltst0 (from .../libglamor-ltst0_0.6.0-0ubuntu4~precise1_amd64.deb) ...
Selecting previously unselected package x11-common.
Unpacking x11-common (from .../x11-common_1%3a7.6+12ubuntu2_all.deb) ...
Selecting previously unselected package libice6.
Unpacking libice6 (from .../libice6_2%3a1.0.7-2build1_amd64.deb) ...
Selecting previously unselected package libpixman-1-0.
Unpacking libpixman-1-0 (from .../libpixman-1-0_0.30.2-1ubuntu0.0.0.0.1_amd64.deb) ...
Selecting previously unselected package libsm6.
Unpacking libsm6 (from .../libsm6_2%3a1.2.0-2build1_amd64.deb) ...
Selecting previously unselected package libxatracker2-lts-trusty.
Unpacking libxatracker2-lts-trusty (from .../libxatracker2-lts-trusty_10.1.3-0ubuntu0.1~precise1_amd64.deb) ...
Selecting previously unselected package libxt6.
Unpacking libxt6 (from .../libxt6_1%3a1.1.1-2ubuntu0.1_amd64.deb) ...
Selecting previously unselected package libxmu6.
Unpacking libxmu6 (from .../libxmu6_2%3a1.1.0-3_amd64.deb) ...
Selecting previously unselected package libxaw7.
Unpacking libxaw7 (from .../libxaw7_2%3a1.0.9-3ubuntu1_amd64.deb) ...
Selecting previously unselected package libxrender1.
Unpacking libxrender1 (from .../libxrender1_1%3a0.9.6-2ubuntu0.1_amd64.deb) ...
Selecting previously unselected package libxcursor1.
Unpacking libxcursor1 (from .../libxcursor1_1%3a1.1.12-1ubuntu0.1_amd64.deb) ...
Selecting previously unselected package libxi6.
Unpacking libxi6 (from .../libxi6_2%3a1.7.1.901-1ubuntu1~precise1_amd64.deb) ...
Selecting previously unselected package libxinerama1.
Unpacking libxinerama1 (from .../libxinerama1_2%3a1.1.1-3ubuntu0.1_amd64.deb) ...
Selecting previously unselected package libxkbfile1.
Unpacking libxkbfile1 (from .../libxkbfile1_1%3a1.0.7-1ubuntu0.1_amd64.deb) ...
Selecting previously unselected package libxrandr-ltst2.
Unpacking libxrandr-ltst2 (from .../libxrandr-ltst2_2%3a1.4.2-1~precise1_amd64.deb) ...
Selecting previously unselected package libxrandr2.
Unpacking libxrandr2 (from .../libxrandr2_2%3a1.3.2-2ubuntu0.2_amd64.deb) ...
Selecting previously unselected package libxv1.
Unpacking libxv1 (from .../libxv1_2%3a1.0.6-2ubuntu0.1_amd64.deb) ...
Selecting previously unselected package linux-image-3.13.0-34-generic.
Unpacking linux-image-3.13.0-34-generic (from .../linux-image-3.13.0-34-generic_3.13.0-34.60~precise1_amd64.deb) ...
Done.
Selecting previously unselected package libtxc-dxtn-s2tc0.
Unpacking libtxc-dxtn-s2tc0 (from .../libtxc-dxtn-s2tc0_0~git20110809-2.1_amd64.deb) ...
Selecting previously unselected package libxcb-util0.
Unpacking libxcb-util0 (from .../libxcb-util0_0.3.8-2_amd64.deb) ...
Selecting previously unselected package libfontenc1.
Unpacking libfontenc1 (from .../libfontenc1_1%3a1.1.0-1_amd64.deb) ...
Selecting previously unselected package libmtdev1.
Unpacking libmtdev1 (from .../libmtdev1_1.1.0-2ubuntu1_amd64.deb) ...
Selecting previously unselected package libxfont1.
Unpacking libxfont1 (from .../libxfont1_1%3a1.4.4-1ubuntu0.2_amd64.deb) ...
Selecting previously unselected package libxvmc1.
Unpacking libxvmc1 (from .../libxvmc1_2%3a1.0.6-1ubuntu2.1_amd64.deb) ...
Selecting previously unselected package linux-image-generic-lts-trusty.
Unpacking linux-image-generic-lts-trusty (from .../linux-image-generic-lts-trusty_3.13.0.34.30_amd64.deb) ...
Selecting previously unselected package linux-headers-3.13.0-34.
Unpacking linux-headers-3.13.0-34 (from .../linux-headers-3.13.0-34_3.13.0-34.60~precise1_all.deb) ...
Selecting previously unselected package linux-headers-3.13.0-34-generic.
Unpacking linux-headers-3.13.0-34-generic (from .../linux-headers-3.13.0-34-generic_3.13.0-34.60~precise1_amd64.deb) ...
Selecting previously unselected package linux-headers-generic-lts-trusty.
Unpacking linux-headers-generic-lts-trusty (from .../linux-headers-generic-lts-trusty_3.13.0.34.30_amd64.deb) ...
Selecting previously unselected package linux-generic-lts-trusty.
Unpacking linux-generic-lts-trusty (from .../linux-generic-lts-trusty_3.13.0.34.30_amd64.deb) ...
Selecting previously unselected package x11-xkb-utils.
Unpacking x11-xkb-utils (from .../x11-xkb-utils_7.6+4_amd64.deb) ...
Selecting previously unselected package x11-xserver-utils.
Unpacking x11-xserver-utils (from .../x11-xserver-utils_7.6+3_amd64.deb) ...
Selecting previously unselected package x11-xserver-utils-lts-trusty.
Unpacking x11-xserver-utils-lts-trusty (from .../x11-xserver-utils-lts-trusty_7.7+2ubuntu1~precise1_amd64.deb) ...
Adding 'diversion of /usr/bin/xrandr to /usr/bin/xrandr.orig by x11-xserver-utils-lts-trusty'
Selecting previously unselected package xfonts-encodings.
Unpacking xfonts-encodings (from .../xfonts-encodings_1%3a1.0.4-1ubuntu1_all.deb) ...
Selecting previously unselected package xfonts-utils.
Unpacking xfonts-utils (from .../xfonts-utils_1%3a7.6+1_amd64.deb) ...
Selecting previously unselected package xfonts-base.
Unpacking xfonts-base (from .../xfonts-base_1%3a1.0.3_all.deb) ...
Selecting previously unselected package xserver-common.
Unpacking xserver-common (from .../xserver-common_2%3a1.11.4-0ubuntu10.14_all.deb) ...
Selecting previously unselected package xserver-common-lts-trusty.
Unpacking xserver-common-lts-trusty (from .../xserver-common-lts-trusty_2%3a1.15.1-0ubuntu2~precise2_all.deb) ...
Adding 'diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-trusty'
Selecting previously unselected package xserver-xorg-core-lts-trusty.
Unpacking xserver-xorg-core-lts-trusty (from .../xserver-xorg-core-lts-trusty_2%3a1.15.1-0ubuntu2~precise2_amd64.deb) ...
Selecting previously unselected package xserver-xorg-input-evdev-lts-trusty.
Unpacking xserver-xorg-input-evdev-lts-trusty (from .../xserver-xorg-input-evdev-lts-trusty_1%3a2.8.2-1ubuntu2~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-input-synaptics-lts-trusty.
Unpacking xserver-xorg-input-synaptics-lts-trusty (from .../xserver-xorg-input-synaptics-lts-trusty_1.7.4-0ubuntu1~precise2_amd64.deb) ...
Selecting previously unselected package xserver-xorg-input-mouse-lts-trusty.
Unpacking xserver-xorg-input-mouse-lts-trusty (from .../xserver-xorg-input-mouse-lts-trusty_1%3a1.9.0-1build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-input-vmmouse-lts-trusty.
Unpacking xserver-xorg-input-vmmouse-lts-trusty (from .../xserver-xorg-input-vmmouse-lts-trusty_1%3a13.0.0-1build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-input-wacom-lts-trusty.
Unpacking xserver-xorg-input-wacom-lts-trusty (from .../xserver-xorg-input-wacom-lts-trusty_1%3a0.23.0-0ubuntu2~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-input-all-lts-trusty.
Unpacking xserver-xorg-input-all-lts-trusty (from .../xserver-xorg-input-all-lts-trusty_1%3a7.7+1ubuntu8~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-glamoregl-lts-trusty.
Unpacking xserver-xorg-video-glamoregl-lts-trusty (from .../xserver-xorg-video-glamoregl-lts-trusty_0.6.0-0ubuntu4~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-r128-lts-trusty.
Unpacking xserver-xorg-video-r128-lts-trusty (from .../xserver-xorg-video-r128-lts-trusty_6.9.2-1build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-mach64-lts-trusty.
Unpacking xserver-xorg-video-mach64-lts-trusty (from .../xserver-xorg-video-mach64-lts-trusty_6.9.4-1build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-radeon-lts-trusty.
Unpacking xserver-xorg-video-radeon-lts-trusty (from .../xserver-xorg-video-radeon-lts-trusty_1%3a7.3.0-1ubuntu3.1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-ati-lts-trusty.
Unpacking xserver-xorg-video-ati-lts-trusty (from .../xserver-xorg-video-ati-lts-trusty_1%3a7.3.0-1ubuntu3.1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-cirrus-lts-trusty.
Unpacking xserver-xorg-video-cirrus-lts-trusty (from .../xserver-xorg-video-cirrus-lts-trusty_1%3a1.5.2-1build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-fbdev-lts-trusty.
Unpacking xserver-xorg-video-fbdev-lts-trusty (from .../xserver-xorg-video-fbdev-lts-trusty_1%3a0.4.4-1build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-intel-lts-trusty.
Unpacking xserver-xorg-video-intel-lts-trusty (from .../xserver-xorg-video-intel-lts-trusty_2%3a2.99.910-0ubuntu1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-mga-lts-trusty.
Unpacking xserver-xorg-video-mga-lts-trusty (from .../xserver-xorg-video-mga-lts-trusty_1%3a1.6.3-1build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-modesetting-lts-trusty.
Unpacking xserver-xorg-video-modesetting-lts-trusty (from .../xserver-xorg-video-modesetting-lts-trusty_0.8.1-1build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-neomagic-lts-trusty.
Unpacking xserver-xorg-video-neomagic-lts-trusty (from .../xserver-xorg-video-neomagic-lts-trusty_1%3a1.2.8-1build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-nouveau-lts-trusty.
Unpacking xserver-xorg-video-nouveau-lts-trusty (from .../xserver-xorg-video-nouveau-lts-trusty_1%3a1.0.10-1ubuntu2~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-openchrome-lts-trusty.
Unpacking xserver-xorg-video-openchrome-lts-trusty (from .../xserver-xorg-video-openchrome-lts-trusty_1%3a0.3.3-1build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-s3-lts-trusty.
Unpacking xserver-xorg-video-s3-lts-trusty (from .../xserver-xorg-video-s3-lts-trusty_1%3a0.6.5-0ubuntu4~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-savage-lts-trusty.
Unpacking xserver-xorg-video-savage-lts-trusty (from .../xserver-xorg-video-savage-lts-trusty_1%3a2.3.7-2ubuntu2~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-siliconmotion-lts-trusty.
Unpacking xserver-xorg-video-siliconmotion-lts-trusty (from .../xserver-xorg-video-siliconmotion-lts-trusty_1%3a1.7.7-2build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-sis-lts-trusty.
Unpacking xserver-xorg-video-sis-lts-trusty (from .../xserver-xorg-video-sis-lts-trusty_1%3a0.10.7-0ubuntu6~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-sisusb-lts-trusty.
Unpacking xserver-xorg-video-sisusb-lts-trusty (from .../xserver-xorg-video-sisusb-lts-trusty_1%3a0.9.6-2build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-tdfx-lts-trusty.
Unpacking xserver-xorg-video-tdfx-lts-trusty (from .../xserver-xorg-video-tdfx-lts-trusty_1%3a1.4.5-1build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-trident-lts-trusty.
Unpacking xserver-xorg-video-trident-lts-trusty (from .../xserver-xorg-video-trident-lts-trusty_1%3a1.3.6-0ubuntu5~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-vesa-lts-trusty.
Unpacking xserver-xorg-video-vesa-lts-trusty (from .../xserver-xorg-video-vesa-lts-trusty_1%3a2.3.3-1build1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-vmware-lts-trusty.
Unpacking xserver-xorg-video-vmware-lts-trusty (from .../xserver-xorg-video-vmware-lts-trusty_1%3a13.0.2-2ubuntu1~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-video-all-lts-trusty.
Unpacking xserver-xorg-video-all-lts-trusty (from .../xserver-xorg-video-all-lts-trusty_1%3a7.7+1ubuntu8~precise1_amd64.deb) ...
Selecting previously unselected package xserver-xorg-lts-trusty.
Unpacking xserver-xorg-lts-trusty (from .../xserver-xorg-lts-trusty_1%3a7.7+1ubuntu8~precise1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up libdrm-nouveau2 (2.4.52-1~precise1) ...
Setting up libllvm3.4 (1:3.4-1ubuntu3~precise1) ...
Setting up libgl1-mesa-dri-lts-trusty (10.1.3-0ubuntu0.1~precise1) ...
Setting up libwayland-ltst-client0 (1.4.0-1ubuntu1~precise1) ...
Setting up libwayland-ltst-server0 (1.4.0-1ubuntu1~precise1) ...
Setting up libxcb-dri2-0 (1.8.1-1ubuntu0.2) ...
Setting up libgbm1-lts-trusty (10.1.3-0ubuntu0.1~precise1) ...
Setting up libx11-xcb1 (2:1.4.99.1-0ubuntu2.2) ...
Setting up libxcb-xfixes0 (1.8.1-1ubuntu0.2) ...
Setting up libegl1-mesa-lts-trusty (10.1.3-0ubuntu0.1~precise1) ...
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode.
Setting up libglapi-mesa-lts-trusty (10.1.3-0ubuntu0.1~precise1) ...
Setting up libopenvg1-mesa-lts-trusty (10.1.3-0ubuntu0.1~precise1) ...
Setting up libxfixes3 (1:5.0-4ubuntu4.2) ...
Setting up libwayland-egl1-mesa-lts-trusty (10.1.3-0ubuntu0.1~precise1) ...
Setting up libegl1-mesa-drivers-lts-trusty (10.1.3-0ubuntu0.1~precise1) ...
Setting up libxcb-glx0 (1.8.1-1ubuntu0.2) ...
Setting up libxdamage1 (1:1.1.3-2build1) ...
Setting up libxxf86vm1 (1:1.1.1-2ubuntu0.1) ...
Setting up libgl1-mesa-glx-lts-trusty (10.1.3-0ubuntu0.1~precise1) ...
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
Setting up libglamor-ltst0 (0.6.0-0ubuntu4~precise1) ...
Setting up x11-common (1:7.6+12ubuntu2) ...
Setting up libice6 (2:1.0.7-2build1) ...
Setting up libpixman-1-0 (0.30.2-1ubuntu0.0.0.0.1) ...
Setting up libsm6 (2:1.2.0-2build1) ...
Setting up libxatracker2-lts-trusty (10.1.3-0ubuntu0.1~precise1) ...
Setting up libxt6 (1:1.1.1-2ubuntu0.1) ...
Setting up libxmu6 (2:1.1.0-3) ...
Setting up libxaw7 (2:1.0.9-3ubuntu1) ...
Setting up libxrender1 (1:0.9.6-2ubuntu0.1) ...
Setting up libxcursor1 (1:1.1.12-1ubuntu0.1) ...
Setting up libxi6 (2:1.7.1.901-1ubuntu1~precise1) ...
Setting up libxinerama1 (2:1.1.1-3ubuntu0.1) ...
Setting up libxkbfile1 (1:1.0.7-1ubuntu0.1) ...
Setting up libxrandr-ltst2 (2:1.4.2-1~precise1) ...
Setting up libxrandr2 (2:1.3.2-2ubuntu0.2) ...
Setting up libxv1 (2:1.0.6-2ubuntu0.1) ...
Setting up linux-image-3.13.0-34-generic (3.13.0-34.60~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found initrd image: /boot/initrd.img-3.8.0-44-generic
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-37-generic
Found initrd image: /boot/initrd.img-3.8.0-37-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found memtest86+ image: /memtest86+.bin
done
Setting up libtxc-dxtn-s2tc0 (0~git20110809-2.1) ...
update-alternatives: using /usr/lib/x86_64-linux-gnu/libtxc_dxtn_s2tc.so.0 to provide /usr/lib/x86_64-linux-gnu/libtxc_dxtn.so (libtxc-dxtn-x86_64-linux-gnu) in auto mode.
Setting up libxcb-util0 (0.3.8-2) ...
Setting up libfontenc1 (1:1.1.0-1) ...
Setting up libmtdev1 (1.1.0-2ubuntu1) ...
Setting up libxfont1 (1:1.4.4-1ubuntu0.2) ...
Setting up libxvmc1 (2:1.0.6-1ubuntu2.1) ...
Setting up linux-image-generic-lts-trusty (3.13.0.34.30) ...
Setting up linux-headers-3.13.0-34 (3.13.0-34.60~precise1) ...
Setting up linux-headers-3.13.0-34-generic (3.13.0-34.60~precise1) ...
Setting up linux-headers-generic-lts-trusty (3.13.0.34.30) ...
Setting up linux-generic-lts-trusty (3.13.0.34.30) ...
Setting up x11-xkb-utils (7.6+4) ...
Setting up x11-xserver-utils (7.6+3) ...
Setting up x11-xserver-utils-lts-trusty (7.7+2ubuntu1~precise1) ...
Setting up xfonts-encodings (1:1.0.4-1ubuntu1) ...
Setting up xfonts-utils (1:7.6+1) ...
Setting up xfonts-base (1:1.0.3) ...
Setting up xserver-common (2:1.11.4-0ubuntu10.14) ...
Setting up xserver-common-lts-trusty (2:1.15.1-0ubuntu2~precise2) ...
Setting up xserver-xorg-core-lts-trusty (2:1.15.1-0ubuntu2~precise2) ...
Setting up xserver-xorg-input-evdev-lts-trusty (1:2.8.2-1ubuntu2~precise1) ...
Setting up xserver-xorg-input-synaptics-lts-trusty (1.7.4-0ubuntu1~precise2) ...
Setting up xserver-xorg-input-mouse-lts-trusty (1:1.9.0-1build1~precise1) ...
Setting up xserver-xorg-input-vmmouse-lts-trusty (1:13.0.0-1build1~precise1) ...
Setting up xserver-xorg-input-wacom-lts-trusty (1:0.23.0-0ubuntu2~precise1) ...
Setting up xserver-xorg-input-all-lts-trusty (1:7.7+1ubuntu8~precise1) ...
Setting up xserver-xorg-video-glamoregl-lts-trusty (0.6.0-0ubuntu4~precise1) ...
Setting up xserver-xorg-video-r128-lts-trusty (6.9.2-1build1~precise1) ...
Setting up xserver-xorg-video-mach64-lts-trusty (6.9.4-1build1~precise1) ...
Setting up xserver-xorg-video-radeon-lts-trusty (1:7.3.0-1ubuntu3.1~precise1) ...
Setting up xserver-xorg-video-ati-lts-trusty (1:7.3.0-1ubuntu3.1~precise1) ...
Setting up xserver-xorg-video-cirrus-lts-trusty (1:1.5.2-1build1~precise1) ...
Setting up xserver-xorg-video-fbdev-lts-trusty (1:0.4.4-1build1~precise1) ...
Setting up xserver-xorg-video-intel-lts-trusty (2:2.99.910-0ubuntu1~precise1) ...
Setting up xserver-xorg-video-mga-lts-trusty (1:1.6.3-1build1~precise1) ...
Setting up xserver-xorg-video-modesetting-lts-trusty (0.8.1-1build1~precise1) ...
Setting up xserver-xorg-video-neomagic-lts-trusty (1:1.2.8-1build1~precise1) ...
Setting up xserver-xorg-video-nouveau-lts-trusty (1:1.0.10-1ubuntu2~precise1) ...
Setting up xserver-xorg-video-openchrome-lts-trusty (1:0.3.3-1build1~precise1) ...
Setting up xserver-xorg-video-s3-lts-trusty (1:0.6.5-0ubuntu4~precise1) ...
Setting up xserver-xorg-video-savage-lts-trusty (1:2.3.7-2ubuntu2~precise1) ...
Setting up xserver-xorg-video-siliconmotion-lts-trusty (1:1.7.7-2build1~precise1) ...
Setting up xserver-xorg-video-sis-lts-trusty (1:0.10.7-0ubuntu6~precise1) ...
Setting up xserver-xorg-video-sisusb-lts-trusty (1:0.9.6-2build1~precise1) ...
Setting up xserver-xorg-video-tdfx-lts-trusty (1:1.4.5-1build1~precise1) ...
Setting up xserver-xorg-video-trident-lts-trusty (1:1.3.6-0ubuntu5~precise1) ...
Setting up xserver-xorg-video-vesa-lts-trusty (1:2.3.3-1build1~precise1) ...
Setting up xserver-xorg-video-vmware-lts-trusty (1:13.0.2-2ubuntu1~precise1) ...
Setting up xserver-xorg-video-all-lts-trusty (1:7.7+1ubuntu8~precise1) ...
Setting up xserver-xorg-lts-trusty (1:7.7+1ubuntu8~precise1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

REBOOT

```
justin@ubuntu:~$ lsb_release -aNo LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise



```
```



justin@ubuntu:~$ uname -r
3.13.0-34-generic



```
```



justin@ubuntu:~$ dpkg -l | grep linux-
ii  linux-firmware                              1.79.16                           Firmware for Linux kernel drivers
ii  linux-generic-lts-raring                    3.8.0.44.44                       Generic Linux kernel image and headers
ii  linux-generic-lts-trusty                    3.13.0.34.30                      Generic Linux kernel image and headers
ii  linux-headers-3.13.0-34                     3.13.0-34.60~precise1             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic             3.13.0-34.60~precise1             Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-36                      3.8.0-36.52~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-36-generic              3.8.0-36.52~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-37                      3.8.0-37.53~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-37-generic              3.8.0-37.53~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-38                      3.8.0-38.56~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-38-generic              3.8.0-38.56~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-39                      3.8.0-39.58~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-39-generic              3.8.0-39.58~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-41                      3.8.0-41.60~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-41-generic              3.8.0-41.60~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-42                      3.8.0-42.63~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-42-generic              3.8.0-42.63~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-44                      3.8.0-44.66~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-44-generic              3.8.0-44.66~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-raring            3.8.0.44.44                       Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty            3.13.0.34.30                      Generic Linux kernel headers
ii  linux-image-3.13.0-34-generic               3.13.0-34.60~precise1             Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-36-generic                3.8.0-36.52~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-37-generic                3.8.0-37.53~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-38-generic                3.8.0-38.56~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-44-generic                3.8.0-44.66~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-raring              3.8.0.44.44                       Generic Linux kernel image
ii  linux-image-generic-lts-trusty              3.13.0.34.30                      Generic Linux kernel image
ii  linux-libc-dev                              3.2.0-67.101                      Linux Kernel Headers for development



```
```



justin@ubuntu:~$ sudo apt-get -f install
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  shtool
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bashing-om on 2014-08-14
bphillips2; Wow !

Get's any brighter, will have to put sun glasses on.
Are you ever feeling good !

all that is left is little bitty details, let me have a bit to look it over, and I get back at you soonest.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-14
I'm feeling great! I'm finally going to have a professionally cleaned system!

Take your time, I have to leave town in about an hour for the weekend.  Can we pick up the final details next Monday?

---

### Post by Bashing-om on 2014-08-14
bphillips2; Hey, on second thought,

Before we do anything further, please satisfy my curiosity, see if the new tools within apt-get have been "back ported" now in your 12.04.5 install.
What results from the terminal command:
```

sudo apt-get autoremove

```
as per advisement:
> 
The following package was automatically installed and is no longer required:
  shtool
Use 'apt-get autoremove' to remove them.
 looking to see if 'autoremove' now does even more.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-14
Here ya go

```
justin@ubuntu:~$ sudo apt-get autoremove[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  shtool
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 557 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 249106 files and directories currently installed.)
Removing shtool ...
Processing triggers for man-db ...
```

---

### Post by Bashing-om on 2014-08-14
bphillips2; Hey.

I am back on this.
Was hopeful that the 'autoremove' command was brought forward and would do our dirty work for us, oh well, it didn't and wont.
We will proceed to do so.
I am perplexed why you used to boot kernel 3.8.0-36 when so many newer kernels were installed and should have been using the latest kernel(s) to boot. Maybe not having the images installed to match the headers for 3 of the image versions (?). 
OH well, you are setting pretty on the 3.13 kernel; Let's do it thusly:
```

sudo dpkg -P linux-headers-3.8.0-{37,38,39,41,42,44}-generic
sudo dpkg -P linux-headers-3.8.0-{37,38,39,41,42,44}
sudo dpkg -P linux-image-3.8.0-{37,38,44}

```
double check that the package manager done it's magic:
```

ls -la /lib/modules

```

That should have the kernels all straightened up:
verify/check one last time:
```

dpkg -l | grep linux-

```
and I think we are down to the final stretch.

[INDENT][INDENT][INDENT]probable a big yes
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-14
Thanks Bashing.

I already left town and am going to be gone until Monday. Can we pick this back up then?

Thanks

---

### Post by Bashing-om on 2014-08-14
bphillips2; K

[INDENT][INDENT]fat lady is drawing her breath, for
[INDENT][INDENT][INDENT]when the fat lady sings it is all over
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-08-15
You two are amazing. Been with you all the way. ;)

  and I hear the fat lady,
      humming as a precursor to the song ....

---

### Post by Bashing-om on 2014-08-15
@ Bucky Ball; Yeah,

This one has been one of those "fun" ones. And another that I have learned from.

I owe my abilities to you and others here on this forum. Who Guide, guard and gave directions in my infantile stages; and to all who continue to come to  my aid looking over my shoulder.

It is this-a-way ->
[INDENT][INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-18
> **Bashing-om said:**
> bphillips2; Hey.

I am back on this.
Was hopeful that the 'autoremove' command was brought forward and would do our dirty work for us, oh well, it didn't and wont.
We will proceed to do so.
I am perplexed why you used to boot kernel 3.8.0-36 when so many newer kernels were installed and should have been using the latest kernel(s) to boot. Maybe not having the images installed to match the headers for 3 of the image versions (?). 
OH well, you are setting pretty on the 3.13 kernel; Let's do it thusly:
```

sudo dpkg -P linux-headers-3.8.0-{37,38,39,41,42,44}-generic
sudo dpkg -P linux-headers-3.8.0-{37,38,39,41,42,44}
sudo dpkg -P linux-image-3.8.0-{37,38,44}

```
double check that the package manager done it's magic:
```

ls -la /lib/modules

```

That should have the kernels all straightened up:
verify/check one last time:
```

dpkg -l | grep linux-

```
and I think we are down to the final stretch.[INDENT][INDENT][INDENT]probable a big yes
[/INDENT]
[/INDENT]
[/INDENT]



Here are the outputs for each of those commands

```
justin@ubuntu:~$ sudo dpkg -P linux-headers-3.8.0-{37,38,39,41,42,44}-generic
[sudo] password for justin: 
(Reading database ... 249053 files and directories currently installed.)
Removing linux-headers-3.8.0-37-generic ...
Removing linux-headers-3.8.0-38-generic ...
Removing linux-headers-3.8.0-39-generic ...
Removing linux-headers-3.8.0-41-generic ...
Removing linux-headers-3.8.0-42-generic ...
dpkg: dependency problems prevent removal of linux-headers-3.8.0-44-generic:
 linux-headers-generic-lts-raring depends on linux-headers-3.8.0-44-generic.
dpkg: error processing linux-headers-3.8.0-44-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.8.0-44-generic



```
```



justin@ubuntu:~$ sudo dpkg -P linux-headers-3.8.0-{37,38,39,41,42,44}
(Reading database ... 204597 files and directories currently installed.)
Removing linux-headers-3.8.0-37 ...
Removing linux-headers-3.8.0-38 ...
Removing linux-headers-3.8.0-39 ...
Removing linux-headers-3.8.0-41 ...
Removing linux-headers-3.8.0-42 ...
dpkg: dependency problems prevent removal of linux-headers-3.8.0-44:
 linux-headers-3.8.0-44-generic depends on linux-headers-3.8.0-44.
dpkg: error processing linux-headers-3.8.0-44 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.8.0-44

```
```



justin@ubuntu:~$ sudo dpkg -P linux-image-3.8.0-{37,38,44}
dpkg: warning: there's no installed package matching linux-image-3.8.0-37
dpkg: warning: there's no installed package matching linux-image-3.8.0-38
dpkg: warning: there's no installed package matching linux-image-3.8.0-44

```
```



justin@ubuntu:~$ ls -la /lib/modules
total 28
drwxr-xr-x  7 root root 4096 Aug 18 13:37 .
drwxr-xr-x 17 root root 4096 Jan 28  2014 ..
drwxr-xr-x  4 root root 4096 Aug 14 13:32 3.13.0-34-generic
drwxr-xr-x  4 root root 4096 Feb 19 06:45 3.8.0-36-generic
drwxr-xr-x  4 root root 4096 Aug 18 13:37 3.8.0-37-generic
drwxr-xr-x  4 root root 4096 Aug 18 13:37 3.8.0-38-generic
drwxr-xr-x  4 root root 4096 Aug 13 23:23 3.8.0-44-generic



```
```



justin@ubuntu:~$ dpkg -l | grep linux-
ii  linux-firmware                              1.79.16                           Firmware for Linux kernel drivers
ii  linux-generic-lts-raring                    3.8.0.44.44                       Generic Linux kernel image and headers
ii  linux-generic-lts-trusty                    3.13.0.34.30                      Generic Linux kernel image and headers
ii  linux-headers-3.13.0-34                     3.13.0-34.60~precise1             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic             3.13.0-34.60~precise1             Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-36                      3.8.0-36.52~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-36-generic              3.8.0-36.52~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
pi  linux-headers-3.8.0-44                      3.8.0-44.66~precise1              Header files related to Linux kernel version 3.8.0
pi  linux-headers-3.8.0-44-generic              3.8.0-44.66~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-raring            3.8.0.44.44                       Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty            3.13.0.34.30                      Generic Linux kernel headers
ii  linux-image-3.13.0-34-generic               3.13.0-34.60~precise1             Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-36-generic                3.8.0-36.52~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-37-generic                3.8.0-37.53~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-38-generic                3.8.0-38.56~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-44-generic                3.8.0-44.66~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-raring              3.8.0.44.44                       Generic Linux kernel image
ii  linux-image-generic-lts-trusty              3.13.0.34.30                      Generic Linux kernel image
ii  linux-libc-dev                              3.2.0-67.101                      Linux Kernel Headers for development
```

---

### Post by Bashing-om on 2014-08-18
bphillips2; Well !

I notice you are up and running on the newest kernel, you done your homework, and are a step ahead.
Question now is why is the package manager concerned about kernel 3.8.0-44-generic (?).

Let's see what the "status" is:
Fire up your text editor and lets look in the file " /var/lib/dpkg/status "
Search on the term " Package: linux-headers-generic-lts-raring " Remember there is that space before "linux"; and post that stanza back to us for inspection.
Is not the 3.8 series of kernels "quantal" ?? What in the world are they still hanging about for ?

We want 'quantal' and 'raring' and all kernels related gone ;
and then drupal7 also in history.

[INDENT][INDENT]must have been a frog in the fat ladies throat
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-18
Here it is

```
[COLOR=#000000]Package: linux-headers-generic-lts-raring[/COLOR]Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 27
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta-lts-raring
Version: 3.8.0.44.44
Depends: linux-headers-3.8.0-44-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic 12.10 kernel headers [COLOR=#000000] available.[/COLOR]
```

---

### Post by Bashing-om on 2014-08-18
bphillips2; Hummm ??

I am Going to have to do some home work here;
Since when does 'raring' depend on a -what I presently think of - a 'quantal' release ->  "Version: 3.8.0.44.44".
Consider maybe, as you are up on the 'trusty' kernel, just see if we can remove the 'raring' kernels and not worry about it ??
Not real sure we can .. will do some thinking about it, maybe try and see what results.

Best I recall, 'raring' is the 3.11 series of kernels.

[INDENT][INDENT]study twice, 
[INDENT][INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-18
bphillips2; Meanwhile;

We have:
> 
justin@ubuntu:~$ sudo dpkg -P linux-image-3.8.0-{37,38,44}
dpkg: warning: there's no installed package matching linux-image-3.8.0-37
dpkg: warning: there's no installed package matching linux-image-3.8.0-38
dpkg: warning: there's no installed package matching linux-image-3.8.0-44

Which is not-true - and totally unexpected !:
> 
ii  linux-image-3.13.0-34-generic               3.13.0-34.60~precise1             Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-36-generic                3.8.0-36.52~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-37-generic                3.8.0-37.53~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-38-generic                3.8.0-38.56~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-44-generic
 Where the 'ii' is installed installed !
So, what results:
```

 sudo dpkg autoremove linux-image-3.8.0-37-generic

```

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT][INDENT]othertimes I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-18
Oops, I think something is missing from the command

```
[COLOR=#000000]justin@ubuntu:~$ sudo dpkg autoremove linux-image-3.8.0-37-generic
[/COLOR]dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
 [COLOR=#000000]Options marked 
[*] produce a lot of output - pipe it through `less' or `more' ![/COLOR]
```

---

### Post by Bashing-om on 2014-08-18
bphillips2; Yikes !

Must have had a brain freeze - or something - that is not a valid option for 'dpkg'.

Try as:
```

sudo apt-get autoremove linux-image-3.8.0-37-generic

```
As I truly had in mind to use apt-get in this case rather than dpkg.

looking to see
[INDENT][INDENT][INDENT]what is to be seen
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-18
All done

```
[COLOR=#000000]justin@ubuntu:~$ sudo apt-get autoremove linux-image-3.8.0-37-generic
[/COLOR][sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.8.0-37-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 177 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 130714 files and directories currently installed.)
Removing linux-image-3.8.0-37-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found initrd image: /boot/initrd.img-3.8.0-44-generic
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found memtest86+ image: /memtest86+.bin [COLOR=#000000]done[/COLOR]
```

---

### Post by Bashing-om on 2014-08-18
bphillips2; Well !

Give apt-get a cookie !
Let's do the other two now !
```

sudo apt-get autoremove linux-image-3.8.0-38-generic
sudo apt-get autoremove linux-image-3.8.0-44-generic

```

A get a new look at what is installed for kernels:
```

dpkg -l | grep linux-

```

As presently I only see 1 kernel for 'trusty' installed, may leave well enough alone here.

[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-18
```
justin@ubuntu:~$ sudo apt-get autoremove linux-image-3.8.0-38-generic
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.8.0-38-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 179 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 126126 files and directories currently installed.)
Removing linux-image-3.8.0-38-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found initrd image: /boot/initrd.img-3.8.0-44-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found memtest86+ image: /memtest86+.bin
done



```
```





justin@ubuntu:~$ sudo apt-get autoremove linux-image-3.8.0-44-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-generic-lts-raring linux-image-3.8.0-44-generic linux-image-generic-lts-raring
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 179 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 121538 files and directories currently installed.)
Removing linux-generic-lts-raring ...
Removing linux-image-generic-lts-raring ...
Removing linux-image-3.8.0-44-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-44-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found memtest86+ image: /memtest86+.bin
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]





```
```



justin@ubuntu:~$ dpkg -l | grep linux-
ii  linux-firmware                              1.79.16                           Firmware for Linux kernel drivers
ii  linux-generic-lts-trusty                    3.13.0.34.30                      Generic Linux kernel image and headers
ii  linux-headers-3.13.0-34                     3.13.0-34.60~precise1             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic             3.13.0-34.60~precise1             Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-36                      3.8.0-36.52~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-36-generic              3.8.0-36.52~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
pi  linux-headers-3.8.0-44                      3.8.0-44.66~precise1              Header files related to Linux kernel version 3.8.0
pi  linux-headers-3.8.0-44-generic              3.8.0-44.66~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-raring            3.8.0.44.44                       Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty            3.13.0.34.30                      Generic Linux kernel headers
ii  linux-image-3.13.0-34-generic               3.13.0-34.60~precise1             Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-36-generic                3.8.0-36.52~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-37-generic                3.8.0-37.53~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-38-generic                3.8.0-38.56~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-44-generic                3.8.0-44.66~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-trusty              3.13.0.34.30                      Generic Linux kernel image
ii  linux-libc-dev                              3.2.0-67.101                      Linux Kernel Headers for development
```

---

### Post by Bashing-om on 2014-08-18
bphillips2; YUK !

Did I loose track ?
> 
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link

I DO not think so; -->> second look, maybe I did !!
as you were booting the trusty kernel !

Before doing as the package manager advises, let's look at what the situation is:
```

ls -al /
ls -al /boot

```
and let's see what the symbolic links are and where they point to.
And then go back and fix my uh oh !


This is one of those times
[INDENT][INDENT][INDENT]we have a need to know
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-18
Here ya go

```

justin@ubuntu:/var/www/owncloud/core/img$ ls -al /
total 218
drwxr-xr-x  27 root     root      4096 Aug 18 20:07 .
drwxr-xr-x  27 root     root      4096 Aug 18 20:07 ..
drwx------   3 bacula   bacula    4096 Sep 24  2013 bacula
drwxr-xr-x   2 root     root      4096 Aug 14 13:32 bin
drwxr-xr-x   4 root     root      2048 Aug 18 20:07 boot
drwxr-xr-x   3 root     root      4096 Aug 26  2013 build
drwxr-xr-x  17 root     root      4360 Aug 18 20:07 dev
drwxr-xr-x 101 root     root      4096 Aug 18 20:07 etc
drwxr-xr-x   3 root     root      4096 Aug 26  2013 home
lrwxrwxrwx   1 root     root        33 Aug 14 13:32 initrd.img -> boot/initrd.img-3.13.0-34-generic
drwxr-xr-x  17 root     root      4096 Jan 28  2014 lib
drwxr-xr-x   2 root     root      4096 Aug 13 22:49 lib64
drwx------   2 root     root     16384 Aug 26  2013 lost+found
drwxr-xr-x   3 root     root      4096 Aug 26  2013 media
drwxr-xr-x   2 root     root      4096 Aug 17  2013 mnt
drwxr-xr-x   2 memcache memcache  4096 Nov  1  2013 nonexistent
drwxr-xr-x   2 root     root      4096 Aug 26  2013 opt
drwxr-xr-x   6 root     root      4096 Jun  7  2012 powerpanel-1.2.3-0
-rw-r--r--   1 root     root     98998 Jun  8  2012 powerpanel_123_x86_64.tar.gz
dr-xr-xr-x 152 root     root         0 Aug 14 13:36 proc
drwx------   2 root     root      4096 Nov  5  2013 root
drwxr-xr-x  19 root     root       720 Aug 18 21:51 run
drwxr-xr-x   2 root     root     12288 Aug 13 22:51 sbin
drwxr-xr-x   2 root     root      4096 Mar  5  2012 selinux
drwxr-xr-x   2 root     root      4096 Aug 26  2013 srv
dr-xr-xr-x  13 root     root         0 Aug 14 13:36 sys
drwxrwxrwt   5 root     root     12288 Aug 18 21:57 tmp
drwxr-xr-x  10 root     root      4096 Aug 26  2013 usr
drwxr-xr-x  13 root     root      4096 Aug 14 13:37 var
lrwxrwxrwx   1 root     root        30 Aug 14 13:32 vmlinuz -> boot/vmlinuz-3.13.0-34-generic

```
```





justin@ubuntu:/var/www/owncloud/core/img$ ls - al /boot
ls: cannot access -: No such file or directory
ls: cannot access al: No such file or directory
/boot:
abi-3.13.0-34-generic     config-3.8.0-36-generic       initrd.img-3.8.0-36-generic  memtest86+_multiboot.bin      vmlinuz-3.13.0-34-generic
abi-3.8.0-36-generic      grub                          lost+found                   System.map-3.13.0-34-generic  vmlinuz-3.8.0-36-generic
config-3.13.0-34-generic  initrd.img-3.13.0-34-generic  memtest86+.bin               System.map-3.8.0-36-generic 
```

---

### Post by Bashing-om on 2014-08-18
bphillips2; Typo !

Silly little space:
correct to be:
```

ls -al /boot

```

and my I am working to correct my boo boo' We will (re-)install the -44 kernel, and see if grub will pick it back up.

[INDENT][INDENT]to err is human
[INDENT][INDENT][INDENT]to really foul things up takes a Bashing-om ( when he gets tired)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-18
here ya go

```
justin@ubuntu:/var/www/owncloud/core/img$ ls -al /boottotal 56022
drwxr-xr-x  4 root root     2048 Aug 18 20:07 .
drwxr-xr-x 27 root root     4096 Aug 18 20:07 ..
-rw-r--r--  1 root root  1162712 Aug 13 11:23 abi-3.13.0-34-generic
-rw-r--r--  1 root root   919810 Feb  3  2014 abi-3.8.0-36-generic
-rw-r--r--  1 root root   165620 Aug 13 11:23 config-3.13.0-34-generic
-rw-r--r--  1 root root   154959 Feb  3  2014 config-3.8.0-36-generic
drwxr-xr-x  3 root root     5120 Aug 18 20:07 grub
-rw-r--r--  1 root root 19455614 Aug 14 13:32 initrd.img-3.13.0-34-generic
-rw-r--r--  1 root root 16837611 Feb 19 06:45 initrd.img-3.8.0-36-generic
drwxr-xr-x  2 root root    12288 Aug 26  2013 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  3516562 Aug 13 11:23 System.map-3.13.0-34-generic
-rw-------  1 root root  3192822 Feb  3  2014 System.map-3.8.0-36-generic
-rw-------  1 root root  5883264 Aug 13 11:23 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  5454928 Feb  3  2014 vmlinuz-3.8.0-36-generic

```

---

### Post by Bashing-om on 2014-08-18
bphillips2; OK ..

Let's fix the boo boo:
```

sudo apt-get install -reinstall linux-image-3.8.0-44-generic
sudo update-grub

```

and a looksee to make sure of what I am doing:
```

ls -al /
ls -al /boot
dpkg -l | grep linux-

```
If all is now good, proceed to remove the headers for those removed images.

[INDENT][INDENT][INDENT]recovery ?
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-18
Output

```

justin@ubuntu:/var/www/owncloud/core/img$ sudo apt-get install -reinstall linux-image-3.8.0-44-generic
E: Command line option 'r' [from -reinstall] is not known.

```
Changed slightly, hope that's right
```

justin@ubuntu:/var/www/owncloud/core/img$ sudo apt-get install linux-image-3.8.0-44-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils linux-lts-raring-doc-3.8.0 linux-lts-raring-source-3.8.0 linux-lts-raring-tools linux-headers-3.8.0-44-generic
The following NEW packages will be installed:
  linux-image-3.8.0-44-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/50.9 MB of archives.
After this operation, 179 MB of additional disk space will be used.
Selecting previously unselected package linux-image-3.8.0-44-generic.
(Reading database ... 116946 files and directories currently installed.)
Unpacking linux-image-3.8.0-44-generic (from .../linux-image-3.8.0-44-generic_3.8.0-44.66~precise1_amd64.deb) ...
Done.
Setting up linux-image-3.8.0-44-generic (3.8.0-44.66~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.8.0-44.66~precise1 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.8.0-44.66~precise1 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-44-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found initrd image: /boot/initrd.img-3.8.0-44-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found memtest86+ image: /memtest86+.bin
done

```
```



justin@ubuntu:/var/www/owncloud/core/img$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found initrd image: /boot/initrd.img-3.8.0-44-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found memtest86+ image: /memtest86+.bin
done



```
```



justin@ubuntu:/$ ls -al /
total 218
drwxr-xr-x  27 root     root      4096 Aug 18 20:07 .
drwxr-xr-x  27 root     root      4096 Aug 18 20:07 ..
drwx------   3 bacula   bacula    4096 Sep 24  2013 bacula
drwxr-xr-x   2 root     root      4096 Aug 14 13:32 bin
drwxr-xr-x   4 root     root      2048 Aug 18 22:38 boot
drwxr-xr-x   3 root     root      4096 Aug 26  2013 build
drwxr-xr-x  17 root     root      4360 Aug 18 22:38 dev
drwxr-xr-x 101 root     root      4096 Aug 18 22:38 etc
drwxr-xr-x   3 root     root      4096 Aug 26  2013 home
lrwxrwxrwx   1 root     root        33 Aug 14 13:32 initrd.img -> boot/initrd.img-3.13.0-34-generic
drwxr-xr-x  17 root     root      4096 Jan 28  2014 lib
drwxr-xr-x   2 root     root      4096 Aug 13 22:49 lib64
drwx------   2 root     root     16384 Aug 26  2013 lost+found
drwxr-xr-x   3 root     root      4096 Aug 26  2013 media
drwxr-xr-x   2 root     root      4096 Aug 17  2013 mnt
drwxr-xr-x   2 memcache memcache  4096 Nov  1  2013 nonexistent
drwxr-xr-x   2 root     root      4096 Aug 26  2013 opt
drwxr-xr-x   6 root     root      4096 Jun  7  2012 powerpanel-1.2.3-0
-rw-r--r--   1 root     root     98998 Jun  8  2012 powerpanel_123_x86_64.tar.gz
dr-xr-xr-x 158 root     root         0 Aug 14 13:36 proc
drwx------   2 root     root      4096 Nov  5  2013 root
drwxr-xr-x  19 root     root       760 Aug 18 22:37 run
drwxr-xr-x   2 root     root     12288 Aug 13 22:51 sbin
drwxr-xr-x   2 root     root      4096 Mar  5  2012 selinux
drwxr-xr-x   2 root     root      4096 Aug 26  2013 srv
dr-xr-xr-x  13 root     root         0 Aug 14 13:36 sys
drwxrwxrwt   5 root     root     12288 Aug 18 22:39 tmp
drwxr-xr-x  10 root     root      4096 Aug 26  2013 usr
drwxr-xr-x  13 root     root      4096 Aug 14 13:37 var
lrwxrwxrwx   1 root     root        30 Aug 14 13:32 vmlinuz -> boot/vmlinuz-3.13.0-34-generic





```
```



justin@ubuntu:/$ ls -al /boot
total 82334
drwxr-xr-x  4 root root     2048 Aug 18 22:38 .
drwxr-xr-x 27 root root     4096 Aug 18 20:07 ..
-rw-r--r--  1 root root  1162712 Aug 13 11:23 abi-3.13.0-34-generic
-rw-r--r--  1 root root   919810 Feb  3  2014 abi-3.8.0-36-generic
-rw-r--r--  1 root root   921155 Jul 14 23:22 abi-3.8.0-44-generic
-rw-r--r--  1 root root   165620 Aug 13 11:23 config-3.13.0-34-generic
-rw-r--r--  1 root root   154959 Feb  3  2014 config-3.8.0-36-generic
-rw-r--r--  1 root root   154959 Jul 14 23:22 config-3.8.0-44-generic
drwxr-xr-x  3 root root     5120 Aug 18 22:38 grub
-rw-r--r--  1 root root 19455614 Aug 14 13:32 initrd.img-3.13.0-34-generic
-rw-r--r--  1 root root 16837611 Feb 19 06:45 initrd.img-3.8.0-36-generic
-rw-r--r--  1 root root 17094882 Aug 18 22:38 initrd.img-3.8.0-44-generic
drwxr-xr-x  2 root root    12288 Aug 26  2013 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  3516562 Aug 13 11:23 System.map-3.13.0-34-generic
-rw-------  1 root root  3192822 Feb  3  2014 System.map-3.8.0-36-generic
-rw-------  1 root root  3196521 Jul 14 23:22 System.map-3.8.0-44-generic
-rw-------  1 root root  5883264 Aug 13 11:23 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  5454928 Feb  3  2014 vmlinuz-3.8.0-36-generic
-rw-------  1 root root  5461488 Jul 14 23:22 vmlinuz-3.8.0-44-generic





```
```



justin@ubuntu:/$ dpkg -l | grep linux-
ii  linux-firmware                              1.79.16                           Firmware for Linux kernel drivers
ii  linux-generic-lts-trusty                    3.13.0.34.30                      Generic Linux kernel image and headers
ii  linux-headers-3.13.0-34                     3.13.0-34.60~precise1             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic             3.13.0-34.60~precise1             Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-36                      3.8.0-36.52~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-36-generic              3.8.0-36.52~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
pi  linux-headers-3.8.0-44                      3.8.0-44.66~precise1              Header files related to Linux kernel version 3.8.0
pi  linux-headers-3.8.0-44-generic              3.8.0-44.66~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-raring            3.8.0.44.44                       Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty            3.13.0.34.30                      Generic Linux kernel headers
ii  linux-image-3.13.0-34-generic               3.13.0-34.60~precise1             Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-36-generic                3.8.0-36.52~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-37-generic                3.8.0-37.53~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-38-generic                3.8.0-38.56~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-44-generic                3.8.0-44.66~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-trusty              3.13.0.34.30                      Generic Linux kernel image
ii  linux-libc-dev                              3.2.0-67.101                      Linux Kernel Headers for development

```

---

### Post by Bashing-om on 2014-08-19
bphillips2; Looks fair;

I am making to many errors that I do not see,. Quitting for this session.
In my am, as grub did not pick up and make the symbolic links. we will make them up.
and get back to the business of removing the headers.
That command should have been:
```

 sudo apt-get install --reinstall linux-image-3.8.0-44-generic

```
2 dashes before 'reinstall' !
The good news is that we are getting close to all cleaned up, and looking good !

[INDENT][INDENT]'till the next time
[INDENT][INDENT][INDENT]good night
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-19
bphillips2; Morning !

Let's remake those symbolic links that I destroyed:
```

sudo ln -s /boot/vmlinuz-3.8.0-44-generic /vmlinuz.old
sudo ln -s  /boot/initrd.img-3.8.0-44-generic /initrd.img.old
vmlinuz-3.8.0-44-generic
sudo update-grub

```

Look again - for my peace of mind - and see that the links are re-established:
```

ls -al /
ls -al /boot

```

Now we can go back to removing kernels and headers (drpal7).

[INDENT][INDENT][INDENT]it is a process
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-19
Outputs
```


justin@ubuntu:~$ sudo ln -s /boot/vmlinuz-3.8.0-44-generic /vmlinuz.old
[sudo] password for justin:
justin@ubuntu:~$

```
```

justin@ubuntu:~$ sudo ln -s  /boot/initrd.img-3.8.0-44-generic /initrd.img.old
justin@ubuntu:~$ 

```

There was a problem with this command
```



justin@ubuntu:~$ vmlinuz-3.8.0-44-generic
vmlinuz-3.8.0-44-generic: command not found
justin@ubuntu:~$ 



```
```

justin@ubuntu:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found initrd image: /boot/initrd.img-3.8.0-44-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found memtest86+ image: /memtest86+.bin
done

```
```





justin@ubuntu:~$ ls -al /
total 218
drwxr-xr-x  27 root     root      4096 Aug 19 09:57 .
drwxr-xr-x  27 root     root      4096 Aug 19 09:57 ..
drwx------   3 bacula   bacula    4096 Sep 24  2013 bacula
drwxr-xr-x   2 root     root      4096 Aug 14 13:32 bin
drwxr-xr-x   4 root     root      2048 Aug 18 22:38 boot
drwxr-xr-x   3 root     root      4096 Aug 26  2013 build
drwxr-xr-x  17 root     root      4360 Aug 19 09:57 dev
drwxr-xr-x 101 root     root      4096 Aug 19 09:57 etc
drwxr-xr-x   3 root     root      4096 Aug 26  2013 home
lrwxrwxrwx   1 root     root        33 Aug 14 13:32 initrd.img -> boot/initrd.img-3.13.0-34-generic
lrwxrwxrwx   1 root     root        33 Aug 19 09:57 initrd.img.old -> /boot/initrd.img-3.8.0-44-generic
drwxr-xr-x  17 root     root      4096 Jan 28  2014 lib
drwxr-xr-x   2 root     root      4096 Aug 13 22:49 lib64
drwx------   2 root     root     16384 Aug 26  2013 lost+found
drwxr-xr-x   3 root     root      4096 Aug 26  2013 media
drwxr-xr-x   2 root     root      4096 Aug 17  2013 mnt
drwxr-xr-x   2 memcache memcache  4096 Nov  1  2013 nonexistent
drwxr-xr-x   2 root     root      4096 Aug 26  2013 opt
drwxr-xr-x   6 root     root      4096 Jun  7  2012 powerpanel-1.2.3-0
-rw-r--r--   1 root     root     98998 Jun  8  2012 powerpanel_123_x86_64.tar.gz
dr-xr-xr-x 154 root     root         0 Aug 19 09:55 proc
drwx------   2 root     root      4096 Nov  5  2013 root
drwxr-xr-x  19 root     root       720 Aug 19 09:56 run
drwxr-xr-x   2 root     root     12288 Aug 13 22:51 sbin
drwxr-xr-x   2 root     root      4096 Mar  5  2012 selinux
drwxr-xr-x   2 root     root      4096 Aug 26  2013 srv
dr-xr-xr-x  13 root     root         0 Aug 19 09:55 sys
drwxrwxrwt   4 root     root     12288 Aug 19 09:58 tmp
drwxr-xr-x  10 root     root      4096 Aug 26  2013 usr
drwxr-xr-x  13 root     root      4096 Aug 19 09:56 var
lrwxrwxrwx   1 root     root        30 Aug 14 13:32 vmlinuz -> boot/vmlinuz-3.13.0-34-generic
lrwxrwxrwx   1 root     root        30 Aug 19 09:56 vmlinuz.old -> /boot/vmlinuz-3.8.0-44-generic

```
```



justin@ubuntu:~$ ls -al /boot
total 82334
drwxr-xr-x  4 root root     2048 Aug 18 22:38 .
drwxr-xr-x 27 root root     4096 Aug 19 09:57 ..
-rw-r--r--  1 root root  1162712 Aug 13 11:23 abi-3.13.0-34-generic
-rw-r--r--  1 root root   919810 Feb  3  2014 abi-3.8.0-36-generic
-rw-r--r--  1 root root   921155 Jul 14 23:22 abi-3.8.0-44-generic
-rw-r--r--  1 root root   165620 Aug 13 11:23 config-3.13.0-34-generic
-rw-r--r--  1 root root   154959 Feb  3  2014 config-3.8.0-36-generic
-rw-r--r--  1 root root   154959 Jul 14 23:22 config-3.8.0-44-generic
drwxr-xr-x  3 root root     5120 Aug 19 09:57 grub
-rw-r--r--  1 root root 19455614 Aug 14 13:32 initrd.img-3.13.0-34-generic
-rw-r--r--  1 root root 16837611 Feb 19 06:45 initrd.img-3.8.0-36-generic
-rw-r--r--  1 root root 17094882 Aug 18 22:38 initrd.img-3.8.0-44-generic
drwxr-xr-x  2 root root    12288 Aug 26  2013 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  3516562 Aug 13 11:23 System.map-3.13.0-34-generic
-rw-------  1 root root  3192822 Feb  3  2014 System.map-3.8.0-36-generic
-rw-------  1 root root  3196521 Jul 14 23:22 System.map-3.8.0-44-generic
-rw-------  1 root root  5883264 Aug 13 11:23 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  5454928 Feb  3  2014 vmlinuz-3.8.0-36-generic
-rw-------  1 root root  5461488 Jul 14 23:22 vmlinuz-3.8.0-44-generic

```

---

### Post by Bashing-om on 2014-08-19
bphillips2; looking good !

That "vmlinuz-3.8.0-44-generic" was a scratch padding I should have removed prior to posting - failed to see it ( still getting my morning coffee)
But no foul done.

Let's get a fresh look at the kernels - and on the same page for reference -:
```

dpkg -l | grep linux-

```

And let's finish this up.

[INDENT][INDENT][INDENT]all good things can come to an end
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-19
```

justin@ubuntu:~$ dpkg -l | grep linux-
ii  linux-firmware                              1.79.16                           Firmware for Linux kernel drivers
ii  linux-generic-lts-trusty                    3.13.0.34.30                      Generic Linux kernel image and headers
ii  linux-headers-3.13.0-34                     3.13.0-34.60~precise1             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic             3.13.0-34.60~precise1             Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-36                      3.8.0-36.52~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-36-generic              3.8.0-36.52~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
pi  linux-headers-3.8.0-44                      3.8.0-44.66~precise1              Header files related to Linux kernel version 3.8.0
pi  linux-headers-3.8.0-44-generic              3.8.0-44.66~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-raring            3.8.0.44.44                       Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty            3.13.0.34.30                      Generic Linux kernel headers
ii  linux-image-3.13.0-34-generic               3.13.0-34.60~precise1             Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-36-generic                3.8.0-36.52~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-37-generic                3.8.0-37.53~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-38-generic                3.8.0-38.56~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-44-generic                3.8.0-44.66~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-trusty              3.13.0.34.30                      Generic Linux kernel image
ii  linux-libc-dev                              3.2.0-67.101                      Linux Kernel Headers for development
```

---

### Post by Bashing-om on 2014-08-19
bphillips2; OK !

Do:
```

sudo apt-get autoremove linux-image-3.8.0-34-generic
sudo apt-get autoremove linux-image-3.8.0-36-generic
sudo apt-get autoremove linux-headers-3.8.0-34-generic
sudo apt-get autoremove linux-headers-3.8.0-34
sudo apt-get autoremove linux-headers-3.8.0-36-generic
sudo apt-get autoremove linux-headers-3.8.0-36

```

And once more:
```

dpkg -l | grep linux-

``` to see if there is any lingering elements to clean up. ( why -37 & -38 are marked 'rc' I presently do not know)

[INDENT][INDENT]close, real close
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-19
Here are the outputs
```

justin@ubuntu:~$ sudo apt-get autoremove linux-image-3.8.0-34-generic
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-3.8.0-34-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
```

justin@ubuntu:~$ sudo apt-get autoremove linux-image-3.8.0-36-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.8.0-36 linux-headers-3.8.0-36-generic linux-image-3.8.0-36-generic
0 upgraded, 0 newly installed, 3 to remove and 1 not upgraded.
After this operation, 249 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 121532 files and directories currently installed.)
Removing linux-headers-3.8.0-36-generic ...
Removing linux-headers-3.8.0-36 ...
Removing linux-image-3.8.0-36-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-36-generic /boot/vmlinuz-3.8.0-36-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-36-generic /boot/vmlinuz-3.8.0-36-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found initrd image: /boot/initrd.img-3.8.0-44-generic
Found memtest86+ image: /memtest86+.bin
done

```
```

justin@ubuntu:~$ sudo apt-get autoremove linux-headers-3.8.0-34-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-3.8.0-34-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
```

justin@ubuntu:~$ sudo apt-get autoremove linux-headers-3.8.0-34
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-3.8.0-34 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
```

justin@ubuntu:~$ sudo apt-get autoremove linux-headers-3.8.0-36-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-3.8.0-36-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
```

justin@ubuntu:~$ sudo apt-get autoremove linux-headers-3.8.0-36
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-3.8.0-36 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
justin@ubuntu:~$ 

```
```

justin@ubuntu:~$ dpkg -l | grep linux-
ii  linux-firmware                              1.79.16                           Firmware for Linux kernel drivers
ii  linux-generic-lts-trusty                    3.13.0.34.30                      Generic Linux kernel image and headers
ii  linux-headers-3.13.0-34                     3.13.0-34.60~precise1             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic             3.13.0-34.60~precise1             Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
pi  linux-headers-3.8.0-44                      3.8.0-44.66~precise1              Header files related to Linux kernel version 3.8.0
pi  linux-headers-3.8.0-44-generic              3.8.0-44.66~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-raring            3.8.0.44.44                       Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty            3.13.0.34.30                      Generic Linux kernel headers
ii  linux-image-3.13.0-34-generic               3.13.0-34.60~precise1             Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-36-generic                3.8.0-36.52~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-37-generic                3.8.0-37.53~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-38-generic                3.8.0-38.56~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-44-generic                3.8.0-44.66~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-trusty              3.13.0.34.30                      Generic Linux kernel image
ii  linux-libc-dev                              3.2.0-67.101                      Linux Kernel Headers for development

```

---

### Post by Bashing-om on 2014-08-19
bphillips2; Humm ..


Disappointed !
Not making a lot of sense is it ?

Let's see if we can fix the -44 header ( why did it break ? have not messed with it !)
```

sudo apt-get install linux-headers-3.8.0-44 inux-headers-3.8.0-44-generic 

```

And try and remove those old headers once more:
```

sudo dpkg -P linux-image-3.13.0-34-generic
sudo dpkg -P linux-headers-3.13.0-34
sudo dpkg -P linux-headers-3.13.0-34-generic

```

At least things are narrowed down to this small amount.

[INDENT][INDENT][INDENT]s l o w l y
[INDENT][INDENT][INDENT][INDENT]making progrss
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-19
```

justin@ubuntu:~$ sudo apt-get install linux-headers-3.8.0-44 inux-headers-3.8.0-44-generic
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-headers-3.8.0-44-generic' for regex 'inux-headers-3.8.0-44-generic'
linux-headers-3.8.0-44 is already the newest version.
linux-headers-3.8.0-44 set to manually installed.
linux-headers-3.8.0-44-generic is already the newest version.
linux-headers-3.8.0-44-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded

```
```

justin@ubuntu:~$ sudo dpkg -P linux-image-3.13.0-34-generic
dpkg: dependency problems prevent removal of linux-image-3.13.0-34-generic:
 linux-image-generic-lts-trusty depends on linux-image-3.13.0-34-generic.
dpkg: error processing linux-image-3.13.0-34-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.13.0-34-generic

```
```

justin@ubuntu:~$ sudo dpkg -P linux-headers-3.13.0-34
dpkg: dependency problems prevent removal of linux-headers-3.13.0-34:
 linux-headers-3.13.0-34-generic depends on linux-headers-3.13.0-34.
dpkg: error processing linux-headers-3.13.0-34 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.13.0-34

```
```

justin@ubuntu:~$ sudo dpkg -P linux-headers-3.13.0-34-generic
dpkg: dependency problems prevent removal of linux-headers-3.13.0-34-generic:
 linux-headers-generic-lts-trusty depends on linux-headers-3.13.0-34-generic.
dpkg: error processing linux-headers-3.13.0-34-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.13.0-34-generic

```

---

### Post by Bashing-om on 2014-08-19
bphillips2; Well, well ,

Not to much to work with .. could at least have given us a hint where the problem lies.
Let's see if the package manager will tell us anything else:
```

sudo apt-get -f install
sudo dpkg -C

```

else we go look'n

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-19
```

justin@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
```

justin@ubuntu:~$ sudo dpkg -C
justin@ubuntu:~$

```

---

### Post by Bashing-om on 2014-08-19
bphillips2; Humm, again ..
Package manager says he is as happy as a pig in sunshine;
Poke:
What returns:
```

apt-mark showauto | grep linux-image
apt-mark showmanual | grep linux-image

```
=============
And I messed this one up too // beats me where my mind was/is !
That is the current booting kernel !
We were good before I did that wrong turn:
let's try and fix this mess I made.
```

sudo apt-get install --reinstall linux-headers-3.13.0-34
sudo apt-get install --reinstall linux-headers-3.13.0-34-generic
sudo apt-get install --reinstall linux-image-3.13.0-34-generic

```

And once more get a new look:
```

dpkg -l | grep linux-

```

Again I do apologize .. I can not fathom where my mind was to not see what I NOT doing.

[INDENT][INDENT]I promise to slow down
[INDENT][INDENT][INDENT][INDENT]focus !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-19
```

justin@ubuntu:~$ apt-mark showauto | grep linux-image

```
```

justin@ubuntu:~$ apt-mark showmanual | grep linux-image
linux-image-3.13.0-34-generic
linux-image-3.8.0-44-generic
linux-image-generic-lts-trusty

```
```

justin@ubuntu:~$ sudo apt-get install --reinstall linux-headers-3.13.0-34
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/12.9 MB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package linux-headers-3.13.0-34.
(Reading database ... 93281 files and directories currently installed.)
Preparing to replace linux-headers-3.13.0-34 3.13.0-34.60~precise1 (using .../linux-headers-3.13.0-34_3.13.0-34.60~precise1_all.deb) ...
Unpacking replacement linux-headers-3.13.0-34 ...
Setting up linux-headers-3.13.0-34 (3.13.0-34.60~precise1) ...

```
```

justin@ubuntu:~$ sudo apt-get install --reinstall linux-headers-3.13.0-34-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/1,124 kB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package linux-headers-3.13.0-34-generic.
(Reading database ... 93281 files and directories currently installed.)
Preparing to replace linux-headers-3.13.0-34-generic 3.13.0-34.60~precise1 (using .../linux-headers-3.13.0-34-generic_3.13.0-34.60~precise1_amd64.deb) ...
Unpacking replacement linux-headers-3.13.0-34-generic ...
Setting up linux-headers-3.13.0-34-generic (3.13.0-34.60~precise1) ...

```
```

justin@ubuntu:~$ sudo apt-get install --reinstall linux-image-3.13.0-34-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/52.4 MB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package linux-image-3.13.0-34-generic.
(Reading database ... 93281 files and directories currently installed.)
Preparing to replace linux-image-3.13.0-34-generic 3.13.0-34.60~precise1 (using .../linux-image-3.13.0-34-generic_3.13.0-34.60~precise1_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.13.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Setting up linux-image-3.13.0-34-generic (3.13.0-34.60~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.13.0-34.60~precise1 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.13.0-34.60~precise1 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found initrd image: /boot/initrd.img-3.8.0-44-generic
Found memtest86+ image: /memtest86+.bin
done

```
```

justin@ubuntu:~$ dpkg -l | grep linux-
ii  linux-firmware                              1.79.16                           Firmware for Linux kernel drivers
ii  linux-generic-lts-trusty                    3.13.0.34.30                      Generic Linux kernel image and headers
ii  linux-headers-3.13.0-34                     3.13.0-34.60~precise1             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic             3.13.0-34.60~precise1             Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
pi  linux-headers-3.8.0-44                      3.8.0-44.66~precise1              Header files related to Linux kernel version 3.8.0
pi  linux-headers-3.8.0-44-generic              3.8.0-44.66~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-raring            3.8.0.44.44                       Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty            3.13.0.34.30                      Generic Linux kernel headers
ii  linux-image-3.13.0-34-generic               3.13.0-34.60~precise1             Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-36-generic                3.8.0-36.52~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-37-generic                3.8.0-37.53~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-38-generic                3.8.0-38.56~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-44-generic                3.8.0-44.66~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-trusty              3.13.0.34.30                      Generic Linux kernel image
ii  linux-libc-dev                              3.2.0-67.101                      Linux Kernel Headers for development

```

---

### Post by Bashing-om on 2014-08-19
bphillips2; recovering nicely .

let's put the kernels back under the package manager's control:
```

apt-mark markauto linux-image.*

```

and now back on :
> 
pi  linux-headers-3.8.0-44                      3.8.0-44.66~precise1              Header files related to Linux kernel version 3.8.0
pi  linux-headers-3.8.0-44-generic              3.8.0-44.66~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP

Where 'pi' is driving me nuts. 'pi' for 'P'urged but some files remain 'I'nstalled.
As that is the backup kernel we must find a way to insure it is fully installed. The image is fully installed the headers are what are giving me the problem.

Let's try this:
```

sudo apt-get install --reinstall linux-headers-3.8.0-44
sudo apt-get install --reinstall linux-headers-3.8.0-44-generic

```
see if we get any hints.
Maybe of great bearing !
> 
linux-headers-3.8.0-44 set to manually installed.

I bet next we also set the headers as "auto" ! We will see.

[INDENT][INDENT][INDENT]gotta be a way
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-19
Here is the output

```

justin@ubuntu:~$ apt-mark markauto linux-image.*
E: Failed to write temporary StateFile /var/lib/apt/extended_states.tmp

```
```

justin@ubuntu:~$ sudo apt-get install --reinstall linux-headers-3.8.0-44
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/12.2 MB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package linux-headers-3.8.0-44.
(Reading database ... 93281 files and directories currently installed.)
Preparing to replace linux-headers-3.8.0-44 3.8.0-44.66~precise1 (using .../linux-headers-3.8.0-44_3.8.0-44.66~precise1_all.deb) ...
Unpacking replacement linux-headers-3.8.0-44 ...
Setting up linux-headers-3.8.0-44 (3.8.0-44.66~precise1) ...

```
```

justin@ubuntu:~$ sudo apt-get install --reinstall linux-headers-3.8.0-44-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/1,002 kB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package linux-headers-3.8.0-44-generic.
(Reading database ... 93281 files and directories currently installed.)
Preparing to replace linux-headers-3.8.0-44-generic 3.8.0-44.66~precise1 (using .../linux-headers-3.8.0-44-generic_3.8.0-44.66~precise1_amd64.deb) ...
Unpacking replacement linux-headers-3.8.0-44-generic ...
Setting up linux-headers-3.8.0-44-generic (3.8.0-44.66~precise1) ...

```

---

### Post by Bashing-om on 2014-08-19
bphillips2; Well.

Looks promising !
And seems I got some more home work to do on:
> 
justin@ubuntu:~$ apt-mark markauto linux-image.*
E: Failed to write temporary StateFile /var/lib/apt/extended_states.tmp

unexpected result, and I do not know what it means.

I bet now we are looking much the better,
Let's look now:
```

sudo dpkg -l | grep linux-

```
I do hope there is but a small amount of cleanup ('rc') to be done. That one "should" be no big deal at all.
and we can come back to the "automark" issue.

[INDENT][INDENT]I think it is forward progress
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-19
Here's where we are at

```

justin@ubuntu:~$ sudo dpkg -l | grep linux-
[sudo] password for justin: 
ii  linux-firmware                              1.79.16                           Firmware for Linux kernel drivers
ii  linux-generic-lts-trusty                    3.13.0.34.30                      Generic Linux kernel image and headers
ii  linux-headers-3.13.0-34                     3.13.0-34.60~precise1             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic             3.13.0-34.60~precise1             Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-44                      3.8.0-44.66~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-44-generic              3.8.0-44.66~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-raring            3.8.0.44.44                       Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty            3.13.0.34.30                      Generic Linux kernel headers
ii  linux-image-3.13.0-34-generic               3.13.0-34.60~precise1             Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-36-generic                3.8.0-36.52~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-37-generic                3.8.0-37.53~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-38-generic                3.8.0-38.56~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-44-generic                3.8.0-44.66~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-trusty              3.13.0.34.30                      Generic Linux kernel image
ii  linux-libc-dev                              3.2.0-67.101                      Linux Kernel Headers for development

```

---

### Post by Bashing-om on 2014-08-19
bphillips2; We are indeed looking good !

OK:
The state is rc, the package is removed, but the config files are not removed. 
Now let’s remove all the kernels marked as rc.
You can remove all configuration data from every removed package with the following command.
```

sudo dpkg -l | awk '/^rc/{print $2}' | sudo xargs dpkg -P 

```

And once more check the progress:
```

sudo dpkg -l | grep linux-

```
and we see them gone gone.

And now for the long awaited:
Let's see if we can remove 'drupal7' !
```

sudo apt-get remove --purge drupal7

```

Pending: -> "automark" -> home work to be done.

[INDENT][INDENT][INDENT]a long road but but
[INDENT][INDENT][INDENT]the end is in sight
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-19
The system got stuck on the first code so I didn't go any further.  I tried splitting the first command into two.  I received the first output but the second one just added a new blank line and sat there for 10 minutes.  Had to ctrl-C to get out of it.

```

justin@ubuntu:~$ sudo dpkg -l | awk '/^rc/{print $2}'
linux-image-3.8.0-36-generic
linux-image-3.8.0-37-generic
linux-image-3.8.0-38-generic
justin@ubuntu:~$ sudo xargs dpkg -P
justin@ubuntu:~$ sudo dpkg -l | awk '/^rc/{print $2}'
linux-image-3.8.0-36-generic
linux-image-3.8.0-37-generic
linux-image-3.8.0-38-generic
justin@ubuntu:~$ sudo xargs dpkg -Pjustin@ubuntu:~$ sudo dpkg -l | awk '/^rc/{print $2}'
linux-image-3.8.0-36-generic
linux-image-3.8.0-37-generic
linux-image-3.8.0-38-generic
justin@ubuntu:~$ sudo xargs dpkg -P
```

---

### Post by Bashing-om on 2014-08-19
bphillips2; youch !

I think it is a no no to use 'awk' in this context:
let's do it as :
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Now that looks much cleaner.

[INDENT][INDENT]maybe yes 
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-19
That appeared to work

```

justin@ubuntu:~$ dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
(Reading database ... 93280 files and directories currently installed.)
Removing linux-image-3.8.0-36-generic ...
Purging configuration files for linux-image-3.8.0-36-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-36-generic /boot/vmlinuz-3.8.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-36-generic /boot/vmlinuz-3.8.0-36-generic
Removing linux-image-3.8.0-37-generic ...
Purging configuration files for linux-image-3.8.0-37-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
Removing linux-image-3.8.0-38-generic ...
Purging configuration files for linux-image-3.8.0-38-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic

```

---

### Post by Bashing-om on 2014-08-19
bphillips2; Yeah ! Much better.

Verify:
```

sudo dpkg -l | grep linux-

```

and try:
```

sudo apt-get remove --purge drupal7

``` and let's see what happens.

[INDENT][INDENT][INDENT]look'n doner alla the time
[/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-19
```

justin@ubuntu:~$ sudo dpkg -l | grep linux-
ii  linux-firmware                              1.79.16                           Firmware for Linux kernel drivers
ii  linux-generic-lts-trusty                    3.13.0.34.30                      Generic Linux kernel image and headers
ii  linux-headers-3.13.0-34                     3.13.0-34.60~precise1             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic             3.13.0-34.60~precise1             Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-44                      3.8.0-44.66~precise1              Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-44-generic              3.8.0-44.66~precise1              Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-raring            3.8.0.44.44                       Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty            3.13.0.34.30                      Generic Linux kernel headers
ii  linux-image-3.13.0-34-generic               3.13.0-34.60~precise1             Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-44-generic                3.8.0-44.66~precise1              Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-trusty              3.13.0.34.30                      Generic Linux kernel image
ii  linux-libc-dev                              3.2.0-67.101                      Linux Kernel Headers for development

```
```

justin@ubuntu:~$ sudo apt-get remove --purge drupal7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dbconfig-common wwwconfig-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  drupal7*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 12.1 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 93280 files and directories currently installed.)
Removing drupal7 ...
Purging configuration files for drupal7 ...
dpkg: warning: while removing drupal7, directory '/var/lib/drupal7/files' not empty so not removed.

```

---

### Post by Bashing-om on 2014-08-19
bphillips2; Welp !

Are we good, or what !

Al that remains is a bit of clean up.
> 
dpkg: warning: while removing drupal7, directory '/var/lib/drupal7/files' not empty so not removed.

So need to look into that directory, see if anything there you want to save; then delete the files and directory(s).

All that is left of this mess is my homework to set the kernels to "automark".

[INDENT][INDENT]can you believe that 
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-19
Ok.  Nothing in there to keep.  Got that erased

---

### Post by Bashing-om on 2014-08-19
bphillips2; Good deal:

Doing that homework and it looks like we encountered a bug:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1175637](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1175637)
and if this is what we experienced, the mark will be changed at the next kernel update.

It has my interest and still investigating.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-21
bphillips2; Welp;

In my "homework" I did find that debian also has a similar bug report. The advisement is the same, that when a new kernel is installed the mark will then be changed.
I can not find where the developers advise where in the code this happens and it is far above my abilities to know. 

If all is well with your system at this time; ( the fat lady sings !)
How about closing this thread solved
and we will pick up any new issues in new threads ?

I do wish
[INDENT][INDENT][INDENT]happy trails to you [/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-21
That's fine by me.  I'm perfectly happy with how the system is now.

I can't begin to tell you how much I appreciate your help with this! You have gone far above and beyond! Thank you so much!

---

### Post by Bashing-om on 2014-08-21
bphillips2; Hey, just great !

I am glad I was of assistance, it sure kept me entertained !
To mark as solved; top of post -> thread tools.

[INDENT][INDENT]I look forward to
[INDENT][INDENT][INDENT]our next adventure
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-21
Marked as solved.  Thanks again!

---

### Post by Bashing-om on 2014-08-29
bphillips2; Hey !

I have not forget. Want to insure ALL is still great. There is a now an update for the kernel "3.13.0-35-generic" this day.
Install it and let's see what the status is now:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

[INDENT][INDENT]all be hunky dory 
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-08-29
Thanks for following up with this! I did the upgrade, I'm not sure if it worked though.  Here are the outputs

```

justin@ubuntu:~$ sudo apt-get update
[sudo] password for justin: 
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]       
Get:2 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]                
Hit http://us.archive.ubuntu.com precise Release                                        
Get:3 http://us.archive.ubuntu.com precise-updates Release [98.7 kB]
Get:4 http://security.ubuntu.com precise-security Release.gpg [198 B]           
Get:5 http://us.archive.ubuntu.com precise-backports Release [50.8 kB]                     
Get:6 http://security.ubuntu.com precise-security Release [50.7 kB]              
Hit http://us.archive.ubuntu.com precise/main Sources                                      
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main amd64 Packages
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:7 http://us.archive.ubuntu.com precise-updates/main Sources [478 kB]
Get:8 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:9 http://us.archive.ubuntu.com precise-updates/universe Sources [109 kB]
Get:10 http://security.ubuntu.com precise-security/main Sources [109 kB]      
Get:11 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]       
Get:12 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [830 kB]      
Get:13 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [13.7 kB]   
Get:14 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [246 kB]         
Get:15 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]  
Get:16 http://us.archive.ubuntu.com precise-updates/main i386 Packages [861 kB]   
Get:17 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]  
Get:18 http://security.ubuntu.com precise-security/universe Sources [32.3 kB]              
Get:19 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]    
Get:20 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]
Get:21 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex           
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Get:22 http://us.archive.ubuntu.com precise-backports/main Sources [5,145 B]
Get:23 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:24 http://us.archive.ubuntu.com precise-backports/universe Sources [39.4 kB]
Get:25 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B]
Get:26 http://security.ubuntu.com precise-security/main amd64 Packages [420 kB]
Get:27 http://us.archive.ubuntu.com precise-backports/multiverse Sources [5,737 B]           
Get:28 http://us.archive.ubuntu.com precise-backports/main amd64 Packages [6,412 B]          
Get:29 http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]        
Get:30 http://us.archive.ubuntu.com precise-backports/universe amd64 Packages [42.4 kB]  
Get:31 http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages [5,405 B]    
Get:32 http://us.archive.ubuntu.com precise-backports/main i386 Packages [6,420 B]            
Get:33 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]         
Get:34 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [42.2 kB]   
Get:35 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [5,399 B]     
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex                      
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex    
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex    
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex      
Hit http://us.archive.ubuntu.com precise/main Translation-en                      
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                
Hit http://us.archive.ubuntu.com precise/universe Translation-en                  
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en              
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en      
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Get:36 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:37 http://security.ubuntu.com precise-security/universe amd64 Packages [96.5 kB]
Get:38 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,451 B]
Get:39 http://security.ubuntu.com precise-security/main i386 Packages [450 kB]
Get:40 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:41 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]
Get:42 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 4,441 kB in 4s (998 kB/s)
Reading package lists... Done

```
```

justin@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apport postfix python-apport python-problem-report
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,555 kB of archives.
After this operation, 5,120 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python-problem-report all 2.0.1-0ubuntu17.7 [9,452 B]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python-apport all 2.0.1-0ubuntu17.7 [79.3 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apport all 2.0.1-0ubuntu17.7 [149 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main postfix amd64 2.9.6-1~12.04.2 [1,318 kB]
Fetched 1,555 kB in 0s (1,865 kB/s)
Preconfiguring packages ...
(Reading database ... 121731 files and directories currently installed.)
Preparing to replace python-problem-report 2.0.1-0ubuntu17.6 (using .../python-problem-report_2.0.1-0ubuntu17.7_all.deb) ...
Unpacking replacement python-problem-report ...
Preparing to replace python-apport 2.0.1-0ubuntu17.6 (using .../python-apport_2.0.1-0ubuntu17.7_all.deb) ...
Unpacking replacement python-apport ...
Preparing to replace apport 2.0.1-0ubuntu17.6 (using .../apport_2.0.1-0ubuntu17.7_all.deb) ...
apport stop/waiting
Unpacking replacement apport ...
Preparing to replace postfix 2.9.6-1~12.04.1 (using .../postfix_2.9.6-1~12.04.2_amd64.deb) ...
 * Stopping Postfix Mail Transport Agent postfix                                                                                                                 [ OK ] 
 * Stopping Postfix Mail Transport Agent postfix                                                                                                                 [ OK ] 
Unpacking replacement postfix ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Setting up python-problem-report (2.0.1-0ubuntu17.7) ...
Setting up python-apport (2.0.1-0ubuntu17.7) ...
Setting up apport (2.0.1-0ubuntu17.7) ...
apport start/running
Setting up postfix (2.9.6-1~12.04.2) ...


Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).


After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.


Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                                                                                                                 [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                                                                                                                 [ OK ] 
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```
```



justin@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Bashing-om on 2014-08-29
bphillips2' Hey;

Looks good, but no new kernel ! // As you are running 'precise' with the HWE, I guess the new kernel has not made it down the pipe to that release.
Maybe I jumped the gun here.
We wait, and see what transpires.

[INDENT][INDENT]we be patient some more
[/INDENT][/INDENT]

---

### Post by bphillips2 on 2014-09-01
Sounds good.

---

