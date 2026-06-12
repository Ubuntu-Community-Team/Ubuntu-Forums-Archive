---
title: "Why isn't my LiveUSB persistent"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by Vinze on 2007-04-29
**ANOTHER UPDATE:** The problem concerned Feisty, if you want to put Gutsy or anything non-Feisty on a USB drive you can follow the normal guide at [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

**UPDATE:** My problem (a bug in Feisty) is now solved (or rather: worked around). Instructions on how to do this yourself with Ubuntu Feisty can be found [here](http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/) on my blog. Or if you'd rather use Xubuntu, I also have [this guide](http://xubuntublog.wordpress.com/2007/07/03/xubuntu-feisty-now-from-usb-drive/).

Hey, I followed [these instructions](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar) (fairly similar to [these](https://wiki.ubuntu.com/LiveUsbPendrivePersistent), but geared towards Feisty) to put Ubuntu on my USB drive. I finally managed to get it working, it booted and all, but after I rebooted I noticed that everything I had configured and installed was gone! Same when I tried it later with Xubuntu.

Why? I've properly named the partition casper-rw :(

---

### Post by daristia on 2007-05-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You may want to look here:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591)

It's a known bug, hopefully it will be fixed soon. Meanwhile, you can use a former version.

Daniel

---

### Post by Vinze on 2007-05-02
> **daristia said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You may want to look here:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591)

It's a known bug, hopefully it will be fixed soon. Meanwhile, you can use a former version.

Daniel

Lol, I had [already found it](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591/comments/12).

Of what should I use a former version? Casper?

---

### Post by daristia on 2007-05-02
No, a former version of Ubuntu; 6.10 is supposed to work.

---

### Post by Vinze on 2007-05-02
> **daristia said:**
> No, a former version of Ubuntu; 6.10 is supposed to work.

Right, I'll try with Feisty Herd 4 when I have the time, thanks :D

---

### Post by calinb on 2007-05-20
I think the reason persistence is not working in 7.04 may be due to a Unionfs / kernel version incompatibility.  As I reported on the bug listing, persistence works okay when vmlinuz and initrd.gz are copied from a 6.10 liveCD to the USB stick.  Other things break, however.

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591)

I read the Unionfs notes in the kernel source.
```
sudo apt-get install linux-source-2.6.20
```
Check out the notes in linux-source-2.6.20/ubuntu/fs/unionfs (or /usr/src/linux/ubuntu/fs/unionfs, if you've already setup a sym link to build the kernel).

Study the "README," "NEWS," and "INSTALL" files.

README: *"This Unionfs release supports only one 2.6 kernel version (run 'make kvers' to find out which)."*

NEWS:  [i]* Unionfs 1.3 (intended for use with 2.6.17)
- Fixed makefile release & build target
- Fixed up uniondbg & unionimap man pages
- Updated RPM specfile
- Implemented export functions (for NFS)
- Updated to compile with 2.6.17[/i]

Gee--persistence works when I hack the 6.10 kernel into the USB stick and which kernel does 6.10 use?  It uses 2.6.17!  That's a match with Unionfs 1.3.  However, 7.04 uses 2.6.20 and it appears to be incompatible with Unionfs 1.3.  I see no indication that the module has been patched for 2.6.20.  No wonder unionfs won't load on 7.04.

The compatibility table at
[http://www.fsl.cs.sunysb.edu/project-unionfs.html](http://www.fsl.cs.sunysb.edu/project-unionfs.html)

also pairs 1.3 with the 2.6.17 kernels and indicates the correct stable unionfs code for 2.6.20 kernels is Unionfs version 2.0, 2.6.20-u1.

From the Unionfs INSTALL file:
[i]"You should be able to just type "make" and Unionfs will build itself for the
running kernel.  The Makefile will look for your running kernel sources in
/lib/modules/`uname -r`/build/include."[/i]

So maybe we can use the 6.10 hack to get persistence working and build a Unionfs version 2.0, 2.6.20-u1 module using source downloaded from the Unionfs website.  Once the new Unionfs module is built and installed, we can switch back the the 7.04 / 2.6.20 kernel.  Of course this is still somewhat of a hack and the right way to do it would be to create a new live CD / USB stick with the correct Unionfs module, rather than relying on casper-rw to carry it, but I don't know how to build a new liveCD yet.

From what I've seen, networking may not work during a build with the hacked-in 2.6.17 kernel so a possible workflow might be something like the following, but I've not had time to try the method.

1.  Boot 7.04 (either USB or live CD) and download the Unionfs source and Ubuntu kernel source to a hard disk.  Actually, it might be a good idea to download everything you need to build the kernel and save the .deb files to the hard disk too.  Don't use FAT for kernel builds.  You may run into problems later.  It's probably best to put the kernel source on the hard disk and setup the /usr/src/linux symlink to the hard disk and go ahead and build a kernel--just to make sure you're got all the .deb files you'll need later.  Save the .deb files from the cache.  Put everything on the hard disk because it will probably fill your USB stick if you expand the sources there.  Keep in mind that persistence is not yet working.  Everything must be on the hard disk for later use.  In general follow the guide:

[http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel+build](http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel+build)

but don't use vanilla sources.  Just use the sources from apt-get install linux-source-2.6.20 and copy /boot/config-2.6.20-15-generic from the 7.04 CD to .config.

2. Copy vmlinz and initrd.gz from a 6.10 CD to /usb and /usb/casper on a fresh 7.04 USB stick.

3.  Boot the hacked USB stick.  Persistence should now be working (but many other things may be broker.) Hopefully, enough stuff is working to build a new unionfs module. 

4.  Install all the .deb packages that you previously saved to the hard disk.

5.  Point the unionfs build to the 2.6.20 kernel source on the hard disk, as described in the INSTALL notes.  It should not be necessary to actually build the entire kernel. I only recommended building the kernel in step 1 to make sure we have all the packages that are needed for a complete kernel build environment but who knows?  It may be necessary to actually build a new kernel but I don't really know how to do a build for the live CD. Obviously it would be a good idea to copy the config file from /boot and re-use it.  

Wow--I could've done all that in the time it took to type it.  Nevertheless, it would be good to have others working on it because I think there will be a few hurdles to overcome.

Let's use this thread to post progress.

Thanks,

-Cal

---

### Post by calinb on 2007-05-20
Update:

It's not as easy as the Unionfs 1.3 notes, contained in the Ubuntu kernel source, indicate.  For 2.0, you will git the entire 2.6.22 kernel tree when you download the Unionfs source.  There's no mention of building unionfs modules into an operating kernel.  It seems you must merge the unionfs/fs... branch you downloaded into /usr/src/linux/ubunbu/fs... and probably merge some .h files elsewhere (I moved some around before I got the unionfs patch installed correctly).  You must apply the unionfs linux-2.6.20-u1.diff patch to patch the kernel tree back to Feisty's 2.6.20 kernel.  Presumably this is how to proceed.

The build is proceeding under a stock 7.04 live boot (no persistence).  Even if it completes, I have no idea if I can just reboot to a hacked 7.04/6.10  live USB (to enable persistence) and install the resulting deb packages from the build, rename the initrd and kernel files and copy them to /usb and /usb/casper.

I also have a strong speculative notion that an Ubuntu dev was here before me, had problems with unionfs, and gave up to meet the release schedule.  The old unionfs files were simply left on the distro.  Until unionfs makes it into the kernel.org linux kernel, I suspect it's a maintenance nightmare for any distro and I can certainly sympathize if that's what happend, or something similar.

-Cal

P.S.  Wow, I'm on to quickcam module in my build:

..
..
  CC [M]  ubuntu/media/quickcam/qc-vv6410.o
  CC [M]  ubuntu/media/quickcam/qc-formats.o
..
..
maybe this thing will at least complete! :)

---

### Post by calinb on 2007-05-20
One more thing...

We could wait until Unionfs version 1.x (legacy code) is released.  Version 1 is what Ubuntu uses.  The Unionfs site says, *"2.6.20 	N/A (1.6 coming soon"*

Of course Ubuntu will be probably be down the road at 2.6.22+ by then.  Maybe Ubuntu will intercept Unionfs 2 in the next release.

-Cal

---

### Post by jerrylamos on 2007-05-20
> **calinb said:**
> Update:

I also have a strong speculative notion that an Ubuntu dev was here before me, had problems with unionfs, and gave up to meet the release schedule.  The old unionfs files were simply left on the distro.  Until unionfs makes it into the kernel.org linux kernel, I suspect it's a maintenance nightmare for any distro and I can certainly sympathize if that's what happened, or something similar.

 :)

Yep, one of the key developers tried just before 2007-04-15  to do a fix and left some changes in:

" Colin Watson  said on 2007-04-12:  (permalink)

I tried as hard as I could to fix this, but I couldn't get it to work for me so couldn't recommend an upload; at this point I'm afraid it's post-feisty. The fixes I attempted are in the main Ubuntu casper bzr branch if anyone wants to try them out.

(Specifically, while my fixes correct the casper-rw label handling, the USB device still doesn't appear until somewhere just shortly after the attempt to detect casper-rw devices. Adding udevtrigger/udevsettle didn't help.)"

It looked to me at the time that the USB device was getting recognized later than it had in 6.10, likely because of the Feisty very slow very complex SCSI simulation of SATA, IDE, CD's, USB, Floppy, and who knows what else.  I would have no idea how to delay the "attempt to detect casper-rw devices" until the SCSI simulation has finally got the USB device to appear, since udevsettle didn't work for Colin.

Cheers, Jerry

---

### Post by calinb on 2007-05-20
Thanks, Jerry.  I'll try to find time to look at the fixes Colin attempted--especially since my first attempt at building Unionfs 2.0 has failed:

root@ubuntu:/usr/src/linux# make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image
...
...
...
WARNING blah blah blah
...
WARNING blah blah blah
...
WARNING: vmlinux - Section mismatch: reference to .init.text: from .text between 'iret_exc' (at offset 0xc02f2220) and '_etext'
WARNING: vmlinux - Section mismatch: reference to .init.text:start_kernel from .paravirtprobe between '__start_paravirtprobe' (at offset 0xc03c2790) and '__stop_paravirtprobe'
WARNING: "drop_pagecache_sb" [ubuntu/fs/unionfs/unionfs.ko] undefined!
WARNING: "pathget" [ubuntu/fs/unionfs/unionfs.ko] undefined!
WARNING: "pathput" [ubuntu/fs/unionfs/unionfs.ko] undefined!
WARNING: "krealloc" [ubuntu/fs/unionfs/unionfs.ko] undefined!
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/mnt/sdc1/linux-source-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2

Looks like it might be path problem as unionfs in the 2.6.20 Ubuntu source tree is under /usr/src/linux/ubuntu/fs/... but the unionfs 2.0 kernel.org fork is at /usr/src/linux/fs/...

Someone more adept at building kernels than I might know better.

-Cal

---

### Post by mjpca on 2007-05-21
Interesting Cal.  Makes sense.  That obviously would explain why the same squashed file system worked with the Herd3 iso files, but not with the Feisty Final iso files.

When fully booted up with my custom squashed filesystem, and running uname -r, it does show that the linux kernal is 2.6.20-6-generic, and persistence is working on that system.  So, it appears you can use the 2.6.20 kernel in the squashed filesystem, so long as the vmlinuz kernel file contains the older kernel.

I don't fully understand how the boot up process works, but that may also make sense.  Maybe, when booting, the ram disk uses the vmlinuz kernel file and the persistent kernel parameter is provided to that kernel.  Maybe that happens before the squashed filesystem is loaded and, as a result, determines whether persistence will work or not.  I.e. if "persistence" is passed to the older kernel, persistence works even if the squashed filesystem uses the newer kernel

Any thoughts on that?  On my system, uname -r definitely shows that I have the 2.6.20 kernel when fully booted, and persistence is working.  So, seems like something like the foregoing may be happening.  But, I'd be interested in any other explanations.

Mike

---

### Post by mjpca on 2007-05-21
Maybe that distinction could help in creating a hybrid image that avoids some of the errors of just changing vmlinuz.

---

### Post by calinb on 2007-05-21
> **mjpca said:**
> When fully booted up with my custom squashed filesystem, and running uname -r, it does show that the linux kernal is 2.6.20-6-generic, and persistence is working on that system.  So, it appears you can use the 2.6.20 kernel in the squashed filesystem, so long as the vmlinuz kernel file contains the older kernel.
Mike, Are you saying that persistence works with your custom squashed filesystem and 2.6.20-6-generic using the older 6.10 vmlinuz to boot?  You're not seeing any of the other failures with this combination?
> **mjpca said:**
> 
I don't fully understand how the boot up process works, but that may also make sense.  Maybe, when booting, the ram disk uses the vmlinuz kernel file and the persistent kernel parameter is provided to that kernel.  Maybe that happens before the squashed filesystem is loaded and, as a result, determines whether persistence will work or not.  I.e. if "persistence" is passed to the older kernel, persistence works even if the squashed filesystem uses the newer kernel

Yes, I'm no expert on live CD/USB configuration but that sounds right to me.  Syslinux (or other boot loader) passes the persistent kernel parameter to vmlinuz.  It seems like the older unionfs module (1.3) must be getting loaded by the older vmlinuz, based on your report, but it also appears to remain loaded and functional after the squashed filesystem is loaded.

I need to study the boot process and also study Colin Watson's notes on his work with unionfs 1.3 and the 7.04 release.  If you confirm your setup is per the above, I'd like to attempt to duplicate it.

-Cal

---

### Post by mjpca on 2007-05-21
Yes, that's essentially my setup.  Squashed filesystem uses the 2.6.20 kernel, but vmlinuz is from, in my case, the Herd3 iso rather than the 6.10 vmlinuz.  Under that setup, persistence seems to work, although with further testing it may be intermittent (maybe due to the errors I mention below).  My squashed filesystem contains the latest feisty files for everything except for those files that were "pinned" by the "preferences" file I attached to the bug report or that were "held back" because of the pinned files.  So, among the upgraded files, the kernel upgraded to the most recent kernel in the squashed fs (obviously without affecting vmlinuz).

When you say I am not getting any of the other errors, I am not exactly sure what errors you mean, but having had a chance to test it further, I do get errors as well.  In terms of severity, I don't know how they compare to the errors you have seen.   I guess I'd say my setup still falls within the "dirty hack" category, though.  E.g. I get a number of errors when shutting down which look like errors writing to the casper-rw partition (don't know if that could be related to the issue that you flagged, but maybe).  Also, while I again haven't tested my setup sufficiently to know for sure, it seems that these shutdown errors may be causing peristence to work somewhat intermittently.  That seems odd to me (seems like it would either work or not work at all), but that may be what I am experiencing.

Honestly, when I saw your post, my reaction was that you were probably dead on as far as the unionfs issue, but also that there may be some unrelated scripting issues that contribute to the breakage (which may be helped by pinning certain files in the manner I have done).  In particular, I'd have to go back and look at it again, but I am not sure Colin's changes were directed at the unionfs issue that you flagged, but rather were directed at some unrelated scripting issues.  If Colin's changes otherwise completely fix those scripting issues, and if they are unrelated to the unionfs issue, it may be a matter of still having the unionfs issue left to resolve.

I guess if that is the case, haivng thought through this further, it may not be possible to come up with a reliable solution until that issue is fixed.  I don't know because I don't know enough about how the system uses unionfs on shutdown.  But, maybe that will be the case.

---

### Post by calinb on 2007-05-22
> **mjpca said:**
> I guess if that is the case, haivng thought through this further, it may not be possible to come up with a reliable solution until that issue is fixed.  I don't know because I don't know enough about how the system uses unionfs on shutdown.  But, maybe that will be the case.haha--I think you and I could fix this, if we quit our day jobs!  To fix it properly for Feisty, I think we'd need to study the scripts to understand the interactions with unionfs, and then port unionfs 2.0 (at least until they release 1.x for 2.6.20 kernels) and learn how to "author" a live CD.  I'd probably use one of the other distros as a learning vehicle too--one that's more into customization of live CDs, like Knoppix or some spin-off.  I'd love to do it, but I'm stuck in a job doing high speed computer interfaces signal integrity and don't have much time to play.  <sigh> Kernel development would be so much more fun!  All in all, 6.10 works and it's plenty good for my live USB needs, but I hate to see a such an obvious bug, crawling about. ;)  

-Cal

---

### Post by mjpca on 2007-05-22
Funny.  I think you are right.  

Would be fun, but where to find the time . . . .

---

### Post by Vinze on 2007-05-22
Well, even if you guys cannot find the time, I'd still like to thank you for all the time you've already put in, it's really appreciated.

---

### Post by EagleRock on 2007-05-28
First off, I'd like to also thank cal and mike for all the work they did on this, as it is most definitely appreciated.  One's time is precious, especially when you're working, so I understand completely that you don't have the time to battle through this.

That being said, I am looking forward to fixing this issue, as it is something I really want to do with Ubuntu.  I plan on using the USB as a personal "get away from Windows" install and to showcase Linux to others to show them their alternatives.  I was able to replicate the issue with my Cruzer Micro 2.0GB drive (with ext3 as the capser_rw partition).

I don't know who is working on this at this point, but I'd be glad to help out with any testing or reporting that's necessary, as I don't think I have the skills to be at the forefront of this bugfix.  However, I am familiar with kernel recompiles and building apps, so I might be of some use.  I didn't want to use Edgy for my USB persistent install, so I will leave my USB drive as is to keep it available for this fix.

Thanks again for everyone's work so far, and I hope I can help out however I can to get this issue fixed.

---

### Post by mjpca on 2007-05-29
Looks like there is a unionfs patch for the 2.6.20 kernel at this link.  The patch looks pretty long.  Don't know if this would help/work or even if it would be appropriate for the Feisty distribution.

[http://iphitus.loudas.com/beyond/2.6.20/2.6.20-beyond2/patches/](http://iphitus.loudas.com/beyond/2.6.20/2.6.20-beyond2/patches/)

---

### Post by EagleRock on 2007-05-30
Good find, Mike!

I took a quick look at the patch myself, but it's doing something I'm not familiar with.  It looks like it's comparing versions and writing the updated code to the necessary source, but I can't figure it out.  For example: 

```
diff --git a/Documentation/filesystems/00-INDEX b/Documentation/filesystems/00-INDEX
```

...refers to two a/Documentation and b/Documentation, but I don't quite grasp where "a" and "b" are.  The only thing I can think of is when you run the patch, it is passed a and b from either the person running the file or the update program.

The site this patch is from is dedicated to a discontinued patch project for ArchLinux, so I don't think the patch itself will help.  The code in the patch might help one of the Ubuntu developers find the issue and fix it, but I don't think I will be able to do anything with it.  :-(

I really wish I could help out more with this, but I never got to using Linux on a daily basis, though this will change soon (especially once this issue is fixed :-) ).  In the meantime, I hope the person assigned to this bug comes along soon, 'cause I noticed this is holding back quite a few Ubuntu users.

In the meantime, I was looking to test workarounds to see if I can get a relatively clean fix.  Cal seemed quite unhappy with his workaround that he mentioned here, and didn't know where I should start.

---

### Post by Vinze on 2007-05-31
I was wondering, as the first Gutsy alpha release (what was its name again?) would it be possible that persistence would work with that one? Probably not, right?

---

### Post by EagleRock on 2007-05-31
It depends on the version of the kernel being used for Gutsy as well as the version of UnionFS that is included in the LiveCD.  If they have upgraded to UnionFS version 2 in the Gutsy release, then persistence should work.  In the meantime, I'm trying to test workarounds to see if I can't get Feisty working with persistence.  However, depending on the person assigned to this bug, we may have to wait for Gutsy for persistence again.

---

### Post by mjpca on 2007-06-01
I was playing around with edgy a bit.  It looks like I get exactly the same errors with edgy as I was getting with my modified Feisty setup (the setup in which I started with Herd3 and modified the squashed filesystem).  It might be that the errors I am experiencing are an issue with my usb drive, rather than an issue with the approach I took.  It probably would be worth someone taking the time to try the approach I outlined in the launchpad bug posting (using the preferences file that I posted there), and seeing what sort of results someone else gets.  Maybe that approach works better than I thought.  Hard for me to confirm because I may have an issue with my usb drive.

As far as Gutsy, I scanned through some of the postings regarding the planned changes, and I saw something that suggested that they may be considering moving to aufs.  Not sure how big of a change that is (e.g. whether aufs would properly execute unionfs scripts - that may be unlikely).  I.e. it may take some work to switch to aufs if they are going to do that.

There were also comments regarding e.g. a possible udev bug, the cdrom mount functionality not working properly, and the need to finish integrating Debian changes that were not integrated in Feisty.  

I guess it is possible, but I would be surprised if the first Gutsy alpha fixed the issue.

---

### Post by EagleRock on 2007-06-01
Mike,

That's certainly good news to hear.  I will try to follow your footsteps and see if the fix is good.  I don't have a working Ubuntu setup at home yet, so I will have to try this on my work PC.

Only one question:  Where can I get a Herd3 LiveCD to start this off?

Thanks,

Peter

---

### Post by mjpca on 2007-06-03
Peter,

My next post is a preferences file that I have used to "pin" the relevant packages starting with Edgy.  You can use this, starting with edgy rather than herd3 of feisty.  I tried to attach this to my message, but received an upload error for some reason.  So, I included it as a separate post.  I have also included in my next post the sources.list that I used.

In the sources.list file, because I start with Edgy, I change all "feisty" references to "edgy."  

When I chroot into the system that I am customizing, I use "sudo aptitude update" followed by "sudo aptitude upgrade" to get the latest version of all of the edgy files (when the sources.list file is refers to the edgy repositories).  It will tell you that some files are being held back.  It might even say a couple of the packages are broken, but try that anyway.

After that, I change all "edgy" references in the sources.list to "feisty" and run "sudo aptitude dist-upgrade."  Every time I do this, I run into a "acpid" error, saying that it cannot configure a variety of files because a device or resource is busy, or something to that effect.  To get around this, I actually have to shut down and then reboot.  This time, when I chroot into the customized system, I omit the the following step:

                sudo mount -t proc -o bind /proc $WORK/new/proc

I then, in the chrooted enviroment, run "sudo apt-get install -f".  That seems to configure the remaining packages.  I haven't found another way around this acpid error.  There are a few "solutions" posted, but they didn't work for me.

I am using an edgy-feisty hybrid system now.  Again, persistence seems to be working, but we'll see how it goes.  One difference I experienced starting edgy, rather than the herd 3 of feisty, is that the system does not seem to hang on the message "unmounting temporary filesystems . . . ." when shutting down.  It actually seems to shut down properly.  I wasn't sure if the system was hanging when I shut down the herd 3 hybrid, but I think it was and wonder if that may be why I was experiencing the errors.  In any event, I am going to try this hybrid edgy-feisty system and see how it goes.

---

### Post by mjpca on 2007-06-03
Here's the preferences file.  Cut and past this into a file called "preferences" that you put in the "/etc/apt" directory.  Make sure no spaces precede the first "Package."  I.e. That first "P" should be the first character in the file.

Package: casper
Pin: version 1.78
Pin-Priority: 1001

Package: ubiquity-casper
Pin: version 1.78
Pin-Priority: 1001

Package: udev
Pin: version 093-0ubuntu18.0edgy2
Pin-Priority: 1001

Package: upstart
Pin: version 0.2.7-7
Pin-Priority: 1001

Package: dmsetup
Pin: version 2:1.02.07-1ubuntu2
Pin-Priority: 1001

Package: initramfs-tools
Pin: version 0.69ubuntu20.0edgy1
Pin-Priority: 1001

Package: initscripts
Pin: version 2.86.ds1-14.1ubuntu16
Pin-Priority: 1001

Package: libvolume-id0
Pin: version 103-0ubuntu6
Pin-Priority: 1001

Package: startup-tasks
Pin: version 0.2.7-7
Pin-Priority: 1001

Package: sysv-rc
Pin: version 2.86.ds1-14.1ubuntu16
Pin-Priority: 1001

Package: sysvutils
Pin: version 2.86.ds1-14.1ubuntu16
Pin-Priority: 1001

Package: upstart-compat-sysv
Pin: version 0.2.7-7
Pin-Priority: 1001

Package: upstart-logd
Pin: version 0.2.7-7
Pin-Priority: 1001

Package: livdevmapper1.02
Pin: version 2:1.02.08-1ubunut1
Pin-Priority: 1001

Package: volumeid
Pin: version 093-0ubuntu18.0edgy2
Pin-Priority: 1001


The following is the sources.list file that I used, also in "/etc/apt" directory.  Nothing special about this, but I have included it for convenience.  I think one of the repositories may have caused an error, so feel free to create your own.  But, this worked for me.

deb file:/var/cache/apt-build/repository apt-build main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

---

### Post by EagleRock on 2007-06-03
Mike,

Sounds great.  I can try it out with Edgy.  I do have experience playing with apt-get (with Debian), so this should be cake.  I'll play with it myself and see how many errors I get or don't get.  If I can't test it tonight, I will definitely be able to do it tomorrow.

Thanks again,

Peter

---

### Post by mjpca on 2007-06-03
I could probably also create an iso and upload it to your computer if you want (you'd have to setup the ssh, as I may not have a chance to figure out how to do that soon).

I have been playing with the edgy hybrid, and so far, it actually looks pretty good.  I haven't tested it enough yet to say for sure, but I haven't had any errors at this stage.  I did 3 things differently than what I did with the setup based upon feisty herd3:

1.  Started with edgy (obviously);

2.  I used the syslinux approach to booting rather than using grub.  No reason to think that that caused a difference, but I did change that.

3.  I am using an external 30GB 2.5" hard drive.

As far as using the hard drive, I am not sure that that really mattered.  With respect to the errors I was experiencing on the pendrive, I found that if I ran e2fsck on the casper-rw partition, it fixed them.  Don't know enough to know what was happening, but something was getting messed up.  I still haven't tried the edgy-feisty custom cd on a pendrive, but will probably do that next (some time next week).

So far, though, the edgy based system seems to be working better than the version based upon feisty herd3.  I haven't gotten any errors and persistence is working.  Still not tested enough to confirm that there are no problems (problems cropped up in my earlier setup after using it for a while), but it at least seems to be working better in the sense that it is actually shutting down properly.  Probably does make sense to have a few people try it out to flesh out errors and problems.

---

### Post by calinb on 2007-06-04
I'm a bit side tracked on another Ubuntu project right now (installing Feisty, and OS X under MOL virtualization on my old PPC Mac mini).

For the persistent USB project, I tried some kernel builds using Unionfs 2.0.  My problem is finding the right set of patches.  Because Unionfs 2.0 is available only as a patch to a plain vanilla kernel, I need to also have a set of Debian/Ubuntu patches to get to/from plain vanilla from/to 2.6.20 Ubuntu Feisty kernel.  It appears the diff file that comes with the .orig Ubuntu kernel sources will not reverse the source all the way back to a plain vanilla 2.6.20.

-Cal

BTW, MOL is pretty cool, if you have a PPC  The new Intel Macs certainly stomp the old PPC macs for crunching performance, but my old mini can run both OS's 24/7 on something like 22 watts.

-Cal

---

### Post by mjpca on 2007-06-05
It may be that the reason this custom edgy live-cd is working is that it appears that the "pinned" files caused the kernel to be held back to the edgy kernel.  But, otherwise the system appears to be the feisty system.

I did find that using the syslinux approach to booting works better than grub, for some unknown reason.  With syslinux, the liveusb shuts down properly.  With grub, it wasn't shutting down properly.  Odd.  I don't think I changed anything else, but don't plan on spending time investigating that.  I am just going to use syslinux.

I do also get a gnome-settings error when booting up the first time with the liveusb.  But, after booting the first time in persistent mode, the error never comes back.  Otherwise, the custom liveusb seems to be working pretty well.

---

### Post by ASPCartman on 2007-06-08
I'm not able to read whole thread (wanna sleep). Have you found ANY way to make fiesty persistence?

---

### Post by Vinze on 2007-06-09
> **ASPCartman said:**
> I'm not able to read whole thread (wanna sleep). Have you found ANY way to make fiesty persistence?

Apparently someone was able to by combining it with Edgy. I'm planning to gather all instructions in a single post and then after the weekend try it at home. Stay tuned ;)

---

### Post by The Gladiator on 2007-06-09
Before you start working, has anyone checked if the new release 7.10 alpha 1 fixed the problem ?

---

### Post by ASPCartman on 2007-06-09
where to download 7.10 :p ???

---

### Post by oilRG on 2007-06-09
here u are

[http://cdimage.ubuntu.com/releases/gutsy/tribe-1/](http://cdimage.ubuntu.com/releases/gutsy/tribe-1/)

---

### Post by Vinze on 2007-06-09
> **The Gladiator said:**
> Before you start working, has anyone checked if the new release 7.10 alpha 1 fixed the problem ?

It's likely that someone will have tested it before somewhere next week when I'll be trying it, but I don't think it has, because all UnionFS packages available in Gutsy are the same as in Feisty: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unionfs&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unionfs&searchon=names&subword=1&version=all&release=all)

---

### Post by Vinze on 2007-06-09
OK, this is what I think I ought to be doing.

First, I follow a [normal tutorial for putting Ubuntu on a USB drive](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar) to put Ubuntu (or Xubuntu, in my case. That's not a problem, is it?) Edgy on my USB drive. Then I boot that USB drive and save the following to /etc/apt/preferences:

> **mjpca said:**
> Package: casper
Pin: version 1.78
Pin-Priority: 1001

Package: ubiquity-casper
Pin: version 1.78
Pin-Priority: 1001

Package: udev
Pin: version 093-0ubuntu18.0edgy2
Pin-Priority: 1001

Package: upstart
Pin: version 0.2.7-7
Pin-Priority: 1001

Package: dmsetup
Pin: version 2:1.02.07-1ubuntu2
Pin-Priority: 1001

Package: initramfs-tools
Pin: version 0.69ubuntu20.0edgy1
Pin-Priority: 1001

Package: initscripts
Pin: version 2.86.ds1-14.1ubuntu16
Pin-Priority: 1001

Package: libvolume-id0
Pin: version 103-0ubuntu6
Pin-Priority: 1001

Package: startup-tasks
Pin: version 0.2.7-7
Pin-Priority: 1001

Package: sysv-rc
Pin: version 2.86.ds1-14.1ubuntu16
Pin-Priority: 1001

Package: sysvutils
Pin: version 2.86.ds1-14.1ubuntu16
Pin-Priority: 1001

Package: upstart-compat-sysv
Pin: version 0.2.7-7
Pin-Priority: 1001

Package: upstart-logd
Pin: version 0.2.7-7
Pin-Priority: 1001

Package: livdevmapper1.02
Pin: version 2:1.02.08-1ubunut1
Pin-Priority: 1001

Package: volumeid
Pin: version 093-0ubuntu18.0edgy2
Pin-Priority: 1001

Then I do an apt-get update and apt-get upgrade, then change all occurrences of "edgy" in /etc/apt/sources.list to "feisty" and then do and apt-get dist-upgrade . If everything went fine I should then have an Edgy/Feisty liveUSB. A lot of space will be taken on casper-rw, but because the other instructions are too complicated for me I'll take that for granted.

Did I miss anything?

---

### Post by ASPCartman on 2007-06-10
THX! I gonna test it!

---

### Post by The Gladiator on 2007-06-10
good luck and keep us posted

---

### Post by ASPCartman on 2007-06-10
Today i gonna finish repairing of Beryl (v 3.0 i not working, damn) And tomorow i gonna test USB ;)

---

### Post by ASPCartman on 2007-06-10
> **Vinze said:**
> OK, this is what I think I ought to be doing.

First, I follow a [normal tutorial for putting Ubuntu on a USB drive](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar) to put Ubuntu (or Xubuntu, in my case. That's not a problem, is it?) Edgy on my USB drive. Then I boot that USB drive and save the following to /etc/apt/preferences:



Then I do an apt-get update and apt-get upgrade, then change all occurrences of "edgy" in /etc/apt/sources.list to "feisty" and then do and apt-get dist-upgrade . If everything went fine I should then have an Edgy/Feisty liveUSB. A lot of space will be taken on casper-rw, but because the other instructions are too complicated for me I'll take that for granted.

Did I miss anything?

You now man, you are great!! ;);):D If not you i would never repair beryl!!! You rulez!
(I'll explain. I used /etc/apt/preferences to make synaptic think that there is no 3.0 v of beryl, only 0.2! Yoy rulez!)

---

### Post by ASPCartman on 2007-06-10
And now i gonna test your way tof making fiesty persistence.
:popcorn:

---

### Post by ASPCartman on 2007-06-10
Work is going well. While update continius i go to have a little sleep ;)

---

### Post by mjpca on 2007-06-11
I've been using the edgy/feisty hybrid since my last post, and it is working fine.  No issues.  Again, I had to use syslinux, rather than grub, to get it to work properly.  Not sure why.

---

### Post by mjpca on 2007-06-11
Vinze,

By the way, I am guessing that the approach you are taking will work just as well as making the custom squashed filesystem.  I thought about trying that approach, but didn't because all of the new ubuntu packages (the feisty packages) will take up space on your casper-rw partition.  If you make the custom squashed filesystem, you won't have to use any space on you casper-rw partition for the new files.  Seems like that approach should work, though, and it is simpler if you have the space on your usb drive.

---

### Post by mjpca on 2007-06-11
Vinze,

Actually, I did try that approach, and I didn't get it to work.  There was an acpi error that arose when upgrading from Edgy to Feisty.  I don't know if that error always arises or not (e.g. don't know if it is specific to my machine).  

I wasn't able to fix it, though, except using the chrooted environment.  If you experience that error and don't fix it, I think the system will hang on re-boot (at least that is what it did for me).  There may be a fix out there, but I didn't look enough to find it.  I actually found it easier to fix it using the chrooted environment.  If you know the fix for that acpi error (assuming you also experience it), then it seems that approach should work.

---

### Post by ASPCartman on 2007-06-11
Guys, you won't belive that. It's still updating :(

---

### Post by ASPCartman on 2007-06-11
I have 3.3Gb on my casper-rw. Is it ok? ))))

---

### Post by ASPCartman on 2007-06-11
> **mjpca said:**
> Vinze,

Actually, I did try that approach, and I didn't get it to work.  There was an acpi error that arose when upgrading from Edgy to Feisty.  I don't know if that error always arises or not (e.g. don't know if it is specific to my machine).  

I wasn't able to fix it, though, except using the chrooted environment.  If you experience that error and don't fix it, I think the system will hang on re-boot (at least that is what it did for me).  There may be a fix out there, but I didn't look enough to find it.  I actually found it easier to fix it using the chrooted environment.  If you know the fix for that acpi error (assuming you also experience it), then it seems that approach should work.

Sorry, my Endlish is still not going to be well. What means 'approach filesystem'?

PS
Still updating

---

### Post by calinb on 2007-06-11
> **mjpca said:**
> Vinze,

By the way, I am guessing that the approach you are taking will work just as well as making the custom squashed filesystem.  <snip>

I may find some time to resume work on this in a week or two.  I think what needs to be done is UnionFS 2.0 needs to be patched into Feisty.  Then a new squash filesystem should be created and a new Live/ USB image created.

I've had some luck with the "hybrid" Edgy/Feisty live USB hack, but I've seen some problems on some systems with it and the proper way to support 2.16.20 kernels is with unionfs 2.0.

-Cal

---

### Post by ASPCartman on 2007-06-11
I have an idea.
We used edgy as main and then update it to feisty (but not some packages)
Maybe we should use feisty main with downgraded packages (only that we need to downgrade) on it's base (on cd that we wrote on USB partition):popcorn:
PS
Still updeting. Someone kill meeeee!:(

---

### Post by ASPCartman on 2007-06-11
What is UnionFS2.0 Squashed filesystem approach filesystem ????

---

### Post by calinb on 2007-06-11
> **ASPCartman said:**
> What is UnionFS2.0 Squashed filesystem approach filesystem ????

Just search.

[http://en.wikipedia.org/wiki/UnionFS](http://en.wikipedia.org/wiki/UnionFS)
[http://www.filesystems.org/project-unionfs.html](http://www.filesystems.org/project-unionfs.html)

[http://en.wikipedia.org/wiki/SquashFS](http://en.wikipedia.org/wiki/SquashFS)
[http://squashfs.sourceforge.net/](http://squashfs.sourceforge.net/)

approach?  A typo error?

-Cal

---

### Post by ASPCartman on 2007-06-11
> I thought about trying that approach
What approach word means?

---

### Post by ASPCartman on 2007-06-11
I read your link's.
How to use this UnionFS 2.0? Is it a visual application, terminal application or what?
Currently i have ext3 and ntfs (vista)  filesystem and i don't know any other (exept fat32):(

---

### Post by Vinze on 2007-06-11
> **ASPCartman said:**
> How to use this UnionFS 2.0? Is it a visual application, terminal application or what?
Currently i have ext3 and ntfs (vista) filesystem and i don't know any other (exept fat32)

As far as I can understand UnionFS is a filesystem just as ext3 and ntfs are, but probably optimized for use with LiveCDs et al. That it's "squashed" means that it has been compressed (shrunken) to fit on a CD (or USB device) and will be uncomressed (returned to its original size) when you boot from the CD.

> **ASPCartman said:**
> What approach word means?

"A way of doing something", i.e. what I posted before on how I would make a hybrid edgy/feisty system.

> **mjpca said:**
> Vinze,

Actually, I did try that approach, and I didn't get it to work.  There was an acpi error that arose when upgrading from Edgy to Feisty.  I don't know if that error always arises or not (e.g. don't know if it is specific to my machine).  

I wasn't able to fix it, though, except using the chrooted environment.  If you experience that error and don't fix it, I think the system will hang on re-boot (at least that is what it did for me).  There may be a fix out there, but I didn't look enough to find it.  I actually found it easier to fix it using the chrooted environment.  If you know the fix for that acpi error (assuming you also experience it), then it seems that approach should work.

I'm hoping to try it this week but there's a few tests coming so I'll have to learn a bit too :(

Anyway, if it works, I'll tell it, if it doesn't, I might still try to do the squashed filesystem, but my guess is that it's too complicated for me.

And if that too doesn't work, all my hopes on Cal with patching UnionFS 2.0.

---

### Post by mjpca on 2007-06-11
> **ASPCartman said:**
> I have an idea.
We used edgy as main and then update it to feisty (but not some packages)
Maybe we should use feisty main with downgraded packages (only that we need to downgrade) on it's base (on cd that we wrote on USB partition):popcorn:
PS
Still updeting. Someone kill meeeee!:(

ASP Cartman, sorry my post wasn't clear.  I was referring to the approach that Vinze described of copying the preferences file into the /etc/apt directory of a persistent edgy usb drive.

The approach you describe above (of holding back packages) is the approach that I took to get this to work (and is the approach that Vinze is describing). You can "pin" the files that I indicated above should be pinned when upgrading from edgy.  You might need to read the bug report 84591 for additional background.  As described in that bug report, I created a modified squashed filesystem that I used with the files from the edgy iso.  It gives me a system that is feisty, except for the packages that are pinned.  Persistence works.

(I did find that the system additionalyl "held back" the linux kernel to the edgy version of the kernel which may be why it is working in spite of the unionfs issue.  It may be that the kernel should also be "pinned."  I am not sure if it will break persistence if that is subsequently upgraded.)

Vinze's approach is essentially the same thing, except he is proposing that, rather than create the customized squashed filesystem, he just use the preferences file on the persistent usb.  My comments above were to explain the issues that I experienced when trying that approach.

I originaly tried downgrading from Feisty, but found it easier to upgrade from edgy.  Having said that, I believe that the 1001 pin code (in the preferences file) will cause the specified packages to downgrade.  If you take that approach, however, then you will still need to use vmlinuz from the edgy iso.  The vmlinuz on the feisty cd uses the 2.6.20 kernel, and persistence completely failed to work with that vmlinuz.

---

### Post by mjpca on 2007-06-11
By the way, I have an iso that has the modified files on it that I expect you could just use like the regular ubuntu iso when creating a persistent usb drive.  I am happy to make that available, but haven't found a good way to do it, other than using scp or ssh to transfer the file.  I was reading up on ssh and scp, and I would either need to let you download it from my machine or upload it to your machine.  If you want it and can set up an account so that I can upload it to you, that would be easiest for me.  I just don't understand scp and ssh well enough yet to be comfortable that I have it properly configured from a security standpoint.

The iso about 840MB, so it is too big for a cd.  There may be a way to cut it back, but I am using it on a larger usb so don't care.

---

### Post by pepeio on 2007-06-12
Hello.
I can provide space and bandwidth for the iso (or any other iso related to that problem)
Please contact me privately. I can setup a ftp or let people download the iso through http.
http ought to be the easiest for everyone.

---

### Post by ASPCartman on 2007-06-12
I was not able to upgrade it. It's toooooooooo long for me. 1 night with half day it's very loong. I skipped. Tonight i tried to continue but it said about version of languge pack that missing.
And  i have 2 questions:
1. How to make it NOT load 'ubuntu' user
2. How to start usb without turning off my main Linux? I don't have so much time to spend it on waiting. Maybe Qemu somehow? 

PS
About iso. Guys. You were using linux toooooooolong :D ssh... i don't even now what is it :D
Answer - torrent. Create torrent, send to tracker. I, and about 1000 people, will download it. ;)

---

### Post by ASPCartman on 2007-06-12
> **mjpca said:**
> ASP Cartman, sorry my post wasn't clear.  I was referring to the approach that Vinze described of copying the preferences file into the /etc/apt directory of a persistent edgy usb drive.

The approach you describe above (of holding back packages) is the approach that I took to get this to work (and is the approach that Vinze is describing). You can "pin" the files that I indicated above should be pinned when upgrading from edgy.  You might need to read the bug report 84591 for additional background.  As described in that bug report, I created a modified squashed filesystem that I used with the files from the edgy iso.  It gives me a system that is feisty, except for the packages that are pinned.  Persistence works.

(I did find that the system additionalyl "held back" the linux kernel to the edgy version of the kernel which may be why it is working in spite of the unionfs issue.  It may be that the kernel should also be "pinned."  I am not sure if it will break persistence if that is subsequently upgraded.)

Vinze's approach is essentially the same thing, except he is proposing that, rather than create the customized squashed filesystem, he just use the preferences file on the persistent usb.  My comments above were to explain the issues that I experienced when trying that approach.

I originaly tried downgrading from Feisty, but found it easier to upgrade from edgy.  Having said that, I believe that the 1001 pin code (in the preferences file) will cause the specified packages to downgrade.  If you take that approach, however, then you will still need to use vmlinuz from the edgy iso.  The vmlinuz on the feisty cd uses the 2.6.20 kernel, and persistence completely failed to work with that vmlinuz.

You shouldn't write so long post. I din't underst half of it :(
I will reread reread reread it
Answer a question. Is here ANY way to downgrade some packages ON MAIN USB PARTITION (700mb, fat32) to make feisty load with downgraded packeges first time?
And i DON"T understand 'approach' word. I never heard it before.

---

### Post by pepeio on 2007-06-12
> And i DON"T understand 'approach' word. I never heard it before.
[http://www.m-w.com/cgi-bin/dictionary?va=approach](http://www.m-w.com/cgi-bin/dictionary?va=approach)
:)

---

### Post by Vinze on 2007-06-12
> **mjpca said:**
> By the way, I have an iso that has the modified files on it that I expect you could just use like the regular ubuntu iso when creating a persistent usb drive.  I am happy to make that available, but haven't found a good way to do it, other than using scp or ssh to transfer the file.  I was reading up on ssh and scp, and I would either need to let you download it from my machine or upload it to your machine.  If you want it and can set up an account so that I can upload it to you, that would be easiest for me.  I just don't understand scp and ssh well enough yet to be comfortable that I have it properly configured from a security standpoint.

The iso about 840MB, so it is too big for a cd.  There may be a way to cut it back, but I am using it on a larger usb so don't care.

If you still manage to put it online somewhere I will try that (I have only little experience with SSH so that might be an option) but as I prefer Xubuntu it won't be disastrous if it doesn't work out ;)

---

### Post by pepeio on 2007-06-14
Good day everyone.

The ISO of MJPCA patches for persistence is available. :popcorn:
[http://88.191.31.14/ubuntuFeistyPatched/](http://88.191.31.14/ubuntuFeistyPatched/)

You will find iso and MD5 files in the directory.
[COLOR=Silver][SIZE=1]
If you care, please report download times and speed _through PM_ (please do not pollute the thread), including your location. ( my server, while mostly idle and having a symmetrical 100mbits line, is still being tested for its qualities, so any advice on its download speed is welcome. Thanks )[/SIZE][/COLOR]

[SIZE=4][B][EDIT] I did setup a ftp, that you can access by that same url (link in a page).
It seemed that http download was far too slow.[/B][/SIZE]

---

### Post by oilRG on 2007-06-14
woohoo! thanks!

is it the same feisty, or something else has been changed?

---

### Post by mjpca on 2007-06-14
Some files are not upgraded to feisty to get it to work.  But, it operates and looks like feisty.  It may be that the most noticeable files that are not upgraded are some of the kernel files.  I didn't "pin" those files, though, so if you upgrade those, it is possible it will break the persistence.  If that happens, you can start over by taking all of the files off of the casper-rw partition.  It may make sense to add those files as "pinned" in the preferences file in /etc/apt.  But, it would also be interesting to test upgrading those files to see if that does in fact break persistence.  I haven't had a chance to test it to see if that will break persistence..

Also, again, for some reason I had to use the syslinux approach to booting off the usb to get it to work properly.  Not sure why.  Lastly, I didn't actually test burning it to a dvd to see if that works.  I have only used it as a persistent usb.  But, I'd be interested in knowing whether it works for others..

---

### Post by mjpca on 2007-06-14
By the way, if you compare the file system manifest with the feisty file system manifest, you can see exactly what files are different in the two squashed file systems.  Except for the file system manifests, the squashed file system, and the md5sum.txt file, the rest of the files on the iso are actually from edgy.  That doesn't really matter because when fully booted, the system that you see is the squashed file system which is mostly feisty.

---

### Post by mjpca on 2007-06-14
One other reminder - - upon first boot, I do get an error message regarding the gnome settings daemon (I think that is what it was).  But, after the first boot into persistent mode, it has never shown up again upon subsequent boots.

---

### Post by Vinze on 2007-06-14
I'm trying anything I can to get my hands on that .iso at the moment but our internet connection isn't exactly cooperating so I don't know when I'll be able to test it.

---

### Post by pepeio on 2007-06-15
Please give it an other try. I did setup a ftp instead, which seemed to have sped things up.

Just click on the link to the page once again.

---

### Post by Vinze on 2007-06-15
> **pepeio said:**
> Please give it an other try. I did setup a ftp instead, which seemed to have sped things up.

Just click on the link to the page once again.

Thanks, I had gotten to 54% over HTTP, I'm now continuing that download over FTP and it does seem considerably faster. Then tomorrow I hope to be able to test it.

---

### Post by oilRG on 2007-06-15
n keep us posted, of course :)

i get my 8gb one only in 2 weeks :(

---

### Post by Vinze on 2007-06-15
> **oilRG said:**
> n keep us posted, of course :)

Naturally ;) (83%)

---

### Post by Vinze on 2007-06-16
Merde!

> dad14f111459025c773849829cef2e71  custom-ubuntu-desktop-i386.iso
35c9fdf92ad29647fbcb945a68b69596  ./custom-ubuntu-desktop-i386.iso

The top line is from [ftp://88.191.31.14/custom-ubuntu-desktop-i386.iso.md5](ftp://88.191.31.14/custom-ubuntu-desktop-i386.iso.md5), the bottom one is mine :(

---

### Post by mjpca on 2007-06-16
May have been a problem with the upload.  I'll get back  to you shortly.

---

### Post by Vinze on 2007-06-16
> **mjpca said:**
> May have been a problem with the upload.  I'll get back  to you shortly.

I am already redownloading it (55%), might that be a problem?

---

### Post by Vinze on 2007-06-16
YESYESYES!
> $ wget -c [ftp://ubuntupatch@88.19114/custom-ubuntu-desktop-i386.iso](ftp://ubuntupatch@88.19114/custom-ubuntu-desktop-i386.iso)
--19:45:37--  [ftp://ubuntupatch@88.191.31.14/custom-ubuntu-desktop-i386.iso](ftp://ubuntupatch@88.191.31.14/custom-ubuntu-desktop-i386.iso)
           => `custom-ubuntu-desktop-i386.iso'
Connecting to 88.191.31.14:21... connected.
Logging in as ubuntupatch ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD not needed.
==> SIZE custom-ubuntu-desktop-i386.iso ... done.
==> PASV ... done.    ==> REST 389377356 ... done.    
==> RETR custom-ubuntu-desktop-i386.iso ... done.
Length: 872,259,584 (832M), 482,882,228 (461M) remaining

100%[++++++++++++++++====================>] 872,259,584   65.98K/s    ETA 00:00

21:36:14 (71.18 KB/s) - `custom-ubuntu-desktop-i386.iso' saved [872259584]


> $ md5sum *6.iso
dad14f111459025c773849829cef2e71  custom-ubuntu-desktop-i386.iso


[ftp://88.191.31.14/custom-ubuntu-desktop-i386.iso.md5](ftp://88.191.31.14/custom-ubuntu-desktop-i386.iso.md5) :
> dad14f111459025c773849829cef2e71  custom-ubuntu-desktop-i386.iso

Tomorrow's the big day!

PS. mjpca, if it works, I'll be blogging about it, how should I credit you? Just "mjpca" or would you like me to provide a full name or something?

---

### Post by mjpca on 2007-06-17
I have a PM in to Pepeio.  I was unable to access the ftp to upload the file again.

As far as credit, I'm not really worried about it.  I'll just be glad if it works for others.

I suppose you could just identify me as Mike and mention mjpca as my login id on the ubuntu forums.  But, no big deal either way.

---

### Post by Vinze on 2007-06-17
> **mjpca said:**
> As far as credit, I'm not really worried about it.  I'll just be glad if it works for others.

I suppose you could just identify me as Mike and mention mjpca as my login id on the ubuntu forums.  But, no big deal either way.

Yeah, it's not like my blog is visited by thousands of people anyway ;)

So... What I wanted to say is:


**I am posting this from my LiveUSB!**


That feels good. And guess what? I cannot see the casper-rw partition, so it most likely is persistent. I'll go for a reboot now and see if my network settings are saved, but I just wanted to say this right away ;)

This is so cool.

Oh, and one more thing: > ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty


---

### Post by Vinze on 2007-06-17
**Success!**

It still worked :D

(Though I now understand why it is so annoying that NetworkManager asks for your password every time you boot)

I made quite some screenshots so I'll post the instructions online soon (my sister wants to use my computer for now).

---

### Post by Vinze on 2007-06-17
OK, for anyone that would also like to try this, I've written [a blog post]("http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/") on how to do this. I also created [a torrent]("http://filegunner.net/file-viewer.php?id=290599custom-ubuntu-desktop-i386.iso.torrent") of the .iso, if anyone who already has it would like to seed it, please do so.

---

### Post by mjpca on 2007-06-17
Great to see Vinze.  Glad it's working for you.

---

### Post by EagleRock on 2007-06-18
Vinze,

Thanks for the fix post!  I was attempting to test Mike's fix myself, but I was having an issue with the Edgy persistent install as well.  I'm currently downloading the .iso that Mike made and will probably get to test it tomorrow.  Thanks again to Mike for all his hard work on this issue and to Vinze for documenting the fix.  I'm sorry that I couldn't help more with this issue, as I did want to, but I'll at least confirm that I could follow the instructions.

Thanks again, guys!

---

### Post by Vinze on 2007-06-18
> **mjpca said:**
> Great to see Vinze.  Glad it's working for you.

Well, I installed all updates (including some kernel-headers) and it still boots. I also finished a download of Xubuntu Edgy so I'll be trying to create a Xubuntu image later this week.

---

### Post by Fisslefink on 2007-06-18
Great job, Mike, Cal, and Pepeio!  I just finished final exams on Friday, and then I had this nice surprise to greet me this morning.  I'm downloading the .iso from pepeio's FTP right now (no one is seeding the torrent presently).  I will seed pepeio's torrent[(link)]("http://filegunner.net/file-viewer.php?id=290599custom-ubuntu-desktop-i386.iso.torrent"), all day today, once I have the files.

I'll report my success (or failures...) with persistence here and on pepeio's blog once I give it a shot.

ES

---

### Post by Fisslefink on 2007-06-18
Good news.  I've downloaded the .iso from the FTP, checked the md5sum (OK!) and now I’m seeding the torrent with 400+ KBps upload bandwidth for the next three hours, and 9-5pm (PST) tomorrow, until some more people pick it up.

Torrent link:  [http://filegunner.net/file-viewer.php?id=290599custom-ubuntu-desktop-i386.iso.torrent](http://filegunner.net/file-viewer.php?id=290599custom-ubuntu-desktop-i386.iso.torrent)

Enjoy,

Fisslefink

---

### Post by mjpca on 2007-06-18
> **Vinze said:**
> Well, I installed all updates (including some kernel-headers) and it still boots. I also finished a download of Xubuntu Edgy so I'll be trying to create a Xubuntu image later this week.

Vinze,

Yeah, I had the same result.  Seems to work fine with all of the upgrades installed, including the 2.6.20 kernel headers.

---

### Post by oilRG on 2007-06-19
all,

how long does it take it to boot approximately?

in the other words,i is it lagging? :D

---

### Post by JackRazz on 2007-06-19
Vinze,
Thanks for the blog entry how to on ubuntu on a usb stick.  I just fired up the torrent for it and will try it out tomorrow. I've been looking for a solution for this for over a year. Perhaps I'll finally be able to do my full backups/restores from within ubuntu all the way instead of slax.  Now all I have to do is get around to reading up on and creating a rsync script to do my full backups/restores.

JackRazz

---

### Post by mjpca on 2007-06-19
Yeah, boot seems slow.  If you boot with the "profile" boot parameter once in persistent, I think it might help.  I haven't timed it, but it seems a little better.

---

### Post by Vinze on 2007-06-19
> **mjpca said:**
> Yeah, boot seems slow.  If you boot with the "profile" boot parameter once in persistent, I think it might help.  I haven't timed it, but it seems a little better.

It could be that boot normally isn't that fast at my PC either, but it doesn't seem slower than a LiveCD for me.

PS. I'm also seeding the torrent as I'm using my PC.

---

### Post by EagleRock on 2007-06-19
Vinze,

Success!  Very well documented, which is always a great plus.  Thanks to Mike for the fix, as my little USB is finally persistent!!!

Only note, Vinze, is that you don't note that the fat-16 "UbuntUSB" partition needs to be set as bootable.  Other than that, the documentation was perfect!

Also, I have some dumb questions by the uninitiated persistent user:

1) - My Syslinux bootloader doesn't have the nice menus (such as "Start Ubuntu in persistent mode"), but rather only shows the name of the different bootload options (such as "persistence, live, etc.")  Interestingly enough, there are periods in some of the options (persistent is "persist.ent").  I'm not sure if I did something wrong, but this happened pretty much every time I did a persistence install, even with Edgy and my previously broken Feisty installs.  Is this an issue caused by the -f switch we use for the install?  I can't seem to find documentation on what -f does, so I'm lost.

2) - With a persistent install, you can't get updates, can you?  If I'm not mistaken, I'll have to mount the install and enter it (as per the procedure Mike used before to modify the .iso), then do apt-get to update the system, right?

3) - If I install programs not included on the image, will it work fine, or will the install go crazy?

Thanks again to everyone that worked on this!

---

### Post by mjpca on 2007-06-19
EagleRock,

You should be able to install updates and new programs just like a regular Ubuntu installation, provided you have enough room on your casper-rw partition.  Unionfs essentially combines a read only partition with a read-wite partition.  From the user's perspective, it appears to be a writable partition. So, everything you add will go onto the casper-rw partition, but appear to be part of the unified installation.  You shouldn't have to modify the squashed filesystem.  That is the nice thing about persistence.  (The reason for modifying the squashed filesystem was really so that the updated files would not use up space on the casper-rw partition, but rather would be included in the base distribution files.  Without doing that, your disk would actually contain both the old and new versions of files that are updated, but only show the new versions.  Also, there was an acpi error that I found easier to work around by updating the squashed filesystem).

There is always a possibility that an update will break something, but feel free to post if that happens to you.

I am going to upload a slightly modified version of the iso to Pepeio's ftp.  In that version, I made additional updates to the squashed filesystem that didn't get included in the current version.  So, when you go into synaptic, everything other than a couple of the files that were held back (e.g. I think hal and libdevmapper) should show up as being up to date, unless more changes are made after the time the iso is created.  I also removed some of the language support, which brought the size of the iso down a little bit, but not a lot (I think it is around 820MB).  If anyone wants to use the language support that I removed, they would need to add it back in persistent mode.

With regard to the slow boots that people are experiencing, it is definitely a good idea to boot once into persistent mode using the "profile" boot parameter.  The readahead files in the iso were created for Edgy, and given how much the distribution has changed from Edgy, the "profile" boot parameter will update the readahead files for this modified distribution.  To me, that seems to help at least a little, but again I haven't timed it.

I saw a few people asking for a smaller iso.  If there is any consensus regarding files that people would want to remove to get the iso down to below 700MB, I could probably eventually create that iso.  I scanned through the files, but there wasn't anything obvious.  Removing OpenOffice might descrease size substantially.  If people wanted to use open office, they could add it back through synaptic when in persistent mode.

I also suspect Vinze's Xubuntu version may be smaller.

---

### Post by mjpca on 2007-06-19
EagleRock,

By the way, I am not that familiar with Syslinux, but I think you can probably make at least some changes by modifying the Syslinux.cfg file.  I think that defines your menu.

---

### Post by ariddell on 2007-06-19
Hey,
        Thanks for putting this together, nice work. This is the first time i have attempted to get this working so followed the instructions in the blog post last night to see if i could get it running.

Everything went through ok, no error messages etc but I can't get it to start up from USB. I'm sure it's something minor that i've missed but all i get is a "Boot Error" message on startup. Having never done this before i'm not overly sure what i've done wrong so any assistance appreciated.

Thanks

---

### Post by mjpca on 2007-06-19
I get that error sometimes when I don't have syslinux setup properly.

Did you execute the command line:

              syslinux /dev/[your live usb partition]

---

### Post by ariddell on 2007-06-19
> **mjpca said:**
> I get that error sometimes when I don't have syslinux setup properly.

Did you execute the command line:

              syslinux /dev/[your live usb partition]


Yes, i did that and it seemed to go through ok - no error message.

I've also just tried re-running syslinux from the windows version but it doesn't seem to have hadany effect.

Would not having an MBR on the stick cause this error? If so how could i replace the MBR to confirm if that's the problem, preferably without redoing the whole proceedure?

Thanks

---

### Post by ariddell on 2007-06-19
Yep, that was my issue - have fixed the mbr on the usb stick and it now boots up.

Now not getting the menu and it comes up with a tty control error but I'll see if i can work that one through.

Thanks

---

### Post by mjpca on 2007-06-20
There is a ubuntu package called "ms-sys" that can be used to create a master boot record.  Not having one could be the problem.

---

### Post by ariddell on 2007-06-20
Yeah, once the MBR was there it booted from the USB.

Alas i'm not able to get much further however, i don't get any syslinux boot menu and during the startup process it bombs out from the Ubuntu scrolling logo to a screen with the following error:

bin/sh can&#8217;t access tty; job control mode off

And won't go any further.

Any ideas on this one?

Thanks

---

### Post by Vinze on 2007-06-20
> **mjpca said:**
> I saw a few people asking for a smaller iso.  If there is any consensus regarding files that people would want to remove to get the iso down to below 700MB, I could probably eventually create that iso.  I scanned through the files, but there wasn't anything obvious.  Removing OpenOffice might descrease size substantially.  If people wanted to use open office, they could add it back through synaptic when in persistent mode.

I also suspect Vinze's Xubuntu version may be smaller.

I finished it yesterday, and the filesystem.squashfs file was 1GB... (It did boot though ;))

Anyway, I did some things I wasn't completely satisfied with, so I'm going to try again now and hopefully it will work this time. Also, I'm wondering too what packages I could remove. I was considering Thunderbird and perhaps Gaim and the GIMP too, but I'm not too sure whether that matters that much. I'll at least remove all the language packs.

---

### Post by awwylach on 2007-06-20
> **ariddell said:**
> Yeah, once the MBR was there it booted from the USB.

Alas i'm not able to get much further however, i don't get any syslinux boot menu and during the startup process it bombs out from the Ubuntu scrolling logo to a screen with the following error:

bin/sh can’t access tty; job control mode off

And won't go any further.

Any ideas on this one?

Thanks

Hi there,

I think that is a problem with PCI IDE/ISA Xcelerator, some ide driver.

if you enter at the prompt (the shell after that can’t access tty; job control mode off message)

modprobe piix (press return)
exit (press return)

the boot process will continue. At least mines does.

--
I can't wait to check out the modified iso with persistency!!! I just need to get an rw dvd volume later on to burn it down.

Greetings from germany!
Andreas W Wylach

---

### Post by pepeio on 2007-06-20
Mike uploaded a new iso to the server.
It is smaller, has been received correctly (previous iso had checksum problems) and includes some updates.

It is available at the same address:
[http://88.191.31.14/ubuntuFeistyPatched/](http://88.191.31.14/ubuntuFeistyPatched/)

---

### Post by Vinze on 2007-06-20
This really, really sucks. This time, I thought it was going allright with the updates, my internet connection remained stable, all updates had finished and I was just about to finish it, when I realized that I had not set /etc/apt/preferences... I guess the next time I'll be able to create the Xubuntu version is next weekend...

---

### Post by EagleRock on 2007-06-20
> **mjpca said:**
> EagleRock,

You should be able to install updates and new programs just like a regular Ubuntu installation, provided you have enough room on your casper-rw partition.  Unionfs essentially combines a read only partition with a read-wite partition.  From the user's perspective, it appears to be a writable partition. So, everything you add will go onto the casper-rw partition, but appear to be part of the unified installation.  You shouldn't have to modify the squashed filesystem.  That is the nice thing about persistence.  (The reason for modifying the squashed filesystem was really so that the updated files would not use up space on the casper-rw partition, but rather would be included in the base distribution files.  Without doing that, your disk would actually contain both the old and new versions of files that are updated, but only show the new versions.  Also, there was an acpi error that I found easier to work around by updating the squashed filesystem).

There is always a possibility that an update will break something, but feel free to post if that happens to you.

Excellent!  Since the squashed filesystem is in essence half ro and half r/w, I was confused at how it would handle updating files.  I figured it WOULD keep an extra file on the casper-rw, for the sake of the LiveCD.  I might even get to install NVIDIA drivers for the USB, since almost all my machines use an NVIDIA GPU (the others I would add a forced xvga persistent boot)...  Gotta love Linux!

> **mjpca said:**
>  In that version, I made additional With regard to the slow boots that people are experiencing, it is definitely a good idea to boot once into persistent mode using the "profile" boot parameter.

Interestingly enough, even without the modified .iso, I am taking less than a minute to boot...on a 5-year old laptop.  Maybe I'm just one of the lucky ones...I'm almost scared to boot with the profile parameter, as it might slow it down!!

---

### Post by EagleRock on 2007-06-20
> **ariddell said:**
> Yeah, once the MBR was there it booted from the USB.

Alas i'm not able to get much further however, i don't get any syslinux boot menu and during the startup process it bombs out from the Ubuntu scrolling logo to a screen with the following error:

bin/sh can’t access tty; job control mode off

And won't go any further.

Any ideas on this one?

Thanks

Actually, I had that issue with my old desktop.  If you add irqpoll to the boot parameters, it will cause the error to pass and allow you to load successfully.  Only caveat is that it will slow down the boot time slightly.  It never bothered me, though.

---

### Post by Vinze on 2007-06-20
Well, I found the time to try and create the XubuntUSB today, and I did everything correctly this time, however... The .iso is 1.1GB large. If anyone has any clues as to the cause of (and solution to) this, I'd be very grateful, as I really want this to work.

---

### Post by mjpca on 2007-06-20
Vinze,

This link was pretty helpful to me; don't know if you followed this.

[http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm](http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm)

Did you use the step of writing a zeroed dummy file to the block device file, and then deleting the dummy file, before squashing it down?  If you do not do that, the squash file could be significantly larger than it needs to be.

sudo dd if=/dev/zero of=$WORK/new/dummyfile
sudo rm $WORK/new/dummyfile

where, new is the mounted ext2 block file that contains the files you plan to squash ($WORK is just the correct path to "new," whatever it is on your system).  This writes zeros to all of the unused space in the "to be squashed" block device file.  Deleting the dummy file allows that space to be squashed down to nothing, I guess.

Also, make sure you run "apt-get clean" before squashing it (and before writing the zeroed dummy file).  Failure to do that will also cause the squashed filesystem to be larger than it needs to be.

---

### Post by Vinze on 2007-06-20
> **mjpca said:**
> Vinze,

This link was pretty helpful to me; don't know if you followed this.

[http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm](http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm)

Did you use the step of writing a zeroed dummy file to the block device file, and then deleting the dummy file, before squashing it down?  If you do not do that, the squash file could be significantly larger than it needs to be.

sudo dd if=/dev/zero of=$WORK/new/dummyfile
sudo rm $WORK/new/dummyfile

where, new is the mounted ext2 block file that contains the files you plan to squash ($WORK is just the correct path to "new," whatever it is on your system).  This writes zeros to all of the unused space in the "to be squashed" block device file.  Deleting the dummy file allows that space to be squashed down to nothing, I guess.



Yep, I followed that tutorial and did all that. 
> **mjpca said:**
> 
Also, make sure you run "apt-get clean" before squashing it (and before writing the zeroed dummy file).  Failure to do that will also cause the squashed filesystem to be larger than it needs to be.


Didn't do that... But could that add +/- 200MB? Anyway, I do want to try it again using apt-get clean but well, that won't be before next week. :(

---

### Post by Vinze on 2007-06-20
> **Vinze said:**
> Yep, I followed that tutorial and did all that. 



Didn't do that... But could that add +/- 200MB? Anyway, I do want to try it again using apt-get clean but well, that won't be before next week. :(

Mike, you are truly awesome. Just as I wanted to shutdown I realized I still had the Edgy/Feisty system mounted, so I chrooted again and did and apt-get clean and now the ISO is just 745.3MB. Pepeio, would you care to host this one too?

---

### Post by oilRG on 2007-06-20
guys, one question:

why don't we need to create a linux swap partition? os uses casper-rw as swap, or it's supposed that i have enough RAM on board?

thx

---

### Post by mjpca on 2007-06-20
oilRG,

I'm no expert, but I know that there has been some discussion about people not using a swap partition on a usb drive because it will wear out the drive quicker.

I don't think there is any reason that you can't create a swap partition.  I also didn't think Linux had to have a swap partition (assuming you have sufficient RAM), but again I'm no expert.

---

### Post by awwylach on 2007-06-21
Hello everybody,

I downloaded the customized ubuntu iso file and installed it like the receipt without any problems, 
everything went smooth and just looked like I be approaching a usable ubuntu linux on an 
4GB memory stick.

Booting the stick seems to result in other problems. First off my network adapter wasn't recognised 
(an attansic L1), so I wasnt able to fetch additional packages via net. First thing that amazed me 
was, that I am not able to boot in regular multi-user mode. I even get no virtual consoles via ALT-Fx.
The boot-process hangs when the rc.local 
script is executed. Actually the script contains nothing but an exit 0; So I thought, it is the network (DHCP) which is not working in my network (no dhcp server) or the gdm settings probably thru the dhcp network 
definition. What I did was booting up my Vista, fetched all needed debian packages and 
copied them to the usb stick. After that I rebooted from stick in single user mode and installed the driver 
for my attansic lan connector. The installation was successful and I was able thru ifconfig to get the network running. Second problem was the graphics card (nvidia geforce 8600M GS). For that I fetch the driver 
from the nvidia site (NVIDIA-Linux-x86-100.14.09-pkg1.run). 
After installing the libc6-dev headers I was able to install that nvidia driver with no problems. Executing 
the nvidia-xconfig program prepared me to start the gnome windows (via startx) sucessfully. After all 
that I  thought, wow, finally i made it after days of experimenting.
It's not like that. I am still not able to boot ubuntu in multiuser mode, it still hangs at the rc.local execution or at least somewhere at the gdm execution, I am really not sure. Then I thought it might be the 
network settings, which I again adjusted, cause they havent been stored, means, after every single 
reboot, I again had the dhcp settings. Editing the /etc/network/interfaces to enter 
an static eth0 ip address definition gets lost after every single reboot.
What process or script is always overwriting my network definitions?? Drop me some science!

So at this point, I am lost, cause I seem not to find any solution to get further. All I can do is booting single  user mode, and that's about it. Last idea I had was to disable the automatic start of gdm, so I edited the
/etc/X11/default-display-manager by commenting out the /usr/sbin/gdm . But no success, after reboot 
it still hangs at rc.local, just about where the gdm gets started.

Further more I am concerned about some error messages during boot. One thing is the squashed fs, which says at every boot, that it would mount an unchecked file system, an e2fsck is recommended. using such commands as "shutdown -F" or touching an file at / (the root) named forcefsck doesn' lead to an fscheck.

Shutting down ubuntu is even loaded with filesystem errors of /dev/sdb2 (the ext2 partition). Only thing
is to switch off / on the notebook .

Well, I tried all kinds of things to get an working ubunto on memory stick, but I think, I am pretty lost 
now. I am really not an deep-inside linux guy, I am using linux to develop software, so I think, I have to leave it for now and either install the good old debain distro or just wait for an official fixed ubuntu 
release where the unionfs / kernel problems are fixed.

The used hardware: I am using an Asus notebook (z53sv) with duo-core Intel T7100, 2 GB main memory.

Would be interesting to hear other peoples experience. Up to now it seems I am the only one facing those problems. Maybe someone of you has a hint, maybe I did miss something or made an mistake at some point.
Maybe some of you have an advice to get my usb ubuntu stick up and running. Any help or hints are 
greatly appreciated.

Greetings!

Andreas W. Wylach

---

### Post by pepeio on 2007-06-21
No problem. 
I will pm the upload ftp data in a few seconds.

By the way, i tried to use the live distro from an usb stick and had problems with graphic cards.
Sometimes it would boot, sometimes not, screen being garbled. Restarting X had no to little effect.
On a nvidia 7300gs (are drivers included?) only booting using xforcevesa worked. :(
On my ati (radeon 9600 se), it used to work (the feisty i installed on hd works fine) but booting from the usb is not fine each time.
Are there any chances that can be checked before you send the iso?

Thank you.

---

### Post by mjpca on 2007-06-21
Wow Awwylach,

Sorry to see you are having so many problems.  Which iso did you download?  I would suggest that you try both iso's.

Probably the next thing to do is figure out which, if any, of those problems you have with the standard edgy distribution and which, if any, of those problems you have with the standard feisty distribution.  If there is something that is a problem with the feisty distribution, or both of the distributions, then there is nothing that I have done that is going to fix it.

E.g. if your driver is not present in either distribution, then it is not going to be present in tihs custom distro.  

If your issue was a problem with the edgy distribution and that problem was "fixed" by one of the files that was "held back" in order to get this to work, then it likely will still be a problem with this custom edgy-feisty distro.

E.g. If your driver is present in feisty, then I would think that the sudo aptitude dist-upgrade command we used would have added it to this custom distro.  If it didn't do that, the only other thing that I can think is that somehow your driver may depend upon one of the packages that were "held back."  You would need to investigate to see if that is the case.  Look in the /etc/apt/preferences file to see most (or maybe all) of the files that were held back and try to figure out whether any of those affect the use of your driver.

If the particular issue was not a problem with either distribution, then it may be there is some interaction between the edgy and feisty files where the aptitude package management system didn't identify the incompatibility.  If it is that type of issue, it may be time consuming to troubleshoot.  

One thing that I had planned to try was to "unpin" packages in the preferences file one at a time to see if "unpinning" them breaks persistence.  If a file can be unpinned without breaking persistence, then we can probably take it out of the preferences file.  If there are files that do not need to be held back that affect your issues, then that may help you.  So, while I am not sure when I would get to that, you or someone could try that approach.  It could be done when working in persistent mode.  I.e. I don't think the squashed filesystem would need to be modified.

With regard to the multi-user mode, has anyone else experienced that?  Awwylach, how did you confirm that that was the case?  I am only asking because I don't know, I haven't look at that, and I can try the same thing on my system to see if I have the same problem.

Not sure why it is hanging on boot.  Again, has anyone else experienced that?  Does that happen toyou Awwylach with edgy or feisty?  Probably need more info to troubleshoot, but honestly I am a bit tight on time right now.  (I am hoping others might be able to help).

With regard to the network settings, that also may take some time to troubleshoot.  Is there a reason you are not using the gnome network manager?  Again, we probably need more info to trouble shoot (I apologize for not being more specific, but again I am just running really low on time).

The squashed filesystem "error" that you mention is a message that I also get whenever I boot and persistence is working (if your casper-rw partition is ext2).  I don't think that has anything to do with this custom distro, but rather relates to your ext2 partition.  E.g. if you use edgy, I think you should get the same message.  I do not get that message in Feisty because persistence is broken in feisty.  But, I welcome others to chime in.

With regard to the shutdown errors, it could be that you in fact do have issues with your ext2 partition.  You may need to boot using a separate disk and run e2fsck on your casper-rw partition to fix those when that partition is not mounted (I am assuimng your casper-rw is ext2).  You might also try using ext3, although people have suggested that ext3 be avoided on a usb flash drive because it may wear it out more quickly.

Also, are you using grub as the boot manager?  I had similar problems on shutdown when using grub.  It would hand, rather than shutdown properly, and then would result in a large number of errors on the ext2 partition.  So, if you are using grub, try using syslinux.  If you are using syslinux already, then try running e2fsck when booting from e.g. a standard livecd and when your casper-rw partition is not mounted..

Unfortunately, I am actually probably going to be pretty unavailable for the next few weeks, so hopefully that at least gives you some places to start.

Regards,

Mike

---

### Post by Vinze on 2007-06-21
OK... I managed to put this modified Xubuntu ISO on my USB drive and I also managed to boot from it, but... I can see the casper-rw partition on my desktop. I'll try and reboot to see if it isn't somehow persistent but I fear the worst.

---

### Post by Vinze on 2007-06-21
> **Vinze said:**
> OK... I managed to put this modified Xubuntu ISO on my USB drive and I also managed to boot from it, but... I can see the casper-rw partition on my desktop. I'll try and reboot to see if it isn't somehow persistent but I fear the worst.

Unbelievable! It did work - sort of. I wasn't expecting it, but persistence on Xubuntu did work, even though I can see the casper-rw partition. I just can't mount it. Two problems I've noticed up till now, though:

[LIST=1]
[*]My network settings weren't saved
[*]My iPod came with two partitions, of which one could never be mounted (and wasn't even visible in Windows). However, that one is the only one I can see, I have to manually mount the one with my files (that also contained my network key ;))
[/LIST]

---

### Post by todlangweilig on 2007-06-21
> **awwylach said:**
> Hi there,

I think that is a problem with PCI IDE/ISA Xcelerator, some ide driver.

if you enter at the prompt (the shell after that can&#8217;t access tty; job control mode off message)

modprobe piix (press return)
exit (press return)

the boot process will continue. At least mines does.

--
I can't wait to check out the modified iso with persistency!!! I just need to get an rw dvd volume later on to burn it down.

Greetings from germany!
Andreas W Wylach
I've run into the same problem on my desktop. I got passed the scrolling screen, the bar is just filling in on the left. Then it goes to the shell. I tried running the commands, but to no avail. I don't get any errors when I run the commands, but nothing happens either.

Pressing Alt-F1, I see this:
cp: unable to open '/root/var/log/casper.log': Input/output error
Target filesystem doesn't have /sbin/init

Running 'modprobe piix' doesn't change the above message. Running 'exit' adds an additional 'Target filesystem doesn't have /sbin/init'

I should also note that running it in live mode seems to work just fine. Does anyone have any ideas?:(

-Toad

---

### Post by todlangweilig on 2007-06-21
I think I may have found some more info. It looks like my casper.log file is invalid. Does someone have a way to repair/replace these files?
```

/media/casper-rw/var/log$ ls -Fl
total 536
?--------- ? ?    ?         ?                ? boot
?--------- ? ?    ?         ?                ? casper.log
-rw-r--r-- 1 root root  24000 2007-06-20 13:29 faillog
-rw-rw-r-- 1 root utmp 292000 2007-06-20 13:29 lastlog
-rw-r--r-- 1 root root 493216 2007-06-21 14:11 scrollkeeper.log
?--------- ? ?    ?         ?                ? wtmp

```

---

### Post by mjpca on 2007-06-21
You guys having the boot problem, which iso are you using?  Can you try both iso's to see if the problem happens with both of them?  

I am wondering if I may have inadvertently created a problem with the second iso.

Also, I guess it is possible that Cal's unionfs incompatibility issue is cropping up.  Maybe we need to pin the kernel at the 2.6.17 version.  Odd that it would only affect some people, though, if that is what is happening.

---

### Post by mjpca on 2007-06-21
Also, can you guys boot with the "debug" boot parameter and see if there are any error messages?

---

### Post by mjpca on 2007-06-21
Another question - do you have anything on your casper-rw partition or is it completely empty?   For what file system is it formatted?  E.g. ext2?

---

### Post by hazridi on 2007-06-21
This is a problem I'd like to fix. I really like the persistent flash drive, but edgy's amarok crashes all the time for me, so I would like to get Feisty persistence working.

I got the unionfs patch working fine for the vanilla 2.6.20 kernel. I'm running etch on my main box, when I get the time I'll install Kubuntu into a VM and see if I can't merge unionfs 2.0 into the patched feisty 2.6.20 kernel. After I do that, though, someone else will have to roll updated packages or show me how, then an entirely new livecd will have to be made as well. I suppose I'll have to merge the unionfs files into both the 2.6.20-15 and 2.6.20-16 packages, so someone else can maintain them in the future.

---

### Post by mjpca on 2007-06-21
Some interesting new information (at least interesting to me).  I think this might actually lead to identifying the problem for a fix in gutsy.

Ignoring the unionfs issue for the moment, I played around with the pinned files.  I found out that persistence works if I only pin the following 4 files:

Package: udev
Pin: version 093-0ubuntu18.0edgy2
Pin-Priority: 1001

Package: upstart
Pin: version 0.2.7-7
Pin-Priority: 1001

Package: upstart-compat-sysv
Pin: version 0.2.7-7
Pin-Priority: 1001

Package: upstart-logd
Pin: version 0.2.7-7
Pin-Priority: 1001

The other thing that I did was upgrade to the 1.91 version of casper from gutsy because I suspected that they had rolled in the other debian changes into the gutsy version of casper.

Sure enough, persistence works fine.  I really think the casper file is fine as it has already been revised for gutsy.

The other thing that I had done, before upgrading to the gutsy version of casper was to unpin the three upstart files.  Again, with this last change, persistence still worked, but I received a failure to umount local filesystems.

I have suspected this from the beginning, but this really re-enforces my belief that there has to be  some issue in udev that is causing this problem.  Alternatively, it could be an interaction between udev and the upstart files.  But, based upon these results, it seems there has to be a problem in one of these.  

I am going to post this on the bug report, and then play around a little more, but I want to play around some more.  I didn't achieve this results in a modified squashed filesystem, but rather only using persistence.

So, those of you that are having issues with the current iso might modify the preferences file in /etc/apt to pin only the foregoing files and then upgrade everything using "sudo aptitude upgrade."  After that, I would install the 1.91 version of casper and see how that works for you.

---

### Post by mjpca on 2007-06-22
Hazridi,

That's great news.  If you can come up with a patched 2.6.20 kernel, we can probably incorporate it.

---

### Post by mjpca on 2007-06-22
Vinze,

The other thing that became pretty obvious to me when playing around with all of these pinned files is that we can probably start with the feisty squashed filesystem and save a lot of time.  The 1001 priority code in the preferences file will force a downgrade to the lower versioned packages.

So if, in addition to having the feisty repositories in your sources list, you add the edgy main and restricted repositories and run sudo aptitude upgrade, it will not only upgrade the feisty files as appropriate, but downgrade the pinned files to the edgy version.  Probably a lot easier.  I had previously thought that this would be the case (and I know ASP Cartmann had also mentioned it), but until I narrowed down the pinned files to a few files, I had just never focused on that approach.

---

### Post by mjpca on 2007-06-22
Ok, so I just confirmed, at least on a persistent usb drive, that if I only pin the udev file, persistence works (although again deleting the upstart files causes a failure in un-mounting local filesystems upon shutdown).

Pinning udev does force the dmsetup file to be held back as well.  I think that that file may have been eliminated in feisty.  So, maybe the issue relates to dmsetup in some manner.

---

### Post by mjpca on 2007-06-22
Pinning udev also causes hal, libdevmapper1.02, and volumeid to be held back.  So, I guess it could be any of those or something about the way they work together.

---

### Post by todlangweilig on 2007-06-22
I'm using the first iso, downloading the second right now. I'm going to test out the "debug" parameter now on the first iso.  

My casper-rw partition is formated ext2 and isn't empty. Here are the contents:
```

/media/casper-rw$ ls -l
total 48
drwxr-xr-x  2 root root  4096 2007-06-20 13:29 cdrom
drwxr-xr-x  2 root root  4096 2007-06-20 13:30 dev
drwxr-xr-x 16 root root  4096 2007-06-21 14:11 etc
drwxr-xr-x  3 root root  4096 2007-06-20 13:29 home
drwx------  2 root root 16384 2007-06-19 14:59 lost+found
drwxr-xr-x  2 root root  4096 2007-06-20 13:29 rofs
?---------  ? ?    ?        ?                ? sbin
drwxrwxrwt  5 root root  4096 2007-06-21 14:11 tmp
drwxr-xr-x  4 root root  4096 2007-06-20 15:02 usr
drwxr-xr-x  5 root root  4096 2007-06-20 13:30 var

```

---

### Post by mjpca on 2007-06-22
Was it empty when you first booted?

If not, you may need to delete everything except for the lost and found directory (and maybe your home directory) and they try it again.

Vinze,

I wasn't able to get the "downgrade" method to work when creating the  squashed filesystem.  So, I have gone back to starting with the edgy squashed filesystem.

---

### Post by todlangweilig on 2007-06-22
I believe it was empty the very first time I booted. I wonder if something in the boot process corrupted it, and later boots didn't overwrite the bad files. I erased my partitions to install the second iso. 

I download the second iso, and it works much better. It booted without error the first time, and noticably faster than before. 

The biggest thing that I noticed is that the desktop effects don't work anymore on my machine. When I click the enable button, the screen turns white. Clicking the button again turns off the effects and restores the screen. 

It also doesn't seem to remember network settings.

Things that worked right:
Installed/remembers idle, remembers background picture, remembers time server selection. 

Yay, this is cool. All in all, it's working much better now. :)

---

### Post by Vinze on 2007-06-22
> **mjpca said:**
> Vinze,

I wasn't able to get the "downgrade" method to work when creating the  squashed filesystem.  So, I have gone back to starting with the edgy squashed filesystem.

Too bad, it sounded really cool. Anyway, the Xubuntu LiveUSB works for me now so I hope I won't need to start the process again.

---

### Post by Fisslefink on 2007-06-22
**[SIZE="3"]How to use GRUB instead of Syslinux[/SIZE]**

For those who care, the GRUB bootloader works with this, which can help clean up your USB key.

Why use GRUB? 
Syslinux is messy.  Following the guide on Vincent's Xubuntu blog ([here]("http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/")), I got the Ubuntu liveUSB persistence working under syslinux.  However, this process put a LOT of files in the root directory of my USB key, since syslinux must access these files at the toplevel directory.  I use my 2GB USB drive as an Ubuntu liveUSB drive and also as a standard USB key for shuttling files between computers, and I don't like having all that stuff there, where I am liable to delete it!  

**With GRUB, the FAT16 partiition of my USB key looks like this:**
```

/boot
/casper
```

**How to get GRUB working**
1. First, get persistence working by following Vincent's guide ([here]("http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/"))
2. Boot from a liveCD (any will do) without the USB key plugged in.
3. Plug in the USBkey.  The FAT16 partition should be mounted and made writeable.  Open a terminal and go to the top level folder in the FAT16 partition.
```
cd /media/UbuntUSB
```
4. Make a directory called "toplevel" where you can store all of the extra files (and get them back if you need them)
```
mkdir toplevel
```
5. Move everything except the "casper" folder into the "toplevel" folder (or move everything, then take the casper folder back out)
```
mv /media/UbuntUSB/* /media/UbuntUSB/toplevel
mv /media/UbuntUSB/toplevel/casper /media/UbuntUSB

```
6.  Make a directory called "boot" and a directory called "MBRbackup"
```
mkdir boot MBRbackup
```
Now ack up the MBR and FAT from your USB key to this folder using the following commands.  You must first determine the drive name of your USB key's FAT16 partition using 'mount'.  Replace 'sdx' below with your correct drive name.
```

dd bs=512 count=1 if=/dev/sdx of=/media/UbuntUSB/MBRbackup/sdx.mbr
dd bs=512 count=1 if=/dev/sdx1 of=/media/UbuntUSB/MBRbackup/sdx1.mbr
dd bs=512 count=1 if=/dev/sdx2 of=/media/UbuntUSB/MBRbackup/sdx2.mbr
```
[INDENT]TROUBLESHOOTING:  To restore your syslinux MBR, just invert the "if=" and "of=" in the above commands[/INDENT]

7.  Install grub to the /boot folder on the USB key. Replace '/dev/sdx' below with your correct drive name.
```

sudo grub-install --root-directory=/media/UbuntUSB --no-floppy /dev/**sdx**
```

[INDENT]TROUBLESHOOTING:  Grub-install will output the device map it determined from the BIOS.  Typically, it will determine something like this: 
```
(hd0)   /dev/sda
(hd1)   /dev/sdb
```
However some computers, especially those with SATA hard drives, will identify the USB key as hd0 when booting from the USB key, and as hd1 when booting from a CD or the hard drive.  If using the default device map does not work for you, make the following file:
/media/UbuntUSB/boot/grub/device.map
containing the following:
```
(hd0)   /dev/sdb
(hd1)   /dev/sda
```
...and rerun step 7.  This way, grub-install will use the new device.map and your USB key will be recognized as (hd0).  Well, it worked for me anyway.
[/INDENT]

8.  Finally, create the file /media/UbuntUSB/boot/grub/menu.lst
containing the following:
```
# menu.lst - Customized for Ubuntu persistent USB drive


default         0
timeout         3

color white/brown yellow/brown
# comment out the 'color' line above if using the splash image!

# uncomment the 3 lines below to use the splash image:
#splashimage 	(hd0,0)/boot/grub/images/usplash.xpm.gz
#foreground = cb966d
#background = 311700

title           Persistent Desktop
root            (hd0,0)
kernel          /casper/vmlinuz boot=casper persistent ramdisk_size=1048576 root=/dev/ram rw quiet splash --
initrd          /casper/initrd.gz

title           Live Desktop
root            (hd0,0)
kernel          /casper/vmlinuz boot=casper ramdisk_size=1048576 root=/dev/ram rw quiet splash --
initrd          /casper/initrd.gz
boot

title           Live Desktop (Verbose)
root            (hd0,0)
kernel          /casper/vmlinuz boot=casper ramdisk_size=1048576 root=/dev/ram rw --
initrd          /casper/initrd.gz
boot

#title           Memory Test
#root            (hd0,0)
#kernel          /install/mt86plus
#boot
```

9.  If you want a slick "Ubuntu" background behind the GRUB menu, follow the commenting/uncommenting directions in my menu.lst (above) and put the attached file (usplash.xpm.gz) in the folder /media/UbuntUSB/boot/grub/images

10.  If everything went smoothly, you have checked that persistence still works, and you're totally happy, then delete the folder 'toplevel' and its contents.  I moved the 'MBRbackup' folder into the 'casper' folder for added neatness.

Credits:  Thanks to K0LO on ubuntuforums.org for his great GRUB on pendrives writeup ([here]("http://ubuntuforums.org/showpost.php?p=1229101&postcount=158"))

Okay, I hope that works for others.  Nice work on these persistence images, everyone.  I'm looking forward to trying the Xubuntu images soon!

Fisslefink

---

### Post by Vinze on 2007-06-22
Fisslefink - thanks for that HowTo. I wanted to, besides the normal ISO, also provide a package that just contains all the files for the FAT16 partition - would that also be possible when using GRUB? 

**Encouraging note:** I'm posting this from my XubuntUSB ;)

---

### Post by Fisslefink on 2007-06-22
Vinze:  That's a cool idea, but I don't know if that will even work with Syslinux... have you tried copying all of the USB files to a folder, wiping the drive, then copying them back?  I would think syslinux must load some data into the MBR of the drive, which you would have to tell the user how to do (using the syslinux command).  Give it a try, but don't fool yourself by leaving the syslinux bootloader in the MBR.  If I were you, I'd wipe the MBR first with:
```
dd bs=512 count=1 if=/dev/zero of=/dev/sdx
```
Then run cfdisk to make your partitions from scratch.

Your idea certainly won't be possible using GRUB, because the user would have to load the GRUB bootloader into the MBR.

You could always make a script......... but then you'd have to maintain it, make it customizable based on different sized USB drives, etc.

GRUB does make things prettier, and it makes life easier if you have several images on the same USB key (if it's big enough).

Cheers,

Fisslefink

---

### Post by Vinze on 2007-06-22
> **Fisslefink said:**
> Vinze:  That's a cool idea, but I don't know if that will even work with Syslinux... have you tried copying all of the USB files to a folder, wiping the drive, then copying them back?  I would think syslinux must load some data into the MBR of the drive, which you would have to tell the user how to do (using the syslinux command).  Give it a try, but don't fool yourself by leaving the syslinux bootloader in the MBR.  If I were you, I'd wipe the MBR first with:
```
dd bs=512 count=1 if=/dev/zero of=/dev/sdx
```
Then run cfdisk to make your partitions from scratch.

Your idea certainly won't be possible using GRUB, because the user would have to load the GRUB bootloader into the MBR.

You could always make a script......... but then you'd have to maintain it, make it customizable based on different sized USB drives, etc.

GRUB does make things prettier, and it makes life easier if you have several images on the same USB key (if it's big enough).

Cheers,

Fisslefink

Well, yeah.. But I just wanted to save people the hassle of extracting the ISO, copying the required files, renaming isolinux.cfg to syslinux.cfg and adding the new content. Of course they still had to do the partitioning manually and run the syslinux command. Would something like that be possible with GRUB?

---

### Post by mburris on 2007-06-23
> **Vinze said:**
> Well, yeah.. But I just wanted to save people the hassle of extracting the ISO, copying the required files, renaming isolinux.cfg to syslinux.cfg and adding the new content. Of course they still had to do the partitioning manually and run the syslinux command. Would something like that be possible with GRUB?

Yes this would be possible, in the instructions, after the user would extract the package or archive you create to the UbuntUSB partition on the usb stick, they would have to run the commands to setup the MBR on the stick:

```
sudo grub-install --root-directory=/media/UbuntUSB --no-floppy /dev/sdx
```

after that this should work fine.

---

### Post by mburris on 2007-06-23
Is it possible to make changes to the system while in persistent mode then incorporate those changes into the extracted squashfs.filesystem?

Looking at the contents of the casper-rw partition after changes have been made, it appears to be basically a root system with all the normal folders you would see in root.  

If i were to merge the content of the casper-rw filesystem with the extracted contents of a squashfs.filesystem, then mksquash (recompress the extracted file system) what would happen?

sounds like a killer way to make customizations to a LiveCD, huh?

I'll update this when I know...


UPDATE:
It works!

I installed beryl, and made some other changes to the system while in persistent mode.

copied most of the stuff from /sbin and /usr on the casper-rw partition to a folder where i extracted the live filesystem (from filesystem.squashfs via mount and cp) recompressed the squashfs file (mksquashfs) and copied it back over to my USB stick over writing the previous squashfs.filesystem file that was in the /casper folder of the fat16 partition of my usb drive.  I booted the usb to the live option... and sure enough there is beryl

---

### Post by Vinze on 2007-06-24
> **mburris said:**
> Yes this would be possible, in the instructions, after the user would extract the package or archive you create to the UbuntUSB partition on the usb stick, they would have to run the commands to setup the MBR on the stick:

```
sudo grub-install --root-directory=/media/UbuntUSB --no-floppy /dev/sdx
```

after that this should work fine.

Great, then I'll do that tomorrow.

> **mburris said:**
> Is it possible to make changes to the system while in persistent mode then incorporate those changes into the extracted squashfs.filesystem?

Looking at the contents of the casper-rw partition after changes have been made, it appears to be basically a root system with all the normal folders you would see in root.  

If i were to merge the content of the casper-rw filesystem with the extracted contents of a squashfs.filesystem, then mksquash (recompress the extracted file system) what would happen?

sounds like a killer way to make customizations to a LiveCD, huh?

I'll update this when I know...


UPDATE:
It works!

I installed beryl, and made some other changes to the system while in persistent mode.

copied most of the stuff from /sbin and /usr on the casper-rw partition to a folder where i extracted the live filesystem (from filesystem.squashfs via mount and cp) recompressed the squashfs file (mksquashfs) and copied it back over to my USB stick over writing the previous squashfs.filesystem file that was in the /casper folder of the fat16 partition of my usb drive.  I booted the usb to the live option... and sure enough there is beryl

Yeah, basically you did what Mike did before. Though if you'd want to make a customized LiveCD that can be [done much easier](http://reconstructor.aperantis.com/).

---

### Post by mburris on 2007-06-24
> **Vinze said:**
> Yeah, basically you did what Mike did before. Though if you'd want to make a customized LiveCD that can be [done much easier](http://reconstructor.aperantis.com/).

I actually started out using reconstructor, but I found that for some reason, after i added custom usplash, gui splash, wallpaper, apps, custom themes, and other stuff, it would not allow me to log in at the welcome screen.  I was disapointed with the amount of support and just overall alive-ness of the project, so I ended up manually doing all the steps.  I did get some good suggestions from the reconstructor.py script that reconstructor uses though.  

At this point in the game i've figured out how to run GUI applications while i'm chroot'ed into my extracted live squashFS, so there's really nothing I fell like i can't do now.  This allows me to use gconf-editor instead of its command-line cousin to make changes to many gnome related things.  The only tricky thing about that was figuring out that you have to move the .gconf files that are created in the %ExtractedLiveSquashFS% root folder to the %ExtractedLiveSquashFS% /etc/skel folder.  Since as you probably already know things in the skel folder become %root%/home/ubuntu in the live environment.

If i didnt say it before, excelent job on patching persistence in 7.04 everyone, i've been following allong since the first report of it not working.

---

### Post by Vinze on 2007-06-26
Fisslefink, I'm now in a LiveCD following your instructions for using GRUB, and I noticed that you said to do the following:

> dd bs=512 count=1 if=/dev/sdx of=/media/UbuntUSB/MBRbackup/sdx.mbr
dd bs=512 count=1 if=/dev/sdx1 of=/media/UbuntUSB/MBRbackup/sdx1.mbr
dd bs=512 count=1 if=/dev/sdx2 of=/media/UbuntUSB/MBRbackup/sdx1.mbr

However, I suppose that last sdx1.mbr ought to be sdx2.mbr ;)

**Edit:** Well, when I rebooted with my USB drive plugged in, my PC would hang before I could do *anything*. I couldn't even "press <del> for setup" or "press F11 for boot menu"! I freaked out, until I recalled that perhaps it would start with my USB drive unplugged. Anyway, I'm reverting back to syslinux ;)

---

### Post by hazridi on 2007-06-26
Building kernel packages is a pain in the ***. Not so much the kernel itself as much as the restricted modules, which requires that EVERY single arch's kernel packages are built... 

I did get unionfs 2.0 merged into 2.6.20-16 from the ubuntu GIT repository, so as soon as everything finishes building I'll copy the initrd and vmlinuz over to the feisty i have installed on the usb drive and see if true Feisty persistence works with a kernel hack.

This has been a long night (I started at 2AM and now it's 1PM).

---

### Post by Vinze on 2007-07-03
Would anyone care to 
[LIST]
[*]Test [my tutorial on how to install Xubuntu on a USB drive](http://xubuntublog.wordpress.com/2007/07/03/xubuntu-feisty-now-from-usb-drive/)
[*]Host my modified Xubuntu files
[*]Seed [the torrent of my modified Xubuntu files](http://linuxtracker.org/torrents-details.php?id=4307)
[/LIST]

Thanks.

---

### Post by pepeio on 2007-07-07
> **Vinze said:**
> Would anyone care to 
[LIST]
[*]Test [my tutorial on how to install Xubuntu on a USB drive](http://xubuntublog.wordpress.com/2007/07/03/xubuntu-feisty-now-from-usb-drive/)
[*]Host my modified Xubuntu files
[*]Seed [the torrent of my modified Xubuntu files](http://linuxtracker.org/torrents-details.php?id=4307)
[/LIST]

Thanks.

The iso can now be downloaded from my server.
[http://88.191.31.14/ubuntuFeistyPatched/](http://88.191.31.14/ubuntuFeistyPatched/)

Thank you, vinze.

---

### Post by Vinze on 2007-07-07
> **pepeio said:**
> The iso can now be downloaded from my server.
[http://88.191.31.14/ubuntuFeistyPatched/](http://88.191.31.14/ubuntuFeistyPatched/)

Thank you, vinze.

Thank you for hosting it pepeio.

---

### Post by pepeio on 2007-07-07
Anyone tested persistence on gutsy tribe2?

[http://cdimage.ubuntu.com/releases/gutsy/tribe-2/](http://cdimage.ubuntu.com/releases/gutsy/tribe-2/)

---

### Post by mjpca on 2007-07-08
As best as I can tell, it looks like persistence may actually be working on tribe2.  

I get a .ICEauthority issue, however, that prevents me from re-booting into persistent mode.  But, I think that that issue shows up because persistence is working and there may be some sort of issue related to the .ICEauthority file that is created in the home directory on the casper-rw partition.

I also confirmed that e.g. my network settings appear to show up on the casper-rw partition.  So, it appears files may be getting created on the casper-rw partition, which I assume would not happen if persistence wasn't working.

It looks like a number of changes were made to the files that were "held back" in the custom iso's.  So, if this .ICEauthority issue can be fixed (assuming others experience that as well), then persistence may be back.

---

### Post by pepeio on 2007-07-08
> **mjpca said:**
> As best as I can tell, it looks like persistence may actually be working on tribe2.  

I get a .ICEauthority issue, however, that prevents me from re-booting into persistent mode.  But, I think that that issue shows up because persistence is working and there may be some sort of issue related to the .ICEauthority file that is created in the home directory on the casper-rw partition.

I also confirmed that e.g. my network settings appear to show up on the casper-rw partition.  So, it appears files may be getting created on the casper-rw partition, which I assume would not happen if persistence wasn't working.

It looks like a number of changes were made to the files that were "held back" in the custom iso's.  So, if this .ICEauthority issue can be fixed (assuming others experience that as well), then persistence may be back.
i also had that .ICEAuthority problem on the custom feisty images, at first boots. I logged in using the console, removed the file then i never had the problem again.
I wil have to try tribe2, i guess. Trying to install a complete java dev environment on feisty seems broken too.
Thanks for the info.

---

### Post by pepeio on 2007-07-11
I kinda confirm too that persistence works on tribe2. At the moment, everything i  changed seemed to have been persisted.
Sounds like good news for the future.
[edit] oh, and i did not have any .ICEauthority problem with tribe2.

---

### Post by Vinze on 2007-07-11
I have had the .ICEauthority problem too, only removing it did not solve it for me. I solved it by wiping my whole casper-rw partition and starting all over again.

Well, I hope persistence will work as it should again in Gutsy.

---

### Post by jimmygoon on 2007-07-14
Which ISO should I use from this page: [http://88.191.31.14/ubuntuFeistyPatched/](http://88.191.31.14/ubuntuFeistyPatched/)

and should I just follow the instructions [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") with one of these ISOs? That will get me a persistent Ubuntu Feisty install?

Thanks!

Reading through this thread invites a sense of nostalgia, I spent weeks customizing, decompressing, recompressing, etc a DSL installation for a picture frame running off a CF card... fun fun... Anywho, I went with the second ISO... This is going to be great. My laptop HD broke so I'm running USB style now.

---

### Post by Vinze on 2007-07-16
> **jimmygoon said:**
> Which ISO should I use from this page: [http://88.191.31.14/ubuntuFeistyPatched/](http://88.191.31.14/ubuntuFeistyPatched/)

and should I just follow the instructions [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") with one of these ISOs? That will get me a persistent Ubuntu Feisty install?

Thanks!

Reading through this thread invites a sense of nostalgia, I spent weeks customizing, decompressing, recompressing, etc a DSL installation for a picture frame running off a CF card... fun fun... Anywho, I went with the second ISO... This is going to be great. My laptop HD broke so I'm running USB style now.

If you want to use Ubuntu then the second ISO was the correct choise ;-)

And I guess you could follow the instructions at [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) too, but be sure to use the customized ISO.

---

### Post by CowzRule on 2007-07-28
> **mburris said:**
> ...   
At this point in the game i've figured out how to run GUI applications while i'm chroot'ed into my extracted live squashFS, so there's really nothing I fell like i can't do now.  This allows me to use gconf-editor instead of its command-line cousin to make changes to many gnome related things.  The only tricky thing about that was figuring out that you have to move the .gconf files that are created in the %ExtractedLiveSquashFS% root folder to the %ExtractedLiveSquashFS% /etc/skel folder.  Since as you probably already know things in the skel folder become %root%/home/ubuntu in the live environment.


How do you run GUI applications while chroot'ed into the extracted live squashFS?

---

### Post by Vinze on 2007-08-05
> **CowzRule said:**
> How do you run GUI applications while chroot'ed into the extracted live squashFS?

I PMed him the same question, and he was so nice as to answer it ;-)

> **mburris][QUOTE=Vinze]Hey, [you said](http://ubuntuforums.org/showthread.php?p=2905900#post2905900)
> At this point in the game i've figured out how to run GUI applications while i'm chroot'ed into my extracted live squashFS, so there's really nothing I fell like i can't do now.

I don't want to get off-topic there, so could you tell me how you did that? I found having to do everything from the command-line a bit awkward, I'm more of a GUI junkie  said:**
> 

Ok first thing you have to do is enable X-server to accept outside graphic input here's how:
open terminal and type:
```
xhost +
```

now copy your existing network resolution file to the squashed filesystem:
(where you see "$squashfs" you need to put the full path to the folder that contains the files that were extracted from the squashfs.filesystem file eg: mine is /home/owner/SquashFS)
```
sudo cp /etc/resolv.conf $squashfs/etc/
```

then you have to mount ubuntu's active proc folder inside the squashed filesystem's root:
(again in terminal type)
```
sudo mount -t proc -o bind /proc $squashfs/proc
```

now we need to chroot into the squashfs folder:
(in terminal)
```
sudo chroot $squashfs /bin/bash
```

now that you are in you can make any changes using whatever tools you want, you just have to start the program from the command line

---

### Post by kdarkentity on 2007-08-05
ive tried getting fiesty to boot off of a usb drive before and i was unsuccessful at making it persistent... as you probably already know the reason has something to do with mounting the second partition to work basicly as your hard drive so that when changes are made they are saved automatically ...fiesty has many issues with mounting things in the right place and detecting what some things are... for example my mp3 player was mounted as a webcam once... this probably wont help u any , but at least im pretty sure thats what the issue is... i have had noo problem booting dapper or edgy from a usb drive... and i have gotten fiesty to run live ... i just cant get the second partition to mount the right way... good luck to you... for all i know u already have your problem fixed

---

### Post by Vinze on 2007-08-06
> **kdarkentity said:**
> ive tried getting fiesty to boot off of a usb drive before and i was unsuccessful at making it persistent... as you probably already know the reason has something to do with mounting the second partition to work basicly as your hard drive so that when changes are made they are saved automatically ...fiesty has many issues with mounting things in the right place and detecting what some things are... for example my mp3 player was mounted as a webcam once... this probably wont help u any , but at least im pretty sure thats what the issue is... i have had noo problem booting dapper or edgy from a usb drive... and i have gotten fiesty to run live ... i just cant get the second partition to mount the right way... good luck to you... for all i know u already have your problem fixed

Yes, it's solved, and I've now updated my first post:

> **Vinze said:**
> **UPDATE:** My problem (a bug in Feisty) is now solved (or rather: worked around). Instructions on how to do this yourself with Ubuntu Feisty can be found [here](http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/) on my blog. Or if you'd rather use Xubuntu, I also have [this guide](http://xubuntublog.wordpress.com/2007/07/03/xubuntu-feisty-now-from-usb-drive/).

Hey, I followed [these instructions](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar) (fairly similar to [these](https://wiki.ubuntu.com/LiveUsbPendrivePersistent), but geared towards Feisty) to put Ubuntu on my USB drive. I finally managed to get it working, it booted and all, but after I rebooted I noticed that everything I had configured and installed was gone! Same when I tried it later with Xubuntu.

Why? I've properly named the partition casper-rw :(

---

### Post by SurJector on 2007-08-21
Hi,

    I've had the same problem as everybody here. I've found what I think is a
  different solution.

    I've needed to modify exactly one file on the initrd: init. More precisely:

    In the initrd, there is exactly one file in the root directory. This file is named
  init. What I had to modify is the following: there is a big 'case $x in ... esac'.
  I've just added the following lines just after the

```

break)
        break=premount
        ;;

```

  and just before the "esac":

```

persistent)
        PERSISTENT=yes
        root_persistence=casper-rw
        home_persistence=home-rw
        ;;

```

    To modify the initrd.gz file you need to do the following:

```

mkdir initrd
cd initrd
gzip -dc /media/cdrom/isolinux/initrd.gz | cpio -i
< change the file "init" as indicated above, using your favorite text editor >
find . | cpio -o -H newc | gzip -9 > ../initrd.gz

```

   You must them either remaster the cd or simply change the initrd.gz on
  your USB key. You can keep each and every other file as is in Feisty, no
  need to pin, you're free to upgrade.

    To be cleaner, you can move the two root_persistence=casper-rw and
  home_persistence=home-rw in file etc/casper.conf (or even in file
  scripts/casper).

     SurJector (posting from its persistent USB key).

---

### Post by bandit36 on 2007-08-28
SurJector -

  You rock!:guitar:

  First off, I'm something of a n00b so someone else smarter than I should verify this.

  After following your instructions I booted my external USB hard drive (w/ Feisty 7.04).  After logging in I changed the desktop color to black and rebooted to test if the change would hold.  When I logged in the second time I found that I was looking at a black desktop - the setting held through the reboot!  I'm assuming that all other changes will also be persistent, but have yet to make sure.

  So far it looks like it works!

---

### Post by Vinze on 2007-08-29
> **bandit36 said:**
> SurJector -

  You rock!:guitar:

  First off, I'm something of a n00b so someone else smarter than I should verify this.

  After following your instructions I booted my external USB hard drive (w/ Feisty 7.04).  After logging in I changed the desktop color to black and rebooted to test if the change would hold.  When I logged in the second time I found that I was looking at a black desktop - the setting held through the reboot!  I'm assuming that all other changes will also be persistent, but have yet to make sure.

  So far it looks like it works!

Great, it seems like a really clean way to work around this!

---

### Post by Faulk_Wulf on 2007-08-29
Hello.

I used Knoppix prior to this, but after working with Ubuntu for a while I came to like it more. 
I came across this thread by going to Google and searching "Feisty Fawn, Persistent Home Directory". 

Would this solution be the equivalent to Knoppix's "home=scan" or is this more about booting from a USB drive instead? 
With Knoppix I used my iPod's hard drive as the hard drive/home directory, and without formating it. 
I was hoping for a solution in Ubuntu that replicated the "home=scan" cheat code option of Knoppix.

Also I want to get some clarification on the procedure that was just described:

* First,  I should open up a terminal and do:*

```

mkdir initrd
cd initrd
gzip -dc /media/cdrom/isolinux/initrd.gz | cpio -i

```

*Then I open up a text editor, and insert the "persistent" section where and as shown below:*

```

break)
        break=premount
        ;;

persistent)
        PERSISTENT=yes
        root_persistence=casper-rw
        home_persistence=home-rw
        ;;

esac

```

*And finally go back into the terminal:*

```

find . | cpio -o -H newc | gzip -9 > ../initrd.gz

```

Assuming I understood all of that,
what do I do after that?

Thank you.

---

### Post by Vinze on 2007-08-30
> **Faulk_Wulf said:**
> Hello.

I used Knoppix prior to this, but after working with Ubuntu for a while I came to like it more. 
I came across this thread by going to Google and searching "Feisty Fawn, Persistent Home Directory". 

Would this solution be the equivalent to Knoppix's "home=scan" or is this more about booting from a USB drive instead? 
With Knoppix I used my iPod's hard drive as the hard drive/home directory, and without formating it. 
I was hoping for a solution in Ubuntu that replicated the "home=scan" cheat code option of Knoppix.

Also I want to get some clarification on the procedure that was just described:

* First,  I should open up a terminal and do:*

```

mkdir initrd
cd initrd
gzip -dc /media/cdrom/isolinux/initrd.gz | cpio -i

```

*Then I open up a text editor, and insert the "persistent" section where and as shown below:*

```

break)
        break=premount
        ;;

persistent)
        PERSISTENT=yes
        root_persistence=casper-rw
        home_persistence=home-rw
        ;;

esac

```

*And finally go back into the terminal:*

```

find . | cpio -o -H newc | gzip -9 > ../initrd.gz

```

Assuming I understood all of that,
what do I do after that?

Thank you.

These steps, as I understand it, would fix the ISO for having a working persistent mode again. However, you still need to put that on a USB drive partition, and have another partition labelled "casper-rw" that will hold all your changes. The partition that you place the extracted ISO on should be formatted with FAT16, casper-rw with ext2.

For detailed instructions, see [this blog post](http://xubuntublog.wordpress.com/2007/07/03/xubuntu-feisty-now-from-usb-drive/), only instead of the *modified Xubuntu image* use the result of the steps you described above. Good luck!

---

### Post by mburris on 2007-08-31
> **SurJector said:**
> Hi,

    I've had the same problem as everybody here. I've found what I think is a
  different solution.

    I've needed to modify exactly one file on the initrd: init. More precisely:

    In the initrd, there is exactly one file in the root directory. This file is named
  init. What I had to modify is the following: there is a big 'case $x in ... esac'.
  I've just added the following lines just after the

```

break)
        break=premount
        ;;

```

  and just before the "esac":

```

persistent)
        PERSISTENT=yes
        root_persistence=casper-rw
        home_persistence=home-rw
        ;;

```

    To modify the initrd.gz file you need to do the following:

```

mkdir initrd
cd initrd
gzip -dc /media/cdrom/isolinux/initrd.gz | cpio -i
< change the file "init" as indicated above, using your favorite text editor >
find . | cpio -o -H newc | gzip -9 > ../initrd.gz

```

   You must them either remaster the cd or simply change the initrd.gz on
  your USB key. You can keep each and every other file as is in Feisty, no
  need to pin, you're free to upgrade.

    To be cleaner, you can move the two root_persistence=casper-rw and
  home_persistence=home-rw in file etc/casper.conf (or even in file
  scripts/casper).

     SurJector (posting from its persistent USB key).

Nice work.  Could have really used this months ago... but very very nice.  And to think, all along it was 1 file in the initrd

---

### Post by GatorDog on 2007-08-31
> **SurJector said:**
> Hi, 
    I've had the same problem as everybody here. I've found what I think is a different solution.
<snip> ....

Editing initrd.gz has solved most of my 'persistence' problems.  My internet
settings, printer setup, etc are persistent between boots. The only thing 
I've run into (so far) that is _not_ persistent is the screen resolution setting.  
Here's my noob approach for a workaround.  I wrote the following bash script 
and attached it to a desktop shortcut.  When I boot up, the first thing I do is:
[LIST]
[*]click on the shortcut
[*]select the screen resolution from dpk-reconfigure
[*]ctrl-alt-backspace  (restarts xserver)
[/LIST]  
After the session logs back in, my screen resulution is set.
The script should be self-explanatory.

```

#!/bin/sh -
#
# program: setup_ScrnRes 0.01 (bash)
# GatorDog/rod  8/29/07
#
#	   Note:either set properties / permissions / execute  in File Browser
#		or  chmod +x setup_ScrnRes in a terminal.
#          I put this program in my home directory. For now I know that
#               /home/me  _does_  get saved on the usb persistent drive!
#
#          Instructions at end of listing for creating Desktop shortcut/launcher.
#
# for: Ubuntu Feisty 7.04 LiveCD on USB jumb drive with persistent partition
#
# reference: "http://ubuntuforums.org/showpost.php?p=3228722&postcount=157"  
#            "http://wiki.ubuntu.com/LiveUsbPendrivePersistent"
#            "http://www.debuntu.org/book/export/html/160"
#            "https://help.ubuntu.com/community/LiveCDPersistence"
#                  
#---------------------------------------------------------------------------------


echo " "
echo "Fiesty 7.04 usb install does _not_ retain screen resolution"
echo "            setting between boots."
echo " "
echo " starting: dpkg-reconfigure -phigh xserver-xorg"
echo " "

echo " Select only the highest resolution that works ;^)"
echo "   (un-mark all lower resolutions, they _should_ )"
echo "   (be included in the resulting listing         )"
echo " "
echo " After selecting resolution, [TAB] to the <OK>    "
echo "   before hitting [ENTER]"
#sleep 2

sudo dpkg-reconfigure -phigh xserver-xorg 2>/dev/null
	#    The "2 > /dev/null" will pipe Standard Error (stderr) 
	#    output to /dev/null (which means i'll not appear on the screen).
	#    To save output: 2>/tmp/myscript_errs.txt

echo " "
echo " "
echo "Xwindows must be restarted to select the new resolutions."
echo "   ( to restart xwindows: )"
echo "    ----------------------
echo "    > ctrl-alt-backspace <"
echo "    ----------------------"
echo " "
echo "After restarting, (ie. ^alt-backspace), the new screen "
echo "      resolution you selected will be active."
echo " "
echo "      If not then: "
echo "         System > Preferences > Screen Resolution "
echo "         Pick desired resulution"
echo " "

echo "----------------------------------------------- "
echo " "
echo "( This window will close --                   )"
echo "( After window closes, allow a moment for     )"
echo "(       config file to be written.            )"
echo "(       ie. wait for usb led to stop blinking.)"

sync
sleep 10

# remove backup files, (they accumulate)
# NOTE: everytime you run dpkg-..... , it creates a new
#       backup file for xorg.conf  in  /etc/X11 with
#       the date appended to it. Cleanup is inevitable.

sudo rm /etc/X11/xorg.conf.* 

# --------------------------------------------------------
#	Create a destop shortcut
#
# -right click on desktop
# -create launcher
#	Type: Application
#	Name: ScrnRes
#	Command: [Browse] select setup_ScrnRes (this program)
#	Comment: 
#       [No Icon] - Click / select an icon. ( gdm-setup.png)
#	[OK]
#
# -right click on new launcher icon
#	Properties > Launcher
#	Command: sudo xterm -title "Select highest screen resolution only" \
#                  /home/ubuntu/setup_ScrnRes -geo 90x40 -fg black -bg white -cr red 
#
#	[Close]
# ---------------------------------------------------------


```

I found out the hard way that the  usb jacks on the side of the Dell monitor
are not dependable.  Several times while trying to get the liveUSB going, the 
usb drive would disappear from the screen and Ubuntu was effectively locked
up.  I thought it was problem with the liveUSB install.  Twice it must have lost 
connection during a write. That made Ubuntu on the usb drive un-bootable.
I was able to recover by using a live CD, mounting the 2nd partition and deleting 
all the files on the 2nd partition.  That is, after the first install, I haven't had 
to repartition or reformat the usb drive. 

I also hosed the liveUSB once by trying to do an apt-get update.  On a 1g usbdrive,
there doesn't appear to be much room left for the 2nd (persistent) partition. 

It seems that if I occasionally make a backup of the 2nd partition, I could easily
restore just by copying a saved backup to the 2nd partition.  


(also posting from persistent USB drive)

---

### Post by regles on 2007-08-31
Maybe you should check out the way MCNlive has solved persistence. I like it a lot. Would be nice if Ubuntu live had such a mechanism

---

### Post by mjpca on 2007-09-01
Yes, Surjector.  Really nice solution.

---

### Post by Hugo Bio on 2007-09-04
Anybody willing to seed a functional iso, for the ones lacking time?
Or maybe a script to do so... even one modified version of the file i need to replace?

Sorry for being such a lazy guy, i'm really busy nowadays...


Thanks!

---

### Post by GatorDog on 2007-09-05
> **Hugo Bio said:**
> Anybody willing to seed a functional iso, for the ones lacking time?
Or maybe a script to do so... even one modified version of the file i need to replace?

Sorry for being such a lazy guy, i'm really busy nowadays...

Thanks!
      *( usb bar = usb drive = usb stick = jumpdrive = pen drive etc....)*

Download the zipped files for partition 1 for the liveUSB drive. 
(Includes the edited file).
>>> [http://www.gigasize.com/get.php/3195500854/Ubuntu_7.04_liveUSB_persistence_partition-1.gz](http://www.gigasize.com/get.php/3195500854/Ubuntu_7.04_liveUSB_persistence_partition-1.gz)
You'll need to know it's path in a couple of more steps. 

If you haven't partitioned your usb drive yet, follow instructions here:
>>> [http://www.debuntu.org/book/export/html/160](http://www.debuntu.org/book/export/html/160)
When you get to **3.3. Copying the files to the usb bar** instead of copying the
files do this.

From the previous step (3.2) your usb drive should be mounted as /tmp/liveusb
Open a terminal window and enter the following lines:  
```

cd /tmp/liveusb
gzip -dc /path/to/Ubuntu_.....gz  |  cpio -i 
```

That should unzip and copy the files for the usb version.  Now continue with
step **3.4. Making the usb bar bootable**  

Sorry if my instructions are sophmoric, I'm noob and don't know what your
level of expertise is.  If the download server is busy, try again later.  The file
should be hosted for 45 days.  It's 600meg+. 

GatorDog/rod

---

### Post by mburris on 2007-09-06
> **GatorDog said:**
> Editing initrd.gz has solved most of my 'persistence' problems.  My internet
settings, printer setup, etc are persistent between boots. The only thing 
I've run into (so far) that is _not_ persistent is the screen resolution setting.  
Here's my noob approach for a workaround.  I wrote the following bash script 
and attached it to a desktop shortcut.  When I boot up, the first thing I do is:
[LIST]
[*]click on the shortcut
[*]select the screen resolution from dpk-reconfigure
[*]ctrl-alt-backspace  (restarts xserver)
[/LIST]  
After the session logs back in, my screen resulution is set.
The script should be self-explanatory.

```

#!/bin/sh -
#
# program: setup_ScrnRes 0.01 (bash)
# GatorDog/rod  8/29/07
#
#	   Note:either set properties / permissions / execute  in File Browser
#		or  chmod +x setup_ScrnRes in a terminal.
#          I put this program in my home directory. For now I know that
#               /home/me  _does_  get saved on the usb persistent drive!
#
#          Instructions at end of listing for creating Desktop shortcut/launcher.
#
# for: Ubuntu Feisty 7.04 LiveCD on USB jumb drive with persistent partition
#
# reference: "http://ubuntuforums.org/showpost.php?p=3228722&postcount=157"  
#            "http://wiki.ubuntu.com/LiveUsbPendrivePersistent"
#            "http://www.debuntu.org/book/export/html/160"
#            "https://help.ubuntu.com/community/LiveCDPersistence"
#                  
#---------------------------------------------------------------------------------


echo " "
echo "Fiesty 7.04 usb install does _not_ retain screen resolution"
echo "            setting between boots."
echo " "
echo " starting: dpkg-reconfigure -phigh xserver-xorg"
echo " "

echo " Select only the highest resolution that works ;^)"
echo "   (un-mark all lower resolutions, they _should_ )"
echo "   (be included in the resulting listing         )"
echo " "
echo " After selecting resolution, [TAB] to the <OK>    "
echo "   before hitting [ENTER]"
#sleep 2

sudo dpkg-reconfigure -phigh xserver-xorg 2>/dev/null
	#    The "2 > /dev/null" will pipe Standard Error (stderr) 
	#    output to /dev/null (which means i'll not appear on the screen).
	#    To save output: 2>/tmp/myscript_errs.txt

echo " "
echo " "
echo "Xwindows must be restarted to select the new resolutions."
echo "   ( to restart xwindows: )"
echo "    ----------------------
echo "    > ctrl-alt-backspace <"
echo "    ----------------------"
echo " "
echo "After restarting, (ie. ^alt-backspace), the new screen "
echo "      resolution you selected will be active."
echo " "
echo "      If not then: "
echo "         System > Preferences > Screen Resolution "
echo "         Pick desired resulution"
echo " "

echo "----------------------------------------------- "
echo " "
echo "( This window will close --                   )"
echo "( After window closes, allow a moment for     )"
echo "(       config file to be written.            )"
echo "(       ie. wait for usb led to stop blinking.)"

sync
sleep 10

# remove backup files, (they accumulate)
# NOTE: everytime you run dpkg-..... , it creates a new
#       backup file for xorg.conf  in  /etc/X11 with
#       the date appended to it. Cleanup is inevitable.

sudo rm /etc/X11/xorg.conf.* 

# --------------------------------------------------------
#	Create a destop shortcut
#
# -right click on desktop
# -create launcher
#	Type: Application
#	Name: ScrnRes
#	Command: [Browse] select setup_ScrnRes (this program)
#	Comment: 
#       [No Icon] - Click / select an icon. ( gdm-setup.png)
#	[OK]
#
# -right click on new launcher icon
#	Properties > Launcher
#	Command: sudo xterm -title "Select highest screen resolution only" \
#                  /home/ubuntu/setup_ScrnRes -geo 90x40 -fg black -bg white -cr red 
#
#	[Close]
# ---------------------------------------------------------


```

I found out the hard way that the  usb jacks on the side of the Dell monitor
are not dependable.  Several times while trying to get the liveUSB going, the 
usb drive would disappear from the screen and Ubuntu was effectively locked
up.  I thought it was problem with the liveUSB install.  Twice it must have lost 
connection during a write. That made Ubuntu on the usb drive un-bootable.
I was able to recover by using a live CD, mounting the 2nd partition and deleting 
all the files on the 2nd partition.  That is, after the first install, I haven't had 
to repartition or reformat the usb drive. 

I also hosed the liveUSB once by trying to do an apt-get update.  On a 1g usbdrive,
there doesn't appear to be much room left for the 2nd (persistent) partition. 

It seems that if I occasionally make a backup of the 2nd partition, I could easily
restore just by copying a saved backup to the 2nd partition.  


(also posting from persistent USB drive)

The resolution going back to a default is probably caused by a particular part of the casper pre-boot script.  This portion of the script is locaed in the initrd compressed archive in /scripts/casper-bottom/ look for a script named 20xconfig (or something like that) and see what happens if you remove this file from the init archive altogether. If that doesnt work, you can remove a specific line from said script file.   that line is something like "casper-reconfigure -phigh xserve-xorg" something like that....

I dont have my dev unit in front of me atm, so i cant confirm.  But im sure someone else would be willing to if i dont get back to this thread anytime soon/

---

### Post by Vinze on 2007-09-12
Has anyone managed to get Gutsy working? I tried to (without the workaround) but the Usplash wouldn't come up, so I haven't even tried persistence. In fact, the menu (the one defined in syslinux.cfg) didn't even show up...

---

### Post by matburton on 2007-11-03
Hey,

Anyone got this grub trick working with gutsy? I just get thrown to busybox after a while when trying to boot.

I have a usb stick with various useful things to boot from: DSL, GPrated Live, True Backup etc using grub. I used to have Feisty on as well with one quirk where I had to press enter half way through booting. Now with the live version of gutsy and grub I just get an instance of busybox after a few moments?

Anyone else tried this? Did you succeed of fail? Any other ways of booting the live version of ubuntu through grub?

Cheers

---

### Post by Vinze on 2007-11-04
> **Vinze said:**
> Has anyone managed to get Gutsy working? I tried to (without the workaround) but the Usplash wouldn't come up, so I haven't even tried persistence. In fact, the menu (the one defined in syslinux.cfg) didn't even show up...

I haven't got it working with Grub (didn't try, too), but I thought I'd post a notice that I got it working for Gutsy.

---

### Post by anirudhlohia on 2007-11-08
Hi,

The settings init file does not seem to work for me :(

I replaced the initrd.gz in liveusb root directory as well as /casper directory.

The boot happens but after selecting "persiste.nt" option after sometime it says unable to read from fd0, block error

However, removing 'persistent' argument from syslinux.cfg file the boot is again sucesssfull but in LiveCD mode

What could I be missing

++Tx
Anirudh

---

### Post by Vinze on 2007-11-08
> **anirudhlohia said:**
> Hi,

The settings init file does not seem to work for me :(

I replaced the initrd.gz in liveusb root directory as well as /casper directory.

The boot happens but after selecting "persiste.nt" option after sometime it says unable to read from fd0, block error

However, removing 'persistent' argument from syslinux.cfg file the boot is again sucesssfull but in LiveCD mode

What could I be missing

++Tx
Anirudh

Are you trying to put Gutsy on USB? If so, see the first post, I've updated it.

---

### Post by anirudhlohia on 2007-11-08
I am trying to install "Ubuntu 7.04, built on 20070415"

The instructions I had used were "http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar" which are very very similar to "https://wiki.ubuntu.com/LiveUsbPendrivePersistent" (or vice versa)

Later, when I found that I cannot persist things. I followed the instructions on "http://ubuntuforums.org/showthread.php?t=427312&page=17" to rectify initrd.gz (and replaced it both in root as well as casper directory)

But, when I have keyword 'persistent' in append section then i am unable to boot only (forget about persistence in this case) but without this word it atleast boots.

What can you suggest. I would avoid installing the new image of 850Mb which has been uploaded cause it would involve downloading image (which i cannot do from office network and in home my liveCD version does not write to other USB sticks [NTFS formatted]) and also formatting my USB again to make it larger for this image (formatting gave me a lot of problem last time). So any other ideas?

Tx

---

### Post by Terrence Enger on 2007-11-11
> **anirudhlohia said:**
> 

The boot happens but after selecting "persiste.nt" option after sometime it says unable to read from fd0, block error


I had the same error.  I think it unlikely that your problem has the same origin, but I do not want to keep my experience secret, either.  So ...

My BIOS showed floppy disk number 1 as a common 1.44MB floppy.  This is strange, as the machine does not have a floopy drive--nor a floppy drive either;  isn't interactive spell check neat?--and never has had one.

Anyway, I marked that entry Disabled in the BIOS, and now I can boot "Persistent".

HTH,
Terry.

---

### Post by crakarjax on 2008-05-18
I'm trying to get this going with xubuntu 8.04, and have added persistance to initrd.gz, and modded the boot loader...

But no persistance.  Anyone do this on the new release  of xubuntu?

---

### Post by Vinze on 2008-05-20
> **crakarjax said:**
> I'm trying to get this going with xubuntu 8.04, and have added persistance to initrd.gz, and modded the boot loader...

But no persistance.  Anyone do this on the new release  of xubuntu?

Yep, me. I'm planning on writing a new guide on this on my weblog, but I'm in the middle of my final exams so I'm a bit short in time at the moment. Keep an eye on my weblog ;)

---

### Post by issih on 2008-05-20
[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

I doubt very much that kubuntu/xubuntu procedures will differ at all.

The site even gives you a patched initrd.gz and a syslinux.cfg file to pull down, so theres very little to get wrong, just follow the instructions carefully and all should be well..

If not you'll have to get a handle on what is actually happening in the boot process, i.e. what kernel and initrd.gz file are actually being loaded and what kernel parameters are required..Its actually pretty simple, but hopefully you can ignore it for now :)

good luck

---

### Post by Vinze on 2008-05-20
> **issih said:**
> [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

I doubt very much that kubuntu/xubuntu procedures will differ at all.

The site even gives you a patched initrd.gz and a syslinux.cfg file to pull down, so theres very little to get wrong, just follow the instructions carefully and all should be well..

If not you'll have to get a handle on what is actually happening in the boot process, i.e. what kernel and initrd.gz file are actually being loaded and what kernel parameters are required..Its actually pretty simple, but hopefully you can ignore it for now :)

good luck

You need to patch your own initrd.gz for Xubuntu or whatever :)
(And I understood from the post above that crakarjax patched his own... But I just see that he is also following [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192) so I'll continue there :))

---

### Post by issih on 2008-05-20
Xubuntu, kubuntu and ubuntu all use the same kernel, and this stuff is all about booting the kernel and loading the correct kernel extensions, the differences between the flavours of ubuntu are much higher level differences between window managers and desktop environments. I'd bet the same exact procedure can be followed for each and every type to get this persistence stuff working, to which end provided the patched initrd.gz file is intended for use with the same kernel (i.e you are aiming for xubuntu 8.04), the patched initrd.gz they supply for ubuntu should work just fine on xubuntu. Give it a try, it won't break anything even if it doesn't. just hit the reset button, its all running from flash and ram anyway..thats the point after all :)

---

### Post by Vinze on 2008-05-21
> **issih said:**
> Xubuntu, kubuntu and ubuntu all use the same kernel, and this stuff is all about booting the kernel and loading the correct kernel extensions, the differences between the flavours of ubuntu are much higher level differences between window managers and desktop environments. I'd bet the same exact procedure can be followed for each and every type to get this persistence stuff working, to which end provided the patched initrd.gz file is intended for use with the same kernel (i.e you are aiming for xubuntu 8.04), the patched initrd.gz they supply for ubuntu should work just fine on xubuntu. Give it a try, it won't break anything even if it doesn't. just hit the reset button, its all running from flash and ram anyway..thats the point after all :)

I already tried using the previously supplied initrd.gz with Xubuntu, and it didn't work, that's why I created my own ;)
(Apart from it not working, it also loaded the Ubuntu Usplash, which isn't really pretty when you're using Xubuntu or whatever :P)

---

