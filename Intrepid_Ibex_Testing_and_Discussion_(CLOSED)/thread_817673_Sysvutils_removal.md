---
title: "Sysvutils removal?"
date: 2008-06-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2008-06-03
Have got this update this evening---has anyone else seen it?

---

### Post by scradock on 2008-06-03
Yes - don't advise going ahead! Wait until they sort it out.

There's an update to apt that won't install without removing synaptic and aptitude, plus a bunch of other stuff, as well......

---

### Post by autocrosser on 2008-06-03
Yes-I've held those updates back. I was very sure that there was a problem in the making :)

---

### Post by scradock on 2008-06-03
Actually, I checked the definition of sysvutils, and it explicitly says that it can be removed without danger, even though it's marked as a System file, and warnings are attached.

So I tried it. I removed just sysvutils in Synaptic; it warned that it would be removing a bunch of other things - startup-tasks, system-services, upstart, ubuntu-minimal, and so on. I wrote them all down, and clicked OK.

Then I upgraded one of the other packages that had been linked to sysvutils, and it pulled in another one. I made sure I re-installed all the packages that had been removed BEFORE doing the re-start.

And it worked! All the linked packages are upgraded, no crashes, reboots fine. I also did the laptop packages that showed up in the middle - no problems. That only leaves the apt problem and a muddle over gcc-4.2 at the moment....


HTH

---

### Post by ShirishAg75 on 2008-06-03
waiting for this to get sorted out as well ;)

---

### Post by autocrosser on 2008-06-03
OK--I did the same as scradock--I used Synaptic & removed sysvutils--Took a screenshot of everything that it was removing & reinstalled all of it after the removal. Reboot was interesting--I saw a "rescan" of the system about 5 sec into the boot & then it settled down nicely.... Only wish that I could run "splash" instead of "quiet splash" to see what it was doing at those times.

(screenshot included)

---

### Post by ShirishAg75 on 2008-06-04
Did the same, have to reboot to see what happens. While it was doing the removal it asked if one wants to update the configuration file or not to the new version. I don't know what I did is right or wrong but I gave for updation of the same. The file which got updated/upgraded is /etc/init.d/rc.local 

Any idea or advice on the same would be nice. 

Another small point, the sysvutils got for the first time merged with debian since dapper, that's really a long long time. 

sysvinit (2.86.ds1-56ubuntu2) intrepid; urgency=low

  * debian/control: Use versioned Conflicts: of sysvinit-utils not unconfuse
    apt during upgrades.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Tue, 03 Jun 2008 22:10:02 +0200

sysvinit (2.86.ds1-56ubuntu1) intrepid; urgency=low

  [B]* Merge with Debian unstable (first time since Dapper!). Debian adopted most
    of our changes, sometimes with slight modifications. Adopt to the Debian
    structure as far as possible to minimize the delta.[/B] Remaining changes:
    - Support Cell processor:
      + debian/initscripts/postinst: Create spu system group and /spu mount
        point if we are running on a Cell processor.
      + debian/initscripts/etc/init.d/mountkernfs.sh: Mount spufs if Cell
        processor is detected.
      + debian/control: Add initscripts dependency 'passwd' for groupadd.
      (Forwarded to Debian #483399)
    - Use tmpfs mounts for /var/lock and /var/run:
      + debian/initscripts/share/default.rcS: Enable RAMRUN and RAMLOCK by
        default.
      + debian/initscripts/postinst: Enable RAMRUN and RAMLOCK in
        /etc/default/rcS on upgrades. This needs to be kept until the next
        LTS.
      + debian/initscripts/etc/init.d/mountkernfs.sh: Propagate files from the
        initramfs to our new /var/run, so that we can populate
        /var/run/sendsigs.omit from initramfs.
    - Different boot order: (to be checked if still required):
      + debian/initscripts/postinst: Change the rcS priorities of a bunch of
        init scripts.
      + Disable bootlogd, since it is handled by upstart in Ubuntu.
    - Usplash support:
      + debian/initscripts/etc/init.d/sendsigs: Call usplash_down on stop.
        (This should go away and get integrated into the existing splash API.)
    - Usplash fsck integration:
      + debian/initscripts/lib/init/usplash-fsck-functions.sh: Functions for
        reporting fsck progress in usplash.
      + debian/initscripts/etc/init.d/check{root,fs}.sh: Include
        usplash-fsck-functions.sh and use it if usplash is running.
    - debian/initscripts/etc/init.d/sendsigs: Always mount devpts, and do not
      touch /dev/ptmx (which is already managed by udev).
    - debian/initscripts/etc/init.d/checkroot.sh: If ACPI is available, load
      the ac module before checking the root filesystem, so that fsck can
      skip the check when running on battery. (LP #89752, forwarded to 
      Debian #483394)
    - debian/initscripts/etc/init.d/mountkernfs.sh: Drop mounting of usbdevfs
    (/proc/bus/usb), it was deprecated long ago. (Forwarded to Debian #483392)
    - debian/patches/91_sulogin_lockedpw.dpatch: Disable "root account is
      locked" warning, since this is the default in Ubuntu. Document this in
      sulogin.8.
    - debian/initscripts/etc/init.d/mountall.sh: Set $LANG from
      /etc/default/locale, so that ntfs-3g and friends can get correct file
      name encodings. (LP #132357, forwarded to Debian #483396)
    - debian/initscripts/etc/init.d/umountroot: mkdir a few essential
      directories (/proc, /sys, /var/{run,lock}), right before mounting root
      r/o. It is a convenient (and one of the very few possible) place to
      ensure that the next boot will succeed. (Forwarded to Debian #483393)
    - debian/initscripts/preinst: Fix typo in eliminate_conffile() which broke
      the entire function. (Forwarded to Debian #483391)
    - debian/control: Do not make sysvinit essential, so that we can replace
      it with upstart.
    - debian/sysv-rc/sbin/update-rc.d: Support 'multiuser' argument for
      backwards compatibility. This is deprecated now, since Debian adopted a
      different strategy, and for getting in sync with Debian the runlevels
      should be specified manually.
    - debian/control: Previous name for sysvinit-utils was 'sysvutils' in
      Ubuntu, so Conflict/Replace/Provide it. Also create a dummy sysvutils
      package, since Hardy has reverse versioned dependencies to it. This
      needs to be kept until after the next LTS.
    - debian/initscripts/{pre,postinst}: waitnfs.sh -> mountnfs.sh renaming
      transition. This needs to be kept until after the next LTS.
  * This version from Debian now kills processes using remote file systems in
    a proper way. (LP: #42121)

 -- Martin Pitt <martin.pitt@ubuntu.com>  Wed, 28 May 2008 17:58:44 +0200

---

### Post by autocrosser on 2008-06-04
Yes-I generally keep my version (I do check to see if not changing to the update version will change things for the "better"). This system still has some Edgy/Feisty parts in it ;) -- so there are times I tread lightly.

---

### Post by ShirishAg75 on 2008-06-04
[long sigh]
Right. Btw I also did the same as scraddock and you did and the system is functioning as well 
[/long sigh]

The differences between the old and new would have been better, unfortunately didn't have the diff. If anybody knows what the differences are in the new file would be nice to know. What actually differed from the previous version.

---

### Post by Eclipse. on 2008-06-04
I did:

sudo apt-get -o APT::Force-LoopBreak=yes install sysvutils

Then updates run fine.

---

### Post by plun on 2008-06-04
Well, something went wrong for me and I lost _**sysvinit**_  

Just to go to "the chroot jail" and reinstall sysvinit

Eclipse solution is probably safe....:)

---

### Post by curtis on 2008-06-04
The easy way is just to manually run apt-get install sysvutils first and it will work (might have to install the other sysv package first)

then dist-upgrade works.

---

### Post by autocrosser on 2008-06-04
I tried the manual apt-get route & got the error in my first post--that is why I ended up going the Synaptic-way. Guess I got caught in a bad loop :)

But hey--that's what pre-alpha is all about:lolflag:

---

### Post by ccw on 2008-06-04
> **scradock said:**
> Actually, I checked the definition of sysvutils, and it explicitly says that it can be removed without danger, even though it's marked as a System file, and warnings are attached.

So I tried it. I removed just sysvutils in Synaptic; it warned that it would be removing a bunch of other things - startup-tasks, system-services, upstart, ubuntu-minimal, and so on. I wrote them all down, and clicked OK.

Then I upgraded one of the other packages that had been linked to sysvutils, and it pulled in another one. I made sure I re-installed all the packages that had been removed BEFORE doing the re-start.

And it worked! All the linked packages are upgraded, no crashes, reboots fine. I also did the laptop packages that showed up in the middle - no problems. That only leaves the apt problem and a muddle over gcc-4.2 at the moment....


I did this successfully too. I'm sure they expect to implement a cleaner transition soon, so I wouldn't recommend it unless you understand what you are doing.

---

### Post by autocrosser on 2008-06-04
As far as I know--we are moving to upstart with this release--I like the idea that it is a dynamic loader.

---

### Post by cariboo on 2008-06-04
I just let it run and it totally hosed my system. Reported it as a bug and got four emails back with a solution to the problem, which is of course the same as the previous post.

Jim

---

### Post by autocrosser on 2008-06-05
Sysvutils got a update again this morning---no drama, just a easy install---I am waiting to see when upstart really takes over.

---

### Post by cariboo on 2008-06-05
Got this email this morning aabout the sysvutils problem

---

### Post by Eclipse. on 2008-06-05
> **cariboo907 said:**
> Got this email this morning aabout the sysvutils problem

Yeah, I seen the changelog.

---

