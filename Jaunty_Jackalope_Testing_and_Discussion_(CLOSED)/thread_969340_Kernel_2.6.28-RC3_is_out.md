---
title: "Kernel 2.6.28-RC3 is out"
date: 2008-11-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2008-11-03
[http://lkml.org/lkml/2008/11/2/214](http://lkml.org/lkml/2008/11/2/214)

> Another week, another -rc.

Unlike -rc2, this one isn't just "critical brown-paper-bag fixes", and is 
more in line with a normal -rc. Yeah, I was hoping for a nice calm week, 
and it really wasn't that bad, but it's also certainly not the small 
minimal kind of -rc that -rc2 was.

From a diffstat standpoint, about 2/3rds are architectyre updates: mainly 
mips, SH and CRIS. Some of it is defconfig files, some of it is header 
file removal (cris header file movement included removing a number of 
stale headers), some of it is just updates.

Another 1/4 of the changes are drivers (input, hid, edac and pcmcia 
updates), and the rest is a smattering of fixes all over (with perhaps 
ftrace standing out a bit).

The one change I'm personally most interested in is the impact of the 
resource handling changes: since 2.6.27 we've changed the order in which 
we scan resources on x86, so that PCI scanning now sets up its resources 
before we do the e820 resouce entries. That, in turn, can cause changes in 
where we allocate PCI devices.

We already found and fixed one regression that caused, but I really am 
very interested in getting wide testing of the new order across as wide a 
range of machines as possible. It would be especially interesting to hear 
from people who have older machines, which are often under-represented in 
the early -rc testing.

I'm including the shortlog - it's big enough that perhaps it's a bit 
ovwewhelming and people don't end up finding it all that useful, but it 
does get a flavor of the changes. 

		Linus



Start Kernelcheck....;)

---

### Post by jfernyhough on 2008-11-03
Been using it since last night. ;) I also trimmed out a load of debug options that don't seem to have any effect during normal use. System is running fine at the moment.

I think I had an oops under RC2, just before I started the RC3 compile - X died and when it came back up my root was read-only. :D

---

### Post by plun on 2008-11-03
RC3 is radical slower for me....  PackageKits "racing" is back with the apt-backend... same as with Intrepids sleepy kernel.

Only 3.5 MB/s if I moves a large file...


Kernelcheck broke (Nouveau drivers),  image and headers was built OK

Messed with Linux source to be able to build an nVidia driver


Testing...;)

---

### Post by jfernyhough on 2008-11-03
> **plun said:**
> RC3 is radical slower for me....  PackageKits "racing" is back with the apt-backend... same as with Intrepids sleepy kernel.Hmm... RC3 is about the same speed, but then I'm not running PackageKit...

> Only 3.5 MB/s if I moves a large file...Getting ~9.9MB/s for a 700MB file from ext3 to ntfs-3g... though I am running with elevator=deadline, not cfq as is default.

> Kernelcheck broke (Nouveau drivers),  image and headers was built OKI had to do a 'dpkg -i --force-overwrite' as RC3 was trying to write firmware files that RC2 had already installed. I probably should have rebooted to 2.6.27, uninstalled 2.6.28-rc2, /then/ installed rc3, but hey...

> Messed with Linux source to be able to build an nVidia driverI got 177.80 working with the patch from here: [http://www.nvnews.net/vbulletin/showpost.php?p=1823327&postcount=21](http://www.nvnews.net/vbulletin/showpost.php?p=1823327&postcount=21)

> Testing...;):D

---

### Post by plun on 2008-11-03
Okidok....too lazy for quotes... sorry.

Studying Fstab

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I wonder about relatime ???

[http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)


Next step... did you enable Ext4 ?


>   Can I mount existing Ext3 as Ext4? And vice versa? Similarly from Ext2 to Ext4 and its reverse?

You can mount any ext3 filesystem as ext4 without any changes. If the filesystem is mounted as ext4 using the "extents" mount option (the default), this will enable the INCOMPAT_EXTENTS feature, and prevent the filesystem from being mounted as ext3 again. **_If you mount with the "-o noextents" option this will not happen_**.

For ext2 the filesystem would first need to have a journal created using tune2fs before it can be mounted as ext3 or ext4. At that point the filesystem is an ext3 filesystem and the above comments apply.

[http://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions](http://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions)

 


But how is the correct syntax  ?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=01d4a969-5b4c-499a-8ef2-6fca71fe2ccd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=1bd53d0e-a190-4358-a24f-cdea59941581 /Min            ext4    relatime      0       2
# /dev/sda4
UUID=ea60a35d-3a50-4b02-8eda-60da18ad08fd /home           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# a swapfile is not a swap partition, so no using swapon|off from here on, use  dphys-swapfile swap[on|off]  for that
```


):P

---

### Post by Slug71 on 2008-11-10
RC-4 is out now.:)

---

### Post by plun on 2008-11-11
> **Slug71 said:**
> RC-4 is out now.:)

Yup....

[http://lkml.org/lkml/2008/11/9/274](http://lkml.org/lkml/2008/11/9/274)

-------------------
Disk I/0 is back to normal.... around 10-11 MB/sec

No fork/apt-backend alerts with PackageKit... "hooray" !


-   tty was broken for me,  recovery mode and root shell for enabling patched nvidia driver.O:)


- No 5 seconds boot....:lolflag:


Nice kernel nevertheless....:)

---

### Post by Slug71 on 2008-11-11
> **plun said:**
> 
- No 5 seconds boot....:lolflag:


:lolflag::lolflag:

---

### Post by zoomy942 on 2008-11-11
> **Slug71 said:**
> :lolflag::lolflag:

i am using the intrepid release.

how can i install this kernel for kicks?

---

### Post by jfernyhough on 2008-11-11
Use KernelCheck. Either grab it from [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/) or add 

## Kernelcheck
deb [http://ppa.launchpad.net/master-kernel/ubuntu/](http://ppa.launchpad.net/master-kernel/ubuntu/) hardy main
# deb-src [http://ppa.launchpad.net/master-kernel/ubuntu/](http://ppa.launchpad.net/master-kernel/ubuntu/) intrepid main

to sources.list, update, and install.

You will have to click Get Kernel Information first, go to New kernel Patch Options and select Development Patch. Build Kernel is hiding under Program at the top.

After KernelCheck downloads the kernel source it will give you a configuration dialogue box. This contains a heck of a lot of options, but don't worry too much - the defaults will be picked up from the currently running kernel. You might like to try tweaking it, for example not building in driver support for devices you don't have (I've never owned a PC with the MCA bus, for example).

HOWEVER. A word of warning.

While the version says RC which normally means Release Candidate, these kernels CAN DESTROY YOUR PC AND ALL ITS DATA. Think back to the Intel e1000 bug - these kernels are worse, and are meant only for kernel developers and testers. And bleeding-edge idiots. :D

Having said this, the worst I've had so far is an oops where something corrupted an inode on my ext3 root drive which remounted read-only. A reboot and 'fsck -fy' fixed it. Silly me for trying an RC2. :D Generally, RCs after RC6 should be stable enough for most knowledgeable users.

> RC4
Just to see what happened, I set the kernel back to using SLAB and Deadline instead of SLUB and CFQ, i.e. back to the way it was back in 2.6.24. Seems to have made little difference - so why was the change made? Or is it noticeable in 64-bit?

---

### Post by zoomy942 on 2008-11-11
> **jfernyhough said:**
> Use KernelCheck. Either grab it from [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/) or add 

## Kernelcheck
deb [http://ppa.launchpad.net/master-kernel/ubuntu/](http://ppa.launchpad.net/master-kernel/ubuntu/) hardy main
# deb-src [http://ppa.launchpad.net/master-kernel/ubuntu/](http://ppa.launchpad.net/master-kernel/ubuntu/) intrepid main

to sources.list, update, and install.

You will have to click Get Kernel Information first, go to New kernel Patch Options and select Development Patch. Build Kernel is hiding under Program at the top.



thansk for the reply!  so i added those to the source.list, and did update manager and it only found 3 little updates, nothing about any kernel updates.

signed,
bleeding edge idiot :)

---

### Post by caryb on 2008-11-11
I question the placing the ppa on this post? It only relates to Hardy which is 2 versions old now & this is a JJ post.


Cary

[QUOTE]## Kernelcheck
deb [http://ppa.launchpad.net/master-kernel/ubuntu/](http://ppa.launchpad.net/master-kernel/ubuntu/) hardy main
# deb-src [http://ppa.launchpad.net/master-kernel/ubuntu/](http://ppa.launchpad.net/master-kernel/ubuntu/) intrepid main
[QUOTE]

BTW The intrepid reference is not there.

---

### Post by zoomy942 on 2008-11-11
> **caryb said:**
> I question the placing the ppa on this post? It only relates to Hardy which is 2 versions old now & this is a JJ post.


Cary

[QUOTE]## Kernelcheck
deb [http://ppa.launchpad.net/master-kernel/ubuntu/](http://ppa.launchpad.net/master-kernel/ubuntu/) hardy main
# deb-src [http://ppa.launchpad.net/master-kernel/ubuntu/](http://ppa.launchpad.net/master-kernel/ubuntu/) intrepid main
[QUOTE]

BTW The intrepid reference is not there.


i just want to install it before i reinstall my tablet :)

---

### Post by jfernyhough on 2008-11-11
Yeah, there's no PPA package for a version other than hardy in that PPA. It still works fine. If in doubt you can always grab the one from Sourceforge - it's the same version anyway.

Anyhow, after adding it to sources.list you should find a kernelcheck package that can be installed - you will have to search for it.

> JJ
Yeah, it's not strictly JJ but it's not something most users are going to do -just devs and people living on the bleeding edge.

---

### Post by plun on 2008-11-17
Time for blocking the PC again with a build.....:)

RC5 is out

> Hmm.. No clear pattern here, mostly random fixes, along with some file 
movement in the Documentation/ subdirectory. Bulk-wise, that's the biggest 
part if you see it as a traditional diff (because of the delete/create 
pairs), but with rename detection on the Doc patches are only about 10% of 
the changes.

The rest tends to be the ppc def_config updates (15%), and then random 
driver updates (65% - mostly due to some new hwmon and rtc drivers and the 
c2port driver).

But in number of commits, most of them are really just random small 
changes all over. ACPI, DM, USB, V4L, ocfs..  Nothing really strikes me as 
standing out, but if I had to pick something, then the ACPI update in 
particular hopefully fixes a few regressions. Along with disabling 
tick_nohz_kick_tick.

			Linus

[http://lkml.org/lkml/2008/11/15/135](http://lkml.org/lkml/2008/11/15/135)




Remember to install kerneloops  ! , its within Intrepid and Jauntys repo.

Kerneloops site for some statitics

[http://www.kerneloops.org/](http://www.kerneloops.org/)

---

### Post by Slug71 on 2008-11-18
Does anyone know yet if 2.6.28 will be in Alpha 1?

---

### Post by plun on 2008-11-18
> **Slug71 said:**
> Does anyone know yet if 2.6.28 will be in Alpha 1?

Nope, I don't think so, a new 2.6.27 kernel for Jaunty is out today.

After all "whinings" about Intrepids challenge and Intel NICs its probably just freaks which are running 2.6.28....:) 


2.6.28-RC5 is just great on my PC....   open "Kernel Next" again.

We are not running Debian... its Ubuntu !

---

### Post by andyrogers2008 on 2008-11-18
I have been brave and installed this KernelCheck, however iam getting this error in Intrepid;-


make[1]: Entering directory '/usr/src/linux-2.6.27'
Makefil:518: /usr/src/linux-2.6.27/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target '/usr/src/linux-2.6.27/arch/xen/Makefile'. Stop.
make[1]: Leaving directory 'usr/src/linux-2.6.27/
make: *** [minimul_clean] Error 2

ABORT: stage5 returned exit status 2

Anyone got any ideas?

Andy

---

### Post by plun on 2008-11-18
Yup and credits to this thread

[http://ubuntuforums.org/showpost.php?p=6047782&postcount=1084](http://ubuntuforums.org/showpost.php?p=6047782&postcount=1084)

> disabling "Paravirtualized guest support" in the configuration

I also don't need it.

The Master kernel thread is important for understanding Kernelcheck.
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)


All my settings attached.  (but its from PC to PC, user to user judge about)

**EDIT**

Kernelcheck also breaks in the end...  DRM module building but you have your deb files within **/usr/src**, 1 header and 1 image deb.

---

### Post by plun on 2008-11-21
And RC6 out

> It's been pretty quiet, and I'm hoping it will continue to be so, because 
I'm off for my yearly scuba-diving trip. And so, before I go away (no 
under-water email), here's a new -rc.

It's really CIFS and mips updates, with some updates and code movement in 
drivers/net, and simply a fair number of small fixes here and there. The 
dirstat says:

   4.8% arch/mips/rb532/
   5.3% arch/mips/
  10.9% arch/
  16.2% drivers/net/
  26.6% drivers/
  40.1% fs/cifs/
  41.8% fs/
   4.1% kernel/trace/
   6.7% kernel/
   8.0% net/

and the full diffstat has a lot of one- and two-liners spread out 
everywhere, but an excerpt from the shortlog is probably even more 
indicative of the level of exciting fixing going on:
[B]
      fbdev: clean the penguin's dirty feet[/B]   

and you guys can figure out what it's all about on your own.

We have regressions fixed (the "vmalloc fails easily" is probably the one 
that more people may actually be hitting in practice), and we have a few 
more to go, but I really hope that we'll have a quiet week, and by the 
time I come back you will all have tested it extensively and sent me fixes 
for any regressions found.

Please don't disappoint me.

			Linus

[http://lkml.org/lkml/2008/11/20/462](http://lkml.org/lkml/2008/11/20/462)




---

### Post by plun on 2008-11-27
Preview....:)

linux-image-2.6.28-1-ub-generic

Linux kernel image for version 2.6.28 on x86/x86_64

[https://lists.ubuntu.com/archives/jaunty-changes/2008-November/001218.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-November/001218.html)


Not all modules are ready.... still no meta package

---

### Post by ShirishAg75 on 2008-11-27
> **plun said:**
> Preview....:)

linux-image-2.6.28-1-ub-generic

Linux kernel image for version 2.6.28 on x86/x86_64

[https://lists.ubuntu.com/archives/jaunty-changes/2008-November/001218.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-November/001218.html)


Not all modules are ready.... still no meta package

I got the same one, I'll do a reboot once the new kernel is done (even if breakage is happening)

although point to note, nothing about ext4 still :(

---

### Post by plun on 2008-11-27
> **ShirishAg75 said:**
> I got the same one, I'll do a reboot once the new kernel is done (even if breakage is happening)

Well... wait until GTK and gnome-desktop is built, GTK was within the build process

[https://launchpad.net/ubuntu/+builds?build_text=&build_state=building](https://launchpad.net/ubuntu/+builds?build_text=&build_state=building)

---

### Post by Slug71 on 2008-11-27
> **ShirishAg75 said:**
> I got the same one, I'll do a reboot once the new kernel is done (even if breakage is happening)

although point to note, nothing about ext4 still :(

WTF! Damnit, we want Ext4! :mad:

---

### Post by klange on 2008-11-27
I'm going to take the jump and test it out. Only missing modules that should cause me problems are wifi-related.

**e**: That went a lot better than expected. Everything works fine. Now I just need a new X server...

---

### Post by plun on 2008-11-27
> **WindowsSucks said:**
> I'm going to take the jump and test it out. Only missing modules that should cause me problems are wifi-related.

**e**: That went a lot better than expected. Everything works fine. Now I just need a new X server...

Yup...I just needed to rebuild PA to 0.9.14 and everything is just fine.

I also don't need a new x-server with nVidia 180.08...:-D

---

### Post by Slug71 on 2008-11-27
Hopefully 2.6.28 will be brought in, in the next few days so i can do an install with the daily build or else ill just do a reinstall and see if i can get Kernelcheck to work.

---

### Post by plun on 2008-11-27
> **Slug71 said:**
> Hopefully 2.6.28 will be brought in, in the next few days so i can do an install with the daily build or else ill just do a reinstall and see if i can get Kernelcheck to work.

It is within Jauntys repo.... without meta package

```
plun@plun:~$ uname -a
Linux plun 2.6.28-1-ub-generic #1 SMP Wed Nov 26 19:15:48 UTC 2008 i686 GNU/Linu
```

It seems to without ext4 support...going to check it..:^o

EDIT not..

> 
/boot/config-2.6.28-1-ub-generic

# CONFIG_EXT4DEV_COMPAT is not set
CONFIG_EXT4_FS=m
CONFIG_EXT4_FS_POSIX_ACL=y
CONFIG_EXT4_FS_SECURITY=y
CONFIG_EXT4_FS_XATTR=y

---

### Post by ronacc on 2008-11-27
I installed 2.6.28-1-ub-generic ,seems to run fine , had to recompile Nvidia 180.08 ofcourse but otherwise even sound didn't mute on reboot :)

---

### Post by Slug71 on 2008-11-27
> **plun said:**
> It is within Jauntys repo.... without meta package

```
plun@plun:~$ uname -a
Linux plun 2.6.28-1-ub-generic #1 SMP Wed Nov 26 19:15:48 UTC 2008 i686 GNU/Linu
```

It seems to without ext4 support...going to check it..:^o

EDIT not..

Thanks plun, I have to do a fresh install anyways. Grub2 broke my Jaunty install but was having trouble with flash anyway. Want to do a fresh install with 2.6.28 though. Maybe when thats possible then Ext4 support will be added. Hopefully will be soon.

---

### Post by oldmanuk on 2008-11-28
does this include S2Api support for DVB-S2 yet?

---

### Post by MadsRH on 2008-11-28
Does anyone know if Kernel 2.6.29 will be shipped with 9.04? Or is it going to be 2.6.28-final?

Some say that if Ubuntu is going to use Plymouth in 9.04 we need 2.6.29, yet Fedora is running just fine without - why is that? :confused:

---

### Post by Slug71 on 2008-11-28
> **MadsRH said:**
> Does anyone know if Kernel 2.6.29 will be shipped with 9.04? Or is it going to be 2.6.28-final?

Some say that if Ubuntu is going to use Plymouth in 9.04 we need 2.6.29, yet Fedora is running just fine without - why is that? :confused:

Im almost certain 9.04 will ship with 2.6.29 but we probably wont see it until Alpha 5/6.

Fedora patched their Kernel with KMS when they were working on F-9. I think it was disabled by default when F-9 shipped though. The patch only provided very limited support for KMS too.

---

### Post by ccw on 2008-11-28
> **plun said:**
> Preview....:)

linux-image-2.6.28-1-ub-generic

Linux kernel image for version 2.6.28 on x86/x86_64

[https://lists.ubuntu.com/archives/jaunty-changes/2008-November/001218.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-November/001218.html)


Not all modules are ready.... still no meta package

Whats with the "ub" naming scheme?

---

### Post by plun on 2008-11-28
> **ccw said:**
> Whats with the "ub" naming scheme?

That we contribute to upstream.....:)

From changelog:

> Add -ub to our versioning to allow kerneloops.org to identify us



Then maybe kerneloops also should be within a developer version....:confused:   just to add it to the meta package.

---

### Post by ShirishAg75 on 2008-11-28
any idea when the meta-package is coming out?

---

### Post by plun on 2008-11-28
> **ShirishAg75 said:**
> any idea when the meta-package is coming out?

Nope....

Start Synaptic and search for linux-image and linux-headers.....

If you are using a "dirty" graphic driver it must be reinstalled.

---

### Post by DougieFresh4U on 2008-11-28
I have been away for a few days and I am wondering when will updates include the .28 kernel or do I need to install from Synaptic myself.
I had 177 updates awaiting me today upon my return and all updated well except the 'libcanberra-gtk0', I am assuming all is good.

---

### Post by Eclipse. on 2008-11-28
> **MadsRH said:**
> Does anyone know if Kernel 2.6.29 will be shipped with 9.04? Or is it going to be 2.6.28-final?

Some say that if Ubuntu is going to use Plymouth in 9.04 we need 2.6.29, yet Fedora is running just fine without - why is that? :confused:

Fedora applied the kernel mode setting patches to their kernel, so we could use the .28 kernel just be would need to apply the patches.For the .29 release the patches are being merged upstream.

---

### Post by Slug71 on 2008-11-28
> **DougieFresh4U said:**
> I have been away for a few days and I am wondering when will updates include the .28 kernel or do I need to install from Synaptic myself.
I had 177 updates awaiting me today upon my return and all updated well except the 'libcanberra-gtk0', I am assuming all is good.

Hopefully soon. I want to do a fresh install with .28 and hopefully Ext4 will be supported.

---

### Post by autocrosser on 2008-11-29
Well--.28 is in Synaptic---DKMS is having a problem with the nVidia driver---check the screenshot........

---

### Post by autocrosser on 2008-11-29
Well--rather a bummer.....28-1-ub boots, but the ralink driver that was "built" by DKMS was not loaded ---so no wireless. I had reset my xorg.conf to the nv driver, so everything else came up. Looks like DKMS has a problem with the .28 :(

Bug report time.................

See:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303357](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303357)

---

### Post by ronacc on 2008-11-29
since installing .28-1-ub  boinc seems to be pushing my CPU temp up about 10 degrees C and also the CPU cycles from min to max speed and back every few seconds and the temp cycles about 5 c in sync with the speed , no time lag instantly up and down the "base" temp slowly creeps up . with .27-x kernels the speed did not cycle up during idle and the temp stayed stable and low , I'm not sure its boinc because libsensors upgraded at about the same time but shutting bown boinc returns things to "normal" . top is not showing anything jumping up and down in cpu usage .  Any Ideas how to troubleshoot this ?

---

### Post by plun on 2008-11-29
> **ronacc said:**
> since installing .28-1-ub  boinc seems to be pushing my CPU temp up about 10 degrees C and also the CPU cycles from min to max speed and back every few seconds and the temp cycles about 5 c in sync with the speed , no time lag instantly up and down the "base" temp slowly creeps up . with .27-x kernels the speed did not cycle up during idle and the temp stayed stable and low , I'm not sure its boinc because libsensors upgraded at about the same time but shutting bown boinc returns things to "normal" . top is not showing anything jumping up and down in cpu usage .  Any Ideas how to troubleshoot this ?

Well, strange. I have reversed conditions and with 2.6.28 everything is stable for me, the GPU core temp is down 8-9 degrees

With 2.6.27 I got partial hardlocks  (Ubuntu built kernels)

Add lm-sensors applet maybe  ?   testing..:)

---

### Post by plun on 2008-11-29
> **autocrosser said:**
> Well--.28 is in Synaptic---DKMS is having a problem with the nVidia driver---check the screenshot........

If you use the 2.6.28 kernel, you must also use a driver from nVidia, I recommends 180.08

tty is also broken so you must install in recovery and the root shell or use nosplash as boot option then tty works. bug filed

Also uninstall nvidia-glx-177 and the DKMS error is gone.

---

### Post by ronacc on 2008-11-29
I think the problem may be with libsensors , I have 2 versions installed libsensors3 and libsensors4 , libsensors4 matches the lm-sensors version number that is installed but attempting to uninstall libsensors3 wants to also take out some otherstuff . also I got an error from the update of libsensors (see attached file ) , I'm also attaching my .xsession-errors for info since I am running .28-1-ub . If it is a sensors problem why does shutting down boinc "fix" it ?? Hmm had to post this from FF manage attachments locked up Opera .

---

### Post by Nullack on 2008-11-29
> **plun said:**
> If you use the 2.6.28 kernel, you must also use a driver from nVidia, I recommends 180.08

tty is also broken so you must install in recovery and the root shell or use nosplash as boot option then tty works. bug filed

Also uninstall nvidia-glx-177 and the DKMS error is gone.

Good stuff mate. Whats the bug number so I can move it along :)

---

### Post by autocrosser on 2008-11-29
I just talked to Alberto & He is on top of the DKMS issue--he is re-working the 180 driver to install with the .28 kernel.....there are patches to "make" the 178 driver work--but I have not had luck with them...His note to me:

The nvidia driver needs a patch in order to work with kernel 2.6.28. See this bug report:
[https://bugs.launchpad.net/bugs/303107](https://bugs.launchpad.net/bugs/303107)

Alberto

---

### Post by plun on 2008-11-29
> **Nullack said:**
> Good stuff mate. Whats the bug number so I can move it along :)

"The tty thing"....  all event.d scripts are changed but it can be complete wrong that it is startup and its is a kernel thing.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301737](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301737)

nosplash boot or recovery works OK....


"The driver thing"

[https://bugs.launchpad.net/bugs/297543](https://bugs.launchpad.net/bugs/297543)

"Spammed bug"....

First it was just 177.82 and then nVidia released both 180.06 and 180.08.

You must use a 180 driver otherwise you must patch it....(for kernel 2.6.28  )

---

### Post by autocrosser on 2008-11-29
> **ronacc said:**
> since installing .28-1-ub  boinc seems to be pushing my CPU temp up about 10 degrees C and also the CPU cycles from min to max speed and back every few seconds and the temp cycles about 5 c in sync with the speed , no time lag instantly up and down the "base" temp slowly creeps up . with .27-x kernels the speed did not cycle up during idle and the temp stayed stable and low , I'm not sure its boinc because libsensors upgraded at about the same time but shutting bown boinc returns things to "normal" . top is not showing anything jumping up and down in cpu usage .  Any Ideas how to troubleshoot this ?


What version of BOINC are you using?  The "short" while I had .28 up was very stable for me--temps were even lower that the .27 kernel--I'm using the latest BOINC---6.4.1--you can get it by asking for "all versions" from SETIsite...just would have to install it the way I do......there were CPU throttling issues with some of the earlier BOINC versions--I would guess that the new kernel adds to the issue.

---

### Post by autocrosser on 2008-11-29
> **Nullack said:**
> Good stuff mate. Whats the bug number so I can move it along :)

See my post at the top of the page--also Alberto sent me a link to a patch for the 178 driver--I've not had it work, but with more of us on it--it could be sorted out.

The patch & info are included......

---

### Post by plun on 2008-11-29
> **autocrosser said:**
> See my post at the top of the page--also Alberto sent me a link to a patch for the 178 driver--I've not had it work, but with more of us on it--it could be sorted out.

The patch & info are included......

There is no reason for using the 178 driver.... all major bugs are resolved with the 180 driver. Both AWN, Compiz and also KDE 4

The 180 driver also includes good stuff for users lucky to have  graphic GPU better then G90 as I understands it...

VDPAU
[http://www.nvnews.net/vbulletin/showthread.php?t=123091](http://www.nvnews.net/vbulletin/showthread.php?t=123091)

The mplayer script including patches works just fine and inside the forum there are threads about VDPAU and also Ubuntu deb packages...:) 

I am looking for a cheap better card.....:)

---

### Post by autocrosser on 2008-11-29
I know my friend---I just don't want to hand-build the 180 driver--Alberto is working at top-speed to get the 180 to us & the new kernel just threw a wrench in the works..........so using the 178 is a stop-gap til he gets things sorted.

---

### Post by ronacc on 2008-11-29
@autocrosser my boinc is 6.2.15 , if I update will it continue my projects in progress or do I need to wait until they complete ?

---

### Post by plun on 2008-11-29
> **autocrosser said:**
> I know my friend---I just don't want to hand-build the 180 driver--Alberto is working at top-speed to get the 180 to us & the new kernel just threw a wrench in the works..........so using the 178 is a stop-gap til he gets things sorted.

OK ... the VDPAU function is "hot stuff" and maybe "political sensitive"..8):???:

---

### Post by autocrosser on 2008-11-29
I've not had a problem with updating--just stop all BOINC & make sure you kill all the processes first...you may need to run the script from your /home, not from /home/Desktop to get it to install correctly.....The new 6.4.1 will kill all processes when you close the window--it's almost a RC....

---

### Post by autocrosser on 2008-11-29
> **plun said:**
> OK ... the VDPAU function is "hot stuff" and maybe "political sensitive"..8):???:

Yes--I'd really like it, but I don't want to muck about with making drivers--Instead, I've been helping Alberto as much as I can--I can wait til the official driver arrives & I've not had any driver problems with my set-up (using SLI)--helps having 1G Vram :)

---

### Post by plun on 2008-11-29
> **ronacc said:**
> I think the problem may be with libsensors , I have 2 versions installed libsensors3 and libsensors4 , libsensors4 matches the lm-sensors version number that is installed but attempting to uninstall libsensors3 wants to also take out some otherstuff . also I got an error from the update of libsensors (see attached file ) , I'm also attaching my .xsession-errors for info since I am running .28-1-ub . If it is a sensors problem why does shutting down boinc "fix" it ?? Hmm had to post this from FF manage attachments locked up Opera .

Screenlets can be a trouble maker and I installed the panel version

about sensors
```

sudo apt-get install lm-sensors sensors-applet
```

Then run sensors-detect

```
sensors-detect
```

reboot

Add your hardware applet to the panel


[IMG]http://ubuntu-pics.de/bild/6534/screenshot_07_YrpyRv.png[/IMG]


I am using the Screenlets/Sysmonitor and have changed update interval a little...

---

### Post by ronacc on 2008-11-29
ok I updated to boinc6.4.1 still the same , setting the cpu allowed in boinc preferences down to 50% helped the temp a bit but its still jumping around faster than I am willing to believe the cores can actualy change temp both up and down  inparticular I don't believe the temp can drop 10C between updates of the sensors applet even if I put an icecube on the heatsink.

---

### Post by plun on 2008-11-29
> **ronacc said:**
> ok I updated to boinc6.4.1 still the same , setting the cpu allowed in boinc preferences down to 50% helped the temp a bit but its still jumping around faster than I am willing to believe the cores can actualy change temp both up and down  inparticular I don't believe the temp can drop 10C between updates of the sensors applet even if I put an icecube on the heatsink.

I added **3 ring sensors** and **3 normal sensors** also sysmonitor running and it is a little peak in the beginning but after a few seconds eveything is normal.

Also checked with htop

Firefox 3.1 is on top with 6.9% load....  (idle)

---

### Post by autocrosser on 2008-11-29
> **ronacc said:**
> ok I updated to boinc6.4.1 still the same , setting the cpu allowed in boinc preferences down to 50% helped the temp a bit but its still jumping around faster than I am willing to believe the cores can actualy change temp both up and down  inparticular I don't believe the temp can drop 10C between updates of the sensors applet even if I put an icecube on the heatsink.

You might try Gkrellm & see what it is doing---I have used it for years & it "seems" more "real" than some of the others--takes more space, but I've always made room for it....Interesting that you are having this problem---are you AMD or Intel?

---

### Post by ronacc on 2008-11-29
I have been running the pannel applet all along not screenlets , I ran sensors-detect again and then stopped and restarted the sensors pannel applet I now have 5 core temp sensors for an AMDx2 ??? core 0,1,1,2,3 (1 shows twice) all with different temps including the two 1's I'm posting from a different box I'll post a screenshot in a minute .

---

### Post by ronacc on 2008-11-29
heres the SS

---

### Post by autocrosser on 2008-11-29
AH-HA!!! I'm running a Intel Q9300---looks like there is a "issue" with AMD----me thinks tis time for a bug report......

---

### Post by plun on 2008-11-29
> **ronacc said:**
> heres the SS

Looks like a bug....

What is the output with the sensors command  ?

```
plun@plun:~/$ sensors
w83697hf-isa-0290
Adapter: ISA adapter
VCore:       +1.47 V  (min =  +1.79 V, max =  +0.21 V)   ALARM
+3.3V:       +3.30 V  (min =  +0.58 V, max =  +2.96 V)   ALARM
+5V:         +4.92 V  (min =  +1.64 V, max =  +1.29 V)   ALARM
+12V:       +11.55 V  (min =  +9.97 V, max =  +4.20 V)   ALARM
-12V:       -11.95 V  (min =  -3.81 V, max = -14.83 V)   ALARM
-5V:         -4.90 V  (min =  -3.49 V, max =  -3.99 V)   ALARM
V5SB:        +5.56 V  (min =  +3.09 V, max =  +3.12 V)   ALARM
VBat:        +3.18 V  (min =  +0.03 V, max =  +1.18 V)   ALARM
fan1:       2909 RPM  (min =  753 RPM, div = 8)
fan2:          0 RPM  (min =  953 RPM, div = 8)  ALARM
temp1:       +41.0°C  (high = +56.0°C, hyst = +60.0°C)  sensor = thermistor
temp2:       +49.5°C  (high = +120.0°C, hyst = +120.0°C)  sensor = diode
beep_enable:enabled
```


:)

---

### Post by Gina on 2008-11-29
Interesting.  I'm running Jaunty on an AMD64X2 and didn't think the startup was that slow but I'll time it next time.  The rotating icon doesn't stop.  Also, thanks to *plun* for the temperature sensor setup info :)

---

### Post by plun on 2008-11-29
> **Gina said:**
>   Also, thanks to *plun* for the temperature sensor setup info :)

Well... maybe rather high "nerd level" :) on this but its rather useful with different kernels and graphic drivers.

Screenlets has 2 types, normal and ring sensors, but lm-sensors must work.

The applet is another solution for showing this....

---

### Post by Gina on 2008-11-29
Just tried the lm-sensors but get errors```
gina@AMD64-Jaunty:~$ sudo apt-get install lm-sensors sensors-applet
[sudo] password for gina: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  hddtemp libsensors-applet-plugin0 libsensors4
Suggested packages:
  ksensors sensord read-edid i2c-tools
The following NEW packages will be installed
  hddtemp libsensors-applet-plugin0 libsensors4 lm-sensors sensors-applet
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 373kB of archives.
After this operation, 1860kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get: 1 http://archive.ubuntu.com jaunty/universe libsensors-applet-plugin0 2.2.1-1ubuntu4 [18.9kB]
Get: 2 http://archive.ubuntu.com jaunty/main libsensors4 1:3.0.2-2ubuntu1 [65.1kB]
Get: 3 http://archive.ubuntu.com jaunty/universe sensors-applet 2.2.1-1ubuntu4 [106kB]
Get: 4 http://archive.ubuntu.com jaunty/universe hddtemp 0.3-beta15-45 [56.3kB]
Get: 5 http://archive.ubuntu.com jaunty/main lm-sensors 1:3.0.2-2ubuntu1 [126kB]
Fetched 373kB in 2s (160kB/s)     
Preconfiguring packages ...
Selecting previously deselected package libsensors-applet-plugin0.
(Reading database ... 103210 files and directories currently installed.)
Unpacking libsensors-applet-plugin0 (from .../libsensors-applet-plugin0_2.2.1-1ubuntu4_amd64.deb) ...
Selecting previously deselected package libsensors4.
Unpacking libsensors4 (from .../libsensors4_1%3a3.0.2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package sensors-applet.
Unpacking sensors-applet (from .../sensors-applet_2.2.1-1ubuntu4_amd64.deb) ...
Selecting previously deselected package hddtemp.
Unpacking hddtemp (from .../hddtemp_0.3-beta15-45_amd64.deb) ...
Selecting previously deselected package lm-sensors.
Unpacking lm-sensors (from .../lm-sensors_1%3a3.0.2-2ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up flashplugin-nonfree (10.0.12.36ubuntu1) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_10_linux.tar.gz
Flash Plugin installed.
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libuuid.so.1: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libsensors-applet-plugin0 (2.2.1-1ubuntu4) ...

Setting up libsensors4 (1:3.0.2-2ubuntu1) ...
udev active, devices will be created in /dev/.static/dev/
rm: cannot remove `i2c-0-': Read-only file system
mknod: `i2c-0-': Read-only file system
makedev i2c-0 c 89 0 root root 0600: failed
rm: cannot remove `i2c-0-': Read-only file system
rm: cannot remove `i2c-1-': Read-only file system
mknod: `i2c-1-': Read-only file system
makedev i2c-1 c 89 1 root root 0600: failed
rm: cannot remove `i2c-1-': Read-only file system
rm: cannot remove `i2c-2-': Read-only file system
mknod: `i2c-2-': Read-only file system
makedev i2c-2 c 89 2 root root 0600: failed
rm: cannot remove `i2c-2-': Read-only file system
rm: cannot remove `i2c-3-': Read-only file system
mknod: `i2c-3-': Read-only file system
makedev i2c-3 c 89 3 root root 0600: failed
rm: cannot remove `i2c-3-': Read-only file system
rm: cannot remove `i2c-4-': Read-only file system
mknod: `i2c-4-': Read-only file system
makedev i2c-4 c 89 4 root root 0600: failed
rm: cannot remove `i2c-4-': Read-only file system
rm: cannot remove `i2c-5-': Read-only file system
mknod: `i2c-5-': Read-only file system
makedev i2c-5 c 89 5 root root 0600: failed
rm: cannot remove `i2c-5-': Read-only file system
rm: cannot remove `i2c-6-': Read-only file system
mknod: `i2c-6-': Read-only file system
makedev i2c-6 c 89 6 root root 0600: failed
rm: cannot remove `i2c-6-': Read-only file system
rm: cannot remove `i2c-7-': Read-only file system
mknod: `i2c-7-': Read-only file system
makedev i2c-7 c 89 7 root root 0600: failed
rm: cannot remove `i2c-7-': Read-only file system

Creating config file /etc/sensors3.conf with new version

Setting up sensors-applet (2.2.1-1ubuntu4) ...

Setting up hddtemp (0.3-beta15-45) ...

Setting up lm-sensors (1:3.0.2-2ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Not too bothered but would have been interesting...

---

### Post by ktp on 2008-11-29
I tried to install and see the same messages about "mknod: `i2c-0-': Read-only file system". 

But in your case it seems like there is something wrong with "flashplugin-nonfree" package.  You can try removing it.

---

### Post by Gina on 2008-11-29
Thought I'd try the next stage anyway ie.```
gina@AMD64-Jaunty:~$ sudo sensors-detect

```Answered all the questions appropriately and let it install some more items and it all seemed to work - I have now added all the sensor readings to the top panel :)

This is my output from sensors :-```
gina@AMD64-Jaunty:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +124.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +24.0°C                                    
Core0 Temp:   +9.0°C                                    
Core1 Temp:  +19.0°C                                    
Core1 Temp:  +15.0°C                                    

it8716-isa-0290
Adapter: ISA adapter
VCore:       +1.10 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:        +2.48 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:       +1.86 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:         +5.67 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:        +4.80 V  (min =  +0.00 V, max = +16.32 V)   
in5:         +1.14 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +2.94 V  (min =  +0.00 V, max =  +4.08 V)   
5VSB:        +5.08 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:        +3.04 V
fan1:          0 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
temp1:       +15.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +31.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
temp3:       +25.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +1.325 V

```

---

### Post by autocrosser on 2008-11-29
Gina--I get those errors during the sensor make everytime I redo the sensors---no problem--they will be made on the next boot.....

I use a sensor setup crib sheet that still works very well--read the Install & configure text & when it talks about "sudo sensors-detect", use the script I included (remove the .doc from the end & chmod 777 it)--the script came straight from Jean Delvare @ Lmsensors--newest script available......

Cheers!!!

---

### Post by Gina on 2008-11-29
> **ktp said:**
> I tried to install and see the same messages about "mknod: `i2c-0-': Read-only file system". 

But in your case it seems like there is something wrong with "flashplugin-nonfree" package.  You can try removing it.Yes, I know there is a flash problem.  I'll try removing as you suggest and reinstalling.  Thank you :)

---

### Post by Gina on 2008-11-29
> **autocrosser said:**
> Gina--I get those errors during the sensor make everytime I redo the sensors---no problem--they will be made on the next boot.....

I use a sensor setup crib sheet that still works very well--read the Install & configure text & when it talks about "sudo sensors-detect, use the script I included (remove the .doc from the end & chmod 777 it)--the script came straight from Jean Delvare @ Lmsensors--newest script available......

Cheers!!!Thank you for that :)  I'll take a look.

---

### Post by autocrosser on 2008-11-29
I had a bear of a time setting up this EVGA 750i-FTW board--Lmsensors still has to write a sensor for the nVidia bridge--Jean helped quite a bit--I would not have half the sensor readings if not for him.........

---

### Post by ronacc on 2008-11-29
@plun  sorry it took awhile to get back to you I was out for awhile , here is the output of sensors.
```
ron@ron-desktop3:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +32.0°C                                    
Core1 Temp:  +30.0°C                                    

it8716-isa-0290
Adapter: ISA adapter
VCore:       +1.12 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:        +1.86 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:       +3.23 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:         +4.92 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:       +11.78 V  (min =  +0.00 V, max = +16.32 V)   
in5:         +3.10 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +1.10 V  (min =  +0.00 V, max =  +4.08 V)   
5VSB:        +4.92 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:        +3.01 V
fan1:       1278 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
temp1:       +31.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +34.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:       +21.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
cpu0_vid:   +0.763 V

```

---

### Post by Slug71 on 2008-11-29
> **Gina said:**
> Just tried the lm-sensors but get errors```
gina@AMD64-Jaunty:~$ sudo apt-get install lm-sensors sensors-applet
[sudo] password for gina: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  hddtemp libsensors-applet-plugin0 libsensors4
Suggested packages:
  ksensors sensord read-edid i2c-tools
The following NEW packages will be installed
  hddtemp libsensors-applet-plugin0 libsensors4 lm-sensors sensors-applet
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 373kB of archives.
After this operation, 1860kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get: 1 http://archive.ubuntu.com jaunty/universe libsensors-applet-plugin0 2.2.1-1ubuntu4 [18.9kB]
Get: 2 http://archive.ubuntu.com jaunty/main libsensors4 1:3.0.2-2ubuntu1 [65.1kB]
Get: 3 http://archive.ubuntu.com jaunty/universe sensors-applet 2.2.1-1ubuntu4 [106kB]
Get: 4 http://archive.ubuntu.com jaunty/universe hddtemp 0.3-beta15-45 [56.3kB]
Get: 5 http://archive.ubuntu.com jaunty/main lm-sensors 1:3.0.2-2ubuntu1 [126kB]
Fetched 373kB in 2s (160kB/s)     
Preconfiguring packages ...
Selecting previously deselected package libsensors-applet-plugin0.
(Reading database ... 103210 files and directories currently installed.)
Unpacking libsensors-applet-plugin0 (from .../libsensors-applet-plugin0_2.2.1-1ubuntu4_amd64.deb) ...
Selecting previously deselected package libsensors4.
Unpacking libsensors4 (from .../libsensors4_1%3a3.0.2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package sensors-applet.
Unpacking sensors-applet (from .../sensors-applet_2.2.1-1ubuntu4_amd64.deb) ...
Selecting previously deselected package hddtemp.
Unpacking hddtemp (from .../hddtemp_0.3-beta15-45_amd64.deb) ...
Selecting previously deselected package lm-sensors.
Unpacking lm-sensors (from .../lm-sensors_1%3a3.0.2-2ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up flashplugin-nonfree (10.0.12.36ubuntu1) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_10_linux.tar.gz
Flash Plugin installed.
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libuuid.so.1: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libsensors-applet-plugin0 (2.2.1-1ubuntu4) ...

Setting up libsensors4 (1:3.0.2-2ubuntu1) ...
udev active, devices will be created in /dev/.static/dev/
rm: cannot remove `i2c-0-': Read-only file system
mknod: `i2c-0-': Read-only file system
makedev i2c-0 c 89 0 root root 0600: failed
rm: cannot remove `i2c-0-': Read-only file system
rm: cannot remove `i2c-1-': Read-only file system
mknod: `i2c-1-': Read-only file system
makedev i2c-1 c 89 1 root root 0600: failed
rm: cannot remove `i2c-1-': Read-only file system
rm: cannot remove `i2c-2-': Read-only file system
mknod: `i2c-2-': Read-only file system
makedev i2c-2 c 89 2 root root 0600: failed
rm: cannot remove `i2c-2-': Read-only file system
rm: cannot remove `i2c-3-': Read-only file system
mknod: `i2c-3-': Read-only file system
makedev i2c-3 c 89 3 root root 0600: failed
rm: cannot remove `i2c-3-': Read-only file system
rm: cannot remove `i2c-4-': Read-only file system
mknod: `i2c-4-': Read-only file system
makedev i2c-4 c 89 4 root root 0600: failed
rm: cannot remove `i2c-4-': Read-only file system
rm: cannot remove `i2c-5-': Read-only file system
mknod: `i2c-5-': Read-only file system
makedev i2c-5 c 89 5 root root 0600: failed
rm: cannot remove `i2c-5-': Read-only file system
rm: cannot remove `i2c-6-': Read-only file system
mknod: `i2c-6-': Read-only file system
makedev i2c-6 c 89 6 root root 0600: failed
rm: cannot remove `i2c-6-': Read-only file system
rm: cannot remove `i2c-7-': Read-only file system
mknod: `i2c-7-': Read-only file system
makedev i2c-7 c 89 7 root root 0600: failed
rm: cannot remove `i2c-7-': Read-only file system

Creating config file /etc/sensors3.conf with new version

Setting up sensors-applet (2.2.1-1ubuntu4) ...

Setting up hddtemp (0.3-beta15-45) ...

Setting up lm-sensors (1:3.0.2-2ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Not too bothered but would have been interesting...

I've been having these same issues with flash. Tried removing and reinstalling and same thing.

---

### Post by ronacc on 2008-11-29
alot of us are getting the same error , has anyone bugged it ?

---

### Post by shirishagarwal on 2008-11-29
Hi all, 
I am the same shirish that you know previously on this thread. For some reason I'm not able to post hence using this username for now. 

I haven't installed kerneloops and neither kernelcheck but I installed it using

```
$ sudo aptitude install linux-image-2.6.28-1-ub-generic linux-image-headers-2.6.28-1-ub-generic
```

It gets stuck at updating grub.

I manually did sudo update-grub but now to do any updates I have to do dpkg --configure -a where again it tries to do /sbin/update-grub and gets stuck there.

This is the output I get when I am trying to do dpkg -configure -a stuff :-

```

$ sudo dpkg --configure -a

Setting up linux-image-2.6.28-1-generic (2.6.28.1.1) .....

Running depmod
update-initramfs: Generating /boot/initrd.img-2.6.28-1-ub-generic
Running postinst hook script
/usr/sbin/update-grub

```

After this it hangs.

Anything I can do or there is just no way out of this. I can boot in 2.6.28-1.1

As said before I'm on intel hardware and yes, the driver is buggy as told in other thread, but till I don't fix the dpkg --configure -a I can't move forward. 

I have also tried the 

```

$ sudo dpkg --configure -a --force-all 

```
method as well with the same result as above.

---

### Post by ronacc on 2008-11-29
you can manualy edit your boot stanza to boot the new kernel . everywhere it says 2.6.28-1 edit it to read 2.6.28-1-ub

---

### Post by shirishagarwal on 2008-11-29
> **ronacc said:**
> you can manualy edit your boot stanza to boot the new kernel . everywhere it says 2.6.28-1 edit it to read 2.6.28-1-ub

Hi ronacc, 
I think you mis-read me, my issue is not booting the new kernel. I can boot/use the new kernel. My issue is with apt-get or aptitude telling me to run the 'dpkg-configure-all' if I want to update/upgrade packages. 

This is my grub.cfg just so you can tell if something is missing. I dunno about what you mean by boot stanza . 

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=1000
set root=(hd0,2)
search --fs-uuid --set fc24631b-c156-4beb-bf61-be84e24bc946
if font /usr/share/grub/ascii.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set root=(hd0,2)
search --fs-uuid --set fc24631b-c156-4beb-bf61-be84e24bc946
insmod tga
if background_image /usr/share/images/grub/Windbuchencom.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
set root=(hd0,1)
search --fs-uuid --set 083eb71a-610b-45fe-b843-2acc97b088ac
menuentry "Ubuntu, linux 2.6.28-1-ub-generic" {
	linux	/vmlinuz-2.6.28-1-ub-generic root=UUID=fc24631b-c156-4beb-bf61-be84e24bc946 ro  
	initrd	/initrd.img-2.6.28-1-ub-generic
}
menuentry "Ubuntu, linux 2.6.28-1-ub-generic (single-user mode)" {
	linux	/vmlinuz-2.6.28-1-ub-generic root=UUID=fc24631b-c156-4beb-bf61-be84e24bc946 ro single 
	initrd	/initrd.img-2.6.28-1-ub-generic
}
menuentry "Ubuntu, linux 2.6.27-7-generic" {
	linux	/vmlinuz-2.6.27-7-generic root=UUID=fc24631b-c156-4beb-bf61-be84e24bc946 ro  
	initrd	/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu, linux 2.6.27-7-generic (single-user mode)" {
	linux	/vmlinuz-2.6.27-7-generic root=UUID=fc24631b-c156-4beb-bf61-be84e24bc946 ro single 
	initrd	/initrd.img-2.6.27-7-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.10, kernel 2.6.27-10-generic (on /dev/sdb5)" {
	set root=(hd1,1)
	linux /boot/vmlinuz-2.6.27-10-generic root=UUID=dcf827c4-c7cb-4d66-9cb9-7baf82a69f3c ro
	initrd /boot/initrd.img-2.6.27-10-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode) (on /dev/sdb5)" {
	set root=(hd1,1)
	linux /boot/vmlinuz-2.6.27-10-generic root=UUID=dcf827c4-c7cb-4d66-9cb9-7baf82a69f3c ro single
	initrd /boot/initrd.img-2.6.27-10-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb5)" {
	set root=(hd1,1)
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=dcf827c4-c7cb-4d66-9cb9-7baf82a69f3c ro
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb5)" {
	set root=(hd1,1)
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=dcf827c4-c7cb-4d66-9cb9-7baf82a69f3c ro single
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sdb5)" {
	set root=(hd1,1)
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

```

Just to make sure, the hd0 is the hard disk where jaunty is loaded and hd1 where Intrepid is .

---

### Post by ronacc on 2008-11-30
a boot stanza is the menuentry for a kernel , I have several installs on my test box and didn't even install grub with jaunty I just added the stanza to another grub . it may be because all the later kernels have lilo as a dependency and it needs to be configured after an update ,I just delete lilo after it gets installed and it doesn't hurt anything , why the heck they have it as a dependency when you are using grub is beyond me .

---

### Post by shirishagarwal on 2008-11-30
ah cool. My query is still stuck on is there a way to do dpkg--configure -a or do normal updates and upgrades or is my box borked (meaning needs to be reinstalled?)

---

### Post by autocrosser on 2008-11-30
Do you have more than one install on it??  If so, you can just chroot on & fix it from the outside...you could also chroot in from a LiveCD---I'll copy the chroot script I use--you would need to change it for your use.

#!/bin/bash
sudo mount --bind /dev /mnt/JJbackup/dev
sudo mount --bind /proc /mnt/JJbackup/proc
sudo mount --bind /sys /mnt/JJbackup/sys
sudo cp /etc/resolv.conf /mnt/JJbackup/etc/resolv.conf
sudo chroot /mnt/JJbackup su

My old crib sheet--use parts of it for a LiveCD chroot.......(you can see how long ago I made it ;)  ).


1. Boot up a live cd, or ubuntu from a different partition.

2. Mount your feisty drive somewhere (replace **** with name of drive, e.g. hda1 or sda2 etc.)
Code:

sudo mkdir /media/feisty sudo mount /dev/**** /media/feisty

NEW NOTE FOR INTREPID & FORWARD
open /etc/resolv.conf & copy the info from the current booted install into it--compare files first!!!!

3. chroot into your feisty drive.
Code:

sudo chroot /media/feisty su

4. Update your system via apt as normal. (sudo not required)
Code:

apt-get update apt-get upgrade apt-get dist-upgrade

5. ctrl+d or type "exit" to exit the chroot, then reboot the computer and you should be able to get back into feisty.

---

### Post by plun on 2008-11-30
> **ronacc said:**
> @plun  sorry it took awhile to get back to you I was out for awhile , here is the output of sensors.


Well, that seems to be OK....    

**sudo** sensors-detect  :confused:

Nevertheless if I boots with a 2.6.27 kernel my **GPU temp** goes up to around 60 Celcius degrees

A pure vanilla kernel, 50<51

Ubuntus 2.6.28 kernel a little higher.... around 52 degress.

CPU work is much smoother with a 2.6.28 kernel.  CPU temp always around 40. Overall the work load is much better.

---

### Post by ronacc on 2008-11-30
rerunning sudo sensors-detect makes no difference , My GPU temp is about the same as yours and stable, it is the CPU temp that I was concerned about, especialy the "jumping around" . with the .27-x kernels it stayed in the 35>40 range depending on load and fairly steady ,now it jumps allover the place from 35>50+ . I removed libsensors3 leaving only libsensors4 ,that made no difference.

---

### Post by plun on 2008-11-30
> **ronacc said:**
> rerunning sudo sensors-detect makes no difference , My GPU temp is about the same as yours and stable, it is the CPU temp that I was concerned about, especialy the "jumping around" . with the .27-x kernels it stayed in the 35>40 range depending on load and fairly steady ,now it jumps allover the place from 35>50+ . I removed libsensors3 leaving only libsensors4 ,that made no difference.

OK... got it.

There is a sensord daemon

[http://packages.ubuntu.com/jaunty/sensord](http://packages.ubuntu.com/jaunty/sensord)

About:
[http://www.lm-sensors.org/browser/lm-sensors/trunk/prog/sensord/README](http://www.lm-sensors.org/browser/lm-sensors/trunk/prog/sensord/README)

Never used it but we can probably figure out howto...:)

---

### Post by ronacc on 2008-11-30
I'm not really worried about the temps they aren't near the limits I was just noting a difference in behavior with the .28 kernel . If the CPU were really getting hot the fan would kick into "pannic mode" and sound like an overloaded helicopter :lolflag:

---

### Post by plun on 2008-11-30
> **ronacc said:**
> I'm not really worried about the temps they aren't near the limits I was just noting a difference in behavior with the .28 kernel . If the CPU were really getting hot the fan would kick into "pannic mode" and sound like an overloaded helicopter :lolflag:

Well, I don't like a CPU "unstable" kernel which goes up and down.
Maybe a sign of partial locks...

Munin is another logging tool....high "nerd level" :lolflag:
[http://www.debian-administration.org/articles/229](http://www.debian-administration.org/articles/229)

We will see if we needs it....:)

---

### Post by shirishagarwal on 2008-11-30
LOL, I'm sure you guys know the title 'much ado about nothing' . This is what happened. When I did through the live CD, and did as suggested, it turned out that the /boot was not being written . Although couldn't get the /etc/resolv.conf and update had found the culprit.

```

root@ubuntu-$ sudo dpkg --configure-a

Setting up linux-image-2.6.28-1-ub-generic (2.6.28-1.1)....
Internal Error : Could not find image (/boot/vmlinuz-2.6.28-1-ub-generic)
dpkg :- error processing linux-image-2.6.28.1-ub-generic (--- configure) :
Subprocess post installation script returned error exit status 2
Setting up linux-headers-2.6.28-1-ub (2.6.28-1.1)....
Setting up linux-headers-2.6.28-1-ub-generic (2.6.28-1.1)

Errors were encountered while processing :
linux-image-2.6.28-1-ub-generic

```

After this did the following :-

booted into 2.6.27-7-generic and did all the updates. It also configured 2.6.28-1-ub-generic and all is happy. Now to get the GUI working at some point in time. No GUI still.

---

### Post by DougieFresh4U on 2008-11-30
Last nite I put the .28 kernel on via Synaptic.
Booted ok except for some thing about the Intel and graphics, never the less it booted to working desktop. 
I still am having 100% CPU usage. When I click  open System Monitor, it's at 4% or near, but it immediatley shoots to 98% - 100%

---

### Post by shirishagarwal on 2008-11-30
That's nice to hear DougieFresh4U, would be looking out to what happens in the coming days. I don't know how can I give the output of startx. I have tried 

```

$ startx >> startx.txt

```
 
This didn't cut it. Otherwise that would have also given people a little bit more to chew. Any ideas people?

---

### Post by ronacc on 2008-11-30
@plun I do not believe the kernel is unstable , I do not even think that the temps are going up and down for real , I think it has something to do with the readings , perhaps something in libsensors4 isn't working quite right or lm-sensors , what version numbers do you have ? top or system monitor do not show anything jumping around and if I shut down boinc the CPU temps are lower by a couple of degrees than they were with the .27-x kernels .

---

### Post by plun on 2008-11-30
> **ronacc said:**
> @plun I do not believe the kernel is unstable , I do not even think that the temps are going up and down for real , I think it has something to do with the readings , perhaps something in libsensors4 isn't working quite right or lm-sensors , what version numbers do you have ? top or system monitor do not show anything jumping around and if I shut down boinc the CPU temps are lower by a couple of degrees than they were with the .27-x kernels .

Ok.. this is the bug which also hit me

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262843)

OT... found my new PC for Jaunty:lolflag:

[http://www.sweclockers.com/imagebank/200811/I7001.jpg](http://www.sweclockers.com/imagebank/200811/I7001.jpg)

Intel Core i7 Extreme, Geforce GTX 280 with trippel-SLI and Velociraptors with RAID :)

---

### Post by ronacc on 2008-11-30
what log are those blocks in ? I checked all of mine and I don't seem to have that happening , I am not running apparmour so maybe that is the problem as the bug report indicates .
OT looks nice but think twice about that lucite case , I've got one ( I fell in love with it too but alas the marriage is not as much fun as the romance).they are a real pain in the butt to work on and my local parts supplier swears that they are MB killers due to static buildup .:lolflag:

---

### Post by autocrosser on 2008-11-30
> **plun said:**
> Ok.. this is the bug which also hit me

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262843)

OT... found my new PC for Jaunty:lolflag:

[http://www.sweclockers.com/imagebank/200811/I7001.jpg](http://www.sweclockers.com/imagebank/200811/I7001.jpg)

Intel Core i7 Extreme, Geforce GTX 280 with trippel-SLI and Velociraptors with RAID :)


I LIKE it!!! Only problem would be the dust:lolflag:

I'm headed for the i7 in about 6 months or so--I'll wait til the memory/cpu/motherboard prices drop a bit :biggrin:

---

### Post by ronacc on 2008-11-30
thats why I got mine , to watch the dust bunnies mating:lolflag:

---

### Post by autocrosser on 2008-11-30
OK---really OT--give me Aluminum any time:guitar:

---

### Post by ktp on 2008-11-30
> **autocrosser said:**
> OK---really OT--give me Aluminum any time:guitar:

oh and the blue lights...now we are talking!!

---

### Post by autocrosser on 2008-11-30
MORE OT-----Specs--

Thermaltake Armour VA8003SWA Aluminum case
EVGA 750i-FTW SLI motherboard
Q9300 Quad O/C @ 3 GHZ
Two BFG 8600GT-OC 512 nVidia cards (O/C @700)--SLI in Linux!!
Four Gig OCZ DDR2 1066 SLI Ram
Three SATA W/D 500G 7200rpm drives
Raidmax RX-630ss PSU
Sony DVD SATA drive
LG Lightscribe ATA DVD drive
Zalman 9500 CPU cooler
Two Zalman Videocard coolers
Sunbeam Rheobus Extreme Fan Controller
Four 120mm Aerocool Blue LED 17db fans
One 250mm Blue LED side fan
One 80mm Blue LED ram cooler
One 60mm bridge cooler
Encore 802.11N wireless card
20-n-1 card reader (in Floppy slot)
Hanns-G 28" Widescreen Monitor

---

### Post by ronacc on 2008-11-30
that almost makes me wish I was a gamer :)

---

### Post by autocrosser on 2008-11-30
I've been playing Unreal from when the original came out---NEVER TO OLD FOR OWNAGE!!!!!!:popcorn:

---

### Post by Gina on 2008-12-01
> **autocrosser said:**
> OK---really OT--give me Aluminum any time:guitar:I too prefer an aluminium case and NOT to see the works!

---

### Post by plun on 2008-12-01
Well... more OT.  

Something for a crazy kernel...:guitar:

[http://www.sweclockers.com/imagebank/200811/Ocrig2001.jpg](http://www.sweclockers.com/imagebank/200811/Ocrig2001.jpg)

Nitrogen cooling.  :)


New world record this weekend on a Dreamhack exhibition in Sweden.

[http://www.sweclockers.com/imagebank/200811/Ocrekord001.jpg](http://www.sweclockers.com/imagebank/200811/Ocrekord001.jpg)

---

### Post by ronacc on 2008-12-01
just for info after yesterdays updates to libc6 and phonon my temps are a lot less jumpy and the jumps are less extreme about 1>2 c instead of 10 c . ant the mean temp is about where it used to be ~40 c . why the heck libc6 or phonon would affect it I dont know .

---

### Post by Slug71 on 2008-12-02
And RC7 is out.

---

### Post by plun on 2008-12-02
> **Slug71 said:**
> And RC7 is out.

Yup.... and our kernel hackers was also fast...

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001475.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001475.html)

Lets hope also for a meta package...;)

---

### Post by shirishagarwal on 2008-12-02
yup, and the builds have started building 

[https://launchpad.net/ubuntu/+builds](https://launchpad.net/ubuntu/+builds)

---

### Post by Slug71 on 2008-12-02
Nice, hope it all works out as i cannot use the .28 Kernel at the moment as i have no wireless with it.

---

### Post by shirishagarwal on 2008-12-02
For linux-restricted-modules missing dependencies linux-headers-2.6.28-2-generic

[https://edge.launchpad.net/ubuntu/+source/linux-restricted-modules/2.6.28-2.1/+build/803036/+files/buildlog_ubuntu-jaunty-i386.linux-restricted-modules_2.6.28-2.1_MANUALDEPWAIT.txt.gz](https://edge.launchpad.net/ubuntu/+source/linux-restricted-modules/2.6.28-2.1/+build/803036/+files/buildlog_ubuntu-jaunty-i386.linux-restricted-modules_2.6.28-2.1_MANUALDEPWAIT.txt.gz)

The kernel has been built 

[FULLYBUILT]   	 i386 build of linux 2.6.28-2.2 in ubuntu jaunty RELEASE
Build started 9 hours ago on palmer (i386) and finished 6 hours ago taking 2 hours 30 minutes &#8212; see the log 

[http://launchpadlibrarian.net/20147393/buildlog_ubuntu-jaunty-i386.linux_2.6.28-2.2_FULLYBUILT.txt.gz](http://launchpadlibrarian.net/20147393/buildlog_ubuntu-jaunty-i386.linux_2.6.28-2.2_FULLYBUILT.txt.gz)

Can't find the linux-headers-2.6.28-2 and that is a dependancy wait for linux-restricted-modules, otherwise there is a possibility of getting a metapackage happening . 

If anybody comes to know something more, please post here.

---

### Post by plun on 2008-12-03
Just installed ub-2, image and headers......  restarts..):P

EDIT works OK....

---

### Post by shirishagarwal on 2008-12-03
you were able to get the headers, image and restricted-modules all the three?

---

### Post by plun on 2008-12-03
> **shirishagarwal said:**
> you were able to get the headers, image and restricted-modules all the three?

The only thing I uses which is restricted is the nVidia driver and it can be installed without restricted modules.

Start Synaptic and search for  **linux-image, linux-headers** and also linux-restricted for a check.

I have restricted modules for the 2.6.27 kernel installed.

---

### Post by shirishagarwal on 2008-12-03
got it, didn't know linux-headers had been built. They did what was promised, although something about cramfs and vfs not right while updating grub but that's another story.

---

### Post by DougieFresh4U on 2008-12-03
> **plun said:**
> Just installed ub-2, image and headers......  restarts..):P

EDIT works OK....
+1
Boots, but still have the 'low graphics mode'

---

### Post by ronacc on 2008-12-03
up and running here too with ub-2 .

---

### Post by andersk on 2008-12-04
For linux-restricted-modules-2.6.28, the current package won’t build; see [**LP #305047**]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/305047").  I have working linux-restricted-modules-2.6.28 packages in [**my PPA**]("https://launchpad.net/~anders-kaseorg/+archive").  I also have packages for the nvidia beta 180.08 driver that work on 2.6.28.

---

### Post by DougieFresh4U on 2008-12-04
> **andersk said:**
> For linux-restricted-modules-2.6.28, the current package won&#8217;t build; see [**LP #305047**]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/305047").  I have working linux-restricted-modules-2.6.28 packages in [**my PPA**]("https://launchpad.net/~anders-kaseorg/+archive").  I also have packages for the nvidia beta 180.08 driver that work on 2.6.28.

I thank you for your work
I used your PPA and when finished in terminal I got the following message
[B]```
Get:1 http://ppa.launchpad.net jaunty/main linux-restricted-modules-common 2.6.28-2.2~andersk1 [10.3kB]
Fetched 10.3kB in 0s (20.4kB/s)                        
(Reading database ... 234140 files and directories currently installed.)
Preparing to replace linux-restricted-modules-common 2.6.27-7.12 (using .../linux-restricted-modules-common_2.6.28-2.2~andersk1_all.deb) ...
Unpacking replacement linux-restricted-modules-common ...
Setting up linux-restricted-modules-common (2.6.28-2.2~andersk1) ...
update-rc.d: warning: /etc/init.d/linux-restricted-modules-common missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>

```[/B]

This is not the first time I have seen this messege. Please, what does it mean and how do I correct it? Would that no good Intel graphics have any thing to do with this messege?
Thanks

---

### Post by shirishagarwal on 2008-12-04
DougieFresh4U, LSB stands for Linux Standards Base 
[http://www.linux-foundation.org/en/LSB](http://www.linux-foundation.org/en/LSB) should be a good starting point on the subject. 

The dependancy-based booting initscripts are ones which help do stuff like

```

$ /etc/init.d/boinc-client status
* Status of BOINC core client: running.

```

I for one would love to see this being used and followed more.

It is usually installed by default. 

```

$ aptitude show lsb-core
Package: lsb-core
State: not installed
Version: 3.2-14ubuntu2
Priority: extra
Section: misc
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 180k
Depends: lsb-release, libc6 (> 2.3.5), libz1, postfix | mail-transport-agent, at, bc, binutils, bsdmainutils,
         bsdutils, cpio, cron, ed, file, libc6-dev | libc-dev, locales, lpr, lprng | cupsys-client, m4, mailx |
         mailutils, make, man-db, mawk | gawk, ncurses-term, passwd, patch, pax, procps, psmisc, rsync, alien (>=
         8.36), python, python-central (>= 0.6.7), debconf (>= 0.5) | debconf-2.0, lsb-base
Conflicts: lsb (< 2.0-2)
Replaces: lsb (< 2.0-2)
Provides: lsb-core-ia32, lsb-core-noarch
Description: Linux Standard Base 3.2 core support package
 The Linux Standard Base (http://www.linuxbase.org/) is a standard core system that third-party applications
 written for Linux can depend upon. 
 
 This package provides an implementation of the core of version 3.2 of the Linux Standard Base for Debian on the
 Intel x86, Intel ia64 (Itanium), IBM S390, and PowerPC 32-bit architectures with the Linux kernel. Future
 revisions of the specification and this package may support the LSB on additional architectures and kernels. 
 
 The intent of this package is to provide a best current practice way of installing and running LSB packages on
 Debian GNU/Linux. Its presence does not imply that Debian fully complies with the Linux Standard Base, and should
 not be construed as a statement that Debian is LSB-compliant.
Homepage: http://www.linux-foundation.org/en/LSB

```

Comments, suggestions and improvements to the same are welcome.

---

### Post by DougieFresh4U on 2008-12-04
> **shirishagarwal said:**
> DougieFresh4U, LSB stands for Linux Standards Base 
[http://www.linux-foundation.org/en/LSB](http://www.linux-foundation.org/en/LSB) should be a good starting point on the subject. 

The dependancy-based booting initscripts are ones which help do stuff like

```

$ /etc/init.d/boinc-client status
* Status of BOINC core client: running.

```

I for one would love to see this being used and followed more.

Therefore, it is not some thing I need be concerned with and nothing is broken, correct??

---

### Post by shirishagarwal on 2008-12-04
Don't think so, btw expect 2.6.28-2.3 within 24 hours. 

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001546.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001546.html)

Its in pending in the build list atm.

---

### Post by shirishagarwal on 2008-12-04
With the newest updates, the 2.6.28-1-ub-generic are obsolete. Although couldn't remove them properly, can somebody help me and see what was I doing wrong. 

```

$ sudo aptitude purge linux-image-2.6.28-1-ub-generic linux-headers-2.6.28-1-ub-generic

```

while the headers got removed/purged the image itself didn't. 

```

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
Failed to process /etc/kernel/prerm.d at /var/lib/dpkg/info/linux-image-2.6.28-1-ub-generic.prerm line 267.
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

All and any help, suggestions would be welcome.

---

### Post by plun on 2008-12-05
> **shirishagarwal said:**
> With the newest updates, the 2.6.28-1-ub-generic are obsolete. Although couldn't remove them properly, can somebody help me and see what was I doing wrong. 

All and any help, suggestions would be welcome.

I have no clue and I am always using Synaptic for kernel removals....

linux-image  > right click, "Mark for complete removal" for one image


I also saw this upgrade for DKMS....maybe it "tricked" aptitude ?
[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001540.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001540.html)

---

### Post by Slug71 on 2008-12-10
And RC-8 is out. :)

---

### Post by plun on 2008-12-11
> **Slug71 said:**
> And RC-8 is out. :)

Yes it is....  Linus got a challenge when to release 2.6.28 and then start with 2.6.29...

> Nothing overly exciting here. Lots of small things, mostly in drivers 
(with some defconfig updates for m68k and mips making the diffs bigger). 

There's some uncomfortably big changes to the intel DRI code, but most of 
that is all about fixes to the new i916 "GEM" code that is only used by 
development X servers, and is a new feature, so it shouldn't be able to 
cause regressions.

Perhaps more interesting is simply the release scheduling issue. I'm 
getting slowly ready to do a real 2.6.28, but I don't think anybody really 
wants the merge window to be around the holidays. So the question is 
really whether to 

 (a) just make the -rc's go on a few more weeks, and do 2.6.28 after xmas

     I like this, because alledgely people are debugging things, and we'd 
     get a more stable 2.6.28.

or

 (b) release in a week or two, but just allow for possibly extending the 
     merge window due to people being drunk on eggnog..

     I like this because let's face it, we get more and better bug 
     information after releases, and everything _should_ be ready for 
     merging *before* the merge window anyway.

or

 (c) some other crazy scheme that somebody comes up with in a drug-induced 
     stupor.

So I haven't quite decided on that thing yet, but I'm open to suggestions. 

			Linus

[http://lkml.org/lkml/2008/12/10/410](http://lkml.org/lkml/2008/12/10/410)



---

### Post by ShirishAg75 on 2008-12-12
And it has been rebased pretty quickly atleast on i386 

[https://launchpad.net/ubuntu/+source/linux/2.6.28-3.4](https://launchpad.net/ubuntu/+source/linux/2.6.28-3.4)

```

linux (2.6.28-3.4) jaunty; urgency=low

  [ Tim Gardner ]

  * Build ecryptfs into the kernel
    - LP: #302870
  * Deprecated gnbd

  [ Upstream Kernel Changes ]

 ** * Rebased to v2.6.28-rc8**

```

---

