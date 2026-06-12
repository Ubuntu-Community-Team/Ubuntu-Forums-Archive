---
title: "zfs.ko missing after update to 12.10"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by RealityMaster on 2012-12-15
I updated to 12.10 from 12.04 and the zfs module for the new version is missing.

```
# zpool list
Failed to load ZFS module stack.
Load the module manually by running 'insmod <location>/zfs.ko' as root.

```

So I looked for it...

```
# uname -a
Linux Gollum 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
```
# find /lib/modules -name zfs.ko
/lib/modules/3.5.0-20-generic/updates/dkms/zfs.ko
/lib/modules/3.5.0-19-generic/updates/dkms/zfs.ko

```

:confused:

So I tried removing and re-installing zfs, 

apt-get remove ubuntu-zfs
apt-get autoclean
...reboot...
apt-get install ubuntu-zfs

(That's a summation....it was successful but same result)

Does anyone have 3.5.0-21-generic ... /zfs.ko ?

---

### Post by dino99 on 2012-12-15
i have no clue about that zfs module, but have you tried modprobe ?

[http://www.google.fr/#hl=fr&gs_nf=3&gs_rn=1&gs_ri=serp&pq=ubuntu%20desktop%20icons&cp=13&gs_id=3b&xhr=t&q=ubuntu+zfs.ko&pf=p&safe=off&tbo=d&sclient=psy-ab&oq=ubuntu+zfs.ko&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=ac9d2c5f7cf2a4ff&bpcl=39967673&biw=1485&bih=909](http://www.google.fr/#hl=fr&gs_nf=3&gs_rn=1&gs_ri=serp&pq=ubuntu%20desktop%20icons&cp=13&gs_id=3b&xhr=t&q=ubuntu+zfs.ko&pf=p&safe=off&tbo=d&sclient=psy-ab&oq=ubuntu+zfs.ko&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=ac9d2c5f7cf2a4ff&bpcl=39967673&biw=1485&bih=909)

---

### Post by bmullan on 2012-12-15
I don't use ZFS but have watching its progress with Ubuntu.

Read this [blog thread on ZFS with Ubuntu 12.04]("https://github.com/dajhorn/pkg-zfs/wiki/HOWTO-install-Ubuntu-to-a-Native-ZFS-Root-Filesystem")

Pay attention to the NOTE:
***Note: The necessary GRUB package will not be published for Ubuntu 12.10 Quantal Quetzal. This issue will be revisited for the next release series.***

You might want to ask the author of that Blog "why" that Note says what it says as he doesn't go into any details beyond the above.

---

### Post by RealityMaster on 2012-12-15
Unfortunately yes, but it fails as the file is not present..

```
 modprobe zfs
FATAL: Module zfs not found.
```

---

### Post by RealityMaster on 2012-12-15
> 
Pay attention to the NOTE:
***Note: The necessary GRUB package will not be published for Ubuntu 12.10 Quantal Quetzal. This issue will be revisited for the next release series.***


Unfortunately I'm not booting zfs, I'm just using it to house an array, so I don't really need grub-zfs

---

### Post by RealityMaster on 2012-12-17
](*,)

bump ?

---

### Post by RealityMaster on 2012-12-17
:guitar:

Ran updates today and it's working again!!!!


```
# find /lib/modules -name zfs.ko
/lib/modules/3.5.0-21-generic/updates/dkms/zfs.ko

```

---

### Post by jameswyse on 2012-12-22
I'm having the same problem.

I've been running ZFS on 12.10 for a few weeks with no issues, today I rebooted as apt had upgraded the kernel and now ZFS is broken.

This is the PPA I'm using: [https://launchpad.net/~zfs-native/+archive/stable](https://launchpad.net/~zfs-native/+archive/stable)

Here's what I've tried so far:

```
$ uname -a
Linux Goon 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

```
$ sudo zpool list
Failed to load ZFS module stack.
Load the module manually by running 'insmod <location>/zfs.ko' as root.
```

```
$ find /lib/modules -name zfs.ko
/lib/modules/3.5.0-19-generic/updates/dkms/zfs.ko
```

```
$ sudo insmod /lib/modules/3.5.0-19-generic/updates/dkms/zfs.ko
insmod: error inserting '/lib/modules/3.5.0-19-generic/updates/dkms/zfs.ko': -1 Unknown symbol in module
```

```
$ sudo modprobe zfs
FATAL: Module zfs not found.
```

```
$ sudo dmesg | grep zfs:
[ 1380.577459] zfs: Unknown symbol __taskq_destroy (err 0)
[ 1380.577472] zfs: Unknown symbol spl_cleanup (err 0)
[ 1380.577480] zfs: Unknown symbol nvpair_value_uint8 (err 0)
[ 1380.577487] zfs: Unknown symbol kmem_debugging (err 0)
[ 1380.577501] zfs: Unknown symbol vn_openat (err 0)

- this continues for hundreds of lines -
```

Now it seems to me that the zfs.ko module should be in ```
/lib/modules/3.5.0-21-generic/updates/dkms/zfs.ko
``` instead of ```
/lib/modules/3.5.0-19-generic/updates/dkms/zfs.ko
``` but I've no idea how to solve this.

Any ideas?

**Update: ** I've added the *daily* PPA and upgraded which seems to have solved the problem.  Though I don't feel too comfortable using the unstable branch on my production filesystem, so still looking for solutions on this! I guess if it comes to it I'll just wait for stable to be updated again and switch back.

---

### Post by Hilbe on 2012-12-24
Just thought I'd chime in.  I also switched to the Daily PPA. I reinstalled everything, but the zfs-dkms package is the one that fixed it.  So if you've tried Daily PPA and reinstalling ubuntu-zfs, try reinstalling zfs-dkms.  I'm good to go now.

---

### Post by RealityMaster on 2013-01-04
Great balls of FIRE:mad:!!!!

This is the third update to cause this problem!!! RAWWRRR!! 

Is no one testing the zfs package before updates are pushed?
I'll assume not as it's not officially supported, but this is getting $^(k!n& annoying.  

Curse, yell, swear, rant, rave, relax, post...

---

### Post by stephanvaningen on 2013-01-25
RealityMaster
I understand your frustration, I have similar experiences. It is not really an issue of the software, as it is an issue of dependencies getting broken for some reason (??) - I don't know much about it. More info on the github of ubuntu-zfs...

---

### Post by stephanvaningen on 2013-01-25
By the way, I solved it just now by doing an install of linux-headers-3.5.0.22-generic. See [http://stephanvaningen.net/wiki/How_to_repair_the_error_%27Failed_to_load_ZFS_module_stack.%27](http://stephanvaningen.net/wiki/How_to_repair_the_error_%27Failed_to_load_ZFS_module_stack.%27) for more info

---

### Post by jameswyse on 2013-02-02
Happened again today with the upgrade to 3.5.0-23-generic

Fixed it with:
```
> sudo apt-get remove zfs-dkms
> sudo apt-get install zfs-dkms ubuntu-zfs
```

So it seems the modules aren't being rebuilt when the kernel is upgraded, there's probably a better way to do that but the above method seems to do the job! Cheers 8)

---

### Post by ConstantK on 2013-02-03
I just tried to remove and reinstall the zfs-dkms as per jameswyse's code above, but I still have the same issue.
These are the module headers I have after a fresh install yesterday with all updates.
3.5.0-17-generic
3.5.0-23-generic

Should I use synaptic and rollback to 3.5.0-22-generic from stephanvaningen's suggestion?

---

### Post by andrewkk on 2013-02-03
See [Ubuntu daily PPA packaging issue: SPL version bump w/o corresponding ZFS version bump breaks dkms build]("https://github.com/zfsonlinux/zfs/issues/1258"):
> The daily PPA isn't completely sync'd for the 0.6.0-rc14 release.  If you need something right now, then you get can get it from the staging area.

This should be resolved before everybody gets home from the football game.
Here's the [Staging Area]("https://launchpad.net/~zfs-native/+archive/staging/+packages?field.name_filter=&field.status_filter=published&field.series_filter=quantal") if you're feeling adventurous, but it'll probably be easiest to just wait it out.

---

### Post by MAFoElffen on 2013-02-03
> **RealityMaster said:**
> Great balls of FIRE:mad:!!!!

This is the third update to cause this problem!!! RAWWRRR!! 

**Is no one testing the zfs package before updates are pushed?**
I'll assume not as it's not officially supported, but this is getting $^(k!n& annoying.  

Curse, yell, swear, rant, rave, relax, post...
> **jameswyse said:**
> **Update: ** I've added the *daily* PPA and upgraded which seems to have solved the problem. ***Though I don't feel too comfortable using the unstable branch on my production filesystem**, so still looking for solutions on this! I guess if it comes to it I'll just wait for stable to be updated again and switch back.

LOL. As I've been involved with dev versions for years... Being on a dev version, you are the tester.

Just a suggestion- (Common sense)
Problems with a dev version and it's packages, to include dailies should be discussed in the Ubuntu +1 section so that they know there are problems, can be discussed and can be addressed.On PP's there's an area to report problems with a PPA.

Even until a day preceding the code lock, there are still many areas were they focus on things needed to be tested... and then, during the code lock, all those approved, tested pieces come back together into the release snapshot. If you go to dailies, expect things to not be stable from day-to-day.

As a tester of a dev versions, we are also responsible for generating launchpad bug reports from problems that arise. Things are going to work one day, then maybe not the next. I just expect "that" as part of the process. 

We also work together to find our own workarounds and fixes. Although fun, adventurous and sometimes somewhat frustrating... there _is_ always a notice posted in that section each dev cylce saying that the dev versions are intended for testing and they are not intended for a production system nor production data. Doing that, once one is warned, then it is at your own risk.

Are PPA's really considered as "stable?" My past experience is that they are test areas or areas for things that are not yet formal packages. Usually on their way to being moved to approved stable... One thing I know is that if you have added PPA's, before you upgrade to another release, purge the ppa, upgrade the release, re-add the PPA. This is a pain if you have many PPA's.

---

### Post by ConstantK on 2013-02-03
I don't want to offend anyone that's working on the ZFS PPA, but is it worth going back to FUSE and waiting for the stability of the PPA to improve before coming back?

---

### Post by ConstantK on 2013-02-03
How about rolling back to the last stable? Does anyone know how I would do that? (sorry, I'm a n00b to ZFS)

---

### Post by stephanvaningen on 2013-02-04
ppa/fuse/ ... yes anyway:


I did it this way this time, similar to jameswyse, but additionally the step I did earlier too:
 ```
sudo apt-get remove linux-headers-`uname -r` zfs-dkms ubuntu-zfs
```
Then did a (without in-between reboot, because otherwise the uname will give different result):
 ```
sudo apt-get install linux-headers-`uname -r`
```
and then:
 ```
sudo apt-get install zfs-dkms ubuntu-zfs
```

Then I see rebuilds of modules & a reboot now results in availability of your ZFS pools again...

---

### Post by Rakeesh on 2013-04-25
It seems like every time I reboot my server, my zfs pool disappears. I am only configured to automatically apply security updates, which I guess includes kernel updates. As one would expect, that breaks the zfs modules.

Is there any way to make sure the zfs binaries/modules stay on top of those changes without any intervention? A power outage for example would just kill my server until I manually intervene, which sort of defeats the high availability aspect of zfs. I'm not sure whether to consider this a ZoL problem or an Ubuntu problem.

This isn't a production environment by the way, it's just a hobby setup I have which has some miscellaneous junk stored on a 4 disk array. I'm hoping to one day apply what I'm learning here to a professional level as I am just about to graduate as a network engineer with some datacenter experience.

---

### Post by 13eastie on 2013-05-19
[B][COLOR="#FF0000"]EDIT:  The approach advised at the post below resolves this version of the problem:
[https://github.com/zfsonlinux/zfs/issues/1155#issuecomment-11499841](https://github.com/zfsonlinux/zfs/issues/1155#issuecomment-11499841)[/COLOR][/B]

I have encountered this error on 12.04.2 LTS after removing a bunch of old kernel modules.

Attempting the final stage in stephenvaningen's post #19 gives
```
# sudo apt-get install zfs-dkms ubuntu-zfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  zfs-auto-snapshot
The following NEW packages will be installed
  ubuntu-zfs zfs-dkms
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,092 kB of archives.
After this operation, 10.5 MB of additional disk space will be used.
Selecting previously unselected package zfs-dkms.
(Reading database ... 426944 files and directories currently installed.)
Unpacking zfs-dkms (from .../zfs-dkms_0.6.1-1~precise_amd64.deb) ...
Selecting previously unselected package ubuntu-zfs.
Unpacking ubuntu-zfs (from .../ubuntu-zfs_7~precise_amd64.deb) ...
Setting up zfs-dkms (0.6.1-1~precise) ...
Loading new zfs-0.6.1 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-43-generic
Building initial module for 3.2.0-43-generic
configure: error: 
	*** Please make sure the kmod spl devel <kernel> package for your
	*** distribution is installed then try again.  If that fails you
	*** can specify the location of the spl objects with the
	*** '--with-spl-obj=PATH' option.
Error! Bad return status for module build on kernel: 3.2.0-43-generic (x86_64)
Consult /var/lib/dkms/zfs/0.6.1/build/make.log for more information.
Setting up ubuntu-zfs (7~precise) ...
```

/var/lib/dkms/zfs/0.6.1/build/make.log shows:
```
DKMS make.log for zfs-0.6.1 for kernel 3.2.0-43-generic (x86_64)
Sun May 19 13:42:25 BST 2013
make: *** No targets specified and no makefile found. Stop.
```

Kernel packages are installed on my system as follows:
```
# dpkg --get-selections | grep linux-image
linux-image-3.2.0-43-generic			install
linux-image-server				install
```

I continue to get this error:
```
# zpool status
Failed to load ZFS module stack.
Load the module manually by running 'insmod <location>/zfs.ko' as root.
Failed to load ZFS module stack.
Load the module manually by running 'insmod <location>/zfs.ko' as root.
```

**Very grateful indeed for any advice on resolving this.**

---

### Post by dereitz on 2013-09-05
I wish things worked seamlessly, but the following worked for me after my last update (I'm on 12.04, but I doubt the Ubuntu version matters here) and seems a little simpler than the earlier workarounds proposed:

```
apt-get install --reinstall zfs-dkms
zfs mount -a
```

Hope this works for others and maybe someone can eventually recommend a true fix.

Regards,
David

---

