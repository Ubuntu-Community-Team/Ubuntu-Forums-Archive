---
title: "Kernel 2.6.28-2"
date: 2008-12-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2008-12-05
Out....):P

Including meta package

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001572.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001572.html)

---

### Post by BwackNinja on 2008-12-05
Running with no problems :D, or rather :( everything has been so stable......

---

### Post by plun on 2008-12-05
> **BwackNinja said:**
> Running with no problems :D, or rather :( everything has been so stable......

yup,but Linus himself is annoyd....

[http://torvalds-family.blogspot.com/2008/12/debugging-hell.html](http://torvalds-family.blogspot.com/2008/12/debugging-hell.html)

"Debugging hell" and suspend

Catch this one from Ubuntu.....\\:D/

---

### Post by defconoii on 2008-12-05
This broke the nvidia driver for the fx 5500

---

### Post by super.rad on 2008-12-05
Working perfectly for me, and so is ext4 now :D

---

### Post by ShirishAg75 on 2008-12-06
Still trying to figure out how to purge/remove the old image. The headers having removed but still show up in grub menu.lst 

```

$ sudo aptitude purge linux-image-2.6.28-1-ub-generic
linux-headers-2.6.28-1-ub-generic

Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
The following packages will be REMOVED:
  linux-image-2.6.28-1-ub-generic{p}
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 96.8MB will be freed.
Do you want to continue? [Y/n/?] Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
The following packages will be REMOVED:
  linux-image-2.6.28-1-ub-generic{p}
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 96.8MB will be freed.
Writing extended state information...
(Reading database ... 215747 files and directories currently installed.)
Removing linux-image-2.6.28-1-ub-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/last-good-boot
/etc/kernel/prerm.d/last-good-boot: 3: /usr/sbin/kernel-helper: not found
run-parts: /etc/kernel/prerm.d/last-good-boot exited with return code 127
Failed to process /etc/kernel/prerm.d at
/var/lib/dpkg/info/linux-image-2.6.28-1-ub-generic.prerm line 267.
dpkg: error processing linux-image-2.6.28-1-ub-generic (--purge):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28-1-ub-generic
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...


```

If anybody gets any idea please lemme know.

---

### Post by DougieFresh4U on 2008-12-06
I am using kernel **2.6.28-2.3**
Updates last nite had the complete kernel **2.6.28-1  Intrepid** update.
Looking at the posted screenshots, how do I make that go away, as I do not have Intrepid on this machine.
I hope I have explained the situation clearly enough
I understand it as going backwards to update a kernel I am not using any more:confused:

---

### Post by shirishagarwal on 2008-12-06
Dougie, 
  Kernel 2.6.28-1 is only in Jaunty. Intrepid (even with proposed only has 2.6.27-10) as of date.

---

### Post by phenest on 2008-12-06
With each kernel update, I have to reinstall VirtualBox OSE to recompile the modules for it. Is there a way for it to do this automatically?

---

### Post by DougieFresh4U on 2008-12-06
> **shirishagarwal said:**
> Dougie, 
  Kernel 2.6.28-1 is only in Jaunty. Intrepid (even with proposed only has 2.6.27-10) as of date.

Understood. But how do I get rid of what my screenshots are saying?

---

### Post by anhvu2875 on 2008-12-06
**DougieFresh4U**
> Updates last nite had the complete kernel 2.6.28-1 Intrepid update.
how ?

---

### Post by Matthewthegreat on 2008-12-06
> **shirishagarwal said:**
> Dougie, 
  Kernel 2.6.28-1 is only in Jaunty. Intrepid (even with proposed only has 2.6.27-10) as of date.

I won't get to use the new kernel until Jaunty :(

---

### Post by Slug71 on 2008-12-06
Up and running on this Kernel.

Will todays daily build have this Kernel by default?

---

### Post by plun on 2008-12-06
> **Slug71 said:**
> Up and running on this Kernel.

Will todays daily build have this Kernel by default?

Yup... because its a released meta package for this kernel.:D

**sudo apt-get install linux** will be this kernel....the same
on a daily built CD (default).

---

### Post by anhvu2875 on 2008-12-06
tried and still no new kernel 2.6.28 for Intrepid !
```
anhvu2875@ubuntu:~$ sudo apt-get install linux
[sudo] password for anhvu2875: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image linux-restricted-modules
The following NEW packages will be installed:
  linux linux-image linux-restricted-modules
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 8620B of archives.
After this operation, 98.3kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com intrepid-updates/main linux-image 2.6.27.9.13 [2860B]
Get:2 http://us.archive.ubuntu.com intrepid-updates/restricted linux-restricted-modules 2.6.27.9.13 [2886B]
Get:3 http://us.archive.ubuntu.com intrepid-updates/restricted linux 2.6.27.9.13 [2874B]
Fetched 8620B in 1s (4330B/s)
Selecting previously deselected package linux-image.
(Reading database ... 110267 files and directories currently installed.)
Unpacking linux-image (from .../linux-image_2.6.27.9.13_i386.deb) ...
Selecting previously deselected package linux-restricted-modules.
Unpacking linux-restricted-modules (from .../linux-restricted-modules_2.6.27.9.13_i386.deb) ...
Selecting previously deselected package linux.
Unpacking linux (from .../linux_2.6.27.9.13_i386.deb) ...
Setting up linux-image (2.6.27.9.13) ...
Setting up linux-restricted-modules (2.6.27.9.13) ...
Setting up linux (2.6.27.9.13) ...
anhvu2875@ubuntu:~$ 
```

---

### Post by plun on 2008-12-06
> **anhvu2875 said:**
> tried and still no new kernel 2.6.28 for Intrepid !

Can you please stop spamming this group with Intrepid questions !

This group is about Jaunty and development !

Thanks !

---

### Post by lonniehenry on 2008-12-06
anhvu2875  - The 2.6.28-2 is in Jaunty not intrepid.  The kernel you have is the latest for intrepid.  From your post you are using intrepid.


edit: plun you beat me to the point.

---

### Post by DougieFresh4U on 2008-12-06
i do not know how to explain this, but I do not have Intrepid on this machine. But looking at the screenshots posted, my Synaptic has the 2 packages marked for upgrade but I get the messege that it can not be done. I would like to make those 'marks' go away as I am using kernel 2.6.28-2.3

---

### Post by adult swim on 2008-12-06
have you tried taking the intrepid backports out of your sources.list?

---

### Post by lonniehenry on 2008-12-06
DougieFresh4U  Could you look at your sources list to see if you left one of the intrepid repositories in your list when you changed to the jaunty ones.  If you left one by accident you may still be getting the list from backports. (I have missed commenting out one in the past and had some problems upgrading.)

Edit: I really have to learn to type faster.

---

### Post by autocrosser on 2008-12-06
I've been getting the same info--Dougie--I'd run Synaptic & remove the .27 kernel stuff unless you need to run it--that way the problem will go away --I finally got my Ralink 'net card to play nice with .28, so I'm removing all the Intrepid sources & removing all the .27 kernel stuff :D:D:D

ABOUT TIME:popcorn:

---

### Post by DougieFresh4U on 2008-12-06
Thanks to those that have replied.
I am not trying to make drama, but I am confused about the mixed messeges I am getting. i would rather fix than re-install.


```
deb http://packages.medibuntu.org/ jaunty free non-free

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.                                    

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in     
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.                                                                   
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.                                                           
## N.B. software from this repository may not have been tested as        
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.                               
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.                                                                
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse

deb http://ppa.launchpad.net/fta/ubuntu jaunty main
deb-src http://ppa.launchpad.net/fta/ubuntu jaunty main
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe

deb http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main
deb-src http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main
```

---

### Post by lonniehenry on 2008-12-06
DougieFresh4U  You have some double entries, but nothing that would cause a problem.  Open synatic and see if you have any linux-backport-module-* items installed.  If you do, uninstall them and you should be ok.

---

### Post by Slug71 on 2008-12-06
> **plun said:**
> Yup... because its a released meta package for this kernel.:D

**sudo apt-get install linux** will be this kernel....the same
on a daily built CD (default).

Thanks plun, 
Downloaded the daily build to see if it had Ext4 as an option but still nothing :(

---

### Post by autocrosser on 2008-12-06
Yes--that's all I'm waiting for now--I've got a drive ready to test EXT4 as soon as I can :) ---thanks for the info slug 71----

DougieFresh4U---I had the backports "stuck" in my system--a quick clean-up of my sources & a search with Synaptic got me up to speed again---you should just have the 2.6.28-2-generic meta-package left after you are done :D.

---

### Post by plun on 2008-12-07
> **Slug71 said:**
> Thanks plun, 
Downloaded the daily build to see if it had Ext4 as an option but still nothing :(

Nope.... still this in Ubuntus kernel config

/boot

> # CONFIG_EXT4DEV_COMPAT is not set
CONFIG_EXT4_FS=m
CONFIG_EXT4_FS_POSIX_ACL=y
CONFIG_EXT4_FS_SECURITY=y
CONFIG_EXT4_FS_XATTR=y

I have built may own 1000Hz kernel with EXT4 support and it works just fine with my EXT4 test partition.

Our devs will probably discuss this during UDS next week....;)

---

### Post by mariuz on 2008-12-07
2.6.28.x locked on my via machine - everex cloudbook

it may be related to padlock but not sure

---

### Post by plun on 2008-12-07
> **mariuz said:**
> 2.6.28.x locked on my via machine - everex cloudbook

it may be related to padlock but not sure

Please file a bug about it....

This is what the kernel team wants included within a bug report.

[https://wiki.ubuntu.com/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeamBugPolicies)

.

---

### Post by k64 on 2008-12-07
As You May Have Discused, Kernel 2.6.28 Comes With Ext4 Prepackaged, Since It Is No Longer Experimental!

---

### Post by Slug71 on 2008-12-07
> **k64 said:**
> As You May Have Discused, Kernel 2.6.28 Comes With Ext4 Prepackaged, Since It Is No Longer Experimental!


Yes but its disabled by default. Therefore you cannot use it at install.

---

### Post by RAOF on 2008-12-07
> **Slug71 said:**
> Yes but its disabled by default. Therefore you cannot use it at install.

Except that this
```

CONFIG_EXT4_FS=m
CONFIG_EXT4_FS_POSIX_ACL=y
CONFIG_EXT4_FS_SECURITY=y
CONFIG_EXT4_FS_XATTR=y 

```
says that it's built as a module that'll be autoloaded when needed.  The fact that the installers don't have the option to format the partition as ext4 is a different matter.

---

### Post by plun on 2008-12-07
> **RAOF said:**
> Except that this
```

CONFIG_EXT4_FS=m
CONFIG_EXT4_FS_POSIX_ACL=y
CONFIG_EXT4_FS_SECURITY=y
CONFIG_EXT4_FS_XATTR=y 

```
says that it's built as a module that'll be autoloaded when needed.  The fact that the installers don't have the option to format the partition as ext4 is a different matter.

I have choosen a "y" for my vanilla RC7 kernel and my ext4 partition can be mounted.

No way with ub-2....

This is my ext4 setup:
[http://ubuntuforums.org/showpost.php?p=6104260&postcount=59](http://ubuntuforums.org/showpost.php?p=6104260&postcount=59)

Works just fine...;)

---

### Post by RAOF on 2008-12-07
I've just formatted and mounted an ext4 partition with the stock Jaunty tools and kernel.  It works fine.

---

### Post by plun on 2008-12-08
> **RAOF said:**
> I've just formatted and mounted an ext4 partition with the stock Jaunty tools and kernel.  It works fine.

Ok...I created a new mount point and then my ext4 partition mounts.;)

I cannot see what differs between a vanilla and ub-2....:confused: 

fstab was nevertheless without the ext4 partition and what is then mounting
a partition with the vanilla kernel .....???

Testing...

---

### Post by mariuz on 2008-12-08
> **plun said:**
> Please file a bug about it....

This is what the kernel team wants included within a bug report.

[https://wiki.ubuntu.com/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeamBugPolicies)

.

Ok i can boot now if  remove the padlock
also i will submit an bug to the launchpad

---

### Post by Gina on 2008-12-08
> **Slug71 said:**
> Yes but its disabled by default. Therefore you cannot use it at install.Well, that's not very clever!!  If it's all ready to use, what's the problem, I wonder. :confused:

---

### Post by plun on 2008-12-08
> **Gina said:**
> Well, that's not very clever!!  If it's all ready to use, what's the problem, I wonder. :confused:

Well... it can be manually done but we still have this bug from
Theodore Tso 

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311)

There is a USD developer blueprint also for this


Basic about Ext4  (Theodore is probably the author also for this)

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)


Nevertheless I can mount a Ext4 partition, but not "automagic" with a Ubuntu kernel, with a Vanilla its done.....

---

### Post by dvalentine on 2008-12-08
Hi Everybody,

I am having trouble with the 2.6.28-2 kernel version. I've got jaunty, I've did the update through the update manager (after i tried the apt-get install linux and synapics for reinstall) and after it successfully update the kernel, it doesnt boot up. It hangs up at the Loading hardware driver. After I tried the synaptic reinstall it puts some debug information, but I am not an expert. Any idea?
The comp. is az Asus nforce3, Athlon 64 2800+, elsa geforce 6600 gt and a diamond mx400 (canyon3d).

Thanks and regards,
David

---

### Post by jfernyhough on 2008-12-08
> **dvalentine said:**
> Hi Everybody,

I am having trouble with the 2.6.28-2 kernel version. I've got jaunty, I've did the update through the update manager (after i tried the apt-get install linux and synapics for reinstall) and after it successfully update the kernel, it doesnt boot up. It hangs up at the Loading hardware driver. After I tried the synaptic reinstall it puts some debug information, but I am not an expert. Any idea?
The comp. is az Asus nforce3, Athlon 64 2800+, elsa geforce 6600 gt and a diamond mx400 (canyon3d).

Thanks and regards,
DavidWhen booting, at the kernel select screen edit the GRUB boot line (press e), then edit the first line (e again). Remove quiet and nosplash, and try booting (enter then b). It should give you some more information on where it's hanging.

---

### Post by dvalentine on 2008-12-09
Thanks, I've managed that it hangs on /sbin/modprobe abnormal exit and after get_netlint_msg invalid event ''. I googled it now the first hit seems like my problem, except it is not with 2.6.28-2 :)

---

### Post by ShirishAg75 on 2008-12-09
better report the same on launchpad. Atleast there would be a precedence for others then. Somebody or the other might be able to give you some idea as to what might be going wrong.

---

### Post by dserodio on 2008-12-19
I'm trying to build a 2.6.28 kernel for my Intrepid system.

I got the 2.6.28-3 source from Jaunty, and followed the instructions at [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) 

The following packages were built:
[LIST]
[*]linux-headers-2.6.28-3-generic_2.6.28-3.4_amd64.deb
[*]linux-headers-2.6.28-3-server_2.6.28-3.4_amd64.deb
[*]linux-image-2.6.28-3-generic_2.6.28-3.4_amd64.deb
[*]linux-image-2.6.28-3-server_2.6.28-3.4_amd64.deb
[*]linux-image-2.6.28-3-virtual_2.6.28-3.4_amd64.deb
[*]linux-libc-dev_2.6.28-3.4_amd64.deb
[/LIST]
I tried to install it using:
```
sudo dpkg -i linux-headers-2.6.28-3-generic_2.6.28-3.4_amd64.deb \
linux-image-2.6.28-3-generic_2.6.28-3.4_amd64.deb
``` but it won't install, because **linux-headers-2.6.28-3-generic** depends on **linux-headers-2.6.28-3** and this package wasn't built.

Did I do something wrong, or is this a bug?

Thanks in advance,
Daniel Serodio

---

### Post by xebian on 2008-12-19
> **dserodio said:**
> I'm trying to build a 2.6.28 kernel for my Intrepid system.

but it won't install, because **linux-headers-2.6.28-3-generic** depends on **linux-headers-2.6.28-3** and this package wasn't built.

Did I do something wrong, or is this a bug?

Thanks in advance,
Daniel Serodio

No it's not  abug.  It's always been that way.

```
ii  linux-headers-2.6.27-3               2.6.27-3.4                                       Header files related to Linux kernel version
ii  linux-headers-2.6.27-3-generic       2.6.27-3.4                                       Linux kernel headers for version 2.6.27 on x
ii  linux-headers-2.6.27-4               2.6.27-4.6                                       Header files related to Linux kernel version
ii  linux-headers-2.6.27-4-generic       2.6.27-4.6                                       Linux kernel headers for version 2.6.27 on x
ii  linux-headers-2.6.27-5               2.6.27-5.8                                       Header files related to Linux kernel version
ii  linux-headers-2.6.27-5-generic       2.6.27-5.8                                       Linux kernel headers for version 2.6.27 on x
ii  linux-headers-2.6.27-6               2.6.27-6.9                                       Header files related to Linux kernel version
ii  linux-headers-2.6.27-6-generic       2.6.27-6.9                                       Linux kernel headers for version 2.6.27 on x
ii  linux-headers-2.6.27-7               2.6.27-7.16                                      Header files related to Linux kernel version
ii  linux-headers-2.6.27-7-generic       2.6.27-7.16                                      Linux kernel headers for version 2.6.27 on x
ii  linux-headers-2.6.27-9               2.6.27-9.19                                      Header files related to Linux kernel version
ii  linux-headers-2.6.27-9-generic       2.6.27-9.19                                      Linux kernel headers for version 2.6.27 on x
ii  linux-headers-2.6.28-3               2.6.28-3.4                                       Header files related to Linux kernel version
ii  linux-headers-2.6.28-3-generic       2.6.28-3.4                                       Linux kernel headers for version 2.6.28 on x

```

---

### Post by xebian on 2008-12-19
> **dserodio said:**
> I'm trying to build a 2.6.28 kernel for my Intrepid system.

I got the 2.6.28-3 source from Jaunty, and followed the instructions at [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) 

Daniel Serodio

I didn't even have to compile them.  I just bring them over from jaunty, and install whatever dependencies they need.  Works fine by me.

---

### Post by Gina on 2008-12-20
Jaunty with kernel 28.3 running fine on my laptop - using it now :)

---

### Post by dserodio on 2008-12-20
> **xebian said:**
> No it's not  abug.  It's always been that way.
So how does this package get built?

---

### Post by dserodio on 2008-12-20
> **xebian said:**
> I didn't even have to compile them.  I just bring them over from jaunty, and install whatever dependencies they need.  Works fine by me.
I was about to try your suggestion, but I noticed it wants to update libc6 along. That's a rather major update I'm not willing to try.

---

### Post by xebian on 2008-12-20
> **dserodio said:**
> So how does this package get built?

Same way you built the others.

---

### Post by xebian on 2008-12-20
> **dserodio said:**
> I was about to try your suggestion, but I noticed it wants to update libc6 along. That's a rather major update I'm not willing to try.

It's not a major update.  It's still libc ver 6,  release 2.9 instead of 2.8.  

Your call.  

For me I'd rather keep them in step because I compile kernel modules as well like nvidia drivers.

---

### Post by Slug71 on 2008-12-24
And 2.6.28 is now the latest stable Kernel.

---

### Post by ShirishAg75 on 2008-12-24
Slug71, you beat me to it :)

Now to see when our lovely developers take it and give it to us :)

---

### Post by Slug71 on 2008-12-24
> **ShirishAg75 said:**
> Slug71, you beat me to it :)

Now to see when our lovely developers take it and give it to us :)

Haha, Hopefully soon! ):P

---

### Post by plun on 2008-12-25
> **Slug71 said:**
> And 2.6.28 is now the latest stable Kernel.

Yup it is....

And a "crazy" message from Linus....):P

> It doesn't really matter what day it is, or what holiday (if any) you're 
celebrating, because even if you sit at home, alone in your dank basement, 
without any holidays or friends, I bring you a tiding of great cheer: you 
can now download Linux-2.6.28, and compile it to your hearts content!

Listen to the cheerful grinding of your harddisk as you reboot into an 
all-new kernel - and I'm sure that if your computer could smile, it would 
have a big silly grin on its non-existent face. So as you sit there in 
your basement, give your computer the holiday cheer too.

In fact, even _if_ you have friends or family, leave them to their endless 
toil over that christmas ham or turkey, and during the night, when they're 
asleep, you can give them that magical present of a newly updated 
computer. When they wake up tomorrow morning, tell them how you saw Santa 
crawl down the chimney with his USB stick in hand, updating the OS of all 
good boys and girls.

Ho, ho, ho,

		Linus "almost Santa" Torvalds

[http://lkml.org/lkml/2008/12/24/105](http://lkml.org/lkml/2008/12/24/105)

---

### Post by Gina on 2008-12-25
:lolflag:

---

### Post by anibalojeda on 2008-12-30
> **phenest said:**
> With each kernel update, I have to reinstall VirtualBox OSE to recompile the modules for it. Is there a way for it to do this automatically?

no thats the way things are ;-)

---

### Post by anibalojeda on 2008-12-30
I just compiled the kernel from the source of [https://launchpad.net/ubuntu/jaunty/+source/linux/2.6.28-4.5/+files/linux_2.6.28.orig.tar.gz](https://launchpad.net/ubuntu/jaunty/+source/linux/2.6.28-4.5/+files/linux_2.6.28.orig.tar.gz)

on my laptop, everything works perfect !

---

### Post by dserodio on 2009-01-12
> **xebian said:**
> Same way you built the others.
I built them (following [Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile") on Ubuntu docs) by typing```
AUTOBUILD=1 fakeroot debian/rules binary-debs
``` inside the linux-2.6.28 folder.

As I mentioned, this package (linux-headers-2.6.28-3) wasn't built.

---

