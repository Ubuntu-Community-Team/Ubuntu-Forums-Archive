---
title: "Unable to install packages - Ubuntu 14.04.1 server"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by robert-mengert on 2014-12-30
Hello everyone.  I have two nested OpenStack hypervisors running 14.04.1 server which are unable to install/upgrade packages.  Whenever any modification of packages is attempted, error messages regarding kernel 3.13.0-43-generic are received:

Hypervisor one
```
[root@compute]# apt-get install wamerican
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-43-generic
The following NEW packages will be installed:
  wamerican
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/269 kB of archives.
After this operation, 151 MB disk space will be freed.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 100716 files and directories currently installed.)
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
dpkg-statoverride: error: an override for '/boot/vmlinuz-3.13.0-43-generic' already exists; aborting
run-parts: /etc/kernel/postinst.d/statoverride exited with return code 2
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Hypervisor two:
```
[root@compute2]# apt-get install wamerican
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  python-psutil
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  wamerican
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 269 kB of archives.
After this operation, 1,014 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main wamerican all 7.1-1 [269 kB]
Fetched 269 kB in 0s (532 kB/s)
Preconfiguring packages ...
Selecting previously unselected package wamerican.
(Reading database ... 104400 files and directories currently installed.)
Preparing to unpack .../wamerican_7.1-1_all.deb ...
Unpacking wamerican (7.1-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
dpkg-statoverride: error: an override for '/boot/vmlinuz-3.13.0-43-generic' already exists; aborting
run-parts: /etc/kernel/postinst.d/statoverride exited with return code 2
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.43.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up wamerican (7.1-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                               Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Seems to be some sort of dependency issue, not sure how to resolve it.  I found [this thread]("https://bugs.launchpad.net/openstack-manuals/+bug/1343738") but the fix in it didn't work.  Any help is much appreciated.

---

### Post by TheFu on 2014-12-30
Actually it is likely that too many kernels on in the /boot partition - which is too small for people who don't clean up old kernels.
This has been a chronic issue with Ubuntu since 11.xx sometime.
[http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt)

So - boot off an old kernel (hopefully that will work) and check the storage for /boot - is it full?

---

### Post by robert-mengert on 2014-12-30
Thanks for the quick response.  I saw that was an issue for some folks but I don't think that's the case here.  There is ample disk space in /boot on both VMs.

Hypervisor one
```
[root@compute]# df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        57G  3.5G   51G   7% /
```

Hypervisor two
```
[root@compute2]# df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        57G  2.5G   52G   5% /
```


I also have three other VMs which were upgraded to the new kernel version without issue, two of which actually have significantly less disk space.

---

### Post by TheFu on 2014-12-30
You are probably correct that it isn't the out-of-storage issue. Still, check the inodes - **df -i**.

Have you run **aptitude update** recently?
Aptitude is like apt-get, just a little smarter.

---

### Post by robert-mengert on 2014-12-30
Confirmed space isnt an issue for either host:

```
[root@compute]# df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/vda1      3801088 114543 3686545    4% /
none            256219     11  256208    1% /sys/fs/cgroup
udev            253506    455  253051    1% /dev
tmpfs           256219    391  255828    1% /run
none            256219      3  256216    1% /run/lock
none            256219      1  256218    1% /run/shm
none            256219      3  256216    1% /run/user

[root@compute2]# df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/vda1      3801088 118814 3682274    4% /
none            256216     11  256205    1% /sys/fs/cgroup
udev            253504    454  253050    1% /dev
tmpfs           256216    377  255839    1% /run
none            256216      3  256213    1% /run/lock
none            256216      1  256215    1% /run/shm
none            256216      3  256213    1% /run/user
```


After running 'aptitude update' on both, still see the same errors when trying to install a new package.

Oddly enough, one of the machines claims it's running the new kernel even though it doesn't appear to have been properly installed:

Hypervisor one
```
[root@compute]# apt-get install wamerican
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-43-generic
The following NEW packages will be installed:
  wamerican
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/269 kB of archives.
After this operation, 151 MB disk space will be freed.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 100716 files and directories currently installed.)
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
dpkg-statoverride: error: an override for '/boot/vmlinuz-3.13.0-43-generic' already exists; aborting
run-parts: /etc/kernel/postinst.d/statoverride exited with return code 2
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

[root@compute]# uname -a
Linux compute 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```


Hypervisor two (apparently running the half installed kernel)
```
[root@compute2]# apt-get install wamerican
Reading package lists... Done
Building dependency tree
Reading state information... Done
wamerican is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
dpkg-statoverride: error: an override for '/boot/vmlinuz-3.13.0-43-generic' already exists; aborting
run-parts: /etc/kernel/postinst.d/statoverride exited with return code 2
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.43.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                               Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

[root@compute2]# uname -a
Linux compute2 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Bashing-om on 2014-12-30
robert-mengert; Hi ;

Server 1:
As there is this advisory:
> 
run-parts: /etc/kernel/postinst.d/statoverride exited with return code 2


Maybe that kernel is marked for hold ?
What returns:
```

apt-mark showauto | grep linux-image
apt-mark showmanual | grep linux-image

```

Server 2:
This advisory:
> 
Package linux-image-extra-3.13.0-43-generic is not configured yet.

What happens or what other hints do we get:
```

sudo apt-get install --reinstall linux-image-3.13.0-43-generic-extra

```

[INDENT]look'n for that cause and effect -> to affect a fix
[/INDENT]

---

### Post by robert-mengert on 2014-12-30
Bashing, thanks for the reply.

It the 'extra' package was somehow manually marked on the first host.  I could have sworn these packages were (attempted to be...) installed via apt-get dist-upgrade, is this the expected marking from that action?
```
[root@compute]# apt-mark showauto | grep linux-image
linux-image-3.13.0-32-generic
linux-image-3.13.0-43-generic
linux-image-extra-3.13.0-32-generic
[root@compute]# apt-mark showmanual | grep linux-image
linux-image-extra-3.13.0-43-generic
```

On the second host,  attempting a reinstall throws an error that there is no linux-image-extra-3.13.0-43-generic package despite apt referencing this exact name.  Should I just attempt to install this package without --reinstall?

```
[root@compute2]# apt-get install wamerican
Reading package lists... Done
Building dependency tree
Reading state information... Done
wamerican is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
dpkg-statoverride: error: an override for '/boot/vmlinuz-3.13.0-43-generic' already exists; aborting
run-parts: /etc/kernel/postinst.d/statoverride exited with return code 2
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.43.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                               Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

[root@compute2]# apt-get install --reinstall linux-image-extra-3.13.0-43-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for linux-image-extra-3.13.0-43-generic:amd64

```

---

### Post by Bashing-om on 2014-12-30
robert-mengert; Hey ;


Making progress.
server 1:
```

sudo apt-mark markauto linux-image.*
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

server2:
Sure, can not hurt a thing to 'install' see what happens or get us some additional hints.
We poke at it 'til something gives.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by TheFu on 2014-12-30
Do you have any idea what may be holding a specific kernel?  It is almost always best to install meta-packages, not specific packages.
My openstack-fu is weak, so I don't know the repercussions.  What do you mean by "nested"?

---

### Post by MAFoElffen on 2014-12-30
Sideline note to [SIZE=3][COLOR=#ff0000]Bashing-om[/COLOR][/SIZE] -- This OP is not alone. Helping another user on same issue. Same kernel, but other User is Desktop Edition.
RE: [http://ubuntuforums.org/showthread.php?t=2258500](http://ubuntuforums.org/showthread.php?t=2258500) (go to post number 19)

Others had him looking at Grub, but I ID'ed that was a goose chase. Grub is failing because in his update that same kernel has all 4 packages broken. (Post #19). He was too busy trying to do what others had asked of him... to follow up on what I had suggested... To correct the kernel install, so that update grub can work on a completely install kernel instead of a broken one... (where they were focusing on, but it is broke before that, so that is just a symptom of the real problem- the broken kernel update)

This is too similar to that one. What is wrong on that one is that kernel has 3 depends (Look at post #19, that thread). On those 3 depends, there is no note of the 3rd depend getting dl'ed (linux-firmware). Kernels also usually come with a linux-header-xxxx file as a mate to the kernel file (At least in the past)... I don't see that in the depends list for that kernel at Launchpad, so I don't know what to think of that for now, yet.

As for as I know, That OP nor this OP had tried to correct the broken packages, via:
```

sudo apt-get install -f

```
...which would ask apt-get to try to fix and supply depends to fix the broken packages. I also had some other suggestions for diagnostics and resolution... If this OP could test those on his, maybe we could work together to find them both some relief. (The other OP has taken a break from it and will return later...)

Whether we get them going or not, We need to get the users to report it to Launchpad as a kernel package bug. Besides it not updating, on now more than one user for the same issue... on both, the update process should have caught the Error 2 on the update failure, but is ignoring it and going onward. (Therefore causing further problems with that.) If no-one is willing, when we get these 2 going, I'll file the bug report myself, If I have to... But better if the 2 users can report it so apport can catch the hardware reports.

Wait one and I'll check at Launchpad to see if anyhting on that has changed since last night...

---

### Post by Bashing-om on 2014-12-30
@MAFoElffen; as always a pleasure to see you.


I am indeed following that other thread, am very interested as to when that OP will take up your advise and follow through.

That same is in my mind here .
And yes I also am of that mind to work toward (RE-)installing the kernel package; but we want to know the why..
so: robert-mengert -> let's progress on with the advise given and do:
```

sudo apt-get install -f

```
isolate the cause, and if deemed appropriate , file that needed bug report .

[INDENT][INDENT]we are all in this together 
[/INDENT][/INDENT]

---

### Post by MAFoElffen on 2014-12-30
linux-headers-3.13.0-43-generic shows in one place as suggested, another as a depends

This is one of the other's broken packages with that same issue for the other OP--
linux-image-generic: depends are [COLOR=#ff0000]linux-firmware[/COLOR], linux-image-3.13.0-43-generic, linux-image-extra-3.13.0-43-generic

Note the file in red is not being downloaded by them, but I see it in my updates... 

This is one of this OP's error's:
> 
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on [COLOR=#ff0000]linux-image-generic[/COLOR] (= 3.13.0.43.50); however:
  Package linux-image-generic is not configured yet.



And no mention of it's dependent file, linux-firmware, being downloaded or used (if was already there)... It should be v 1.121.10

---

### Post by Jacob_Goff on 2014-12-30
If worse come to worse with the kernels, just go into your computer and hit the system recovery button.

---

### Post by Bashing-om on 2014-12-30
Noted.
The good thing here is that it is readily (likely) fixable > To really know the why of the situation may well be beyond my present skill level.
The reason I do this - I might learn the why .

in that process of learning

---

### Post by MAFoElffen on 2014-12-30
On the why and on diagnostics... if the Op does:
```

sudo apt-get install -s >> ~/test01.txt

```
That would do a dry-run simulation without changing anything... When it does a simulation/test, apt goes into a verbose mode, and will print out all the broken packages and depends. That may be better for diagnostics of this.

---

### Post by robert-mengert on 2014-12-31
Thanks MAFoElffen for jumping in as well.

Unfortunately, updating the marking and attempting an upgrade on the first host didn't resolve the issue and similar errors were thrown:

```
[root@compute]# apt-mark markauto linux-image.*
[root@compute]# apt-get update ; apt-get upgrade
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Hit http://security.ubuntu.com trusty-security Release.gpg
Ign http://us.archive.ubuntu.com trusty-backports InRelease
Hit http://security.ubuntu.com trusty-security Release
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://security.ubuntu.com trusty-security/main Sources
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://us.archive.ubuntu.com trusty Release
Hit http://security.ubuntu.com trusty-security/multiverse Sources
Get:2 http://us.archive.ubuntu.com trusty-updates Release [62.0 kB]
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports Release
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Get:3 http://us.archive.ubuntu.com trusty-updates/main Sources [149 kB]
Get:4 http://us.archive.ubuntu.com trusty-updates/restricted Sources [2,057 B]
Get:5 http://us.archive.ubuntu.com trusty-updates/universe Sources [95.6 kB]
Get:6 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [3,539 B]
Get:7 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [387 kB]
Get:8 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [8,861 B]
Get:9 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [229 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [9,356 B]
Get:11 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [379 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [8,832 B]
Get:13 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [230 kB]
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [9,539 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 1,576 kB in 5s (286 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-43-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 152 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 100716 files and directories currently installed.)
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
dpkg-statoverride: error: an override for '/boot/vmlinuz-3.13.0-43-generic' already exists; aborting
run-parts: /etc/kernel/postinst.d/statoverride exited with return code 2
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

On the second host, trying to do a straight install of the linux-image-extra-3.13.0-43-generic package throws an error that it's not configured:

```
[root@compute2]# apt-get install linux-image-extra-3.13.0-43-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-image-extra-3.13.0-43-generic is already the newest version.
linux-image-extra-3.13.0-43-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
dpkg-statoverride: error: an override for '/boot/vmlinuz-3.13.0-43-generic' already exists; aborting
run-parts: /etc/kernel/postinst.d/statoverride exited with return code 2
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-43-generic; however:
  Package linux-image-extra-3.13.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.43.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                              Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by MAFoElffen on 2014-12-31
It is apparent on both that is wants to remove linux-image-extra-3.13.0-43-generic... and it stuck in the process because it is not configured and a broken /boot/vmlinuz-3.13.0-43-generic exits.


So we first want to try to get rid of those:
```

sudo apt-get remove --purge linux-image-3.13.0-43-generic linux-image-extra-3.13.0-43-generic

```
Then we want to get the other two to reinstall with that kernel:
```

sudo apt-get install --reinstall linux-image-generic linux-generic

```
Then we want to give try to get to simulate installing that kernel without actually installing it, to see what would happen:
```

sudo apt-get build-dep --simulate --install-recommends linux-image-3.13.0-43-generic
sudo apt-get install --simulate --install-recommends linux-image-3.13.0-43-generic

```
These two commands should test those without making changes. Please post the output from those.

---

### Post by robert-mengert on 2014-12-31
Unfortunately, even trying to remove the packages is resulting in errors being throw:

```
[root@compute]# apt-get remove --purge linux-image-3.13.0-43-generic linux-image-extra-3.13.0-43-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.13.0-43-generic* linux-image-extra-3.13.0-43-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 194 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 100716 files and directories currently installed.)
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
dpkg-statoverride: error: an override for '/boot/vmlinuz-3.13.0-43-generic' already exists; aborting
run-parts: /etc/kernel/postinst.d/statoverride exited with return code 2
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Got some interesting errors on the second host regarding damaged links:
```
[root@compute2]# apt-get remove --purge linux-image-3.13.0-43-generic linux-image-extra-3.13.0-43-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-generic* linux-image-3.13.0-43-generic*
  linux-image-extra-3.13.0-43-generic* linux-image-generic*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 194 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 104411 files and directories currently installed.)
Removing linux-generic (3.13.0.43.50) ...
Removing linux-image-generic (3.13.0.43.50) ...
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
dpkg-statoverride: error: an override for '/boot/vmlinuz-3.13.0-43-generic' already exists; aborting
run-parts: /etc/kernel/postinst.d/statoverride exited with return code 2
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-43-generic (3.13.0-43.72) ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


The second host is the host that claims it's running the partially installed kernel.  Should I boot off of another kernel and retry the removal of 3.13.0-43?

---

### Post by Bashing-om on 2014-12-31
robert-mengert; MAFoElffen ; Hummm ...

Got me now scratching my head,

Server 1:
We did rest the 'apt-mark' . Has something reset it back to 'manual' ??
```

apt-mark showmanual | grep linux-image

```

On server 2 ...
MAFoElffen; is it time to delve deep into how the server is booting ?

Maybe time now to see what the status file(s) relate ?

Since the invocation of " linux-image-extra " I have had no occasion to investigate:
> 
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.


Is this what we have going on here ?


Maybe boot with an older kernel and try again to "purge" -> linux-image-extra-3.13.0-43-generic ?

And yes, more than happy to take a back seat here and see where MAFoElffen leads us .

There is no substitute for experience

---

### Post by schragge on 2014-12-31
Hi, and Happy New Year to you all!
@**MAFoElffen**: Sorry, but this has nothing to do with [thread=2258500]the other thread[/thread] save for the same kernel. There the installation process got stuck at update-grub, here it's dpkg-override that complains. The linux-firmware package doesn't show up in the dpkg messages most probably because it's already successfully installed so there's nothing to complain about. Other packages that depend on particular kernel like linux-generic, linux-image-generic, linux-image-extra-3.13.0-43-generic etc. cannot  be configured until the issue with linux-image-3.13.0-43-generic is resolved.

@OP: Please have a look at LP #[lpbug]1275080[/lpbug] and LP #[lpbug]1343738[/lpbug]. Both bug reports also contain workarounds.

---

### Post by MAFoElffen on 2014-12-31
Yes, it probably does not have to do with linux-firmware. No, it is the same problem as the other User and both are hanging on the boot image build, when it is build on a broken system. 

It looks like it fails when it hits this part:
```

Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic [COLOR=#ff0000]/boot/vmlinuz-3.13.0-43-generic[/COLOR]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic [COLOR=#ff0000]/boot/vmlinuz-3.13.0-43-generic[/COLOR]
update-initramfs: Generating [COLOR=#ff0000]/boot/initrd.img-3.13.0-43-generic[/COLOR]
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic [COLOR=#ff0000]/boot/vmlinuz-3.13.0-43-generic[/COLOR]
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic [COLOR=#ff0000]/boot/vmlinuz-3.13.0-43-generic[/COLOR]
dpkg-statoverride: [COLOR=#ff8c00]error[/COLOR]: an override for '[COLOR=#ff0000]/boot/vmlinuz-3.13.0-43-generic[/COLOR]' [COLOR=#ff8c00]already exists; aborting[/COLOR]
run-parts: /etc/kernel/postinst.d/statoverride exited with return code 2

```
where /boot/vmlinuz-3.13.0-43-generic exists still.

I'm thinking if you ensure that you are booted from 3.13.34 (previous kernel), then manual delete the boot image, then try to remove the kernel package, then it might get past that.
That would be:
```

sudo mv /boot/vmlinuz-3.13.0-43-generic ~/vmlinuz-3.13.0-43-generic   # to move it out of that directory, but keep it, for the just in cases...
sudo apt-get remove --purge linux-image-3.13.0-43-generic linux-image-extra-3.13.0-43-generic

```
*** I think the only reason more users are getting this error at this moment, is that "this" kernel update is not released for all yet (only released to a test slice of users so far). None of my own machines have hit this kernel update yet.

What was susgeested on one of those two bugs was not confirmed as a solution, but a statement on what might be part of the problem.  

What was a solution for earlier Launchpad bugs with the same error message as that (on a failed kernel update)  when that happened for earlier kernel versions-- The problem back then was that the process was trying to create a file with the same filename... So they used the apt-get "--force" option to push it through...

---

### Post by schragge on 2014-12-31
> **MAFoElffen said:**
> *** I think the only reason more users are getting this error at this moment, is that "this" kernel update is not released for all yet (only released to a test slice of users so far). None of my own machines have hit this kernel update yet.What Ubuntu release are your machines running on? Your profile says *Ubuntu Development Release*, [this kernel]("http://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=linux-image-3.13.0-43&searchon=names") is a security update for trusty and also available for precise as a backport.

> No, it is the same problem as the other User
Well, to begin with the issue in question cannot occur on a normal Ubuntu install simply because the post-installation script */etc/kernel/postinst.d/statoverride* doesn't exist there -- it's OpenStack's peculiarity. Moreover, the suggestion to put this script in there [was recently removed]("https://git.openstack.org/cgit/openstack/openstack-manuals/commit/?id=945c99dce992f136e69074bac5a934f1523a2132") from OpenStack Install Guide, too.

---

### Post by MAFoElffen on 2014-12-31
Directed to me?

At home I have 25 hard machines. I'm on the Ubuntu Server Team and do U+1 testing, so I have a test suite of hard machines to test desktop and server editions on hardware and in various virtual suites. But some of those are my infrasture, so I have those on LTS versions. My main infrastructure is on 4 Enterprise class hardware server equipment and 4 desktops. The rest is flexible, dedicated  to my test suite and to development.

But a portion of those are to test upstream issues (GNU, Linux Kernel and Xorg)... The intranet here is upt and multi-mode fiber. I can recreate a lot of various complex test scenarios here at home.

---

### Post by Bashing-om on 2014-12-31
Guys, I have :
> 
sysop@1404mini:~$ ls -al etc/kernel/postinst.d/statoverride
ls: cannot access etc/kernel/postinst.d/statoverride: No such file or directory

sysop@1404mini:~$ uname -a
Linux 1404mini 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
sysop@1404mini:~$ 

On a minimal install that I updated to the -43 kernel a few days past, with no problem encountered.

Hope this helps -> points to a direction and gets us
[INDENT][INDENT][INDENT]on track
[/INDENT][/INDENT][/INDENT]

---

### Post by robert-mengert on 2014-12-31
@Bashing, yes the markings seem to have fallen back to manual despite being changed (see post 16)

```
[root@compute]# apt-mark showmanual | grep linux-image
linux-image-3.13.0-43-generic
linux-image-extra-3.13.0-43-generic
```

@MAFoElffen

The first hypervisor it seems will only boot the earlier kernel (3.13.0-32) but still throws an error when attempting to remove the problematic one:

```
[root@compute]# mv /boot/vmlinuz-3.13.0-43-generic ~/vmlinuz-3.13.0-43-generic

[root@compute]# uname -a
Linux compute 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

[root@compute]# apt-get remove --purge linux-image-3.13.0-43-generic linux-image-extra-3.13.0-43-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.13.0-43-generic* linux-image-extra-3.13.0-43-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 194 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 100716 files and directories currently installed.)
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
dpkg-statoverride: error: an override for '/boot/vmlinuz-3.13.0-43-generic' already exists; aborting
run-parts: /etc/kernel/postinst.d/statoverride exited with return code 2
dpkg: error processing package linux-image-extra-3.13.0-43-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-43-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Having trouble getting on the console of the second host, will try the same process on that host when I'm able and post it here.

---

### Post by schragge on 2014-12-31
The problem is the script */etc/kernel/postinst.d/statoverride* tries to add a stat override for file */boot/vmlinuz-3.13.0-43-generic* which already was overridden previously. If you run
```
dpkg-statoverride --list /boot/vmlinuz-\*
```
it will be shown in the output.

The simplest workaround to try is
```

sudo sed -i '/dpkg-statoverride/s/$/||:/' /etc/kernel/postinst.d/statoverride

```

After that, both installing and removing the kernel should work.

---

### Post by Bashing-om on 2014-12-31
robert-mengert; schragge

Need to move the kernel back into place, first, yes ?
> 
mv /boot/vmlinuz-3.13.0-43-generic ~/vmlinuz-3.13.0-43-generic


I also ran across this  IRT what 'statoverride' is:
```

dpkg-statoverride --remove /boot/vmlinuz-3.13.0-43-generic

```
Maybe same same for " linux-image-extra-3.13.0-43-generic" .

Then to make the package manager happy:
```

sudo apt-get upgrade -f

```
//
Either way - I do not really like 'removing' - changing the status I bet is the better way to go.
However the override was set, now let's see what results with update/upgrade is conducted.

[INDENT][INDENT][INDENT]progress,
[INDENT][INDENT][INDENT]one step at a time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by robert-mengert on 2014-12-31
@Schrage, thanks that did the trick on both:

```
[root@compute]# cp /etc/kernel/postinst.d/statoverride ~/
[root@compute]# sed -i '/dpkg-statoverride/s/$/||:/' /etc/kernel/postinst.d/statoverride
[root@compute]# apt-get install wamerican
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-43-generic
The following NEW packages will be installed:
  wamerican
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/269 kB of archives.
After this operation, 151 MB disk space will be freed.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 100716 files and directories currently installed.)
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
dpkg-statoverride: error: an override for '/boot/vmlinuz-3.13.0-43-generic' already exists; aborting
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Selecting previously unselected package wamerican.
(Reading database ... 100716 files and directories currently installed.)
Preparing to unpack .../wamerican_7.1-1_all.deb ...
Unpacking wamerican (7.1-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up wamerican (7.1-1) ...
```

```
[root@compute2]# apt-get install wamerican
Reading package lists... Done
Building dependency tree
Reading state information... Done
wamerican is already the newest version.
The following packages will be REMOVED:
  linux-image-extra-3.13.0-43-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 152 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 99587 files and directories currently installed.)
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-43-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
grep: /boot/config-3.13.0-43-generic: No such file or directory
depmod: WARNING: could not open /lib/modules/3.13.0-43-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/3.13.0-43-generic/modules.builtin: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_g3H4xQ/lib/modules/3.13.0-43-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_g3H4xQ/lib/modules/3.13.0-43-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/statoverride 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
dpkg-statoverride: error: an override for '/boot/vmlinuz-3.13.0-43-generic' already exists; aborting
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
[root@compute2]# uname -a
Linux compute2 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

The second box appears to have rewritten it's grub config file to boot off of the previous kernel.  Confirmed after a reboot that 3.13.0-32 is running:

```
[root@compute2]# reboot
[root@compute2]#
Broadcast message from rmengert@compute2
        (/dev/pts/0) at 16:11 ...

The system is going down for reboot NOW!
Using username "rmengert".
Authenticating with public key "imported-openssh-key"
Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-32-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Wed Dec 31 16:11:41 MST 2014

  System load: 0.0               Memory usage: 2%   Processes:       91
  Usage of /:  4.0% of 56.96GB   Swap usage:   0%   Users logged in: 0

  => There are 4 zombie processes.

  Graph this data and manage this system at:
    https://landscape.canonical.com/

Last login: Wed Dec 31 10:30:21 2014 from 192.168.230.70
[rmengert@compute2]# uname -a
Linux compute2 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

Thanks everyone for your help!  Much appreciated.

---

### Post by schragge on 2015-01-01
@OP: Glad you've got it sorted out. Don't forget to mark this thread SOLVED (See [uwiki]UnansweredPostsTeam/SolvedThreads[/uwiki]).

@**Bashing-om**: Yes, *dpkg-statoverride --remove* would fix this, too. At least, until the next kernel update. If OP's systems somehow managed to get into this strange state once, there's no guarantees they wouldn't get into it again. My workaround is less elegant, for sure, it just makes dpkg ignore any errors caused by dpkg-statoverride, but it works for any future kernel updates.  I'd say the cleanest solution would be probably just to remove both */etc/kernel/postinst.d/statoverride* and */etc/kernel/postrm.d/statoverride* as they are not needed anymore according to discussion in LP #[lpbug]1343738[/lpbug]. But suggesting this would be rather unresponsible on my part -- I do not have an OpenStack cluster available to check if the latter statement actually holds true.

---

### Post by Bashing-om on 2015-01-01
> **schragge said:**
> @OP: Glad you've got it sorted out. Don't forget to mark this thread SOLVED (See [uwiki]UnansweredPostsTeam/SolvedThreads[/uwiki]).

@**Bashing-om**: Yes, *dpkg-statoverride --remove* would fix this, too. At least, until the next kernel update. If OP's systems somehow managed to get into this strange state once, there's no guarantees they wouldn't get into it again. My workaround is less elegant, for sure, it just makes dpkg ignore any errors caused by dpkg-statoverride, but it works fo any future kernel updates.  I'd say the cleanest solution would be probably just to remove both */etc/kernel/postinst.d/statoverride* and */etc/kernel/postrm.d/statoverride* as they are not needed anymore according to discussion in LP #[lpbug]1343738[/lpbug]. But suggesting this would be rather unresponsible on my part -- I do not have an OpenStack cluster available to check if the latter statement actually holds true.

I would not be surprised we see other incidences of this nature. Isolating the cause of the formation of the override file in this event will put a feather in our cap.

[INDENT][INDENT][INDENT]next !
[/INDENT][/INDENT][/INDENT]

---

### Post by MAFoElffen on 2015-01-01
> **schragge said:**
> @**Bashing-om**: Yes, *dpkg-statoverride --remove* would fix this, too. At least, until the next kernel update. If OP's systems somehow managed to get into this strange state once, there's no guarantees they wouldn't get into it again. My workaround is less elegant, for sure, it just makes dpkg ignore any errors caused by dpkg-statoverride, but it works fo any future kernel updates.  I'd say the cleanest solution would be probably just to remove both */etc/kernel/postinst.d/statoverride* and */etc/kernel/postrm.d/statoverride* as they are not needed anymore according to discussion in LP #[lpbug]1343738[/lpbug]. But suggesting this would be rather unresponsible on my part -- I do not have an OpenStack cluster available to check if the latter statement actually holds true.
@**schragge:** Thanks for that. I set up a current Openstack cluster last night to see what that fix actually changes...To see if there might be a similar tie to anything with the other user. I know the other is not Openstack, is Desktop, but could be a similar logic error iin that script... Curiosity on my part.

---

### Post by schragge on 2015-01-01
@**MAFoElffen** My pleasure. Citing [a comment]("https://bugs.launchpad.net/openstack-manuals/+bug/1343738/comments/2") from the bug report discussion:
[quote="Matt Kassawara"]Icehouse and potentially Juno no longer depend on the 'python-guestfs'  package that seems to cause this permissions issue. I think we can  remove the 'python-guestfs' package and this note from both versions of  the guide.[/quote]
From this I infer that the issue in question (python-guestfs unable to access kernel image without the dpkg-statoverride hack) is probably irrelevant for the current OpenStack release (Juno) and the previous one (Icehouse), but affects systems running second-to-last release (Havana). The dpkg-override hack was introduced to OpenStack [in December 2013]("https://git.openstack.org/cgit/openstack/openstack-manuals/commit/doc/install-guide/section_nova-compute.xml?id=fd49c1cf89d57b9c1e511fd20640d46afaa784fb") as a workaround for LP #[lpbug]759725[/lpbug]. It is [described]("http://docs.openstack.org/havana/install-guide/install/apt/content/nova-compute.html") in the Installation Guide for Havana and still [mentioned]("http://docs.openstack.org/training-guides/content/operator-compute-node-lab.html") in the Training Guides for Icehouse (likely through an oversight), but absent from documentation for current release. My understanding is that many existent installs of Icehouse (OpenStack 2014.1) may still feature */etc/kernel/post{inst,rm}.d/override* scripts because the Installation Guide was updated only in September 2014.  Hope this helps to pinpoint it.

---

### Post by robert-mengert on 2015-01-02
Thanks again everyone for your help, the thread has been marked as solved.  I was in the process of upgrading my OpenStack install from Icehouse to Juno when I started seeing these errors.  OpenStack doesn't have the concept of an LTS release (yet...) as Ubuntu does.  As such, [the Havana release is already considered end of life]("https://wiki.openstack.org/wiki/Releases").  Hopefully this issue just goes away after more folks upgrade to later releases.

---

