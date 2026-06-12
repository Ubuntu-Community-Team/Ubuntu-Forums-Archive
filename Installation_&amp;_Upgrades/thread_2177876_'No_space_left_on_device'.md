---
title: "'No space left on device'"
date: 2013-09-30
forum: Installation &amp; Upgrades
---

### Post by zurga on 2013-09-30
```
james@ubuntu:~$ uname -a
Linux ubuntu 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:09:12 UTC 2013 i686 i686 i386 GNU/Linux
james@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise


```

The software updater attempted to install some linux headers, but failed due to unmet dependencies. To fix the problem I tried apt-get as follows:
```
james@ubuntu:~$ sudo apt-get -f install
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-54 linux-headers-3.2.0-54-generic-pae
The following NEW packages will be installed
  linux-headers-3.2.0-54 linux-headers-3.2.0-54-generic-pae
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/12.7 MB of archives.
After this operation, 67.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 1027830 files and directories currently installed.)
Unpacking linux-headers-3.2.0-54 (from .../linux-headers-3.2.0-54_3.2.0-54.82_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-54_3.2.0-54.82_all.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.2.0-54/Documentation': [COLOR=#ff0000]No space left on device[/COLOR]
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-54-generic-pae (from .../linux-headers-3.2.0-54-generic-pae_3.2.0-54.82_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-54-generic-pae_3.2.0-54.82_i386.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.2.0-54-generic-pae/include/config/ecrypt': [COLOR=#ff0000]No space left on device[/COLOR]
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-54_3.2.0-54.82_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-54-generic-pae_3.2.0-54.82_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

and this too failed. It is really strange that apt-get reports "No space left on device" when we have a free space of 130GB available. It is not now possible to use apt-get for any purpose, as it will immediately find the unmet dependencies and stops. The software updater also has shut down for the same reason. There are two questions:
[LIST=1]
[*]Is the problem caused by some corruption of my software/data in my computer, or is it some problem with the latest system updates? 
[*]How can I climb out of this cul-de-sac? 
[/LIST]
Many thanks

---

### Post by Bashing-om on 2013-09-30
zurga; Hi !

The general thing we see here with those conditions is your /boot directory is full (old kernels).
The following command is useful for finding out which directories are using all your space...
```

du -h --max-depth=1 | sort -hr

```
and going directly to the suspected heart of the situation:
```

dpkg -l | grep linux-image 
ls -la /boot

```
 If it does turn out to be a full /boot directory. it is "generally" not that difficult to clean up.

Think the above answers both your questions.

[INDENT][INDENT]a tale in the telling
[/INDENT][/INDENT]

---

### Post by zurga on 2013-10-01
Bashing-om Thank you for responding to my questions.
From your comment I infer that the error report "No space left on device" does not refer to the space left on the main drive (more than 120 GB), but to space specifically allocated to the boot kernel or some such: is that correct?
Acting on the assumption that /boot is too full I did:
```
$ du -h /boot
16K    /boot/grub/locale
4.3M    /boot/grub
576M    /boot
```
Also, listing the files in /boot, I find many old versions of the following types of files:
```
abi-*-generic
config-*-generic
initrd.img-*-generic
System.map-*-generic
vmlinuz-*-generic
```
I assume that it is safe to remove these except the latest few by ordinary commands such as 'mv' which would create a temporary backup. If so, then hopefully the saved space in /boot will enable 'apt-get' to become operational again. Then I will be able to purge old kernel files of which there are many.
Thanks for your help.

---

### Post by Bashing-om on 2013-10-01
zurga;
Your understanding of the space usage is correct.
In this instance from your advisements, I do not see the /boot directory as a problem.

what results from :
```

df -i

```

too see what the inode situation is. As out of inodes will produce the same errors.
As to removing old kernels.
To install any thing installed use the package manager ! .. Else dependencies and config files resolvement will drive you insane. Manually removing files related to the kernel is a chore !

The GUI method is via "synaptic" package manager; or,
from the command line a procedure I prefer:
```

uname -r ##identify the kernel you are presently booting DO NOT remove this one ! Keep one other for a back up.
dpkg -l | grep linux-image- ##identify all installed kernel images
dpkg -l | grep linux-headers- ##identify all kernel header files
sudo apt-get --purge remove linux-image-3.2.0-31-generic ##for example
sudo apt-get --purge remove linux-headers-3.2.0-31-generic ##for example

```
Run the "dpkg" commands once more and I expect you will see files marked as "rc" -(R)emoved but (C)onfig files remain.

While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command.
```

dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg

```

Now if you prefer the GUI method instead, I will provide guidance for it also.

[INDENT][INDENT]we wont know 'till we know
[/INDENT][/INDENT]

---

### Post by zurga on 2013-10-02
Bashing-om

Following is list of inodes as you suggested. They are only 1% used, so they do not seem to be the problem - except /dev/loop0:
```
$ df -ih
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/loop0       1.1M  1.1M   317  100% /
udev             208K   545  207K    1% /dev
tmpfs            211K   462  211K    1% /run
none             211K     3  211K    1% /run/lock
none             211K     8  211K    1% /run/shm
/dev/sda5        123M   28K  123M    1% /host
/dev/sda3         86M  178K   86M    1% /home/zurga/mnt/c-disk
```
And also just for the record:
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       17G   12G  3.7G  76% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           579M  868K  579M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  160K  1.5G   1% /run/shm
/dev/sda5       147G   24G  123G  17% /host
/dev/sda3       143G   57G   86G  40% /home/zurga/mnt/c-disk
```
For the purpose of this discussion /dev/sda3 should be entirely disregarded as an external device.

I am fully aware of the risk entailed in the manual modification of installed files, due to possible violation of dependencies, and would not ordinarily contemplate such action. However the problem in this case is that apt-get is not operational and cannot be used. As for prference between using gui or command line, I far prefer the latter as only it will give me a documented and verifiable method for performing a task. As a matter of curiousity, I would like to know what criteria determine whether too much space is occupied by old kernels in the /boot.

Thanks again for your help.

---

### Post by Bashing-om on 2013-10-02
zurga; Hi !

I still fail to see where the problem lies, in spite of my expectations.
We need to examine the "/usr" directory as per the error message:
> 
error creating directory `./usr/src/linux-headers-3.2.0-54/Documentation': No space left on device


As to apt-get, I anticipate it only has a problem installing any additional kernels and related installs, That should not effect it's ability to remove software from the system.

Headroom: Well as a general rule 85% capacity is generally considered max, the larger the partition the greater one may raise that percentage. As what you see is not really what you have in use... house keeping - disk file allocation info - and such, as well as "root's space" as dedicated space a normal user has no access to.

--------
Now I could be totally wrong .. but I would think purging kernels as related in the /boot directory that action would also remove the files residing in "/usr/src" directory.

Worth a shot and see what results.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by zurga on 2013-10-02
Hi Bashing-om

The oldest kernel version I have is 2.6.38-11. The one that is currently active, and suffers from unmet dependencies is 3.2.0-54. If I try to remove the oldest version:
```
$ sudo apt-get --purge remove linux-image-2.6.38-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-headers-3.2.0-54-generic : Depends: linux-headers-3.2.0-54 but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-54-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
you will see that it trips over the unmet dependencies, and suggests to use 'apt-get -f install'. And if I try to 'install' then I get the 'No space left on device'

Following indicates the state of /usr showing 100% inode usage:
```
$ df -h /usr
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       17G   12G  3.7G  76% /
$ df -ih /usr
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/loop0       1.1M  1.1M   281  100% /
```

What would happen if I remove the two packages that are broken, which also happen to be in the current kernel? That is if I succeed to remove them either directly by apt-get or through the Synaptic gui, will the system end up in no-mans-land, or will it end up in the previous generation of kernel which was in good working order?

Thanks.

---

### Post by Bashing-om on 2013-10-02
zurga; Well good. The problem is identified !


Can you boot an older kernel with no problem booting ? Preferably a kernel directly under the problem kernel version.
and:
Show me the output of :
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```

and I will craft us a "dpkg" code and see if dpkg can get us out of this hole. As I have said we do not want to go the manual method to hunt up all those files to remove !
Apt-get is a front end for the base of the package manager "dpkg" . We can use "dpkg" directly and sometime to greater effect.

[INDENT][INDENT][/INDENT][/INDENT]

---

### Post by zurga on 2013-10-02
Hi Bashing
So what is the problem? As you suggested I booted on the previous kernel version 3.2.0-53 and listed the following as you suggested:
```
$ uname -r
3.2.0-53-generic

$ dpkg -l | grep linux-image-
ii  linux-image-2.6.38-11-generic          2.6.38-11.50                               Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-2.6.38-8-generic           2.6.38-8.42                                Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-3.0.0-12-generic           3.0.0-12.20                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-13-generic           3.0.0-13.22                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-14-generic           3.0.0-14.23                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-15-generic           3.0.0-15.26                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-16-generic           3.0.0-16.29                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-17-generic           3.0.0-17.30                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-19-generic           3.0.0-19.33                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-20-generic           3.0.0-20.34                                Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.2.0-24-generic           3.2.0-24.39                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-25-generic           3.2.0-25.40                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-26-generic           3.2.0-26.41                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-27-generic           3.2.0-27.43                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-29-generic           3.2.0-29.46                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-30-generic           3.2.0-30.48                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-31-generic           3.2.0-31.50                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-generic           3.2.0-32.51                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic           3.2.0-33.52                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic           3.2.0-34.53                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic           3.2.0-35.55                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-36-generic           3.2.0-36.57                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-generic           3.2.0-37.58                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-38-generic           3.2.0-38.61                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-generic           3.2.0-39.62                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-40-generic           3.2.0-40.64                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-41-generic           3.2.0-41.66                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-43-generic           3.2.0-43.68                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-44-generic           3.2.0-44.69                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-45-generic           3.2.0-45.70                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-48-generic           3.2.0-48.74                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-49-generic           3.2.0-49.75                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-51-generic           3.2.0-51.77                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-52-generic           3.2.0-52.78                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic           3.2.0-53.81                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-54-generic           3.2.0-54.82                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.54.64                                Generic Linux kernel image

$ dpkg -l | grep linux-headers
ii  linux-headers-3.2.0-25                 3.2.0-25.40                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-25-generic         3.2.0-25.40                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-25-generic-pae     3.2.0-25.40                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-26                 3.2.0-26.41                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-26-generic         3.2.0-26.41                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-26-generic-pae     3.2.0-26.41                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-27                 3.2.0-27.43                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-27-generic         3.2.0-27.43                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-27-generic-pae     3.2.0-27.43                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-29                 3.2.0-29.46                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-29-generic         3.2.0-29.46                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-29-generic-pae     3.2.0-29.46                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-30                 3.2.0-30.48                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-30-generic         3.2.0-30.48                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-30-generic-pae     3.2.0-30.48                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-31                 3.2.0-31.50                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic         3.2.0-31.50                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-31-generic-pae     3.2.0-31.50                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-32                 3.2.0-32.51                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic         3.2.0-32.51                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-32-generic-pae     3.2.0-32.51                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-33                 3.2.0-33.52                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-33-generic         3.2.0-33.52                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-33-generic-pae     3.2.0-33.52                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-34                 3.2.0-34.53                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-34-generic         3.2.0-34.53                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-34-generic-pae     3.2.0-34.53                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-35                 3.2.0-35.55                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic         3.2.0-35.55                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-35-generic-pae     3.2.0-35.55                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-36                 3.2.0-36.57                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic         3.2.0-36.57                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-36-generic-pae     3.2.0-36.57                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-37                 3.2.0-37.58                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic         3.2.0-37.58                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-37-generic-pae     3.2.0-37.58                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38                 3.2.0-38.61                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic         3.2.0-38.61                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38-generic-pae     3.2.0-38.61                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-39                 3.2.0-39.62                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-39-generic         3.2.0-39.62                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-39-generic-pae     3.2.0-39.62                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-40                 3.2.0-40.64                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic         3.2.0-40.64                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-40-generic-pae     3.2.0-40.64                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-41                 3.2.0-41.66                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic         3.2.0-41.66                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-41-generic-pae     3.2.0-41.66                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-43                 3.2.0-43.68                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-43-generic         3.2.0-43.68                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-43-generic-pae     3.2.0-43.68                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-44                 3.2.0-44.69                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic         3.2.0-44.69                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-44-generic-pae     3.2.0-44.69                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-45                 3.2.0-45.70                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-45-generic         3.2.0-45.70                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-45-generic-pae     3.2.0-45.70                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-48                 3.2.0-48.74                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic         3.2.0-48.74                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-48-generic-pae     3.2.0-48.74                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-49                 3.2.0-49.75                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic         3.2.0-49.75                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-49-generic-pae     3.2.0-49.75                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51                 3.2.0-51.77                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic         3.2.0-51.77                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51-generic-pae     3.2.0-51.77                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52                 3.2.0-52.78                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic         3.2.0-52.78                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52-generic-pae     3.2.0-52.78                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53                 3.2.0-53.81                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic         3.2.0-53.81                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53-generic-pae     3.2.0-53.81                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
iU  linux-headers-3.2.0-54-generic         3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
iU  linux-headers-generic                  3.2.0.54.64                                Generic Linux kernel headers
iU  linux-headers-generic-pae              3.2.0.54.64                                Generic Linux kernel headers


```
Awaiting your response with abated breath! Thanks.

---

### Post by Bashing-om on 2013-10-03
zurga; Sorry for the delay in getting back at ya .. system problems happen to the best of us - my grub could not find my hard drives when I rebooted !

To you, lets try; making sure you are booting the  3.2.0-53 kernel :
Copy and paste ::
```

sudo dpkg -P linux-image-3.2.0-{24,25,26,27,29,30,31,32,33,34,35,36,37,39,40,41,43,44,45,48,49,54}-generic
sudo dpkg -P linux-headers-3.2.0-{24,25,26,27,29,30,31,32,33,34,35,36,37,39,40,41,43,44,45,48,49,54}-generic

```

And look again and see what there is now to clean up:
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```

As to what is going on, I assume from the references to repeated "/dev/loop0" and it being related to the directory  "/usr" .. that this is a wubi install .. and as such the virtual disk is full ! Please verify my thought.

Give this a try .. and 
[INDENT][INDENT][INDENT]my fingers are crossed
[/INDENT][/INDENT][/INDENT]

---

### Post by zurga on 2013-10-03
Hi Bashing-om

We are obviouly living in very different time zones, so I hope you do get to sleep sometimes.
Yes, my installation is a la wubi, which means that half of my pc is wasted on Windows 7 that I never use.

The images did purge successfully, except the 54 due to the dependency problem. Headers all purged fine. And there is no doubt which image I have booted on:
```
$ uname -r
3.2.0-53-generic
```

This is what we have left now:

```
~$ dpkg -l | grep linux-image-
ii  linux-image-2.6.38-11-generic          2.6.38-11.50                               Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-2.6.38-8-generic           2.6.38-8.42                                Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-3.0.0-12-generic           3.0.0-12.20                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-13-generic           3.0.0-13.22                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-14-generic           3.0.0-14.23                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-15-generic           3.0.0-15.26                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-16-generic           3.0.0-16.29                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-17-generic           3.0.0-17.30                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-19-generic           3.0.0-19.33                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-20-generic           3.0.0-20.34                                Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.2.0-38-generic           3.2.0-38.61                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-51-generic           3.2.0-51.77                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-52-generic           3.2.0-52.78                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic           3.2.0-53.81                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
pi  linux-image-3.2.0-54-generic           3.2.0-54.82                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.54.64                                Generic Linux kernel image
$ dpkg -l | grep linux-headers
ii  linux-headers-3.2.0-25                 3.2.0-25.40                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-25-generic-pae     3.2.0-25.40                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-26                 3.2.0-26.41                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-26-generic-pae     3.2.0-26.41                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-27                 3.2.0-27.43                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-27-generic-pae     3.2.0-27.43                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-29                 3.2.0-29.46                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-29-generic-pae     3.2.0-29.46                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-30                 3.2.0-30.48                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-30-generic-pae     3.2.0-30.48                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-31                 3.2.0-31.50                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic-pae     3.2.0-31.50                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-32                 3.2.0-32.51                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic-pae     3.2.0-32.51                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-33                 3.2.0-33.52                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-33-generic-pae     3.2.0-33.52                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-34                 3.2.0-34.53                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-34-generic-pae     3.2.0-34.53                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-35                 3.2.0-35.55                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic-pae     3.2.0-35.55                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-36                 3.2.0-36.57                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic-pae     3.2.0-36.57                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-37                 3.2.0-37.58                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic-pae     3.2.0-37.58                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38                 3.2.0-38.61                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic         3.2.0-38.61                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38-generic-pae     3.2.0-38.61                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-39                 3.2.0-39.62                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-39-generic-pae     3.2.0-39.62                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-40                 3.2.0-40.64                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic-pae     3.2.0-40.64                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-41                 3.2.0-41.66                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic-pae     3.2.0-41.66                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-43                 3.2.0-43.68                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-43-generic-pae     3.2.0-43.68                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-44                 3.2.0-44.69                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic-pae     3.2.0-44.69                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-45                 3.2.0-45.70                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-45-generic-pae     3.2.0-45.70                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-48                 3.2.0-48.74                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic-pae     3.2.0-48.74                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-49                 3.2.0-49.75                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic-pae     3.2.0-49.75                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51                 3.2.0-51.77                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic         3.2.0-51.77                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51-generic-pae     3.2.0-51.77                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52                 3.2.0-52.78                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic         3.2.0-52.78                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52-generic-pae     3.2.0-52.78                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53                 3.2.0-53.81                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic         3.2.0-53.81                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53-generic-pae     3.2.0-53.81                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
iU  linux-headers-generic                  3.2.0.54.64                                Generic Linux kernel headers
iU  linux-headers-generic-pae             3.2.0.54.64                                Generic Linux kernel headers  
```

After the purge, I did try to fix the two broken packages, and it appears I succeeded.So I really appreciate your working so hard on this and my many thanks. I still need to spend a little more time to be confident that all is well.

---

### Post by Bashing-om on 2013-10-03
zurga; To be honest I almost live and breath this Operating system on this earth !

But to continued cleanup of your system:
```

sudo apt-get purge linux-headers-3.2.0-{25,26,27,29,31,32,33,34,35,36,37,38,39,40,41,43,44,49,51,52}-generic-pae

```
And another refresh to see what is yet to be done !

```

dpkg -l | grep linux-headers-

```
Just because I am a one-step-at-a-time kinda guy.
Slowly getting there and making good progress.
[INDENT][INDENT]step by step - inch by inch
[/INDENT][/INDENT]

---

### Post by zurga on 2013-10-03
Hi Bashing

I had already cleaned up the other two header types linux-headers-3.2.0-* and linux-headers-3.2.0-*-generic-pae, and the good thing is that /dev/loop0 inodes are now only 37% used.

The headers are now just the few latest ones:
```
$ dpkg -l | grep linux-headers
ii  linux-headers-3.2.0-38                 3.2.0-38.61                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic         3.2.0-38.61                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38-generic-pae     3.2.0-38.61                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51                 3.2.0-51.77                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic         3.2.0-51.77                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51-generic-pae     3.2.0-51.77                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52                 3.2.0-52.78                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic         3.2.0-52.78                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52-generic-pae     3.2.0-52.78                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53                 3.2.0-53.81                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic         3.2.0-53.81                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53-generic-pae     3.2.0-53.81                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54                 3.2.0-54.82                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic         3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54-generic-pae     3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic                  3.2.0.54.64                                Generic Linux kernel headers
ii  linux-headers-generic-pae              3.2.0.54.64                                Generic Linux kernel headers
```

I see that *38* set have escaped the purge, but they will go on the next clean up cycle. Obviously having gone through this experience, I shall keep a watch in future and clean up the kernels before there are too many. Perhaps it is not surprising that no general advice is issued to users concerning this problem, because such advice would not be noticed or remembered. But it would be a good idea if the update system would check space usage on each new kernel installation and would advise user to take action when a certain threshold is reached. You say you live on the op system, and I am glad you do, otherwise I might have been forced to take the nuclear option of re-installing Ubuntu from scratch.
Thanks.

---

### Post by Bashing-om on 2013-10-03
zurga; Well..
-38 looks to have been scheduled to have been removed. In any event let's slow down a bit and look for what the package manager advises:
```

sudo apt-get purge linux-headers-3.2.0-38
sudo apt-get purge linux-headers-3.2.0-38-generic
sudo apt-get purge linux-headers-3.2.0-38-generic-pae

```
And then continue cleaning up ..
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```
Bear in mind ,in the conclusion .. version between -images and -headers MUST match.

Are you now booting the -54 kernel ?

As to advisories for disk usage, I can not say about wubi .. in the normal install operating from a command line interface, that advisory does exist.
Speaking of the wubi (RE-)install... uhh, are you aware that wubi is no longer supported ? It might be time to install ubuntu as stand alone.; either as a dual boot or simply the primary sole operating system.

[INDENT][INDENT]Progress, we can see light !
[/INDENT][/INDENT]

---

### Post by zurga on 2013-10-03
Hi Bashing
We only have versions [51-54] now, and of course it is 54 that I am booting from.

```
$ dpkg -l | grep linux-image
ii  linux-image-3.2.0-51-generic           3.2.0-51.77                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-52-generic           3.2.0-52.78                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic           3.2.0-53.81                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
pi  linux-image-3.2.0-54-generic           3.2.0-54.82                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.54.64                                Generic Linux kernel image
$ dpkg -l | grep linux-headers
ii  linux-headers-3.2.0-51                 3.2.0-51.77                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic         3.2.0-51.77                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51-generic-pae     3.2.0-51.77                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52                 3.2.0-52.78                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic         3.2.0-52.78                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52-generic-pae     3.2.0-52.78                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53                 3.2.0-53.81                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic         3.2.0-53.81                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53-generic-pae     3.2.0-53.81                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54                 3.2.0-54.82                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic         3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54-generic-pae     3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic                  3.2.0.54.64                                Generic Linux kernel headers
ii  linux-headers-generic-pae              3.2.0.54.64                                Generic Linux kernel headers
```

I did not know that wubi is no longer supported. If I change my system, I would want to convert to a stand-alone ubuntu only, as I never use the Windows. I have to read up on this to determine the most optimum way of achieving this such that my own personal files currently in the Ubuntu space remain intact. I probably need to reformat the hard drive from its current NTFS to a more Ubuntu friendly format such as EXT3. If you have any advice or comment on the subject, it will of course be greatly appreciated.

Thanks.

---

### Post by Bashing-om on 2013-10-03
zurga; Hey !

All looking good. I think that should conclude this thread.

As to installing 'buntu: easy as falling out of bed wide awake.

-save your personal data to an outside medium- --> There is no way to preserve them that I know of.. Now to be fair, there is a procedure that is supposed to enable one to migrate the wubi install to hard disk ... But my advise is install from scratch. (then you have a liveDVD on hand for emergency/play use)

Download your preferred flavor's .iso (see some recommended options at the top of thread "ubuntu community");
verify the download integrity - md5sum;
Burn that .iso as an -image- to CD/DVD/USB or Pen Drive as wanted;
Set in bios as that device as 1st boot priority;
Boot the installMEDIUM into "try ubuntu" mode;
Test ya like all ya see/want/need within this "try ubuntu" ->all good;
Hit the install button and answer a few simple set up questions;
With a wired internet connection, in about 15 minutes, all done.

The install wizard does a standard install of the system if you choose the option "erase and use entire disk" that is quick, fast, and easy. You may if you know before hand how you want the partitioning done, set up before hand with GParted (available in the install disk); or with careful consideration choose from that options menu  "something else" -- I do the before hand with gparted -- however I do have the experience to know how the system is going to be used ( my wife's Lubuntu is a standard install .. leter rip Sam install"). There is also the third option to dual boot set up that is also equally painless.

The installer takes care of everything if ya want easy .

I hope to see you there !


To mark this thread "solved" - as an aid to others seeking a solution, and to help keep the forum tidy- 1st post ->thread tools.

[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

### Post by zurga on 2013-10-04
Bashing Hi

Yes all is well again and many thanks to you being so helpful.
Best wishes
Zurga

---

