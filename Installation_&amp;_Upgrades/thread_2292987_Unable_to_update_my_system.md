---
title: "Unable to update my system"
date: 2015-09-01
forum: Installation &amp; Upgrades
---

### Post by aab001 on 2015-09-01
Hi Every time I tried to update my system, I got the message "Not all updates can be installed" so I do the partial upgrade but also I got the message "Failed to run /usr/bin/update-manager '--dist-upgrade' as user root.

Unable to copy the user's Xauthorization file."

any Idea???/

---

### Post by Bashing-om on 2015-09-01
aab001; Humm ..

Peculiar, to say the least. As on my system, 14.04 :
> 
sysop@1404mini:~$ ls -al /usr/bin/update-manager
ls: cannot access /usr/bin/update-manager: No such file or directory
sysop@1404mini:~$

One has to wonder what is calling such a script ?
Take a look at the sources that the package manager is fetching.
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

And what in the world is :
> 
Unable to copy the user's Xauthorization file.

A new one on me .... What file could it be in reference to ?
Show what is in your /home :
```

ls -al /home/<user_name>/

```

Then, once we know what we are looking at .. and sources.list files are confrimed, we see what the package manager has to advise on the state of the system .

[INDENT][INDENT]just my ideas
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-09-01
Try running these and report any and all errors between code tags, please (see last link in my signature):

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

* Just saw bashing-om's post. Yes, xauth is odd. Let's see everything! :D

---

### Post by aab001 on 2015-09-01
Thank you all in advance,

sudo apt-get autoremove

```


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 



```

then,
```


aab@aab-Latitude-E6400:~$ sudo dpkg --configure -a
dpkg: error: failed to open '/var/lib/dpkg/status' for writing status database: No space left on device
aab@aab-Latitude-E6400:~$ 

 



```

---

### Post by Bashing-om on 2015-09-01
aab001; Sheesshh ...

3 steps back and only 1 forward.
OK:
> 
for writing status database: No space left on device

Let's find out what that is all about.
Post back the return:
```

df -h
df -i

```
To begin the process to find where the space constraint is.

[INDENT][INDENT]gotta have the operating head room 
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-09-01
There are 4 reasons why the system suggests running a Partial Update. which one applies to your system?

1) A previous upgrade which did not complete.
2) Problems with some of the installed software.
3) Unofficial software packages not provided by Ubuntu.
4) Normal changes of a pre-release version of Ubuntu.

Can you eliminate any in that list?

Regards.

---

### Post by aab001 on 2015-09-02
```


aab@aab-Latitude-E6400:~$ df -h
Filesystem          Size  Used Avail Use% Mounted on
/dev/sda6            33G   27G  3.6G  89% /
udev                992M  4.0K  992M   1% /dev
tmpfs               201M  1.2M  200M   1% /run
none                5.0M     0  5.0M   0% /run/lock
none               1001M  1.2M 1000M   1% /run/shm
/dev/sda7            72G   64G  4.6G  94% /home
/home/aab/.Private   72G   64G  4.6G  94% /home/aab
/dev/mmcblk0p1      7.5G  2.4G  5.1G  33% /media/266E-405B
aab@aab-Latitude-E6400:~$ df -i
Filesystem          Inodes   IUsed   IFree IUse% Mounted on
/dev/sda6          2138112 2138112       0  100% /
udev                213492     539  212953    1% /dev
tmpfs               218513     481  218032    1% /run
none                218513       3  218510    1% /run/lock
none                218513      10  218503    1% /run/shm
/dev/sda7          4784128   47445 4736683    1% /home
/home/aab/.Private 4784128   47445 4736683    1% /home/aab
/dev/mmcblk0p1           0       0       0     - /media/266E-405B

 



```


how can I release more space!!!

---

### Post by Bashing-om on 2015-09-02
aab001; Morning !

It is more of not having any more numbers to address any more files than anything else, though you are pushing the limits on several partitions. Running out of inodes. 

At 94% capacity, you are looking at file system problems in the making, You do need to devote some attention to creating another partition, and moving data from these partitions to the "data partition" . Is " /home/aab/.Private " a backup partition ? Consider making your backups to an external medium.

For the immediate concern is the inode issue in '/' :
The better course of action is to delete files in '/' to free up some inodes to allow the addressing of files.
To that end let us look at what can be and should be deleted.
```

cd /
sudo du -sx * | sort -n

```
Where 'du' is (D)isk (U)sage .
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes, (The "x" switch limits du to a single file system, in this case the root file system).

[INDENT][INDENT]can not put 11 pounds of sugar
[INDENT][INDENT][INDENT]in a 10 pound sack
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-09-03
using the code 
```


cd /
sudo du -sx * | sort -n

```I got the following but it took looong time!!!!
```


du: cannot access `proc/10872': No such file or directory
du: cannot access `proc/10873': No such file or directory
0    initrd.img
0    initrd.img.old
0    libnss3.so
0    proc
0    sys
0    vmlinuz
0    vmlinuz.old
4    cdrom
4    dev
4    mnt
4    selinux
4    srv
16    Dropbox
16    lost+found
52    media
1204    run
1788    root
8672    bin
8840    sbin
17176    tmp
20048    etc
108716    opt
1097140    boot
2259856    var
6824264    lib
17228904    usr
68466080    home
aab@aab-Latitude-E6400:/$ 



 



```

---

### Post by Bashing-om on 2015-09-03
aab001; Well ...

@VMC; Always a pleasure to see you drop in .
 
As we narrow things down to specifics.
We know that /boot is rather large;
We know that /home is huge .
Lets take a look at /boot and see what is to be done:
```

dpkg -l | grep linux-
ls -al /boot
uname -r

```

As to /home. need to move a LOT of stuff to an external storage media and delete them from the system. 

[INDENT][INDENT]small steps
[INDENT][INDENT][INDENT]progress made
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by VMC on 2015-09-03
I use a little more readable **du** comand:
```
sudo du --exclude=/proc --exclude=/run -schx /* | sort -hr | head -n 20
```

Also a great utility called '[**ncdu** (NCurses Disk Usage)]("http://dev.yorhel.nl/ncdu/scr")' makes comparing usage a snap! You'll be amazed. I used it to locate the size difference between Trusty and Wily:
```
sudo apt-get install ncdu
```

---

### Post by Bashing-om on 2015-09-03
@ VMC; :)

Noted and 
Added 'ncdu' to the tool box !

[INDENT][INDENT]our forum ->
[INDENT][INDENT]seek and you will find
[INDENT][INDENT][INDENT]given without even the asking
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-09-06
by using the codes 
```

dpkg -l | grep linux-
ls -al /boot
uname -r

```
I got

```

-rw-------  1 root root  2263334 Jul  6 23:20 System.map-3.2.0-88-generic
-rw-------  1 root root  2263334 Jul 28 11:49 System.map-3.2.0-89-generic
-rw-------  1 root root     1217 Jun 28  2011 vmcoreinfo-2.6.38-10-generic
-rw-------  1 root root     1217 Sep 13  2011 vmcoreinfo-2.6.38-11-generic
-rw-------  1 root root     1216 Apr 11  2011 vmcoreinfo-2.6.38-8-generic
-rw-------  1 root root     1215 Sep 25  2012 vmcoreinfo-3.0.0-26-generic
-rw-------  1 root root  4522224 Jun 28  2011 vmlinuz-2.6.38-10-generic
-rw-------  1 root root  4522960 Sep 13  2011 vmlinuz-2.6.38-11-generic
-rw-------  1 root root  4521296 Apr 11  2011 vmlinuz-2.6.38-8-generic
-rw-------  1 root root  4653536 Sep 25  2012 vmlinuz-3.0.0-26-generic
-rw-------  1 root root  4865760 Feb 27  2013 vmlinuz-3.2.0-39-generic
-rw-------  1 root root  4872544 Jul 24  2013 vmlinuz-3.2.0-51-generic
-rw-------  1 root root  4872544 Jul 26  2013 vmlinuz-3.2.0-52-generic
-rw-------  1 root root  4873888 Aug 22  2013 vmlinuz-3.2.0-53-generic
-rw-------  1 root root  4873664 Sep 10  2013 vmlinuz-3.2.0-54-generic
-rw-------  1 root root  4874240 Oct  2  2013 vmlinuz-3.2.0-55-generic
-rw-------  1 root root  4874240 Oct 23  2013 vmlinuz-3.2.0-56-generic
-rw-------  1 root root  4875808 Nov 12  2013 vmlinuz-3.2.0-57-generic
-rw-------  1 root root  4878176 May  2  2014 vmlinuz-3.2.0-61-generic
-rw-------  1 root root  4889952 Jul  6 23:20 vmlinuz-3.2.0-88-generic
-rw-------  1 root root  4890208 Jul 28 11:49 vmlinuz-3.2.0-89-generic
aab@aab-Latitude-E6400:~$ uname -r
3.2.0-88-generic
aab@aab-Latitude-E6400:~$ 


```
I am really desperate, some times some of the application is not working e.g firefox, libra office

P.S 
I have removed many media from the /home to external storage

also I could not install ncdu!!!

```

aab@aab-Latitude-E6400:~$ sudo apt-get install ncdu
[sudo] password for aab: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
aab@aab-Latitude-E6400:~$ 


```

---

### Post by Bashing-om on 2015-09-06
aab001; Hey !

It do appear we are on the right path:
> 
-rw-------  1 root root  4890208 Jul 28 11:49 vmlinuz-3.2.0-89-generic

aab@aab-Latitude-E6400:~$ uname -r
3.2.0-88-generic

the -89 kernel is installed and should be the booting kernel, but instead booting the older -88 . You have many old -no-longer-needed kernels installed.

Let's remove the old kernel images, see then if we can (RE-)install the -89 version.

Show what is presently the installed kernels:
```

dpkg -l | grep linux-

```

[INDENT][INDENT]making headway
[/INDENT][/INDENT]

---

### Post by aab001 on 2015-09-06
thank you for your cooperation, the following is the output

```


      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-79-generic           3.2.0-79.115                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-80-generic           3.2.0-80.116                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-82-generic           3.2.0-82.119                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-83-generic           3.2.0-83.120                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-84-generic           3.2.0-84.121                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-85-generic           3.2.0-85.122                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-86-generic           3.2.0-86.124                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-88-generic           3.2.0-88.126                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iF  linux-image-3.2.0-89-generic           3.2.0-89.127                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iU  linux-image-generic                    3.2.0.89.103                               Generic Linux kernel image
ii  linux-libc-dev                         3.2.0-88.126                               Linux Kernel Headers for development
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu1.1                     base package for ALSA and OSS sound systems
ii  syslinux-common                        2:4.05+dfsg-2                              collection of boot loaders (common files)
ii  syslinux-legacy                        2:3.63+dfsg-2ubuntu5                       Bootloader for Linux/i386 using MS-DOS floppies
aab@aab-Latitude-E6400:~$ 


```

---

### Post by Bashing-om on 2015-09-06
aab001; HUH ??

Does not compute. Many differences between " ls -al /boot" and "dpkg -l | grep linux-" ! WHY ?
They should reflect the same installed versions. And in the 'dpkg' output there are no headers files .. HUH ?
for reference only my output for comaprison.
```

sysop@1404mini:~$ dpkg -l | grep linux-
ii  linux-firmware                        1.127.15                             all          Firmware for Linux kernel drivers
ii  linux-generic                         3.13.0.63.71                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-62               3.13.0-62.102                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic       3.13.0-62.102                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63               3.13.0-63.103                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic       3.13.0-63.103                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                 3.13.0.63.71                         amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-58-generic         3.13.0-58.97                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-59-generic         3.13.0-59.98                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-61-generic         3.13.0-61.100                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-62-generic         3.13.0-62.102                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic         3.13.0-63.103                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic   3.13.0-58.97                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic   3.13.0-59.98                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic   3.13.0-61.100                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic   3.13.0-62.102                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic   3.13.0-63.103                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                   3.13.0.63.71                         amd64        Generic Linux kernel image
sysop@1404mini:~$ 

```

Have you rm'd kernels and headers ? We may have to go behind the package manager's back and remove individual files, and fix the package manager later . It is a pain but can be done.

But tell us, what have you done ?

[INDENT][INDENT]gonna be a chore
[/INDENT][/INDENT]

---

### Post by aab001 on 2015-09-07
Hi Bashing-om[B],
[/B]Before I post my  problem here, I found in one article in Ubuntu forum that I have to rm  some of kernals to have more space, but unfortunately it didn't fix the  problem.

---

### Post by Bashing-om on 2015-09-07
aab001; K;

Then we do this the wrong way, and clean up the mess we make. 
For those reading this thread - not a good thing to do ! Always stay within the bounds of the package management system. In this case those bounds have already been broke .

@aab001; Preparing to take matters into our own hands, show :
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/

```

We remove the files manually, install what we need, and get the system updated and up on the new kernel.

[INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT]

---

### Post by aab001 on 2015-09-07
Thank you very much Bashing-om for your cooperation, the following is the output of the codes

```

aab@aab-Latitude-E6400:~$ ls -al /usr/src/

```
```

drwxr-xr-x  24 root root  4096 Mar 24 13:48 linux-headers-3.2.0-79
drwxr-xr-x   7 root root  4096 Mar 24 13:48 linux-headers-3.2.0-79-generic
drwxr-xr-x   7 root root  4096 Mar 24 13:48 linux-headers-3.2.0-79-generic-pae
drwxr-xr-x  24 root root  4096 Apr 20 16:54 linux-headers-3.2.0-80
drwxr-xr-x   7 root root  4096 Apr 20 16:54 linux-headers-3.2.0-80-generic
drwxr-xr-x   7 root root  4096 Apr 20 16:55 linux-headers-3.2.0-80-generic-pae
drwxr-xr-x  24 root root  4096 Apr 30 14:30 linux-headers-3.2.0-82
drwxr-xr-x   7 root root  4096 Apr 30 14:30 linux-headers-3.2.0-82-generic
drwxr-xr-x   7 root root  4096 Apr 30 14:30 linux-headers-3.2.0-82-generic-pae
drwxr-xr-x  24 root root  4096 May  6 15:46 linux-headers-3.2.0-83
drwxr-xr-x   7 root root  4096 May  6 15:46 linux-headers-3.2.0-83-generic
drwxr-xr-x   7 root root  4096 May  6 15:46 linux-headers-3.2.0-83-generic-pae
drwxr-xr-x  24 root root  4096 May 20 15:34 linux-headers-3.2.0-84
drwxr-xr-x   7 root root  4096 May 20 15:35 linux-headers-3.2.0-84-generic
drwxr-xr-x   7 root root  4096 May 20 15:35 linux-headers-3.2.0-84-generic-pae
drwxr-xr-x  24 root root  4096 Jun 11 15:07 linux-headers-3.2.0-85
drwxr-xr-x   7 root root  4096 Jun 11 15:07 linux-headers-3.2.0-85-generic
drwxr-xr-x   7 root root  4096 Jun 11 15:07 linux-headers-3.2.0-85-generic-pae
drwxr-xr-x  24 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86
drwxr-xr-x   7 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86-generic
drwxr-xr-x   7 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86-generic-pae
drwxr-xr-x  24 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88
drwxr-xr-x   7 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88-generic
drwxr-xr-x   7 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88-generic-pae
drwxr-xr-x  24 root root  4096 Aug 23 18:24 linux-headers-3.2.0-89
drwxr-xr-x   7 root root  4096 Aug 23 18:24 linux-headers-3.2.0-89-generic
drwxr-xr-x   3 root root  4096 Feb  3  2014 nvidia-173-173.14.39
drwxr-xr-x   3 root root  4096 Dec 12  2014 nvidia-304-304.125
drwxr-xr-x   3 root root  4096 Dec 12  2014 nvidia-331-331.113
aab@aab-Latitude-E6400:~$ 



```

```

ls -al /lib/modules/

```

```

drwxr-xr-x  24 root root  4096 Mar 24 13:48 linux-headers-3.2.0-79
drwxr-xr-x   7 root root  4096 Mar 24 13:48 linux-headers-3.2.0-79-generic
drwxr-xr-x   7 root root  4096 Mar 24 13:48 linux-headers-3.2.0-79-generic-pae
drwxr-xr-x  24 root root  4096 Apr 20 16:54 linux-headers-3.2.0-80
drwxr-xr-x   7 root root  4096 Apr 20 16:54 linux-headers-3.2.0-80-generic
drwxr-xr-x   7 root root  4096 Apr 20 16:55 linux-headers-3.2.0-80-generic-pae
drwxr-xr-x  24 root root  4096 Apr 30 14:30 linux-headers-3.2.0-82
drwxr-xr-x   7 root root  4096 Apr 30 14:30 linux-headers-3.2.0-82-generic
drwxr-xr-x   7 root root  4096 Apr 30 14:30 linux-headers-3.2.0-82-generic-pae
drwxr-xr-x  24 root root  4096 May  6 15:46 linux-headers-3.2.0-83
drwxr-xr-x   7 root root  4096 May  6 15:46 linux-headers-3.2.0-83-generic
drwxr-xr-x   7 root root  4096 May  6 15:46 linux-headers-3.2.0-83-generic-pae
drwxr-xr-x  24 root root  4096 May 20 15:34 linux-headers-3.2.0-84
drwxr-xr-x   7 root root  4096 May 20 15:35 linux-headers-3.2.0-84-generic
drwxr-xr-x   7 root root  4096 May 20 15:35 linux-headers-3.2.0-84-generic-pae
drwxr-xr-x  24 root root  4096 Jun 11 15:07 linux-headers-3.2.0-85
drwxr-xr-x   7 root root  4096 Jun 11 15:07 linux-headers-3.2.0-85-generic
drwxr-xr-x   7 root root  4096 Jun 11 15:07 linux-headers-3.2.0-85-generic-pae
drwxr-xr-x  24 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86
drwxr-xr-x   7 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86-generic
drwxr-xr-x   7 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86-generic-pae
drwxr-xr-x  24 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88
drwxr-xr-x   7 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88-generic
drwxr-xr-x   7 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88-generic-pae
drwxr-xr-x  24 root root  4096 Aug 23 18:24 linux-headers-3.2.0-89
drwxr-xr-x   7 root root  4096 Aug 23 18:24 linux-headers-3.2.0-89-generic
drwxr-xr-x   3 root root  4096 Feb  3  2014 nvidia-173-173.14.39
drwxr-xr-x   3 root root  4096 Dec 12  2014 nvidia-304-304.125
drwxr-xr-x   3 root root  4096 Dec 12  2014 nvidia-331-331.113


```

```

aab@aab-Latitude-E6400:~$ ls -al /boot/


```

```

-rw-------  1 root root  2262516 Mar 10 18:27 System.map-3.2.0-77-generic
-rw-------  1 root root  2263145 Mar 12 15:05 System.map-3.2.0-79-generic
-rw-------  1 root root  2263145 Mar 23 18:13 System.map-3.2.0-80-generic
-rw-------  1 root root  2263145 Apr 27 23:08 System.map-3.2.0-82-generic
-rw-------  1 root root  2263170 Apr 29 17:40 System.map-3.2.0-83-generic
-rw-------  1 root root  2263170 May  5 20:40 System.map-3.2.0-84-generic
-rw-------  1 root root  2263401 May 26 18:17 System.map-3.2.0-85-generic
-rw-------  1 root root  2263401 Jun 17 23:44 System.map-3.2.0-86-generic
-rw-------  1 root root  2263334 Jul  6 23:20 System.map-3.2.0-88-generic
-rw-------  1 root root  2263334 Jul 28 11:49 System.map-3.2.0-89-generic
-rw-------  1 root root     1217 Jun 28  2011 vmcoreinfo-2.6.38-10-generic
-rw-------  1 root root     1217 Sep 13  2011 vmcoreinfo-2.6.38-11-generic
-rw-------  1 root root     1216 Apr 11  2011 vmcoreinfo-2.6.38-8-generic
-rw-------  1 root root     1215 Sep 25  2012 vmcoreinfo-3.0.0-26-generic
-rw-------  1 root root  4522224 Jun 28  2011 vmlinuz-2.6.38-10-generic
-rw-------  1 root root  4522960 Sep 13  2011 vmlinuz-2.6.38-11-generic
-rw-------  1 root root  4521296 Apr 11  2011 vmlinuz-2.6.38-8-generic
-rw-------  1 root root  4653536 Sep 25  2012 vmlinuz-3.0.0-26-generic
-rw-------  1 root root  4865760 Feb 27  2013 vmlinuz-3.2.0-39-generic
-rw-------  1 root root  4872544 Jul 24  2013 vmlinuz-3.2.0-51-generic
-rw-------  1 root root  4872544 Jul 26  2013 vmlinuz-3.2.0-52-generic
-rw-------  1 root root  4873888 Aug 22  2013 vmlinuz-3.2.0-53-generic
-rw-------  1 root root  4873664 Sep 10  2013 vmlinuz-3.2.0-54-generic
-rw-------  1 root root  4874240 Oct  2  2013 vmlinuz-3.2.0-55-generic
-rw-------  1 root root  4874240 Oct 23  2013 vmlinuz-3.2.0-56-generic
-rw-------  1 root root  4875808 Nov 12  2013 vmlinuz-3.2.0-57-generic
-rw-------  1 root root  4878176 May  2  2014 vmlinuz-3.2.0-61-generic
-rw-------  1 root root  4889952 Jul  6 23:20 vmlinuz-3.2.0-88-generic
-rw-------  1 root root  4890208 Jul 28 11:49 vmlinuz-3.2.0-89-generic


```

---

### Post by Bashing-om on 2015-09-07
aab001; Well ..
For now, IF we are to complete this in one setting; do:
```

sudo rm -rf /usr/src/linux-headers-3.2.0-{79,80,82,83,84,85}
sudo rm -rf /usr/src/linux-headers-3.2.0-{79,80,82,83,84,85}-generic
sudo rm -rf /usr/src/linux-headers-3.2.0-{79,80,82,83,84,85}-generic-pae

```

to take care of '/usr/src/ directory.

The output for the requested '/lib/modules/' is a duplicate for '/usr/src' .
Please try again:
```

ls -al /lib/modules/

```

And we pare that directory down ... then address '/boot' .

Else if we can not complete all 4 steps - to be done - at this time, we await a more opportune time.

[INDENT][INDENT]small steps
[INDENT][INDENT][INDENT]but getting there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-10-03
> **Bashing-om said:**
> aab001; Well ..
For now, IF we are to complete this in one setting; do:
```

sudo rm -rf /usr/src/linux-headers-3.2.0-{79,80,82,83,84,85}
sudo rm -rf /usr/src/linux-headers-3.2.0-{79,80,82,83,84,85}-generic
sudo rm -rf /usr/src/linux-headers-3.2.0-{79,80,82,83,84,85}-generic-pae

```

to take care of '/usr/src/ directory.

The output for the requested '/lib/modules/' is a duplicate for '/usr/src' .
Please try again:
```

ls -al /lib/modules/

```

And we pare that directory down ... then address '/boot' .

Else if we can not complete all 4 steps - to be done - at this time, we await a more opportune time.
[INDENT][INDENT]small steps[INDENT][INDENT][INDENT]but getting there
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hi 
the following is my output
```


aab@aab-Latitude-E6400:~$ sudo rm -rf /usr/src/linux-headers-3.2.0-{79,80,82,83,84,85}
[sudo] password for aab: 
Sorry, try again.
[sudo] password for aab: 
aab@aab-Latitude-E6400:~$ sudo rm -rf /usr/src/linux-headers-3.2.0-{79,80,82,83,84,85}-generic
aab@aab-Latitude-E6400:~$ sudo rm -rf /usr/src/linux-headers-3.2.0-{79,80,82,83,84,85}-generic-pae
aab@aab-Latitude-E6400:~$ ls -al /lib/modules/
total 400
drwxr-xr-x 98 root root  4096 Aug 23 18:22 .
drwxr-xr-x 27 root root 12288 May 22 21:15 ..
drwxr-xr-x  3 root root  4096 Oct 19  2011 2.6.35-28-generic
drwxr-xr-x  5 root root  4096 Oct 15  2011 2.6.38-10-generic
drwxr-xr-x  6 root root  4096 Oct 13  2012 2.6.38-11-generic
drwxr-xr-x  5 root root  4096 Oct 15  2011 2.6.38-8-generic
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.0.0-26-generic
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-32-generic
drwxr-xr-x  2 root root  4096 Oct 13  2012 3.2.0-32-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-33-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-33-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-34-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-34-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-35-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-35-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-36-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-36-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-37-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-37-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-38-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-38-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-39-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-39-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-40-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-40-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-41-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-41-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-43-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-43-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-44-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-44-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-45-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-45-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-48-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-48-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-49-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-49-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-51-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-51-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-52-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-52-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-53-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-53-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-54-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-54-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-55-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-55-generic-pae
drwxr-xr-x  5 root root  4096 Feb  3  2014 3.2.0-56-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-56-generic-pae
drwxr-xr-x  5 root root  4096 May 25  2014 3.2.0-57-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-57-generic-pae
drwxr-xr-x  5 root root  4096 Oct 28  2014 3.2.0-58-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-58-generic-pae
drwxr-xr-x  5 root root  4096 Oct 28  2014 3.2.0-59-generic
drwxr-xr-x  3 root root  4096 Oct 28  2014 3.2.0-59-generic-pae
drwxr-xr-x  5 root root  4096 Oct 28  2014 3.2.0-60-generic
drwxr-xr-x  3 root root  4096 Oct 28  2014 3.2.0-60-generic-pae
drwxr-xr-x  5 root root  4096 Dec 12  2014 3.2.0-61-generic
drwxr-xr-x  3 root root  4096 Oct 28  2014 3.2.0-61-generic-pae
drwxr-xr-x  5 root root  4096 Dec 12  2014 3.2.0-63-generic
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-63-generic-pae
drwxr-xr-x  5 root root  4096 Dec 12  2014 3.2.0-64-generic
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-64-generic-pae
drwxr-xr-x  5 root root  4096 Dec 12  2014 3.2.0-67-generic
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-67-generic-pae
drwxr-xr-x  5 root root  4096 Dec 12  2014 3.2.0-68-generic
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-68-generic-pae
drwxr-xr-x  5 root root  4096 Dec 12  2014 3.2.0-69-generic
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-69-generic-pae
drwxr-xr-x  5 root root  4096 Dec 12  2014 3.2.0-70-generic
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-70-generic-pae
drwxr-xr-x  5 root root  4096 Dec 12  2014 3.2.0-72-generic
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-72-generic-pae
drwxr-xr-x  5 root root  4096 Dec 12  2014 3.2.0-74-generic
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-74-generic-pae
drwxr-xr-x  5 root root  4096 Jan 13  2015 3.2.0-75-generic
drwxr-xr-x  3 root root  4096 Jan 13  2015 3.2.0-75-generic-pae
drwxr-xr-x  5 root root  4096 Feb  9  2015 3.2.0-76-generic
drwxr-xr-x  3 root root  4096 Feb  9  2015 3.2.0-76-generic-pae
drwxr-xr-x  5 root root  4096 Mar 13  2015 3.2.0-77-generic
drwxr-xr-x  3 root root  4096 Mar  5  2015 3.2.0-77-generic-pae
drwxr-xr-x  5 root root  4096 Mar 24  2015 3.2.0-79-generic
drwxr-xr-x  3 root root  4096 Mar 24  2015 3.2.0-79-generic-pae
drwxr-xr-x  5 root root  4096 Apr 20 16:57 3.2.0-80-generic
drwxr-xr-x  3 root root  4096 Apr 20 16:59 3.2.0-80-generic-pae
drwxr-xr-x  5 root root  4096 Apr 30 14:31 3.2.0-82-generic
drwxr-xr-x  3 root root  4096 Apr 30 14:33 3.2.0-82-generic-pae
drwxr-xr-x  5 root root  4096 May  6 15:48 3.2.0-83-generic
drwxr-xr-x  3 root root  4096 May  6 15:51 3.2.0-83-generic-pae
drwxr-xr-x  5 root root  4096 May 20 15:37 3.2.0-84-generic
drwxr-xr-x  3 root root  4096 May 20 15:39 3.2.0-84-generic-pae
drwxr-xr-x  5 root root  4096 Jun 11 15:11 3.2.0-85-generic
drwxr-xr-x  3 root root  4096 Jun 11 15:13 3.2.0-85-generic-pae
drwxr-xr-x  5 root root  4096 Jun 22 13:12 3.2.0-86-generic
drwxr-xr-x  3 root root  4096 Jun 16 11:31 3.2.0-86-generic-pae
drwxr-xr-x  5 root root  4096 Jul 29 01:51 3.2.0-88-generic
drwxr-xr-x  3 root root  4096 Jul 29 01:52 3.2.0-88-generic-pae
drwxr-xr-x  5 root root  4096 Sep 12 15:01 3.2.0-89-generic
aab@aab-Latitude-E6400:~$ 


```
 
becuse this problem my system now is useless.
I am appreciating your help

---

### Post by Bashing-om on 2015-10-03
aab001; Yeah; I can understand -

In a situation such as this, that is to be expected. We try and make it all better.
Next is to remove those files in the /lib/modules/ directory.
```

sudo rm -rf /lib/modules/2.6.35-28-generic
sudo rm -rf /lib/modules/2.6.38-{8,10,11}
sudo rm -rf /lib/modules/3.0.0-26-generic
sudo rm -rf /lib/modules/3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77,79,80,82,83,84,85}
sudo rm -rf /lib/modules/3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77,79,80,82,83,84,85}-generic
sudo rm /boot/*-2.6.38-{8,10,11}-generic
sudo rm /boot/*-3.0.0-26-generic
sudo rm /boot/*-3.2.0-{39,51,52,53,54,55,56,57,61}-generic

```

Now before proceeding to - put the pieces back together, as there has been a long time for things to change -

Get a new look at what is and make sure that what all we have matches:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/

```

Then is to properly remove the images whose files we have removed - if and when all matches.

[INDENT][INDENT]just try'n
[INDENT][INDENT][INDENT]clean a mess up
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-10-05
> **Bashing-om said:**
> aab001; Yeah; I can understand -

In a situation such as this, that is to be expected. We try and make it all better.
Next is to remove those files in the /lib/modules/ directory.
```

sudo rm -rf /lib/modules/2.6.35-28-generic
sudo rm -rf /lib/modules/2.6.38-{8,10,11}
sudo rm -rf /lib/modules/3.0.0-26-generic
sudo rm -rf /lib/modules/3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77,79,80,82,83,84,85}
sudo rm -rf /lib/modules/3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77,79,80,82,83,84,85}-generic
sudo rm /boot/*-2.6.38-{8,10,11}-generic
sudo rm /boot/*-3.0.0-26-generic
sudo rm /boot/*-3.2.0-{39,51,52,53,54,55,56,57,61}-generic

```

Now before proceeding to - put the pieces back together, as there has been a long time for things to change -

Get a new look at what is and make sure that what all we have matches:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/

```

Then is to properly remove the images whose files we have removed - if and when all matches.
[INDENT][INDENT]just try'n[INDENT][INDENT][INDENT]clean a mess up
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



Hi
these are my output
```

aab@aab-Latitude-E6400:~$ ls -al /usr/src/
total 532
drwxrwsr-x 131 root src  12288 Sep  8 16:01 .
drwxr-xr-x  11 root root  4096 Oct 15  2011 ..
drwxr-xr-x   5 root root  4096 Sep 24  2013 bcmwl-6.20.155.1+bdcom
drwxr-xr-x  24 root root  4096 Jul 19  2011 linux-headers-2.6.38-10
drwxr-xr-x   7 root root  4096 Jul 19  2011 linux-headers-2.6.38-10-generic
drwxr-xr-x  24 root root  4096 Sep 23  2011 linux-headers-2.6.38-11
drwxr-xr-x   7 root root  4096 Sep 23  2011 linux-headers-2.6.38-11-generic
drwxr-xr-x  24 root root  4096 Jun 13  2011 linux-headers-2.6.38-8
drwxr-xr-x   7 root root  4096 Jun 13  2011 linux-headers-2.6.38-8-generic
drwxr-xr-x  24 root root  4096 Oct 13  2012 linux-headers-3.2.0-32
drwxr-xr-x   7 root root  4096 Oct 13  2012 linux-headers-3.2.0-32-generic
drwxr-xr-x   7 root root  4096 Oct 13  2012 linux-headers-3.2.0-32-generic-pae
drwxr-xr-x  24 root root  4096 Nov 17  2012 linux-headers-3.2.0-33
drwxr-xr-x   7 root root  4096 Nov 17  2012 linux-headers-3.2.0-33-generic
drwxr-xr-x   7 root root  4096 Nov 17  2012 linux-headers-3.2.0-33-generic-pae
drwxr-xr-x  24 root root  4096 Dec  1  2012 linux-headers-3.2.0-34
drwxr-xr-x   7 root root  4096 Dec  1  2012 linux-headers-3.2.0-34-generic
drwxr-xr-x   7 root root  4096 Dec  1  2012 linux-headers-3.2.0-34-generic-pae
drwxr-xr-x  24 root root  4096 Dec 19  2012 linux-headers-3.2.0-35
drwxr-xr-x   7 root root  4096 Dec 19  2012 linux-headers-3.2.0-35-generic
drwxr-xr-x   7 root root  4096 Dec 19  2012 linux-headers-3.2.0-35-generic-pae
drwxr-xr-x  24 root root  4096 Jan 18  2013 linux-headers-3.2.0-36
drwxr-xr-x   7 root root  4096 Jan 18  2013 linux-headers-3.2.0-36-generic
drwxr-xr-x   7 root root  4096 Jan 18  2013 linux-headers-3.2.0-36-generic-pae
drwxr-xr-x  24 root root  4096 Feb  1  2013 linux-headers-3.2.0-37
drwxr-xr-x   7 root root  4096 Feb  1  2013 linux-headers-3.2.0-37-generic
drwxr-xr-x   7 root root  4096 Feb  1  2013 linux-headers-3.2.0-37-generic-pae
drwxr-xr-x  24 root root  4096 Feb 22  2013 linux-headers-3.2.0-38
drwxr-xr-x   7 root root  4096 Feb 22  2013 linux-headers-3.2.0-38-generic
drwxr-xr-x   7 root root  4096 Feb 22  2013 linux-headers-3.2.0-38-generic-pae
drwxr-xr-x  24 root root  4096 Mar 19  2013 linux-headers-3.2.0-39
drwxr-xr-x   7 root root  4096 Mar 19  2013 linux-headers-3.2.0-39-generic
drwxr-xr-x   7 root root  4096 Mar 19  2013 linux-headers-3.2.0-39-generic-pae
drwxr-xr-x  24 root root  4096 Apr 15  2013 linux-headers-3.2.0-40
drwxr-xr-x   7 root root  4096 Apr 15  2013 linux-headers-3.2.0-40-generic
drwxr-xr-x   7 root root  4096 Apr 15  2013 linux-headers-3.2.0-40-generic-pae
drwxr-xr-x  24 root root  4096 May  2  2013 linux-headers-3.2.0-41
drwxr-xr-x   7 root root  4096 May  2  2013 linux-headers-3.2.0-41-generic
drwxr-xr-x   7 root root  4096 May  2  2013 linux-headers-3.2.0-41-generic-pae
drwxr-xr-x  24 root root  4096 May 17  2013 linux-headers-3.2.0-43
drwxr-xr-x   7 root root  4096 May 17  2013 linux-headers-3.2.0-43-generic
drwxr-xr-x   7 root root  4096 May 17  2013 linux-headers-3.2.0-43-generic-pae
drwxr-xr-x  24 root root  4096 May 24  2013 linux-headers-3.2.0-44
drwxr-xr-x   7 root root  4096 May 24  2013 linux-headers-3.2.0-44-generic
drwxr-xr-x   7 root root  4096 May 24  2013 linux-headers-3.2.0-44-generic-pae
drwxr-xr-x  24 root root  4096 Jun  1  2013 linux-headers-3.2.0-45
drwxr-xr-x   7 root root  4096 Jun  1  2013 linux-headers-3.2.0-45-generic
drwxr-xr-x   7 root root  4096 Jun  1  2013 linux-headers-3.2.0-45-generic-pae
drwxr-xr-x  24 root root  4096 Jun 15  2013 linux-headers-3.2.0-48
drwxr-xr-x   7 root root  4096 Jun 15  2013 linux-headers-3.2.0-48-generic
drwxr-xr-x   7 root root  4096 Jun 15  2013 linux-headers-3.2.0-48-generic-pae
drwxr-xr-x  24 root root  4096 Jul  6  2013 linux-headers-3.2.0-49
drwxr-xr-x   7 root root  4096 Jul  6  2013 linux-headers-3.2.0-49-generic
drwxr-xr-x   7 root root  4096 Jul  6  2013 linux-headers-3.2.0-49-generic-pae
drwxr-xr-x  24 root root  4096 Aug 10  2013 linux-headers-3.2.0-51
drwxr-xr-x   7 root root  4096 Aug 10  2013 linux-headers-3.2.0-51-generic
drwxr-xr-x   7 root root  4096 Aug 10  2013 linux-headers-3.2.0-51-generic-pae
drwxr-xr-x  24 root root  4096 Aug 21  2013 linux-headers-3.2.0-52
drwxr-xr-x   7 root root  4096 Aug 21  2013 linux-headers-3.2.0-52-generic
drwxr-xr-x   7 root root  4096 Aug 21  2013 linux-headers-3.2.0-52-generic-pae
drwxr-xr-x  24 root root  4096 Sep  8  2013 linux-headers-3.2.0-53
drwxr-xr-x   7 root root  4096 Sep  8  2013 linux-headers-3.2.0-53-generic
drwxr-xr-x   7 root root  4096 Sep  8  2013 linux-headers-3.2.0-53-generic-pae
drwxr-xr-x  24 root root  4096 Sep 29  2013 linux-headers-3.2.0-54
drwxr-xr-x   7 root root  4096 Sep 29  2013 linux-headers-3.2.0-54-generic
drwxr-xr-x   7 root root  4096 Sep 29  2013 linux-headers-3.2.0-54-generic-pae
drwxr-xr-x  24 root root  4096 Oct 25  2013 linux-headers-3.2.0-55
drwxr-xr-x   7 root root  4096 Oct 25  2013 linux-headers-3.2.0-55-generic
drwxr-xr-x   7 root root  4096 Oct 25  2013 linux-headers-3.2.0-55-generic-pae
drwxr-xr-x  24 root root  4096 Nov  8  2013 linux-headers-3.2.0-56
drwxr-xr-x   7 root root  4096 Nov  8  2013 linux-headers-3.2.0-56-generic
drwxr-xr-x   7 root root  4096 Nov  8  2013 linux-headers-3.2.0-56-generic-pae
drwxr-xr-x  24 root root  4096 Dec  3  2013 linux-headers-3.2.0-57
drwxr-xr-x   7 root root  4096 Dec  3  2013 linux-headers-3.2.0-57-generic
drwxr-xr-x   7 root root  4096 Dec  3  2013 linux-headers-3.2.0-57-generic-pae
drwxr-xr-x  24 root root  4096 Jan  7  2014 linux-headers-3.2.0-58
drwxr-xr-x   7 root root  4096 Jan  7  2014 linux-headers-3.2.0-58-generic
drwxr-xr-x   7 root root  4096 Jan  7  2014 linux-headers-3.2.0-58-generic-pae
drwxr-xr-x  24 root root  4096 Feb 20  2014 linux-headers-3.2.0-59
drwxr-xr-x   7 root root  4096 Feb 20  2014 linux-headers-3.2.0-59-generic
drwxr-xr-x   7 root root  4096 Feb 20  2014 linux-headers-3.2.0-59-generic-pae
drwxr-xr-x  24 root root  4096 Mar  8  2014 linux-headers-3.2.0-60
drwxr-xr-x   7 root root  4096 Mar  8  2014 linux-headers-3.2.0-60-generic
drwxr-xr-x   7 root root  4096 Mar  8  2014 linux-headers-3.2.0-60-generic-pae
drwxr-xr-x  24 root root  4096 May  6  2014 linux-headers-3.2.0-61
drwxr-xr-x   7 root root  4096 May  6  2014 linux-headers-3.2.0-61-generic
drwxr-xr-x   7 root root  4096 May  6  2014 linux-headers-3.2.0-61-generic-pae
drwxr-xr-x  24 root root  4096 May 27  2014 linux-headers-3.2.0-63
drwxr-xr-x   7 root root  4096 May 27  2014 linux-headers-3.2.0-63-generic
drwxr-xr-x   7 root root  4096 May 27  2014 linux-headers-3.2.0-63-generic-pae
drwxr-xr-x  24 root root  4096 Jun  7  2014 linux-headers-3.2.0-64
drwxr-xr-x   7 root root  4096 Jun  7  2014 linux-headers-3.2.0-64-generic
drwxr-xr-x   7 root root  4096 Jun  7  2014 linux-headers-3.2.0-64-generic-pae
drwxr-xr-x  24 root root  4096 Aug 13  2014 linux-headers-3.2.0-67
drwxr-xr-x   7 root root  4096 Aug 13  2014 linux-headers-3.2.0-67-generic
drwxr-xr-x   7 root root  4096 Aug 13  2014 linux-headers-3.2.0-67-generic-pae
drwxr-xr-x  24 root root  4096 Sep 16  2014 linux-headers-3.2.0-68
drwxr-xr-x   7 root root  4096 Sep 16  2014 linux-headers-3.2.0-68-generic
drwxr-xr-x   7 root root  4096 Sep 16  2014 linux-headers-3.2.0-68-generic-pae
drwxr-xr-x  24 root root  4096 Sep 24  2014 linux-headers-3.2.0-69
drwxr-xr-x   7 root root  4096 Sep 24  2014 linux-headers-3.2.0-69-generic
drwxr-xr-x   7 root root  4096 Sep 24  2014 linux-headers-3.2.0-69-generic-pae
drwxr-xr-x  24 root root  4096 Oct  9  2014 linux-headers-3.2.0-70
drwxr-xr-x   7 root root  4096 Oct  9  2014 linux-headers-3.2.0-70-generic
drwxr-xr-x   7 root root  4096 Oct  9  2014 linux-headers-3.2.0-70-generic-pae
drwxr-xr-x  24 root root  4096 Nov 25  2014 linux-headers-3.2.0-72
drwxr-xr-x   7 root root  4096 Nov 25  2014 linux-headers-3.2.0-72-generic
drwxr-xr-x   7 root root  4096 Nov 25  2014 linux-headers-3.2.0-72-generic-pae
drwxr-xr-x  24 root root  4096 Dec 12  2014 linux-headers-3.2.0-74
drwxr-xr-x   7 root root  4096 Dec 12  2014 linux-headers-3.2.0-74-generic
drwxr-xr-x   7 root root  4096 Dec 12  2014 linux-headers-3.2.0-74-generic-pae
drwxr-xr-x  24 root root  4096 Jan 13  2015 linux-headers-3.2.0-75
drwxr-xr-x   7 root root  4096 Jan 13  2015 linux-headers-3.2.0-75-generic
drwxr-xr-x   7 root root  4096 Jan 13  2015 linux-headers-3.2.0-75-generic-pae
drwxr-xr-x  24 root root  4096 Feb  9  2015 linux-headers-3.2.0-76
drwxr-xr-x   7 root root  4096 Feb  9  2015 linux-headers-3.2.0-76-generic
drwxr-xr-x   7 root root  4096 Feb  9  2015 linux-headers-3.2.0-76-generic-pae
drwxr-xr-x  24 root root  4096 Mar 13  2015 linux-headers-3.2.0-77
drwxr-xr-x   7 root root  4096 Mar 13  2015 linux-headers-3.2.0-77-generic
drwxr-xr-x   7 root root  4096 Mar 13  2015 linux-headers-3.2.0-77-generic-pae
drwxr-xr-x  24 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86
drwxr-xr-x   7 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86-generic
drwxr-xr-x   7 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86-generic-pae
drwxr-xr-x  24 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88
drwxr-xr-x   7 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88-generic
drwxr-xr-x   7 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88-generic-pae
drwxr-xr-x  24 root root  4096 Aug 23 18:24 linux-headers-3.2.0-89
drwxr-xr-x   7 root root  4096 Aug 23 18:24 linux-headers-3.2.0-89-generic
drwxr-xr-x   3 root root  4096 Feb  3  2014 nvidia-173-173.14.39
drwxr-xr-x   3 root root  4096 Dec 12  2014 nvidia-304-304.125
drwxr-xr-x   3 root root  4096 Dec 12  2014 nvidia-331-331.113
aab@aab-Latitude-E6400:~$ ls -al /lib/modules/
total 220
drwxr-xr-x 53 root root  4096 Oct  5 14:54 .
drwxr-xr-x 27 root root 12288 May 22 21:15 ..
drwxr-xr-x  5 root root  4096 Oct 15  2011 2.6.38-10-generic
drwxr-xr-x  6 root root  4096 Oct 13  2012 2.6.38-11-generic
drwxr-xr-x  5 root root  4096 Oct 15  2011 2.6.38-8-generic
drwxr-xr-x  2 root root  4096 Oct 13  2012 3.2.0-32-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-33-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-34-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-35-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-36-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-37-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-38-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-39-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-40-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-41-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-43-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-44-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-45-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-48-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-49-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-51-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-52-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-53-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-54-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-55-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-56-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-57-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 3.2.0-58-generic-pae
drwxr-xr-x  3 root root  4096 Oct 28  2014 3.2.0-59-generic-pae
drwxr-xr-x  3 root root  4096 Oct 28  2014 3.2.0-60-generic-pae
drwxr-xr-x  3 root root  4096 Oct 28  2014 3.2.0-61-generic-pae
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-63-generic-pae
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-64-generic-pae
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-67-generic-pae
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-68-generic-pae
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-69-generic-pae
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-70-generic-pae
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-72-generic-pae
drwxr-xr-x  3 root root  4096 Dec 12  2014 3.2.0-74-generic-pae
drwxr-xr-x  3 root root  4096 Jan 13  2015 3.2.0-75-generic-pae
drwxr-xr-x  3 root root  4096 Feb  9  2015 3.2.0-76-generic-pae
drwxr-xr-x  3 root root  4096 Mar  5  2015 3.2.0-77-generic-pae
drwxr-xr-x  3 root root  4096 Mar 24  2015 3.2.0-79-generic-pae
drwxr-xr-x  3 root root  4096 Apr 20 16:59 3.2.0-80-generic-pae
drwxr-xr-x  3 root root  4096 Apr 30 14:33 3.2.0-82-generic-pae
drwxr-xr-x  3 root root  4096 May  6 15:51 3.2.0-83-generic-pae
drwxr-xr-x  3 root root  4096 May 20 15:39 3.2.0-84-generic-pae
drwxr-xr-x  3 root root  4096 Jun 11 15:13 3.2.0-85-generic-pae
drwxr-xr-x  5 root root  4096 Jun 22 13:12 3.2.0-86-generic
drwxr-xr-x  3 root root  4096 Jun 16 11:31 3.2.0-86-generic-pae
drwxr-xr-x  5 root root  4096 Jul 29 01:51 3.2.0-88-generic
drwxr-xr-x  3 root root  4096 Jul 29 01:52 3.2.0-88-generic-pae
drwxr-xr-x  5 root root  4096 Sep 12 15:01 3.2.0-89-generic
aab@aab-Latitude-E6400:~$ ls -al /boot/
total 800812
drwxr-xr-x  3 root root    20480 Oct  5 14:55 .
drwxr-xr-x 25 root root     4096 Sep 12 15:01 ..
-rw-r--r--  1 root root   797027 Sep 26  2012 abi-3.2.0-32-generic
-rw-r--r--  1 root root   797027 Oct 18  2012 abi-3.2.0-33-generic
-rw-r--r--  1 root root   797082 Nov 15  2012 abi-3.2.0-34-generic
-rw-r--r--  1 root root   797121 Dec  5  2012 abi-3.2.0-35-generic
-rw-r--r--  1 root root   797231 Jan  8  2013 abi-3.2.0-36-generic
-rw-r--r--  1 root root   797231 Jan 24  2013 abi-3.2.0-37-generic
-rw-r--r--  1 root root   797340 Feb 19  2013 abi-3.2.0-38-generic
-rw-r--r--  1 root root   799443 Mar 25  2013 abi-3.2.0-40-generic
-rw-r--r--  1 root root   799506 Apr 25  2013 abi-3.2.0-41-generic
-rw-r--r--  1 root root   799506 May 15  2013 abi-3.2.0-43-generic
-rw-r--r--  1 root root   799656 May 16  2013 abi-3.2.0-44-generic
-rw-r--r--  1 root root   799656 May 29  2013 abi-3.2.0-45-generic
-rw-r--r--  1 root root   799875 Jun  6  2013 abi-3.2.0-48-generic
-rw-r--r--  1 root root   799875 Jun 18  2013 abi-3.2.0-49-generic
-rw-r--r--  1 root root   800261 Dec  3  2013 abi-3.2.0-58-generic
-rw-r--r--  1 root root   800261 Jan  7  2014 abi-3.2.0-59-generic
-rw-r--r--  1 root root   800253 Feb 19  2014 abi-3.2.0-60-generic
-rw-r--r--  1 root root   800421 May 16  2014 abi-3.2.0-63-generic
-rw-r--r--  1 root root   800421 Jun  5  2014 abi-3.2.0-64-generic
-rw-r--r--  1 root root   800473 Jul 15  2014 abi-3.2.0-67-generic
-rw-r--r--  1 root root   800473 Aug 13  2014 abi-3.2.0-68-generic
-rw-r--r--  1 root root   800473 Sep  2  2014 abi-3.2.0-69-generic
-rw-r--r--  1 root root   800524 Sep 24  2014 abi-3.2.0-70-generic
-rw-r--r--  1 root root   801045 Nov  6  2014 abi-3.2.0-72-generic
-rw-r--r--  1 root root   801045 Dec  9  2014 abi-3.2.0-74-generic
-rw-r--r--  1 root root   801045 Dec 16  2014 abi-3.2.0-75-generic
-rw-r--r--  1 root root   801107 Jan 13  2015 abi-3.2.0-76-generic
-rw-r--r--  1 root root   801107 Mar 10  2015 abi-3.2.0-77-generic
-rw-r--r--  1 root root   801170 Mar 12  2015 abi-3.2.0-79-generic
-rw-r--r--  1 root root   801170 Mar 23  2015 abi-3.2.0-80-generic
-rw-r--r--  1 root root   801170 Apr 27 23:08 abi-3.2.0-82-generic
-rw-r--r--  1 root root   801170 Apr 29 17:40 abi-3.2.0-83-generic
-rw-r--r--  1 root root   801170 May  5 20:40 abi-3.2.0-84-generic
-rw-r--r--  1 root root   801170 May 26 18:17 abi-3.2.0-85-generic
-rw-r--r--  1 root root   801170 Jun 17 23:44 abi-3.2.0-86-generic
-rw-r--r--  1 root root   801170 Jul  6 23:20 abi-3.2.0-88-generic
-rw-r--r--  1 root root   801170 Jul 28 11:49 abi-3.2.0-89-generic
-rw-r--r--  1 root root   147497 Sep 26  2012 config-3.2.0-32-generic
-rw-r--r--  1 root root   147497 Oct 18  2012 config-3.2.0-33-generic
-rw-r--r--  1 root root   147514 Nov 15  2012 config-3.2.0-34-generic
-rw-r--r--  1 root root   147514 Dec  5  2012 config-3.2.0-35-generic
-rw-r--r--  1 root root   147514 Jan  8  2013 config-3.2.0-36-generic
-rw-r--r--  1 root root   147514 Jan 24  2013 config-3.2.0-37-generic
-rw-r--r--  1 root root   147497 Feb 19  2013 config-3.2.0-38-generic
-rw-r--r--  1 root root   147595 Mar 25  2013 config-3.2.0-40-generic
-rw-r--r--  1 root root   147631 Apr 25  2013 config-3.2.0-41-generic
-rw-r--r--  1 root root   147631 May 15  2013 config-3.2.0-43-generic
-rw-r--r--  1 root root   147631 May 16  2013 config-3.2.0-44-generic
-rw-r--r--  1 root root   147631 May 29  2013 config-3.2.0-45-generic
-rw-r--r--  1 root root   147631 Jun  6  2013 config-3.2.0-48-generic
-rw-r--r--  1 root root   147631 Jun 18  2013 config-3.2.0-49-generic
-rw-r--r--  1 root root   147649 Jun  5  2014 config-3.2.0-64-generic
-rw-r--r--  1 root root   147650 Jul 15  2014 config-3.2.0-67-generic
-rw-r--r--  1 root root   147684 Aug 13  2014 config-3.2.0-68-generic
-rw-r--r--  1 root root   147684 Sep  2  2014 config-3.2.0-69-generic
-rw-r--r--  1 root root   147714 Sep 24  2014 config-3.2.0-70-generic
-rw-r--r--  1 root root   147799 Jul  6 23:20 config-3.2.0-88-generic
-rw-r--r--  1 root root   147799 Jul 28 11:49 config-3.2.0-89-generic
drwxr-xr-x  3 root root    12288 Sep 12 15:02 grub
-rw-r--r--  1 root root 19748958 Nov 17  2012 initrd.img-3.2.0-33-generic
-rw-r--r--  1 root root 19747645 Dec 19  2012 initrd.img-3.2.0-35-generic
-rw-r--r--  1 root root 19756690 Jan 29  2013 initrd.img-3.2.0-36-generic
-rw-r--r--  1 root root 19760848 Feb  3  2013 initrd.img-3.2.0-37-generic
-rw-r--r--  1 root root 19757559 Mar 18  2013 initrd.img-3.2.0-38-generic
-rw-r--r--  1 root root 19793963 Apr 15  2013 initrd.img-3.2.0-40-generic
-rw-r--r--  1 root root 19796543 May  2  2013 initrd.img-3.2.0-41-generic
-rw-r--r--  1 root root 19798181 May 17  2013 initrd.img-3.2.0-43-generic
-rw-r--r--  1 root root 19799426 May 24  2013 initrd.img-3.2.0-44-generic
-rw-r--r--  1 root root 19799498 Jun  1  2013 initrd.img-3.2.0-45-generic
-rw-r--r--  1 root root 19802532 Jun 15  2013 initrd.img-3.2.0-48-generic
-rw-r--r--  1 root root 19803557 Jul  6  2013 initrd.img-3.2.0-49-generic
-rw-r--r--  1 root root 19824709 Feb  6  2014 initrd.img-3.2.0-58-generic
-rw-r--r--  1 root root 19826898 Feb 20  2014 initrd.img-3.2.0-59-generic
-rw-r--r--  1 root root 19829781 Apr  2  2014 initrd.img-3.2.0-60-generic
-rw-r--r--  1 root root 19830600 May 27  2014 initrd.img-3.2.0-63-generic
-rw-r--r--  1 root root 19813131 Aug 13  2014 initrd.img-3.2.0-64-generic
-rw-r--r--  1 root root 19815469 Aug 13  2014 initrd.img-3.2.0-67-generic
-rw-r--r--  1 root root 19816373 Sep 16  2014 initrd.img-3.2.0-68-generic
-rw-r--r--  1 root root 19815794 Sep 24  2014 initrd.img-3.2.0-69-generic
-rw-r--r--  1 root root 19816326 Oct  9  2014 initrd.img-3.2.0-70-generic
-rw-r--r--  1 root root 19814521 Dec 12  2014 initrd.img-3.2.0-72-generic
-rw-r--r--  1 root root 19816897 Dec 12  2014 initrd.img-3.2.0-74-generic
-rw-r--r--  1 root root 19816179 Jan 13  2015 initrd.img-3.2.0-75-generic
-rw-r--r--  1 root root 19816643 Feb 18  2015 initrd.img-3.2.0-76-generic
-rw-r--r--  1 root root 19822814 Mar 13  2015 initrd.img-3.2.0-77-generic
-rw-r--r--  1 root root 19824547 Mar 24  2015 initrd.img-3.2.0-79-generic
-rw-r--r--  1 root root 19822666 Apr 20 16:57 initrd.img-3.2.0-80-generic
-rw-r--r--  1 root root 19822446 Apr 30 14:32 initrd.img-3.2.0-82-generic
-rw-r--r--  1 root root 19821821 May  6 15:48 initrd.img-3.2.0-83-generic
-rw-r--r--  1 root root 19822303 May 22 21:17 initrd.img-3.2.0-84-generic
-rw-r--r--  1 root root 19824487 Jun 11 15:11 initrd.img-3.2.0-85-generic
-rw-r--r--  1 root root 19823822 Jun 22 13:13 initrd.img-3.2.0-86-generic
-rw-r--r--  1 root root 19821946 Jul 29 01:50 initrd.img-3.2.0-88-generic
-rw-r--r--  1 root root 19822747 Sep 12 15:02 initrd.img-3.2.0-89-generic
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2251691 Sep 26  2012 System.map-3.2.0-32-generic
-rw-------  1 root root  2251905 Oct 18  2012 System.map-3.2.0-33-generic
-rw-------  1 root root  2252451 Nov 15  2012 System.map-3.2.0-34-generic
-rw-------  1 root root  2252128 Dec  5  2012 System.map-3.2.0-35-generic
-rw-------  1 root root  2252687 Jan  8  2013 System.map-3.2.0-36-generic
-rw-------  1 root root  2252511 Jan 24  2013 System.map-3.2.0-37-generic
-rw-------  1 root root  2253664 Feb 19  2013 System.map-3.2.0-38-generic
-rw-------  1 root root  2256417 Mar 25  2013 System.map-3.2.0-40-generic
-rw-------  1 root root  2256808 Apr 25  2013 System.map-3.2.0-41-generic
-rw-------  1 root root  2256808 May 15  2013 System.map-3.2.0-43-generic
-rw-------  1 root root  2257186 May 16  2013 System.map-3.2.0-44-generic
-rw-------  1 root root  2257186 May 29  2013 System.map-3.2.0-45-generic
-rw-------  1 root root  2258125 Jun  6  2013 System.map-3.2.0-48-generic
-rw-------  1 root root  2258125 Jun 18  2013 System.map-3.2.0-49-generic
-rw-------  1 root root  2259695 Dec  3  2013 System.map-3.2.0-58-generic
-rw-------  1 root root  2259808 Jan  7  2014 System.map-3.2.0-59-generic
-rw-------  1 root root  2259642 Feb 19  2014 System.map-3.2.0-60-generic
-rw-------  1 root root  2260419 May 16  2014 System.map-3.2.0-63-generic
-rw-------  1 root root  2261279 Jun  5  2014 System.map-3.2.0-64-generic
-rw-------  1 root root  2261493 Jul 15  2014 System.map-3.2.0-67-generic
-rw-------  1 root root  2261768 Aug 13  2014 System.map-3.2.0-68-generic
-rw-------  1 root root  2261768 Sep  2  2014 System.map-3.2.0-69-generic
-rw-------  1 root root  2261833 Sep 24  2014 System.map-3.2.0-70-generic
-rw-------  1 root root  2262122 Nov  6  2014 System.map-3.2.0-72-generic
-rw-------  1 root root  2262122 Dec  9  2014 System.map-3.2.0-74-generic
-rw-------  1 root root  2262103 Dec 16  2014 System.map-3.2.0-75-generic
-rw-------  1 root root  2262487 Jan 13  2015 System.map-3.2.0-76-generic
-rw-------  1 root root  2262516 Mar 10  2015 System.map-3.2.0-77-generic
-rw-------  1 root root  2263145 Mar 12  2015 System.map-3.2.0-79-generic
-rw-------  1 root root  2263145 Mar 23  2015 System.map-3.2.0-80-generic
-rw-------  1 root root  2263145 Apr 27 23:08 System.map-3.2.0-82-generic
-rw-------  1 root root  2263170 Apr 29 17:40 System.map-3.2.0-83-generic
-rw-------  1 root root  2263170 May  5 20:40 System.map-3.2.0-84-generic
-rw-------  1 root root  2263401 May 26 18:17 System.map-3.2.0-85-generic
-rw-------  1 root root  2263401 Jun 17 23:44 System.map-3.2.0-86-generic
-rw-------  1 root root  2263334 Jul  6 23:20 System.map-3.2.0-88-generic
-rw-------  1 root root  2263334 Jul 28 11:49 System.map-3.2.0-89-generic
-rw-------  1 root root  4889952 Jul  6 23:20 vmlinuz-3.2.0-88-generic
-rw-------  1 root root  4890208 Jul 28 11:49 vmlinuz-3.2.0-89-generic
aab@aab-Latitude-E6400:~$ 



```
I think we should clean them up!!!

---

### Post by Bashing-om on 2015-10-05
aab001; Yes !

"I think we should clean them up!!!" YES !

Copy and paste the following into your terminal and execute :

```

sudo rm -rf /usr/src/linux-headers-2.6.38-{8,10,11}
sudo rm -rf /usr/src/linux-headers-2.6.38-{8,10,11}-generic
sudo rm -rf /usr/src/linux-headers-3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77}
sudo rm -rf /usr/src/linux-headers-3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77}-generic
sudo rm -rf /usr/src/linux-headers-3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77}-greneric-pae

sudo rm -rf /lib/modules/2.6.38-{8,10,11}-generic
sudo rm -rf /lib/modules/3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77,79,80,82,83,84,85}-generic-pae

sudo rm /boot/abi-3.2.0-{32,33,34,35,36,37,38,40,41,43,44,45,48,49,58,59,60,63,64,67,68,69,70,72,74,75,76,77,79,80,82,83,84,85}-generic
sudo rm /boot/config-3.2.0-{32,33,34,35,36,37,38,40,41,43,44,45,48,49,64,67,68,69,70}-generic
sudo rm /boot/initrd.img-3.2.0-{32,35,36,37,38,40,41,43,44,45,48,49,58,59,60,63,64,67,68,69,70,72,74,75,76,77,79,80,83,84,85}-generic
sudo rm /boot/System.map-3.2.0-{32,33,34,35,36,37,38,40,41,43,44,45,48,49,58,59,60,63,64,67,68,69,70,72,74,75,76,77,79,80,82,83,84,85}-generic

```

Now lets' get a fresh new look and see what all I have missed and what remains to be done before putting these pieces back together.

Show me a new:
```

uname -r
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```
So we can properly proceed to clean this mess up. There is still more to be done before we can purge the system of the old kernels's files .

What a mess, try'n to get these files down to somewhat of a more manageable situation to the point we can readily see what else is to be done. Get us out of this too many numbers/conflicts overload !

[INDENT][INDENT]getting there
[INDENT][INDENT][INDENT]little by little
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-10-06
> **Bashing-om said:**
> aab001; Yes !

"I think we should clean them up!!!" YES !

Copy and paste the following into your terminal and execute :

```

sudo rm -rf /usr/src/linux-headers-2.6.38-{8,10,11}
sudo rm -rf /usr/src/linux-headers-2.6.38-{8,10,11}-generic
sudo rm -rf /usr/src/linux-headers-3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77}
sudo rm -rf /usr/src/linux-headers-3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77}-generic
sudo rm -rf /usr/src/linux-headers-3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77}-greneric-pae

sudo rm -rf /lib/modules/2.6.38-{8,10,11}-generic
sudo rm -rf /lib/modules/3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77,79,80,82,83,84,85}-generic-pae

sudo rm /boot/abi-3.2.0-{32,33,34,35,36,37,38,40,41,43,44,45,48,49,58,59,60,63,64,67,68,69,70,72,74,75,76,77,79,80,82,83,84,85}-generic
sudo rm /boot/config-3.2.0-{32,33,34,35,36,37,38,40,41,43,44,45,48,49,64,67,68,69,70}-generic
sudo rm /boot/initrd.img-3.2.0-{32,35,36,37,38,40,41,43,44,45,48,49,58,59,60,63,64,67,68,69,70,72,74,75,76,77,79,80,83,84,85}-generic
sudo rm /boot/System.map-3.2.0-{32,33,34,35,36,37,38,40,41,43,44,45,48,49,58,59,60,63,64,67,68,69,70,72,74,75,76,77,79,80,82,83,84,85}-generic

```

Now lets' get a fresh new look and see what all I have missed and what remains to be done before putting these pieces back together.

Show me a new:
```

uname -r
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```
So we can properly proceed to clean this mess up. There is still more to be done before we can purge the system of the old kernels's files .

What a mess, try'n to get these files down to somewhat of a more manageable situation to the point we can readily see what else is to be done. Get us out of this too many numbers/conflicts overload !
[INDENT][INDENT]getting there[INDENT][INDENT][INDENT]little by little
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thank you very much Bashing-om, here is my output

```

aab@aab-Latitude-E6400:~$ uname -r
3.2.0-89-generic
aab@aab-Latitude-E6400:~$ ls -al /usr/src/
total 212
drwxrwsr-x 51 root src  12288 Oct  6 22:07 .
drwxr-xr-x 11 root root  4096 Oct 15  2011 ..
drwxr-xr-x  5 root root  4096 Sep 24  2013 bcmwl-6.20.155.1+bdcom
drwxr-xr-x  7 root root  4096 Oct 13  2012 linux-headers-3.2.0-32-generic-pae
drwxr-xr-x  7 root root  4096 Nov 17  2012 linux-headers-3.2.0-33-generic-pae
drwxr-xr-x  7 root root  4096 Dec  1  2012 linux-headers-3.2.0-34-generic-pae
drwxr-xr-x  7 root root  4096 Dec 19  2012 linux-headers-3.2.0-35-generic-pae
drwxr-xr-x  7 root root  4096 Jan 18  2013 linux-headers-3.2.0-36-generic-pae
drwxr-xr-x  7 root root  4096 Feb  1  2013 linux-headers-3.2.0-37-generic-pae
drwxr-xr-x  7 root root  4096 Feb 22  2013 linux-headers-3.2.0-38-generic-pae
drwxr-xr-x  7 root root  4096 Mar 19  2013 linux-headers-3.2.0-39-generic-pae
drwxr-xr-x  7 root root  4096 Apr 15  2013 linux-headers-3.2.0-40-generic-pae
drwxr-xr-x  7 root root  4096 May  2  2013 linux-headers-3.2.0-41-generic-pae
drwxr-xr-x  7 root root  4096 May 17  2013 linux-headers-3.2.0-43-generic-pae
drwxr-xr-x  7 root root  4096 May 24  2013 linux-headers-3.2.0-44-generic-pae
drwxr-xr-x  7 root root  4096 Jun  1  2013 linux-headers-3.2.0-45-generic-pae
drwxr-xr-x  7 root root  4096 Jun 15  2013 linux-headers-3.2.0-48-generic-pae
drwxr-xr-x  7 root root  4096 Jul  6  2013 linux-headers-3.2.0-49-generic-pae
drwxr-xr-x  7 root root  4096 Aug 10  2013 linux-headers-3.2.0-51-generic-pae
drwxr-xr-x  7 root root  4096 Aug 21  2013 linux-headers-3.2.0-52-generic-pae
drwxr-xr-x  7 root root  4096 Sep  8  2013 linux-headers-3.2.0-53-generic-pae
drwxr-xr-x  7 root root  4096 Sep 29  2013 linux-headers-3.2.0-54-generic-pae
drwxr-xr-x  7 root root  4096 Oct 25  2013 linux-headers-3.2.0-55-generic-pae
drwxr-xr-x  7 root root  4096 Nov  8  2013 linux-headers-3.2.0-56-generic-pae
drwxr-xr-x  7 root root  4096 Dec  3  2013 linux-headers-3.2.0-57-generic-pae
drwxr-xr-x  7 root root  4096 Jan  7  2014 linux-headers-3.2.0-58-generic-pae
drwxr-xr-x  7 root root  4096 Feb 20  2014 linux-headers-3.2.0-59-generic-pae
drwxr-xr-x  7 root root  4096 Mar  8  2014 linux-headers-3.2.0-60-generic-pae
drwxr-xr-x  7 root root  4096 May  6  2014 linux-headers-3.2.0-61-generic-pae
drwxr-xr-x  7 root root  4096 May 27  2014 linux-headers-3.2.0-63-generic-pae
drwxr-xr-x  7 root root  4096 Jun  7  2014 linux-headers-3.2.0-64-generic-pae
drwxr-xr-x  7 root root  4096 Aug 13  2014 linux-headers-3.2.0-67-generic-pae
drwxr-xr-x  7 root root  4096 Sep 16  2014 linux-headers-3.2.0-68-generic-pae
drwxr-xr-x  7 root root  4096 Sep 24  2014 linux-headers-3.2.0-69-generic-pae
drwxr-xr-x  7 root root  4096 Oct  9  2014 linux-headers-3.2.0-70-generic-pae
drwxr-xr-x  7 root root  4096 Nov 25  2014 linux-headers-3.2.0-72-generic-pae
drwxr-xr-x  7 root root  4096 Dec 12  2014 linux-headers-3.2.0-74-generic-pae
drwxr-xr-x  7 root root  4096 Jan 13  2015 linux-headers-3.2.0-75-generic-pae
drwxr-xr-x  7 root root  4096 Feb  9  2015 linux-headers-3.2.0-76-generic-pae
drwxr-xr-x  7 root root  4096 Mar 13  2015 linux-headers-3.2.0-77-generic-pae
drwxr-xr-x 24 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86
drwxr-xr-x  7 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86-generic
drwxr-xr-x  7 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86-generic-pae
drwxr-xr-x 24 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88
drwxr-xr-x  7 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88-generic
drwxr-xr-x  7 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88-generic-pae
drwxr-xr-x 24 root root  4096 Aug 23 18:24 linux-headers-3.2.0-89
drwxr-xr-x  7 root root  4096 Aug 23 18:24 linux-headers-3.2.0-89-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 nvidia-173-173.14.39
drwxr-xr-x  3 root root  4096 Dec 12  2014 nvidia-304-304.125
drwxr-xr-x  3 root root  4096 Dec 12  2014 nvidia-331-331.113
aab@aab-Latitude-E6400:~$ ls -al /lib/modules/
total 36
drwxr-xr-x  7 root root  4096 Oct  6 22:09 .
drwxr-xr-x 27 root root 12288 May 22 21:15 ..
drwxr-xr-x  5 root root  4096 Jun 22 13:12 3.2.0-86-generic
drwxr-xr-x  3 root root  4096 Jun 16 11:31 3.2.0-86-generic-pae
drwxr-xr-x  5 root root  4096 Jul 29 01:51 3.2.0-88-generic
drwxr-xr-x  3 root root  4096 Jul 29 01:52 3.2.0-88-generic-pae
drwxr-xr-x  5 root root  4096 Sep 12 15:01 3.2.0-89-generic
aab@aab-Latitude-E6400:~$ ls -al /boot/
total 115960
drwxr-xr-x  3 root root    20480 Oct  6 22:13 .
drwxr-xr-x 25 root root     4096 Sep 12 15:01 ..
-rw-r--r--  1 root root   801170 Jun 17 23:44 abi-3.2.0-86-generic
-rw-r--r--  1 root root   801170 Jul  6 23:20 abi-3.2.0-88-generic
-rw-r--r--  1 root root   801170 Jul 28 11:49 abi-3.2.0-89-generic
-rw-r--r--  1 root root   147799 Jul  6 23:20 config-3.2.0-88-generic
-rw-r--r--  1 root root   147799 Jul 28 11:49 config-3.2.0-89-generic
drwxr-xr-x  3 root root    12288 Sep 12 15:02 grub
-rw-r--r--  1 root root 19748958 Nov 17  2012 initrd.img-3.2.0-33-generic
-rw-r--r--  1 root root 19822446 Apr 30 14:32 initrd.img-3.2.0-82-generic
-rw-r--r--  1 root root 19823822 Jun 22 13:13 initrd.img-3.2.0-86-generic
-rw-r--r--  1 root root 19821946 Jul 29 01:50 initrd.img-3.2.0-88-generic
-rw-r--r--  1 root root 19822747 Sep 12 15:02 initrd.img-3.2.0-89-generic
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2263401 Jun 17 23:44 System.map-3.2.0-86-generic
-rw-------  1 root root  2263334 Jul  6 23:20 System.map-3.2.0-88-generic
-rw-------  1 root root  2263334 Jul 28 11:49 System.map-3.2.0-89-generic
-rw-------  1 root root  4889952 Jul  6 23:20 vmlinuz-3.2.0-88-generic
-rw-------  1 root root  4890208 Jul 28 11:49 vmlinuz-3.2.0-89-generic
aab@aab-Latitude-E6400:~$ dpkg -l | grep linux-
ii  linux-firmware                         1.79.18                                    Firmware for Linux kernel drivers
ii  linux-generic                          3.2.0.89.103                               Complete Generic Linux kernel
ii  linux-headers-2.6.38-10                2.6.38-10.46                               Header files related to Linux kernel version 2.6.38
ii  linux-headers-2.6.38-10-generic        2.6.38-10.46                               Linux kernel headers for version 2.6.38 on x86/x86_64
ii  linux-headers-2.6.38-11                2.6.38-11.50                               Header files related to Linux kernel version 2.6.38
ii  linux-headers-2.6.38-11-generic        2.6.38-11.50                               Linux kernel headers for version 2.6.38 on x86/x86_64
ii  linux-headers-2.6.38-8                 2.6.38-8.42                                Header files related to Linux kernel version 2.6.38
ii  linux-headers-2.6.38-8-generic         2.6.38-8.42                                Linux kernel headers for version 2.6.38 on x86/x86_64
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
ii  linux-headers-3.2.0-54                 3.2.0-54.82                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic         3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54-generic-pae     3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55                 3.2.0-55.85                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic         3.2.0-55.85                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55-generic-pae     3.2.0-55.85                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-56                 3.2.0-56.86                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-56-generic         3.2.0-56.86                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-56-generic-pae     3.2.0-56.86                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-57                 3.2.0-57.87                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-57-generic         3.2.0-57.87                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-57-generic-pae     3.2.0-57.87                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-58                 3.2.0-58.88                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-58-generic         3.2.0-58.88                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-58-generic-pae     3.2.0-58.88                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-59                 3.2.0-59.90                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-59-generic         3.2.0-59.90                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-59-generic-pae     3.2.0-59.90                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-60                 3.2.0-60.91                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-60-generic         3.2.0-60.91                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-60-generic-pae     3.2.0-60.91                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-61                 3.2.0-61.93                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-61-generic         3.2.0-61.93                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-61-generic-pae     3.2.0-61.93                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-63                 3.2.0-63.95                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-63-generic         3.2.0-63.95                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-63-generic-pae     3.2.0-63.95                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-64                 3.2.0-64.97                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-64-generic         3.2.0-64.97                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-64-generic-pae     3.2.0-64.97                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-67                 3.2.0-67.101                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67-generic         3.2.0-67.101                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-67-generic-pae     3.2.0-67.101                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-68                 3.2.0-68.102                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-68-generic         3.2.0-68.102                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-68-generic-pae     3.2.0-68.102                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-69                 3.2.0-69.103                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-69-generic         3.2.0-69.103                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-69-generic-pae     3.2.0-69.103                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-70                 3.2.0-70.105                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-70-generic         3.2.0-70.105                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-70-generic-pae     3.2.0-70.105                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-72                 3.2.0-72.107                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-72-generic         3.2.0-72.107                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-72-generic-pae     3.2.0-72.107                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-74                 3.2.0-74.109                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-74-generic         3.2.0-74.109                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-74-generic-pae     3.2.0-74.109                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-75                 3.2.0-75.110                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-75-generic         3.2.0-75.110                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-75-generic-pae     3.2.0-75.110                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-76                 3.2.0-76.111                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-76-generic         3.2.0-76.111                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-76-generic-pae     3.2.0-76.111                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-77                 3.2.0-77.114                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-77-generic         3.2.0-77.114                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-77-generic-pae     3.2.0-77.114                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-79                 3.2.0-79.115                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-79-generic         3.2.0-79.115                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-79-generic-pae     3.2.0-79.115                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-80                 3.2.0-80.116                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-80-generic         3.2.0-80.116                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-80-generic-pae     3.2.0-80.116                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-82                 3.2.0-82.119                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-82-generic         3.2.0-82.119                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-82-generic-pae     3.2.0-82.119                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-83                 3.2.0-83.120                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-83-generic         3.2.0-83.120                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-83-generic-pae     3.2.0-83.120                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-84                 3.2.0-84.121                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-84-generic         3.2.0-84.121                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-84-generic-pae     3.2.0-84.121                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-85                 3.2.0-85.122                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-85-generic         3.2.0-85.122                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-85-generic-pae     3.2.0-85.122                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-86                 3.2.0-86.124                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-86-generic         3.2.0-86.124                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-86-generic-pae     3.2.0-86.124                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-88                 3.2.0-88.126                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-88-generic         3.2.0-88.126                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-88-generic-pae     3.2.0-88.126                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-89                 3.2.0-89.127                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-89-generic         3.2.0-89.127                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic                  3.2.0.89.103                               Generic Linux kernel headers
iU  linux-headers-generic-pae              3.2.0.89.103                               Generic Linux kernel headers
rc  linux-image-2.6.35-22-generic          2.6.35-22.35                               Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.35-25-generic          2.6.35-25.44                               Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.35-27-generic          2.6.35-27.48                               Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.35-28-generic          2.6.35-28.50                               Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.38-10-generic          2.6.38-10.46                               Linux kernel image for version 2.6.38 on x86/x86_64
ii  linux-image-2.6.38-11-generic          2.6.38-11.50                               Linux kernel image for version 2.6.38 on x86/x86_64
ii  linux-image-2.6.38-8-generic           2.6.38-8.42                                Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-3.0.0-12-generic           3.0.0-12.20                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-13-generic           3.0.0-13.22                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-14-generic           3.0.0-14.23                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-15-generic           3.0.0-15.26                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-16-generic           3.0.0-16.29                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-17-generic           3.0.0-17.30                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-19-generic           3.0.0-19.33                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-20-generic           3.0.0-20.34                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-21-generic           3.0.0-21.35                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-22-generic           3.0.0-22.36                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-23-generic           3.0.0-23.39                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-25-generic           3.0.0-25.41                                Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-26-generic           3.0.0-26.43                                Linux kernel image for version 3.0.0 on x86/x86_64
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
ii  linux-image-3.2.0-55-generic           3.2.0-55.85                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-56-generic           3.2.0-56.86                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-57-generic           3.2.0-57.87                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-58-generic           3.2.0-58.88                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-59-generic           3.2.0-59.90                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-60-generic           3.2.0-60.91                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-61-generic           3.2.0-61.93                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-63-generic           3.2.0-63.95                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-64-generic           3.2.0-64.97                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-67-generic           3.2.0-67.101                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-68-generic           3.2.0-68.102                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-69-generic           3.2.0-69.103                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-70-generic           3.2.0-70.105                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-72-generic           3.2.0-72.107                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-74-generic           3.2.0-74.109                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-75-generic           3.2.0-75.110                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-76-generic           3.2.0-76.111                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-77-generic           3.2.0-77.114                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-79-generic           3.2.0-79.115                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-80-generic           3.2.0-80.116                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-82-generic           3.2.0-82.119                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-83-generic           3.2.0-83.120                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-84-generic           3.2.0-84.121                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-85-generic           3.2.0-85.122                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-86-generic           3.2.0-86.124                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-88-generic           3.2.0-88.126                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-89-generic           3.2.0-89.127                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.89.103                               Generic Linux kernel image
ii  linux-libc-dev                         3.2.0-88.126                               Linux Kernel Headers for development
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu1.1                     base package for ALSA and OSS sound systems
ii  syslinux-common                        2:4.05+dfsg-2                              collection of boot loaders (common files)
ii  syslinux-legacy                        2:3.63+dfsg-2ubuntu5                       Bootloader for Linux/i386 using MS-DOS floppies
aab@aab-Latitude-E6400:~$ 



```

---

### Post by Bashing-om on 2015-10-06
aab001; Hey :

Is there a problem in my communications skills that what I direct to do does not get accomplished ? We do not move forward for having to keep going back .. and then taking the time to redo what has already been done and then the time to check that what is to be redone is correct. Not to discount the mental effort to keep track of where we are in this long process .

The directive was to " sudo rm -rf /usr/src/linux-headers-3.2.0-{32,A-Whole-bunch-of-Versions}
and yet all those directories still exist in /usr/src/
Is there a problem that the command is not completing ?
Is my usage of the English language a barrier here ?

We can not move forward until we get ALL those old obsolete files removed from the system and then we look forward to purging the kernels whose files are now gone . The removal process must be completed before the purging begins.

In the event there is some problem in removing these files and directories, we need to address that .

Then when we complete the removal of the directories in /usr/src/. We Can then "look" to see what else remains. And then finally finish this up.
[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-10-09
aab001; Hello :

Been a while, request to know your current status.
What are 'we' going to do ?

[INDENT][INDENT]we will not leave you,
[INDENT][INDENT][INDENT]so long as a problem exists
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-10-11
> **Bashing-om said:**
> aab001; Hello :

Been a while, request to know your current status.
What are 'we' going to do ?
[INDENT][INDENT]we will not leave you,[INDENT][INDENT][INDENT]so long as a problem exists
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Dear Bashing-om

I am really sorry for upsetting you. In fact, you don't have communication problem maybe I do (English is not my first language) and my weak background in ubuntu I think it makes it worst!!! but trust me I did my best. Before I posted my problem here I tried to solve it my self and I did delete the files one by one but every time I find it's still there!!!
maybe also it is my mistake that I didn't tell you about this but I thought there is something wrong with the things that I do. But I paste all the results just to give you a clear vision about what's happing..
   I am really delighted that you still want to help me but I do the same commands but the results are the same!!!!no files deleted (I was afraid to tell you that)

 

 many thanks in advance
 



Best

---

### Post by Bashing-om on 2015-10-11
aab001; Hi .

I appreciate your frankness... 
Look, we know and understand that one is not born knowing, we do know there is a learning curve here. Not knowing will not be held against you in the least .

Let's address removing files that are a part of a package as in kernels. There is the package management system, and when we step outside the bounds of what the package manager controls by manually removing files behind the package manager's back ... we are asking for problems. ... This package management system exists for very good reasons. The tools to manage packages include 'apt', based on 'dpkg' and we generally use these tools . 
OK, the integrity of the package management system has been breached by manually removing files. Such that our task is to get the package manager in a consistent state. We do that by removing the inconsistent files and making sure that the files remaining in the directories /usr/src/, /lib/modules, /boot ALL match .. Then we have the package manager repair the damage - with what it can now work with. The tools we work with to get the package manager in a consistent state do vary. From manaully removing files in /usr/src and /lib/modules, to 'dpkg' to remove the old kernel file fragments ,,,,

How about we backup and regroup ... start this process all over from scratch .. get a new look at what is, as the files may have undergone changes since our last "look".

I have no "heartburn" in the least to take things slowly .. nor do I mind in the least explaining what we are doing, how we are doing it and why we are doing it ... Learning is the only means for you to know .  Always ask any question . We are all here to help.
----------------------------
Let's start all over:
Post back the outputs of terminal commands:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-
uname -r

```
the output of 'uname' is the currently booting kernel .. We MUST not remove it ! Keep that booting kernel in mind for me .. as I can and have lost sight of what that booting kernel is, and I can make an error ! If in any step something does not complete or go as expected,, we need to immediately address that failure before proceeding further .. We must get all files reflecting the same version sequence. That is the process .

Our present intermediate goal is to get all the associated directories to match with the version contents. Once that is done we can have the package manager repair it's self.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by aab001 on 2015-10-12
> **Bashing-om said:**
> aab001; Hi .

I appreciate your frankness... 
Look, we know and understand that one is not born knowing, we do know there is a learning curve here. Not knowing will not be held against you in the least .

Let's address removing files that are a part of a package as in kernels. There is the package management system, and when we step outside the bounds of what the package manager controls by manually removing files behind the package manager's back ... we are asking for problems. ... This package management system exists for very good reasons. The tools to manage packages include 'apt', based on 'dpkg' and we generally use these tools . 
OK, the integrity of the package management system has been breached by manually removing files. Such that our task is to get the package manager in a consistent state. We do that by removing the inconsistent files and making sure that the files remaining in the directories /usr/src/, /lib/modules, /boot ALL match .. Then we have the package manager repair the damage - with what it can now work with. The tools we work with to get the package manager in a consistent state do vary. From manaully removing files in /usr/src and /lib/modules, to 'dpkg' to remove the old kernel file fragments ,,,,

How about we backup and regroup ... start this process all over from scratch .. get a new look at what is, as the files may have undergone changes since our last "look".

I have no "heartburn" in the least to take things slowly .. nor do I mind in the least explaining what we are doing, how we are doing it and why we are doing it ... Learning is the only means for you to know .  Always ask any question . We are all here to help.
----------------------------
Let's start all over:
Post back the outputs of terminal commands:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-
uname -r

```
the output of 'uname' is the currently booting kernel .. We MUST not remove it ! Keep that booting kernel in mind for me .. as I can and have lost sight of what that booting kernel is, and I can make an error ! If in any step something does not complete or go as expected,, we need to immediately address that failure before proceeding further .. We must get all files reflecting the same version sequence. That is the process .

Our present intermediate goal is to get all the associated directories to match with the version contents. Once that is done we can have the package manager repair it's self.
[INDENT][INDENT]we can do this
[/INDENT]
[/INDENT]


   

 Dear Bashing-om,
 

 I am really delighted and optimistic since there are good people like you in this world who like to help others with patient.
 

 Here is my output
 ```

 aab@aab-Latitude-E6400:~$ ls -al /usr/src/ 
 total 212 
 drwxrwsr-x 51 root src  12288 Oct  6 22:07 . 
 drwxr-xr-x 11 root root  4096 Oct 15  2011 .. 
 drwxr-xr-x  5 root root  4096 Sep 24  2013 bcmwl-6.20.155.1+bdcom 
 drwxr-xr-x  7 root root  4096 Oct 13  2012 linux-headers-3.2.0-32-generic-pae 
 drwxr-xr-x  7 root root  4096 Nov 17  2012 linux-headers-3.2.0-33-generic-pae 
 drwxr-xr-x  7 root root  4096 Dec  1  2012 linux-headers-3.2.0-34-generic-pae 
 drwxr-xr-x  7 root root  4096 Dec 19  2012 linux-headers-3.2.0-35-generic-pae 
 drwxr-xr-x  7 root root  4096 Jan 18  2013 linux-headers-3.2.0-36-generic-pae 
 drwxr-xr-x  7 root root  4096 Feb  1  2013 linux-headers-3.2.0-37-generic-pae 
 drwxr-xr-x  7 root root  4096 Feb 22  2013 linux-headers-3.2.0-38-generic-pae 
 drwxr-xr-x  7 root root  4096 Mar 19  2013 linux-headers-3.2.0-39-generic-pae 
 drwxr-xr-x  7 root root  4096 Apr 15  2013 linux-headers-3.2.0-40-generic-pae 
 drwxr-xr-x  7 root root  4096 May  2  2013 linux-headers-3.2.0-41-generic-pae 
 drwxr-xr-x  7 root root  4096 May 17  2013 linux-headers-3.2.0-43-generic-pae 
 drwxr-xr-x  7 root root  4096 May 24  2013 linux-headers-3.2.0-44-generic-pae 
 drwxr-xr-x  7 root root  4096 Jun  1  2013 linux-headers-3.2.0-45-generic-pae 
 drwxr-xr-x  7 root root  4096 Jun 15  2013 linux-headers-3.2.0-48-generic-pae 
 drwxr-xr-x  7 root root  4096 Jul  6  2013 linux-headers-3.2.0-49-generic-pae 
 drwxr-xr-x  7 root root  4096 Aug 10  2013 linux-headers-3.2.0-51-generic-pae 
 drwxr-xr-x  7 root root  4096 Aug 21  2013 linux-headers-3.2.0-52-generic-pae 
 drwxr-xr-x  7 root root  4096 Sep  8  2013 linux-headers-3.2.0-53-generic-pae 
 drwxr-xr-x  7 root root  4096 Sep 29  2013 linux-headers-3.2.0-54-generic-pae 
 drwxr-xr-x  7 root root  4096 Oct 25  2013 linux-headers-3.2.0-55-generic-pae 
 drwxr-xr-x  7 root root  4096 Nov  8  2013 linux-headers-3.2.0-56-generic-pae 
 drwxr-xr-x  7 root root  4096 Dec  3  2013 linux-headers-3.2.0-57-generic-pae 
 drwxr-xr-x  7 root root  4096 Jan  7  2014 linux-headers-3.2.0-58-generic-pae 
 drwxr-xr-x  7 root root  4096 Feb 20  2014 linux-headers-3.2.0-59-generic-pae 
 drwxr-xr-x  7 root root  4096 Mar  8  2014 linux-headers-3.2.0-60-generic-pae 
 drwxr-xr-x  7 root root  4096 May  6  2014 linux-headers-3.2.0-61-generic-pae 
 drwxr-xr-x  7 root root  4096 May 27  2014 linux-headers-3.2.0-63-generic-pae 
 drwxr-xr-x  7 root root  4096 Jun  7  2014 linux-headers-3.2.0-64-generic-pae 
 drwxr-xr-x  7 root root  4096 Aug 13  2014 linux-headers-3.2.0-67-generic-pae 
 drwxr-xr-x  7 root root  4096 Sep 16  2014 linux-headers-3.2.0-68-generic-pae 
 drwxr-xr-x  7 root root  4096 Sep 24  2014 linux-headers-3.2.0-69-generic-pae 
 drwxr-xr-x  7 root root  4096 Oct  9  2014 linux-headers-3.2.0-70-generic-pae 
 drwxr-xr-x  7 root root  4096 Nov 25  2014 linux-headers-3.2.0-72-generic-pae 
 drwxr-xr-x  7 root root  4096 Dec 12  2014 linux-headers-3.2.0-74-generic-pae 
 drwxr-xr-x  7 root root  4096 Jan 13  2015 linux-headers-3.2.0-75-generic-pae 
 drwxr-xr-x  7 root root  4096 Feb  9  2015 linux-headers-3.2.0-76-generic-pae 
 drwxr-xr-x  7 root root  4096 Mar 13  2015 linux-headers-3.2.0-77-generic-pae 
 drwxr-xr-x 24 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86 
 drwxr-xr-x  7 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86-generic 
 drwxr-xr-x  7 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86-generic-pae 
 drwxr-xr-x 24 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88 
 drwxr-xr-x  7 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88-generic 
 drwxr-xr-x  7 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88-generic-pae 
 drwxr-xr-x 24 root root  4096 Aug 23 18:24 linux-headers-3.2.0-89 
 drwxr-xr-x  7 root root  4096 Aug 23 18:24 linux-headers-3.2.0-89-generic 
 drwxr-xr-x  3 root root  4096 Feb  3  2014 nvidia-173-173.14.39 
 drwxr-xr-x  3 root root  4096 Dec 12  2014 nvidia-304-304.125 
 drwxr-xr-x  3 root root  4096 Dec 12  2014 nvidia-331-331.113 
 aab@aab-Latitude-E6400:~$ ls -al /lib/modules/ 
 total 36 
 drwxr-xr-x  7 root root  4096 Oct  6 22:09 . 
 drwxr-xr-x 27 root root 12288 May 22 21:15 .. 
 drwxr-xr-x  5 root root  4096 Jun 22 13:12 3.2.0-86-generic 
 drwxr-xr-x  3 root root  4096 Jun 16 11:31 3.2.0-86-generic-pae 
 drwxr-xr-x  5 root root  4096 Jul 29 01:51 3.2.0-88-generic 
 drwxr-xr-x  3 root root  4096 Jul 29 01:52 3.2.0-88-generic-pae 
 drwxr-xr-x  5 root root  4096 Sep 12 15:01 3.2.0-89-generic 
 aab@aab-Latitude-E6400:~$ ls -al /boot/ 
 total 115960 
 drwxr-xr-x  3 root root    20480 Oct  6 22:13 . 
 drwxr-xr-x 25 root root     4096 Sep 12 15:01 .. 
 -rw-r--r--  1 root root   801170 Jun 17 23:44 abi-3.2.0-86-generic 
 -rw-r--r--  1 root root   801170 Jul  6 23:20 abi-3.2.0-88-generic 
 -rw-r--r--  1 root root   801170 Jul 28 11:49 abi-3.2.0-89-generic 
 -rw-r--r--  1 root root   147799 Jul  6 23:20 config-3.2.0-88-generic 
 -rw-r--r--  1 root root   147799 Jul 28 11:49 config-3.2.0-89-generic 
 drwxr-xr-x  3 root root    12288 Sep 12 15:02 grub 
 -rw-r--r--  1 root root 19748958 Nov 17  2012 initrd.img-3.2.0-33-generic 
 -rw-r--r--  1 root root 19822446 Apr 30 14:32 initrd.img-3.2.0-82-generic 
 -rw-r--r--  1 root root 19823822 Jun 22 13:13 initrd.img-3.2.0-86-generic 
 -rw-r--r--  1 root root 19821946 Jul 29 01:50 initrd.img-3.2.0-88-generic 
 -rw-r--r--  1 root root 19822747 Sep 12 15:02 initrd.img-3.2.0-89-generic 
 -rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin 
 -rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin 
 -rw-------  1 root root  2263401 Jun 17 23:44 System.map-3.2.0-86-generic 
 -rw-------  1 root root  2263334 Jul  6 23:20 System.map-3.2.0-88-generic 
 -rw-------  1 root root  2263334 Jul 28 11:49 System.map-3.2.0-89-generic 
 -rw-------  1 root root  4889952 Jul  6 23:20 vmlinuz-3.2.0-88-generic 
 -rw-------  1 root root  4890208 Jul 28 11:49 vmlinuz-3.2.0-89-generic 
 aab@aab-Latitude-E6400:~$ dpkg -l | grep linux- 
 ii  linux-firmware                         1.79.18                                    Firmware for Linux kernel drivers 
 ii  linux-generic                          3.2.0.89.103                               Complete Generic Linux kernel 
 ii  linux-headers-2.6.38-10                2.6.38-10.46                               Header files related to Linux kernel version 2.6.38 
 ii  linux-headers-2.6.38-10-generic        2.6.38-10.46                               Linux kernel headers for version 2.6.38 on x86/x86_64 
 ii  linux-headers-2.6.38-11                2.6.38-11.50                               Header files related to Linux kernel version 2.6.38 
 ii  linux-headers-2.6.38-11-generic        2.6.38-11.50                               Linux kernel headers for version 2.6.38 on x86/x86_64 
 ii  linux-headers-2.6.38-8                 2.6.38-8.42                                Header files related to Linux kernel version 2.6.38 
 ii  linux-headers-2.6.38-8-generic         2.6.38-8.42                                Linux kernel headers for version 2.6.38 on x86/x86_64 
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
 ii  linux-headers-3.2.0-54                 3.2.0-54.82                                Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-54-generic         3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-54-generic-pae     3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-55                 3.2.0-55.85                                Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-55-generic         3.2.0-55.85                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-55-generic-pae     3.2.0-55.85                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-56                 3.2.0-56.86                                Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-56-generic         3.2.0-56.86                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-56-generic-pae     3.2.0-56.86                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-57                 3.2.0-57.87                                Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-57-generic         3.2.0-57.87                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-57-generic-pae     3.2.0-57.87                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-58                 3.2.0-58.88                                Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-58-generic         3.2.0-58.88                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-58-generic-pae     3.2.0-58.88                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-59                 3.2.0-59.90                                Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-59-generic         3.2.0-59.90                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-59-generic-pae     3.2.0-59.90                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-60                 3.2.0-60.91                                Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-60-generic         3.2.0-60.91                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-60-generic-pae     3.2.0-60.91                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-61                 3.2.0-61.93                                Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-61-generic         3.2.0-61.93                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-61-generic-pae     3.2.0-61.93                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-63                 3.2.0-63.95                                Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-63-generic         3.2.0-63.95                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-63-generic-pae     3.2.0-63.95                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-64                 3.2.0-64.97                                Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-64-generic         3.2.0-64.97                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-64-generic-pae     3.2.0-64.97                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-67                 3.2.0-67.101                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-67-generic         3.2.0-67.101                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-67-generic-pae     3.2.0-67.101                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-68                 3.2.0-68.102                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-68-generic         3.2.0-68.102                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-68-generic-pae     3.2.0-68.102                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-69                 3.2.0-69.103                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-69-generic         3.2.0-69.103                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-69-generic-pae     3.2.0-69.103                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-70                 3.2.0-70.105                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-70-generic         3.2.0-70.105                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-70-generic-pae     3.2.0-70.105                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-72                 3.2.0-72.107                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-72-generic         3.2.0-72.107                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-72-generic-pae     3.2.0-72.107                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-74                 3.2.0-74.109                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-74-generic         3.2.0-74.109                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-74-generic-pae     3.2.0-74.109                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-75                 3.2.0-75.110                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-75-generic         3.2.0-75.110                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-75-generic-pae     3.2.0-75.110                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-76                 3.2.0-76.111                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-76-generic         3.2.0-76.111                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-76-generic-pae     3.2.0-76.111                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-77                 3.2.0-77.114                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-77-generic         3.2.0-77.114                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-77-generic-pae     3.2.0-77.114                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-79                 3.2.0-79.115                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-79-generic         3.2.0-79.115                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-79-generic-pae     3.2.0-79.115                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-80                 3.2.0-80.116                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-80-generic         3.2.0-80.116                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-80-generic-pae     3.2.0-80.116                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-82                 3.2.0-82.119                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-82-generic         3.2.0-82.119                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-82-generic-pae     3.2.0-82.119                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-83                 3.2.0-83.120                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-83-generic         3.2.0-83.120                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-83-generic-pae     3.2.0-83.120                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-84                 3.2.0-84.121                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-84-generic         3.2.0-84.121                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-84-generic-pae     3.2.0-84.121                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-85                 3.2.0-85.122                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-85-generic         3.2.0-85.122                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-85-generic-pae     3.2.0-85.122                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-86                 3.2.0-86.124                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-86-generic         3.2.0-86.124                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-86-generic-pae     3.2.0-86.124                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-88                 3.2.0-88.126                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-88-generic         3.2.0-88.126                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-88-generic-pae     3.2.0-88.126                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-3.2.0-89                 3.2.0-89.127                               Header files related to Linux kernel version 3.2.0 
 ii  linux-headers-3.2.0-89-generic         3.2.0-89.127                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-headers-generic                  3.2.0.89.103                               Generic Linux kernel headers 
 iU  linux-headers-generic-pae              3.2.0.89.103                               Generic Linux kernel headers 
 rc  linux-image-2.6.35-22-generic          2.6.35-22.35                               Linux kernel image for version 2.6.35 on x86/x86_64 
 rc  linux-image-2.6.35-25-generic          2.6.35-25.44                               Linux kernel image for version 2.6.35 on x86/x86_64 
 rc  linux-image-2.6.35-27-generic          2.6.35-27.48                               Linux kernel image for version 2.6.35 on x86/x86_64 
 rc  linux-image-2.6.35-28-generic          2.6.35-28.50                               Linux kernel image for version 2.6.35 on x86/x86_64 
 ii  linux-image-2.6.38-10-generic          2.6.38-10.46                               Linux kernel image for version 2.6.38 on x86/x86_64 
 ii  linux-image-2.6.38-11-generic          2.6.38-11.50                               Linux kernel image for version 2.6.38 on x86/x86_64 
 ii  linux-image-2.6.38-8-generic           2.6.38-8.42                                Linux kernel image for version 2.6.38 on x86/x86_64 
 rc  linux-image-3.0.0-12-generic           3.0.0-12.20                                Linux kernel image for version 3.0.0 on x86/x86_64 
 rc  linux-image-3.0.0-13-generic           3.0.0-13.22                                Linux kernel image for version 3.0.0 on x86/x86_64 
 rc  linux-image-3.0.0-14-generic           3.0.0-14.23                                Linux kernel image for version 3.0.0 on x86/x86_64 
 rc  linux-image-3.0.0-15-generic           3.0.0-15.26                                Linux kernel image for version 3.0.0 on x86/x86_64 
 rc  linux-image-3.0.0-16-generic           3.0.0-16.29                                Linux kernel image for version 3.0.0 on x86/x86_64 
 rc  linux-image-3.0.0-17-generic           3.0.0-17.30                                Linux kernel image for version 3.0.0 on x86/x86_64 
 rc  linux-image-3.0.0-19-generic           3.0.0-19.33                                Linux kernel image for version 3.0.0 on x86/x86_64 
 rc  linux-image-3.0.0-20-generic           3.0.0-20.34                                Linux kernel image for version 3.0.0 on x86/x86_64 
 rc  linux-image-3.0.0-21-generic           3.0.0-21.35                                Linux kernel image for version 3.0.0 on x86/x86_64 
 rc  linux-image-3.0.0-22-generic           3.0.0-22.36                                Linux kernel image for version 3.0.0 on x86/x86_64 
 rc  linux-image-3.0.0-23-generic           3.0.0-23.39                                Linux kernel image for version 3.0.0 on x86/x86_64 
 rc  linux-image-3.0.0-25-generic           3.0.0-25.41                                Linux kernel image for version 3.0.0 on x86/x86_64 
 ii  linux-image-3.0.0-26-generic           3.0.0-26.43                                Linux kernel image for version 3.0.0 on x86/x86_64 
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
 ii  linux-image-3.2.0-55-generic           3.2.0-55.85                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-56-generic           3.2.0-56.86                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-57-generic           3.2.0-57.87                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-58-generic           3.2.0-58.88                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-59-generic           3.2.0-59.90                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-60-generic           3.2.0-60.91                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-61-generic           3.2.0-61.93                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-63-generic           3.2.0-63.95                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-64-generic           3.2.0-64.97                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-67-generic           3.2.0-67.101                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-68-generic           3.2.0-68.102                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-69-generic           3.2.0-69.103                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-70-generic           3.2.0-70.105                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-72-generic           3.2.0-72.107                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-74-generic           3.2.0-74.109                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-75-generic           3.2.0-75.110                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-76-generic           3.2.0-76.111                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-77-generic           3.2.0-77.114                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-79-generic           3.2.0-79.115                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-80-generic           3.2.0-80.116                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-82-generic           3.2.0-82.119                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-83-generic           3.2.0-83.120                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-84-generic           3.2.0-84.121                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-85-generic           3.2.0-85.122                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-86-generic           3.2.0-86.124                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-88-generic           3.2.0-88.126                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-3.2.0-89-generic           3.2.0-89.127                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP 
 ii  linux-image-generic                    3.2.0.89.103                               Generic Linux kernel image 
 ii  linux-libc-dev                         3.2.0-88.126                               Linux Kernel Headers for development 
 ii  linux-sound-base                       1.0.25+dfsg-0ubuntu1.1                     base package for ALSA and OSS sound systems 
 ii  syslinux-common                        2:4.05+dfsg-2                              collection of boot loaders (common files) 
 ii  syslinux-legacy                        2:3.63+dfsg-2ubuntu5                       Bootloader for Linux/i386 using MS-DOS floppies 
 aab@aab-Latitude-E6400:~$ uname -r 
 3.2.0-89-generic 
 aab@aab-Latitude-E6400:~$  
 
```

---

### Post by Bashing-om on 2015-10-12
aab001; Hello;

So long as you are trying - and learning- I will keep working to resolution .
OK, in small steps here, we are working to make all the directories hold matching version files for the respective directories.
Now we work on the /usr/src/ directory.
Run this ONE terminal command :
```

sudo rm -rf /usr/src/linux-headers-3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77}-greneric-pae

```
Then when this ONE command completes, we focus on the /boot directory .
Then continue on to the next steps // only a bit at the time as I do not want to overwhelm you and nor Miss anything in the process . Making sure that all is correct prior to repairing the package management system .

[INDENT][INDENT]It is a process and we will
[INDENT][INDENT][INDENT]arrive to the end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-10-13
> **Bashing-om said:**
> aab001; Hello;

So long as you are trying - and learning- I will keep working to resolution .
OK, in small steps here, we are working to make all the directories hold matching version files for the respective directories.
Now we work on the /usr/src/ directory.
Run this ONE terminal command :
```

sudo rm -rf /usr/src/linux-headers-3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77}-greneric-pae

```
Then when this ONE command completes, we focus on the /boot directory .
Then continue on to the next steps // only a bit at the time as I do not want to overwhelm you and nor Miss anything in the process . Making sure that all is correct prior to repairing the package management system .[INDENT][INDENT]It is a process and we will[INDENT][INDENT][INDENT]arrive to the end
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

Hi

I did complete this command.
```

aab@aab-Latitude-E6400:~$ sudo rm -rf /usr/src/linux-headers-3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77}-greneric-pae
[sudo] password for aab: 
aab@aab-Latitude-E6400:~$ 


```

---

### Post by Bashing-om on 2015-10-13
aab001; Great ...

Next up is the /boot partition to be cleaned up.

I need confirmation at this time what kernel you are presently booting - we must not mess with this kernel:
Post back:
```

uname -r

```
And as well a fresh "look" at what we are working with:
Post back :
```

ls -al /boot

```

Once we are sure the directories are consistent, we have the package manager heal it's self .

[INDENT][INDENT]small steps still, but
[INDENT][INDENT][INDENT]getting there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-10-14
> **Bashing-om said:**
> aab001; Great ...

Next up is the /boot partition to be cleaned up.

I need confirmation at this time what kernel you are presently booting - we must not mess with this kernel:
Post back:
```

uname -r

```
And as well a fresh "look" at what we are working with:
Post back :
```

ls -al /boot

```

Once we are sure the directories are consistent, we have the package manager heal it's self .[INDENT][INDENT]small steps still, but[INDENT][INDENT][INDENT]getting there
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hi, this is my output
```

aab@aab-Latitude-E6400:~$ uname -r
3.2.0-89-generic
aab@aab-Latitude-E6400:~$ ls -al /boot
total 115960
drwxr-xr-x  3 root root    20480 Oct  6 22:13 .
drwxr-xr-x 25 root root     4096 Sep 12 15:01 ..
-rw-r--r--  1 root root   801170 Jun 17 23:44 abi-3.2.0-86-generic
-rw-r--r--  1 root root   801170 Jul  6 23:20 abi-3.2.0-88-generic
-rw-r--r--  1 root root   801170 Jul 28 11:49 abi-3.2.0-89-generic
-rw-r--r--  1 root root   147799 Jul  6 23:20 config-3.2.0-88-generic
-rw-r--r--  1 root root   147799 Jul 28 11:49 config-3.2.0-89-generic
drwxr-xr-x  3 root root    12288 Sep 12 15:02 grub
-rw-r--r--  1 root root 19748958 Nov 17  2012 initrd.img-3.2.0-33-generic
-rw-r--r--  1 root root 19822446 Apr 30 14:32 initrd.img-3.2.0-82-generic
-rw-r--r--  1 root root 19823822 Jun 22 13:13 initrd.img-3.2.0-86-generic
-rw-r--r--  1 root root 19821946 Jul 29 01:50 initrd.img-3.2.0-88-generic
-rw-r--r--  1 root root 19822747 Sep 12 15:02 initrd.img-3.2.0-89-generic
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2263401 Jun 17 23:44 System.map-3.2.0-86-generic
-rw-------  1 root root  2263334 Jul  6 23:20 System.map-3.2.0-88-generic
-rw-------  1 root root  2263334 Jul 28 11:49 System.map-3.2.0-89-generic
-rw-------  1 root root  4889952 Jul  6 23:20 vmlinuz-3.2.0-88-generic
-rw-------  1 root root  4890208 Jul 28 11:49 vmlinuz-3.2.0-89-generic
aab@aab-Latitude-E6400:~$ 



```

---

### Post by Bashing-om on 2015-10-14
aab001; Good morning.

Making good progress.
Now we clean up the /boot directory. 

Run terminal commands:
```

sudo rm /boot/initrd.img-3.2.0-33-generic
sudo rm /boot/initrd.img-3.2.0-82-generic

```

Next repair the package system. I do need to see this output .
```

sudo apt-get -f install

```

Then we are down to the final step of cleaning up our vestiges of what remains.

[INDENT][INDENT]long process
[INDENT][INDENT][INDENT]getting short
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-10-14
> **Bashing-om said:**
> aab001; Good morning.

Making good progress.
Now we clean up the /boot directory. 

Run terminal commands:
```

sudo rm /boot/initrd.img-3.2.0-33-generic
sudo rm /boot/initrd.img-3.2.0-82-generic

```

Next repair the package system. I do need to see this output .
```

sudo apt-get -f install

```

Then we are down to the final step of cleaning up our vestiges of what remains.
[INDENT][INDENT]long process[INDENT][INDENT][INDENT]getting short
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

 Good evening, I hope this error is not some thing serious :(

```

aab@aab-Latitude-E6400:~$ sudo rm /boot/initrd.img-3.2.0-33-generic
[sudo] password for aab: 
aab@aab-Latitude-E6400:~$ sudo rm /boot/initrd.img-3.2.0-82-generic
aab@aab-Latitude-E6400:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libunity6 gir1.2-ubuntuoneui-3.0 linux-headers-3.2.0-32 linux-headers-3.2.0-32-generic libubuntuoneui-3.0-1 nvidia-settings-304
  libdee-1.0-1 linux-headers-3.2.0-32-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-91 linux-headers-3.2.0-91-generic-pae linux-headers-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-91 linux-headers-3.2.0-91-generic-pae
The following packages will be upgraded:
  linux-headers-generic-pae
1 upgraded, 2 newly installed, 0 to remove and 64 not upgraded.
1 not fully installed or removed.
Need to get 12.7 MB of archives.
After this operation, 67.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-91 all 3.2.0-91.129 [11.7 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-91-generic-pae i386 3.2.0-91.129 [981 kB]                
Get:3 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic-pae i386 3.2.0.91.105 [2,286 B]                        
Fetched 12.7 MB in 11s (1,064 kB/s)                                                                                                          
Selecting previously unselected package linux-headers-3.2.0-91.
(Reading database ... 1966968 files and directories currently installed.)
Unpacking linux-headers-3.2.0-91 (from .../linux-headers-3.2.0-91_3.2.0-91.129_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-91-generic-pae.
Unpacking linux-headers-3.2.0-91-generic-pae (from .../linux-headers-3.2.0-91-generic-pae_3.2.0-91.129_i386.deb) ...
Setting up linux-headers-3.2.0-91 (3.2.0-91.129) ...
Setting up linux-headers-3.2.0-91-generic-pae (3.2.0-91.129) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-91-generic-pae /boot/vmlinuz-3.2.0-91-generic-pae
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-89-generic-pae; however:
  Package linux-headers-3.2.0-89-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-headers-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
aab@aab-Latitude-E6400:~$ ^C




```

---

### Post by Bashing-om on 2015-10-14
aab001; Hey, hey !

Actually, looks quite good !

Now do:
```

sudo apt-get install --reinstall linux-headers-3.2.0-89-generic-pae

```

If that runs clean, and the package manager is in a happy state, we finish cleaning up the mess we made .

[INDENT][INDENT]so close now
[INDENT][INDENT][INDENT]I can smell the end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-10-14
> **Bashing-om said:**
> aab001; Hey, hey !

Actually, looks quite good !

Now do:
```

sudo apt-get install --reinstall linux-headers-3.2.0-89-generic-pae

```

If that runs clean, and the package manager is in a happy state, we finish cleaning up the mess we made .
[INDENT][INDENT]so close now[INDENT][INDENT][INDENT]I can smell the end
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hi, I can see it too

```

aab@aab-Latitude-E6400:~$ sudo apt-get install --reinstall linux-headers-3.2.0-89-generic-pae
[sudo] password for aab: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunity6 gir1.2-ubuntuoneui-3.0 linux-headers-3.2.0-32 linux-headers-3.2.0-32-generic libubuntuoneui-3.0-1 nvidia-settings-304
  libdee-1.0-1 linux-headers-3.2.0-32-generic-pae
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-3.2.0-89-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 65 not upgraded.
1 not fully installed or removed.
Need to get 968 kB of archives.
After this operation, 11.4 MB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-89-generic-pae i386 3.2.0-89.127 [968 kB]
Fetched 968 kB in 0s (1,177 kB/s)                      
(Reading database ... 1989313 files and directories currently installed.)
Unpacking linux-headers-3.2.0-89-generic-pae (from .../linux-headers-3.2.0-89-generic-pae_3.2.0-89.127_i386.deb) ...
Setting up linux-headers-3.2.0-89-generic-pae (3.2.0-89.127) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-89-generic-pae /boot/vmlinuz-3.2.0-89-generic-pae
Setting up linux-headers-generic-pae (3.2.0.89.103) ...
aab@aab-Latitude-E6400:~$ 



```

---

### Post by Bashing-om on 2015-10-14
aab001; Who said it could not happen ? ... Look'n good .

OK, finally .. clean up and make the package manager consistent.
Run this series of commands, carefully copy and paste - one at a time - these 10 commands: 
```

sudo apt-get purge linux-image-2.6.35-28-generic
sudo apt-get purge linux-headers-2.6.35-28-generic
sudo apt-get purge linux-headers-2.6.35-28

sudo apt-get purge linux-image-2.6.38-{8,10,11}-generic
sudo apt-get purge linux-headers-2.6.38-{8,10,11}-generic
sudo apt-get purge linux-headers-2.6.38-{8,10,11}

sudo apt-get purge linux-image-3.0.0-26-generic
sudo apt-get purge linux-headers-3.0.0-26-generic
sudo apt-get purge linux-headers-3.0.0-26

sudo apt-get purge linux-{headers,image}-3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77,79,80,82,83,84.85}-*

```

And now to verify our work .. see if now there is anything I have overlooked or forgot:
Give a fresh new look by posting anew these commands:
```

df-h
df -i
uname -r
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-
ls -al /vmlinuz*
ls -al /initrd*

```
What do we look like now ?

[INDENT][INDENT]wipe the sweat off ?
[/INDENT][/INDENT]

---

### Post by eightbits2010 on 2015-10-15
I am attempting to upgrade from 14.10 to 15.04, but it doesn't seem to accomplish that i get error messages when going through using the software updater.
Now, I have no idea how to get around this issue(?).

I have attached a screen shot of the message from the updater. I don't remember this happening on older Ubuntu versions. I thought I would have to upgrade to 15.04 , i can't install anything from the software center or at least the ones I tried to install today.

The message is: "Failed to download repository information". so, I have no idea what or why ????

I hope the screen shot is helpful.

---

### Post by Bashing-om on 2015-10-15
eightbits2010; Hello;

14.10 is End_Of_Life and the software repository no longer exists as you once knew it.
You must change your sources to old_releases:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
For the guide.

Any additional problems, please open your own thread on that issue. Your issue is not related to this thread.

[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by aab001 on 2015-10-16
> **Bashing-om said:**
> aab001; Who said it could not happen ? ... Look'n good .

OK, finally .. clean up and make the package manager consistent.
Run this series of commands, carefully copy and paste - one at a time - these 10 commands: 
```

sudo apt-get purge linux-image-2.6.35-28-generic
sudo apt-get purge linux-headers-2.6.35-28-generic
sudo apt-get purge linux-headers-2.6.35-28

sudo apt-get purge linux-image-2.6.38-{8,10,11}-generic
sudo apt-get purge linux-headers-2.6.38-{8,10,11}-generic
sudo apt-get purge linux-headers-2.6.38-{8,10,11}

sudo apt-get purge linux-image-3.0.0-26-generic
sudo apt-get purge linux-headers-3.0.0-26-generic
sudo apt-get purge linux-headers-3.0.0-26

sudo apt-get purge linux-{headers,image}-3.2.0-{32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,67,68,69,70,72,74,75,76,77,79,80,82,83,84.85}-*

```

And now to verify our work .. see if now there is anything I have overlooked or forgot:
Give a fresh new look by posting anew these commands:
```

df-h
df -i
uname -r
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-
ls -al /vmlinuz*
ls -al /initrd*

```
What do we look like now ?
[INDENT][INDENT]wipe the sweat off ?
[/INDENT]
[/INDENT]


Good morning,:confused:

```


aab@aab-Latitude-E6400:~$ 
aab@aab-Latitude-E6400:~$ df -h
Filesystem          Size  Used Avail Use% Mounted on
/dev/sda6            33G   16G   15G  51% /
udev                992M   12K  992M   1% /dev
tmpfs               201M  1.2M  200M   1% /run
none                5.0M     0  5.0M   0% /run/lock
none               1001M  1.4M 1000M   1% /run/shm
/dev/sda7            72G   68G  418M 100% /home
/home/aab/.Private   72G   68G  418M 100% /home/aab
aab@aab-Latitude-E6400:~$ df -i
Filesystem          Inodes  IUsed   IFree IUse% Mounted on
/dev/sda6          2138112 895463 1242649   42% /
udev                213492    543  212949    1% /dev
tmpfs               218513    488  218025    1% /run
none                218513      3  218510    1% /run/lock
none                218513     11  218502    1% /run/shm
/dev/sda7          4784128  44768 4739360    1% /home
/home/aab/.Private 4784128  44768 4739360    1% /home/aab
aab@aab-Latitude-E6400:~$ uname -r
3.2.0-89-generic
aab@aab-Latitude-E6400:~$ ls -al /usr/src/
total 224
drwxrwsr-x 54 root src  12288 Oct 14 23:40 .
drwxr-xr-x 11 root root  4096 Oct 15  2011 ..
drwxr-xr-x  5 root root  4096 Sep 24  2013 bcmwl-6.20.155.1+bdcom
drwxr-xr-x  7 root root  4096 Oct 13  2012 linux-headers-3.2.0-32-generic-pae
drwxr-xr-x  7 root root  4096 Nov 17  2012 linux-headers-3.2.0-33-generic-pae
drwxr-xr-x  7 root root  4096 Dec  1  2012 linux-headers-3.2.0-34-generic-pae
drwxr-xr-x  7 root root  4096 Dec 19  2012 linux-headers-3.2.0-35-generic-pae
drwxr-xr-x  7 root root  4096 Jan 18  2013 linux-headers-3.2.0-36-generic-pae
drwxr-xr-x  7 root root  4096 Feb  1  2013 linux-headers-3.2.0-37-generic-pae
drwxr-xr-x  7 root root  4096 Feb 22  2013 linux-headers-3.2.0-38-generic-pae
drwxr-xr-x  7 root root  4096 Mar 19  2013 linux-headers-3.2.0-39-generic-pae
drwxr-xr-x  7 root root  4096 Apr 15  2013 linux-headers-3.2.0-40-generic-pae
drwxr-xr-x  7 root root  4096 May  2  2013 linux-headers-3.2.0-41-generic-pae
drwxr-xr-x  7 root root  4096 May 17  2013 linux-headers-3.2.0-43-generic-pae
drwxr-xr-x  7 root root  4096 May 24  2013 linux-headers-3.2.0-44-generic-pae
drwxr-xr-x  7 root root  4096 Jun  1  2013 linux-headers-3.2.0-45-generic-pae
drwxr-xr-x  7 root root  4096 Jun 15  2013 linux-headers-3.2.0-48-generic-pae
drwxr-xr-x  7 root root  4096 Jul  6  2013 linux-headers-3.2.0-49-generic-pae
drwxr-xr-x  7 root root  4096 Aug 10  2013 linux-headers-3.2.0-51-generic-pae
drwxr-xr-x  7 root root  4096 Aug 21  2013 linux-headers-3.2.0-52-generic-pae
drwxr-xr-x  7 root root  4096 Sep  8  2013 linux-headers-3.2.0-53-generic-pae
drwxr-xr-x  7 root root  4096 Sep 29  2013 linux-headers-3.2.0-54-generic-pae
drwxr-xr-x  7 root root  4096 Oct 25  2013 linux-headers-3.2.0-55-generic-pae
drwxr-xr-x  7 root root  4096 Nov  8  2013 linux-headers-3.2.0-56-generic-pae
drwxr-xr-x  7 root root  4096 Dec  3  2013 linux-headers-3.2.0-57-generic-pae
drwxr-xr-x  7 root root  4096 Jan  7  2014 linux-headers-3.2.0-58-generic-pae
drwxr-xr-x  7 root root  4096 Feb 20  2014 linux-headers-3.2.0-59-generic-pae
drwxr-xr-x  7 root root  4096 Mar  8  2014 linux-headers-3.2.0-60-generic-pae
drwxr-xr-x  7 root root  4096 May  6  2014 linux-headers-3.2.0-61-generic-pae
drwxr-xr-x  7 root root  4096 May 27  2014 linux-headers-3.2.0-63-generic-pae
drwxr-xr-x  7 root root  4096 Jun  7  2014 linux-headers-3.2.0-64-generic-pae
drwxr-xr-x  7 root root  4096 Aug 13  2014 linux-headers-3.2.0-67-generic-pae
drwxr-xr-x  7 root root  4096 Sep 16  2014 linux-headers-3.2.0-68-generic-pae
drwxr-xr-x  7 root root  4096 Sep 24  2014 linux-headers-3.2.0-69-generic-pae
drwxr-xr-x  7 root root  4096 Oct  9  2014 linux-headers-3.2.0-70-generic-pae
drwxr-xr-x  7 root root  4096 Nov 25  2014 linux-headers-3.2.0-72-generic-pae
drwxr-xr-x  7 root root  4096 Dec 12  2014 linux-headers-3.2.0-74-generic-pae
drwxr-xr-x  7 root root  4096 Jan 13  2015 linux-headers-3.2.0-75-generic-pae
drwxr-xr-x  7 root root  4096 Feb  9  2015 linux-headers-3.2.0-76-generic-pae
drwxr-xr-x  7 root root  4096 Mar 13  2015 linux-headers-3.2.0-77-generic-pae
drwxr-xr-x 24 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86
drwxr-xr-x  7 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86-generic
drwxr-xr-x  7 root root  4096 Jun 22 13:12 linux-headers-3.2.0-86-generic-pae
drwxr-xr-x 24 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88
drwxr-xr-x  7 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88-generic
drwxr-xr-x  7 root root  4096 Jul 29 01:48 linux-headers-3.2.0-88-generic-pae
drwxr-xr-x 24 root root  4096 Aug 23 18:24 linux-headers-3.2.0-89
drwxr-xr-x  7 root root  4096 Aug 23 18:24 linux-headers-3.2.0-89-generic
drwxr-xr-x  7 root root  4096 Oct 14 23:40 linux-headers-3.2.0-89-generic-pae
drwxr-xr-x 24 root root  4096 Oct 14 18:21 linux-headers-3.2.0-91
drwxr-xr-x  7 root root  4096 Oct 14 18:21 linux-headers-3.2.0-91-generic-pae
drwxr-xr-x  3 root root  4096 Feb  3  2014 nvidia-173-173.14.39
drwxr-xr-x  3 root root  4096 Dec 12  2014 nvidia-304-304.125
drwxr-xr-x  3 root root  4096 Dec 12  2014 nvidia-331-331.113
aab@aab-Latitude-E6400:~$ ls -al /lib/modules/
total 44
drwxr-xr-x  9 root root  4096 Oct 14 23:40 .
drwxr-xr-x 27 root root 12288 May 22 21:15 ..
drwxr-xr-x  5 root root  4096 Jun 22 13:12 3.2.0-86-generic
drwxr-xr-x  3 root root  4096 Jun 16 11:31 3.2.0-86-generic-pae
drwxr-xr-x  5 root root  4096 Jul 29 01:51 3.2.0-88-generic
drwxr-xr-x  3 root root  4096 Jul 29 01:52 3.2.0-88-generic-pae
drwxr-xr-x  5 root root  4096 Sep 12 15:01 3.2.0-89-generic
drwxr-xr-x  3 root root  4096 Oct 14 23:42 3.2.0-89-generic-pae
drwxr-xr-x  3 root root  4096 Oct 14 18:23 3.2.0-91-generic-pae
aab@aab-Latitude-E6400:~$ ls -al /boot/
total 77312
drwxr-xr-x  3 root root    20480 Oct 14 18:19 .
drwxr-xr-x 25 root root     4096 Sep 12 15:01 ..
-rw-r--r--  1 root root   801170 Jun 17 23:44 abi-3.2.0-86-generic
-rw-r--r--  1 root root   801170 Jul  6 23:20 abi-3.2.0-88-generic
-rw-r--r--  1 root root   801170 Jul 28 11:49 abi-3.2.0-89-generic
-rw-r--r--  1 root root   147799 Jul  6 23:20 config-3.2.0-88-generic
-rw-r--r--  1 root root   147799 Jul 28 11:49 config-3.2.0-89-generic
drwxr-xr-x  3 root root    12288 Oct 15 19:30 grub
-rw-r--r--  1 root root 19823822 Jun 22 13:13 initrd.img-3.2.0-86-generic
-rw-r--r--  1 root root 19821946 Jul 29 01:50 initrd.img-3.2.0-88-generic
-rw-r--r--  1 root root 19822747 Sep 12 15:02 initrd.img-3.2.0-89-generic
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2263401 Jun 17 23:44 System.map-3.2.0-86-generic
-rw-------  1 root root  2263334 Jul  6 23:20 System.map-3.2.0-88-generic
-rw-------  1 root root  2263334 Jul 28 11:49 System.map-3.2.0-89-generic
-rw-------  1 root root  4889952 Jul  6 23:20 vmlinuz-3.2.0-88-generic
-rw-------  1 root root  4890208 Jul 28 11:49 vmlinuz-3.2.0-89-generic
aab@aab-Latitude-E6400:~$ dpkg -l | grep linux-
ii  linux-firmware                         1.79.18                                    Firmware for Linux kernel drivers
ii  linux-generic                          3.2.0.89.103                               Complete Generic Linux kernel
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
ii  linux-headers-3.2.0-54                 3.2.0-54.82                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic         3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54-generic-pae     3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55                 3.2.0-55.85                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic         3.2.0-55.85                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55-generic-pae     3.2.0-55.85                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-56                 3.2.0-56.86                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-56-generic         3.2.0-56.86                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-56-generic-pae     3.2.0-56.86                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-57                 3.2.0-57.87                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-57-generic         3.2.0-57.87                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-57-generic-pae     3.2.0-57.87                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-58                 3.2.0-58.88                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-58-generic         3.2.0-58.88                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-58-generic-pae     3.2.0-58.88                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-59                 3.2.0-59.90                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-59-generic         3.2.0-59.90                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-59-generic-pae     3.2.0-59.90                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-60                 3.2.0-60.91                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-60-generic         3.2.0-60.91                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-60-generic-pae     3.2.0-60.91                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-61                 3.2.0-61.93                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-61-generic         3.2.0-61.93                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-61-generic-pae     3.2.0-61.93                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-63                 3.2.0-63.95                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-63-generic         3.2.0-63.95                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-63-generic-pae     3.2.0-63.95                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-64                 3.2.0-64.97                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-64-generic         3.2.0-64.97                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-64-generic-pae     3.2.0-64.97                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-67                 3.2.0-67.101                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67-generic         3.2.0-67.101                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-67-generic-pae     3.2.0-67.101                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-68                 3.2.0-68.102                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-68-generic         3.2.0-68.102                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-68-generic-pae     3.2.0-68.102                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-69                 3.2.0-69.103                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-69-generic         3.2.0-69.103                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-69-generic-pae     3.2.0-69.103                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-70                 3.2.0-70.105                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-70-generic         3.2.0-70.105                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-70-generic-pae     3.2.0-70.105                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-72                 3.2.0-72.107                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-72-generic         3.2.0-72.107                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-72-generic-pae     3.2.0-72.107                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-74                 3.2.0-74.109                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-74-generic         3.2.0-74.109                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-74-generic-pae     3.2.0-74.109                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-75                 3.2.0-75.110                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-75-generic         3.2.0-75.110                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-75-generic-pae     3.2.0-75.110                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-76                 3.2.0-76.111                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-76-generic         3.2.0-76.111                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-76-generic-pae     3.2.0-76.111                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-77                 3.2.0-77.114                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-77-generic         3.2.0-77.114                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-77-generic-pae     3.2.0-77.114                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-79                 3.2.0-79.115                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-79-generic         3.2.0-79.115                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-79-generic-pae     3.2.0-79.115                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-80                 3.2.0-80.116                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-80-generic         3.2.0-80.116                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-80-generic-pae     3.2.0-80.116                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-82                 3.2.0-82.119                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-82-generic         3.2.0-82.119                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-82-generic-pae     3.2.0-82.119                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-83                 3.2.0-83.120                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-83-generic         3.2.0-83.120                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-83-generic-pae     3.2.0-83.120                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-84                 3.2.0-84.121                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-84-generic         3.2.0-84.121                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-84-generic-pae     3.2.0-84.121                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-85                 3.2.0-85.122                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-85-generic         3.2.0-85.122                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-85-generic-pae     3.2.0-85.122                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-86                 3.2.0-86.124                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-86-generic         3.2.0-86.124                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-86-generic-pae     3.2.0-86.124                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-88                 3.2.0-88.126                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-88-generic         3.2.0-88.126                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-88-generic-pae     3.2.0-88.126                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-89                 3.2.0-89.127                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-89-generic         3.2.0-89.127                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-89-generic-pae     3.2.0-89.127                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-91                 3.2.0-91.129                               Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-91-generic-pae     3.2.0-91.129                               Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic                  3.2.0.89.103                               Generic Linux kernel headers
ii  linux-headers-generic-pae              3.2.0.89.103                               Generic Linux kernel headers
rc  linux-image-2.6.35-22-generic          2.6.35-22.35                               Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.35-25-generic          2.6.35-25.44                               Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.35-27-generic          2.6.35-27.48                               Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-3.0.0-12-generic           3.0.0-12.20                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-13-generic           3.0.0-13.22                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-14-generic           3.0.0-14.23                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-15-generic           3.0.0-15.26                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-16-generic           3.0.0-16.29                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-17-generic           3.0.0-17.30                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-19-generic           3.0.0-19.33                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-20-generic           3.0.0-20.34                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-21-generic           3.0.0-21.35                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-22-generic           3.0.0-22.36                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-23-generic           3.0.0-23.39                                Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-25-generic           3.0.0-25.41                                Linux kernel image for version 3.0.0 on x86/x86_64
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
ii  linux-image-3.2.0-55-generic           3.2.0-55.85                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-56-generic           3.2.0-56.86                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-57-generic           3.2.0-57.87                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-58-generic           3.2.0-58.88                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-59-generic           3.2.0-59.90                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-60-generic           3.2.0-60.91                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-61-generic           3.2.0-61.93                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-63-generic           3.2.0-63.95                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-64-generic           3.2.0-64.97                                Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-67-generic           3.2.0-67.101                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-68-generic           3.2.0-68.102                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-69-generic           3.2.0-69.103                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-70-generic           3.2.0-70.105                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-72-generic           3.2.0-72.107                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-74-generic           3.2.0-74.109                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-75-generic           3.2.0-75.110                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-76-generic           3.2.0-76.111                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-77-generic           3.2.0-77.114                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-79-generic           3.2.0-79.115                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-80-generic           3.2.0-80.116                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-82-generic           3.2.0-82.119                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-83-generic           3.2.0-83.120                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-84-generic           3.2.0-84.121                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-85-generic           3.2.0-85.122                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-86-generic           3.2.0-86.124                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-88-generic           3.2.0-88.126                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-89-generic           3.2.0-89.127                               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.89.103                               Generic Linux kernel image
ii  linux-libc-dev                         3.2.0-88.126                               Linux Kernel Headers for development
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu1.1                     base package for ALSA and OSS sound systems
ii  syslinux-common                        2:4.05+dfsg-2                              collection of boot loaders (common files)
ii  syslinux-legacy                        2:3.63+dfsg-2ubuntu5                       Bootloader for Linux/i386 using MS-DOS floppies
aab@aab-Latitude-E6400:~$ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 29 Sep 12 15:01 /vmlinuz -> boot/vmlinuz-3.2.0-89-generic
lrwxrwxrwx 1 root root 29 Sep  6 14:32 /vmlinuz.old -> boot/vmlinuz-3.2.0-89-generic
aab@aab-Latitude-E6400:~$ ls -al /initrd*
lrwxrwxrwx 1 root root 33 Sep 12 15:01 /initrd.img -> /boot/initrd.img-3.2.0-89-generic
lrwxrwxrwx 1 root root 33 Sep  6 14:32 /initrd.img.old -> /boot/initrd.img-3.2.0-89-generic
aab@aab-Latitude-E6400:~$ 


```

---

### Post by Bashing-om on 2015-10-16
aab001; Yuk !

I do not have a clue of what is going on !
Nor can I explain why:
> 
drwxr-xr-x  7 root root  4096 Oct 13  2012 linux-headers-3.2.0-32-generic-pae
drwxr-xr-x  7 root root  4096 Nov 17  2012 linux-headers-3.2.0-33-generic-pae
drwxr-xr-x  7 root root  4096 Dec  1  2012 linux-headers-3.2.0-34-generic-pae
drwxr-xr-x  7 root root  4096 Dec 19  2012 linux-headers-3.2.0-35-generic-pae
drwxr-xr-x  7 root root  4096 Jan 18  2013 linux-headers-3.2.0-36-generic-pae
drwxr-xr-x  7 root root  4096 Feb  1  2013 linux-headers-3.2.0-37-generic-pae
drwxr-xr-x  7 root root  4096 Feb 22  2013 linux-headers-3.2.0-38-generic-pae
drwxr-xr-x  7 root root  4096 Mar 19  2013 linux-headers-3.2.0-39-generic-pae
drwxr-xr-x  7 root root  4096 Apr 15  2013 linux-headers-3.2.0-40-generic-pae
drwxr-xr-x  7 root root  4096 May  2  2013 linux-headers-3.2.0-41-generic-pae
drwxr-xr-x  7 root root  4096 May 17  2013 linux-headers-3.2.0-43-generic-pae
drwxr-xr-x  7 root root  4096 May 24  2013 linux-headers-3.2.0-44-generic-pae
drwxr-xr-x  7 root root  4096 Jun  1  2013 linux-headers-3.2.0-45-generic-pae
drwxr-xr-x  7 root root  4096 Jun 15  2013 linux-headers-3.2.0-48-generic-pae
drwxr-xr-x  7 root root  4096 Jul  6  2013 linux-headers-3.2.0-49-generic-pae
drwxr-xr-x  7 root root  4096 Aug 10  2013 linux-headers-3.2.0-51-generic-pae
drwxr-xr-x  7 root root  4096 Aug 21  2013 linux-headers-3.2.0-52-generic-pae
drwxr-xr-x  7 root root  4096 Sep  8  2013 linux-headers-3.2.0-53-generic-pae
drwxr-xr-x  7 root root  4096 Sep 29  2013 linux-headers-3.2.0-54-generic-pae
drwxr-xr-x  7 root root  4096 Oct 25  2013 linux-headers-3.2.0-55-generic-pae
drwxr-xr-x  7 root root  4096 Nov  8  2013 linux-headers-3.2.0-56-generic-pae
drwxr-xr-x  7 root root  4096 Dec  3  2013 linux-headers-3.2.0-57-generic-pae
drwxr-xr-x  7 root root  4096 Jan  7  2014 linux-headers-3.2.0-58-generic-pae
drwxr-xr-x  7 root root  4096 Feb 20  2014 linux-headers-3.2.0-59-generic-pae
drwxr-xr-x  7 root root  4096 Mar  8  2014 linux-headers-3.2.0-60-generic-pae
drwxr-xr-x  7 root root  4096 May  6  2014 linux-headers-3.2.0-61-generic-pae
drwxr-xr-x  7 root root  4096 May 27  2014 linux-headers-3.2.0-63-generic-pae
drwxr-xr-x  7 root root  4096 Jun  7  2014 linux-headers-3.2.0-64-generic-pae
drwxr-xr-x  7 root root  4096 Aug 13  2014 linux-headers-3.2.0-67-generic-pae
drwxr-xr-x  7 root root  4096 Sep 16  2014 linux-headers-3.2.0-68-generic-pae
drwxr-xr-x  7 root root  4096 Sep 24  2014 linux-headers-3.2.0-69-generic-pae
drwxr-xr-x  7 root root  4096 Oct  9  2014 linux-headers-3.2.0-70-generic-pae
drwxr-xr-x  7 root root  4096 Nov 25  2014 linux-headers-3.2.0-72-generic-pae
drwxr-xr-x  7 root root  4096 Dec 12  2014 linux-headers-3.2.0-74-generic-pae
drwxr-xr-x  7 root root  4096 Jan 13  2015 linux-headers-3.2.0-75-generic-pae
drwxr-xr-x  7 root root  4096 Feb  9  2015 linux-headers-3.2.0-76-generic-pae
drwxr-xr-x  7 root root  4096 Mar 13  2015 linux-headers-3.2.0-77-generic-pae

have come back to haunt us. Can you explain ?

In addition these have re-appeared !
> 
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
ii  linux-headers-3.2.0-54                 3.2.0-54.82                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic         3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54-generic-pae     3.2.0-54.82                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55                 3.2.0-55.85                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic         3.2.0-55.85                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55-generic-pae     3.2.0-55.85                                Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii


I guess we once again back up and start all over one more time from scratch, and see if we can complete this.

Moreover, you still or once more - have your /home partition filled to capacity. That too must be addressed. 
> 
/dev/sda7            72G   68G  418M 100% /home
/home/aab/.Private   72G   68G  418M 100% 

Whatever " /home/aab " might be.

[INDENT]5 steps forward and 7 yet back
[INDENT][INDENT][INDENT]will not get the job done
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-11-06
> **Bashing-om said:**
> aab001; Yuk !

I do not have a clue of what is going on !
Nor can I explain why:

have come back to haunt us. Can you explain ?

In addition these have re-appeared !


I guess we once again back up and start all over one more time from scratch, and see if we can complete this.

Moreover, you still or once more - have your /home partition filled to capacity. That too must be addressed. 

Whatever " /home/aab " might be.
[INDENT]5 steps forward and 7 yet back[INDENT][INDENT][INDENT]will not get the job done
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Dear 

I was very busy but fortunately I have solved the problem by :
1- I have emptied the home folder.
2- From the updating screen I have chosen to upgrade to 14.04 LTS.
It took long time to upgrade, but after that every thing works fine. Now, I can update my system. 

Many thanks for your cooperation and patient.

The following is my output
```

aab@aab-Latitude-E6400:~$ df -h
Filesystem          Size  Used Avail Use% Mounted on
/dev/sda6            32G   17G   14G  56% /
none                4.0K     0  4.0K   0% /sys/fs/cgroup
udev                989M   12K  989M   1% /dev
tmpfs               201M  1.9M  199M   1% /run
none                5.0M     0  5.0M   0% /run/lock
none               1003M  244K 1002M   1% /run/shm
none                100M   72K  100M   1% /run/user
/dev/sda7            72G   61G  7.9G  89% /home
/home/aab/.Private   72G   61G  7.9G  89% /home/aab
/dev/mmcblk0p1      7.5G  2.4G  5.1G  33% /media/aab/266E-405B
aab@aab-Latitude-E6400:~$ df -i
Filesystem          Inodes  IUsed   IFree IUse% Mounted on
/dev/sda6          2138112 578699 1559413   28% /
none                220144      2  220142    1% /sys/fs/cgroup
udev                213383    511  212872    1% /dev
tmpfs               220144    566  219578    1% /run
none                220144      4  220140    1% /run/lock
none                220144     11  220133    1% /run/shm
none                220144     33  220111    1% /run/user
/dev/sda7          4784128 150802 4633326    4% /home
/home/aab/.Private 4784128 150802 4633326    4% /home/aab
/dev/mmcblk0p1           0      0       0     - /media/aab/266E-405B
aab@aab-Latitude-E6400:~$ uname -r
3.13.0-66-generic
aab@aab-Latitude-E6400:~$ ls -al /usr/src/
total 44
drwxrwsr-x  9 root src  12288 Nov  5 12:33 .
drwxr-xr-x 11 root root  4096 Oct 15  2011 ..
drwxr-xr-x  5 root root  4096 Oct 21 14:04 bcmwl-6.30.223.248+bdcom
drwxr-xr-x 24 root root  4096 Oct 21 14:14 linux-headers-3.13.0-66
drwxr-xr-x  7 root root  4096 Oct 21 14:14 linux-headers-3.13.0-66-generic
drwxr-xr-x 24 root root  4096 Nov  5 12:33 linux-headers-3.13.0-67
drwxr-xr-x  7 root root  4096 Nov  5 12:33 linux-headers-3.13.0-67-generic
drwxr-xr-x  3 root root  4096 Feb  3  2014 nvidia-173-173.14.39
drwxr-xr-x  3 root root  4096 Oct 21 00:41 nvidia-304-304.128
aab@aab-Latitude-E6400:~$ ls -al /lib/modules/
total 44
drwxr-xr-x  9 root root  4096 Nov  5 12:33 .
drwxr-xr-x 28 root root 12288 Oct 21 15:03 ..
drwxr-xr-x  6 root root  4096 Oct 21 15:02 3.13.0-66-generic
drwxr-xr-x  6 root root  4096 Nov  6 08:48 3.13.0-67-generic
drwxr-xr-x  3 root root  4096 Oct 21 15:09 3.2.0-86-generic-pae
drwxr-xr-x  3 root root  4096 Oct 21 15:10 3.2.0-88-generic-pae
drwxr-xr-x  5 root root  4096 Oct 21 15:10 3.2.0-89-generic
drwxr-xr-x  3 root root  4096 Oct 21 15:10 3.2.0-89-generic-pae
drwxr-xr-x  3 root root  4096 Oct 21 15:10 3.2.0-91-generic-pae
aab@aab-Latitude-E6400:~$ ls -al /boot/
total 99768
drwxr-xr-x  3 root root    20480 Nov  6 08:49 .
drwxr-xr-x 24 root root     4096 Nov  5 12:34 ..
-rw-r--r--  1 root root  1169477 Oct  7 18:21 abi-3.13.0-66-generic
-rw-r--r--  1 root root  1169477 Oct 23 15:47 abi-3.13.0-67-generic
-rw-r--r--  1 root root   801170 Jul 28 11:49 abi-3.2.0-89-generic
-rw-r--r--  1 root root   169833 Oct  7 18:21 config-3.13.0-66-generic
-rw-r--r--  1 root root   169833 Oct 23 15:47 config-3.13.0-67-generic
-rw-r--r--  1 root root   147799 Jul 28 11:49 config-3.2.0-89-generic
drwxr-xr-x  5 root root    12288 Nov  6 08:49 grub
-rw-r--r--  1 root root 26789011 Oct 21 14:58 initrd.img-3.13.0-66-generic
-rw-r--r--  1 root root 26789296 Nov  6 08:49 initrd.img-3.13.0-67-generic
-rw-r--r--  1 root root 20107101 Oct 21 14:34 initrd.img-3.2.0-89-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  2701632 Oct  7 18:21 System.map-3.13.0-66-generic
-rw-------  1 root root  2701612 Oct 23 15:47 System.map-3.13.0-67-generic
-rw-------  1 root root  2263334 Jul 28 11:49 System.map-3.2.0-89-generic
-rw-------  1 root root  5843920 Oct  7 18:21 vmlinuz-3.13.0-66-generic
-rw-------  1 root root  5842704 Oct 23 15:47 vmlinuz-3.13.0-67-generic
-rw-------  1 root root  4890208 Jul 28 11:49 vmlinuz-3.2.0-89-generic
aab@aab-Latitude-E6400:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.16                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                         3.13.0.67.73                                        i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-66                               3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                       3.13.0-66.108                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-67                               3.13.0-67.110                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                       3.13.0-67.110                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.67.73                                        i386         Generic Linux kernel headers
ii  linux-headers-generic-pae                             3.13.0.67.73                                        i386         Transitional package
rc  linux-image-2.6.35-22-generic                         2.6.35-22.35                                        i386         Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.35-25-generic                         2.6.35-25.44                                        i386         Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.35-27-generic                         2.6.35-27.48                                        i386         Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-3.0.0-12-generic                          3.0.0-12.20                                         i386         Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-13-generic                          3.0.0-13.22                                         i386         Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-14-generic                          3.0.0-14.23                                         i386         Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-15-generic                          3.0.0-15.26                                         i386         Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-16-generic                          3.0.0-16.29                                         i386         Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-17-generic                          3.0.0-17.30                                         i386         Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-19-generic                          3.0.0-19.33                                         i386         Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-20-generic                          3.0.0-20.34                                         i386         Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-21-generic                          3.0.0-21.35                                         i386         Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-22-generic                          3.0.0-22.36                                         i386         Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-23-generic                          3.0.0-23.39                                         i386         Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-25-generic                          3.0.0-25.41                                         i386         Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-67-generic                         3.13.0-67.110                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-32-generic                          3.2.0-32.51                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-33-generic                          3.2.0-33.52                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-34-generic                          3.2.0-34.53                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-35-generic                          3.2.0-35.55                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-36-generic                          3.2.0-36.57                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-37-generic                          3.2.0-37.58                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-38-generic                          3.2.0-38.61                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-39-generic                          3.2.0-39.62                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-40-generic                          3.2.0-40.64                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-41-generic                          3.2.0-41.66                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-43-generic                          3.2.0-43.68                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-44-generic                          3.2.0-44.69                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-45-generic                          3.2.0-45.70                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-48-generic                          3.2.0-48.74                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-49-generic                          3.2.0-49.75                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-51-generic                          3.2.0-51.77                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-52-generic                          3.2.0-52.78                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-53-generic                          3.2.0-53.81                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-54-generic                          3.2.0-54.82                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-55-generic                          3.2.0-55.85                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-56-generic                          3.2.0-56.86                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-57-generic                          3.2.0-57.87                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-58-generic                          3.2.0-58.88                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-59-generic                          3.2.0-59.90                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-60-generic                          3.2.0-60.91                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-61-generic                          3.2.0-61.93                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-63-generic                          3.2.0-63.95                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-64-generic                          3.2.0-64.97                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-67-generic                          3.2.0-67.101                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-68-generic                          3.2.0-68.102                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-69-generic                          3.2.0-69.103                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-70-generic                          3.2.0-70.105                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-72-generic                          3.2.0-72.107                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-74-generic                          3.2.0-74.109                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-75-generic                          3.2.0-75.110                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-76-generic                          3.2.0-76.111                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-77-generic                          3.2.0-77.114                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-79-generic                          3.2.0-79.115                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-80-generic                          3.2.0-80.116                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-82-generic                          3.2.0-82.119                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-83-generic                          3.2.0-83.120                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-84-generic                          3.2.0-84.121                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-85-generic                          3.2.0-85.122                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-86-generic                          3.2.0-86.124                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-88-generic                          3.2.0-88.126                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-89-generic                          3.2.0-89.127                                        i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic                   3.13.0-67.110                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                   3.13.0.67.73                                        i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-67.110                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
aab@aab-Latitude-E6400:~$ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 30 Nov  5 12:34 /vmlinuz -> boot/vmlinuz-3.13.0-67-generic
lrwxrwxrwx 1 root root 30 Oct 21 14:44 /vmlinuz.old -> boot/vmlinuz-3.13.0-66-generic
aab@aab-Latitude-E6400:~$ ls -al /initrd*
lrwxrwxrwx 1 root root 33 Nov  5 12:34 /initrd.img -> boot/initrd.img-3.13.0-67-generic
lrwxrwxrwx 1 root root 33 Oct 21 14:44 /initrd.img.old -> boot/initrd.img-3.13.0-66-generic
aab@aab-Latitude-E6400:~$ 



```

---

### Post by Bashing-om on 2015-11-06
aab001; Outstanding ;

I see a bit if cleanup remaining:
do:
```

sudo rm -rf /lib/modules/3.2.0-{86,88,89,91}
sudo apt-get -f install
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Now what results:
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```

[INDENT][INDENT][INDENT]all good 
[/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-11-13
> **Bashing-om said:**
> aab001; Outstanding ;

I see a bit if cleanup remaining:
do:
```

sudo rm -rf /lib/modules/3.2.0-{86,88,89,91}
sudo apt-get -f install
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Now what results:
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```
[INDENT][INDENT][INDENT]all good 
[/INDENT]
[/INDENT]
[/INDENT]


Dear Bashing-om,

this is my output

```

aab@aab-Latitude-E6400:~$ sudo rm -rf /lib/modules/3.2.0-{86,88,89,91}
aab@aab-Latitude-E6400:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  aglfn browser-plugin-vlc chktex clisp dvidvi fonts-cabin fonts-comfortaa
  fonts-font-awesome fonts-freefont-otf fonts-gfs-artemisia
  fonts-gfs-baskerville fonts-gfs-bodoni-classic fonts-gfs-complutum
  fonts-gfs-didot fonts-gfs-didot-classic fonts-gfs-gazis
  fonts-gfs-neohellenic fonts-gfs-olga fonts-gfs-porson fonts-gfs-solomos
  fonts-gfs-theokritos fonts-hosny-amiri fonts-inconsolata fonts-junicode
  fonts-lato fonts-linuxlibertine fonts-lobster fonts-lobstertwo
  fonts-oflb-asana-math fonts-sil-gentium-basic hal-info hyphen-en-us lacheck
  latexdiff lcdf-typetools libffcall1 libfile-which-perl libintl-perl
  libmagick++5 libplot2c2 libppl-c2 libppl7 libpstoedit0c2a libptexenc1
  libquvi-scripts libquvi7 libruby1.9.1 libtext-unidecode-perl
  libtorrent-rasterbar7 libyaml-0-2 linux-headers-3.13.0-66
  linux-headers-3.13.0-66-generic linux-image-3.13.0-66-generic
  linux-image-extra-3.13.0-66-generic pfb2t1c2pfb printer-driver-hpijs ps2eps
  pstoedit ruby ruby1.9.1 swath texinfo ttf-adf-accanthis ttf-adf-gillius
  unity-2d-shell xindy xindy-rules
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
aab@aab-Latitude-E6400:~$ dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
(Reading database ... 312597 files and directories currently installed.)
Removing asymptote (2.15-2build2) ...
Purging configuration files for asymptote (2.15-2build2) ...
Removing freeglut3:i386 (2.8.1-1) ...
Purging configuration files for freeglut3:i386 (2.8.1-1) ...
Removing texmaker (4.1-1) ...
Purging configuration files for texmaker (4.1-1) ...
Processing triggers for menu (2.1.46ubuntu1) ...
aab@aab-Latitude-E6400:~$ sudo apt update
Ign cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release i386 (20150218.1) trusty InRelease
Ign cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release i386 (20150218.1) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release i386 (20150218.1) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release i386 (20150218.1) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release i386 (20150218.1) trusty/restricted Translation-en
Ign http://archive.canonical.com trusty InRelease                              
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://gb.archive.ubuntu.com trusty InRelease                              
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://gb.archive.ubuntu.com trusty-updates InRelease                      
Hit http://archive.canonical.com trusty Release                                
Hit http://gb.archive.ubuntu.com trusty Release.gpg                            
Hit http://ppa.launchpad.net trusty/main Translation-en               
Hit http://gb.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://gb.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://gb.archive.ubuntu.com trusty-updates/universe Sources               
Ign http://archive.canonical.com trusty/partner Translation-en                 
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://security.ubuntu.com trusty-security InRelease           
Hit http://gb.archive.ubuntu.com trusty-updates/main i386 Packages  
Hit http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com trusty-updates/main Translation-en 
Hit http://security.ubuntu.com trusty-security/main Sources         
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com trusty Release                     
Hit http://gb.archive.ubuntu.com trusty/main Sources                 
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://gb.archive.ubuntu.com trusty/restricted Sources          
Hit http://security.ubuntu.com trusty-security/universe Sources     
Hit http://gb.archive.ubuntu.com trusty/universe Sources            
Hit http://gb.archive.ubuntu.com trusty/multiverse Sources                
Hit http://gb.archive.ubuntu.com trusty/main i386 Packages                
Hit http://gb.archive.ubuntu.com trusty/restricted i386 Packages          
Hit http://gb.archive.ubuntu.com trusty/universe i386 Packages            
Hit http://security.ubuntu.com trusty-security/multiverse Sources         
Hit http://gb.archive.ubuntu.com trusty/multiverse i386 Packages          
Hit http://gb.archive.ubuntu.com trusty/main Translation-en
Hit http://security.ubuntu.com trusty-security/main i386 Packages         
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en        
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en         
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en 
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Ign http://gb.archive.ubuntu.com trusty/main Translation-en_US    
Ign http://gb.archive.ubuntu.com trusty/multiverse Translation-en_US
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://gb.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://gb.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done               
aab@aab-Latitude-E6400:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  aglfn browser-plugin-vlc chktex clisp dvidvi fonts-cabin fonts-comfortaa
  fonts-font-awesome fonts-freefont-otf fonts-gfs-artemisia
  fonts-gfs-baskerville fonts-gfs-bodoni-classic fonts-gfs-complutum
  fonts-gfs-didot fonts-gfs-didot-classic fonts-gfs-gazis
  fonts-gfs-neohellenic fonts-gfs-olga fonts-gfs-porson fonts-gfs-solomos
  fonts-gfs-theokritos fonts-hosny-amiri fonts-inconsolata fonts-junicode
  fonts-lato fonts-linuxlibertine fonts-lobster fonts-lobstertwo
  fonts-oflb-asana-math fonts-sil-gentium-basic hal-info hyphen-en-us lacheck
  latexdiff lcdf-typetools libffcall1 libfile-which-perl libintl-perl
  libmagick++5 libplot2c2 libppl-c2 libppl7 libpstoedit0c2a libptexenc1
  libquvi-scripts libquvi7 libruby1.9.1 libtext-unidecode-perl
  libtorrent-rasterbar7 libyaml-0-2 linux-headers-3.13.0-66
  linux-headers-3.13.0-66-generic linux-image-3.13.0-66-generic
  linux-image-extra-3.13.0-66-generic pfb2t1c2pfb printer-driver-hpijs ps2eps
  pstoedit ruby ruby1.9.1 swath texinfo ttf-adf-accanthis ttf-adf-gillius
  unity-2d-shell xindy xindy-rules
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  nvidia-173
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
aab@aab-Latitude-E6400:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  aglfn browser-plugin-vlc chktex clisp dvidvi fonts-cabin fonts-comfortaa
  fonts-font-awesome fonts-freefont-otf fonts-gfs-artemisia
  fonts-gfs-baskerville fonts-gfs-bodoni-classic fonts-gfs-complutum
  fonts-gfs-didot fonts-gfs-didot-classic fonts-gfs-gazis
  fonts-gfs-neohellenic fonts-gfs-olga fonts-gfs-porson fonts-gfs-solomos
  fonts-gfs-theokritos fonts-hosny-amiri fonts-inconsolata fonts-junicode
  fonts-lato fonts-linuxlibertine fonts-lobster fonts-lobstertwo
  fonts-oflb-asana-math fonts-sil-gentium-basic hal-info hyphen-en-us lacheck
  latexdiff lcdf-typetools libffcall1 libfile-which-perl libintl-perl
  libmagick++5 libplot2c2 libppl-c2 libppl7 libpstoedit0c2a libptexenc1
  libquvi-scripts libquvi7 libruby1.9.1 libtext-unidecode-perl
  libtorrent-rasterbar7 libyaml-0-2 linux-headers-3.13.0-66
  linux-headers-3.13.0-66-generic linux-image-3.13.0-66-generic
  linux-image-extra-3.13.0-66-generic pfb2t1c2pfb printer-driver-hpijs ps2eps
  pstoedit ruby ruby1.9.1 swath texinfo ttf-adf-accanthis ttf-adf-gillius
  unity-2d-shell xindy xindy-rules
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  nvidia-173
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
aab@aab-Latitude-E6400:~$ 



```

---

### Post by Bashing-om on 2015-11-13
aab001; Hey !

I am so confused - getting diverted from the end goals here - ...
Now we have:
> 
Ign cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release i386 (20150218.1) trusty InRelease

0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

The following packages have been kept back:
  nvidia-173


1) uncheck the check box for the CDrom in Software center . You should have no need to access old files .
2) We return to this after item 3 is addressed .

3) why is such an old driver even on the system ? I do not recall messing about with this driver .
show us what is now installed for drivers:
```

dpkg -l | grep nvidia

```

[INDENT][INDENT]what ever it takes
[INDENT][INDENT][INDENT]to clean up a system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aab001 on 2015-11-23
> **Bashing-om said:**
> aab001; Hey !

I am so confused - getting diverted from the end goals here - ...
Now we have:


1) uncheck the check box for the CDrom in Software center . You should have no need to access old files .
2) We return to this after item 3 is addressed .

3) why is such an old driver even on the system ? I do not recall messing about with this driver .
show us what is now installed for drivers:
```

dpkg -l | grep nvidia

```
[INDENT][INDENT]what ever it takes[INDENT][INDENT][INDENT]to clean up a system
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hi Bashing-om,

Please have a look to my output.

Thank you

```

aab@aab-Latitude-E6400:~$ dpkg -l | grep nvidia
ii  nvidia-173                                            173.14.39-0ubuntu0.0.1                              i386         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-304                                            304.131-0ubuntu0.14.04.1                            i386         NVIDIA legacy binary driver - version 304.131
ii  nvidia-304-dev                                        304.131-0ubuntu0.14.04.1                            i386         NVIDIA binary Xorg driver development files
ii  nvidia-common                                         1:0.2.91.11                                         i386         transitional package for ubuntu-drivers-common
ii  nvidia-current                                        304.131-0ubuntu0.14.04.1                            i386         Transitional package for nvidia-current
ii  nvidia-current-dev                                    304.131-0ubuntu0.14.04.1                            i386         Transitional package for nvidia-current-dev
ii  nvidia-opencl-icd-304                                 304.131-0ubuntu0.14.04.1                            i386         NVIDIA OpenCL ICD
ii  nvidia-settings                                       331.20-0ubuntu8                                     i386         Tool for configuring the NVIDIA graphics driver
aab@aab-Latitude-E6400:~$ 



```

---

### Post by Bashing-om on 2015-11-23
aab001; Yuk ...

This :
> 
ii  nvidia-173                                            173.14.39-0ubuntu0.0.1                              i386         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-304                                            304.131-0ubuntu0.14.04.1                            i386 <snip>

Shows a driver conflict. One must purge an old driver prior to installing another.
( that 1st column 'ii' where it is Installed as desired and installed in actuality )

[INDENT][INDENT]keep it clean
[/INDENT][/INDENT]

---

