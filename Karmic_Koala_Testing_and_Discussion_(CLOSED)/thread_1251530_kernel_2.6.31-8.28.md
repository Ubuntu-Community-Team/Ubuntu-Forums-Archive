---
title: "kernel 2.6.31-8.28"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by infamousrev on 2009-08-27
How can kernel                                     2.6.31-8.28 be in building queue while kernel.org rc8 is not released yet.

Just a question, not complaining :)

---

### Post by zoomy942 on 2009-08-27
anything to get off of the rc7 kernel.  yikes.

---

### Post by Starks on 2009-08-27
As far as I know, this release is an ABI bump. ABI bumps are not tied to release candidates, but more often than not, they are.

**THE KERNEL IS STILL RC7.**

---

### Post by xebian on 2009-08-27
Seem to have solved the shutdown problem

```
Linux kuntu 2.6.31-8-generic #28-Ubuntu SMP Thu Aug 27 14:42:57 UTC 2009 x86_64 GNU/Linux

```

---

### Post by jithin1987 on 2009-08-27
I am not able to upgrade to 2.6.31-8. 
Aptitude says this.

The following packages are BROKEN:
  linux-headers-generic linux-image-generic
The following packages will be upgraded:
  linux-generic
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8334B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  linux-headers-generic: Depends: linux-headers-2.6.31-8-generic which is a virtual package.
  linux-image-generic: Depends: linux-image-2.6.31-8-generic which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
linux-generic

Keep the following packages at their current version:
linux-headers-generic [2.6.31.7.18 (now)]
linux-image-generic [2.6.31.7.18 (now)]

---

### Post by xebian on 2009-08-27
You need to wait till the repo is complete.

---

### Post by autocrosser on 2009-08-27
You need to purge the Linux-Generic stuff before you can update--or wait until things clear out...The -Generic packages are just metas & won't hurt to be rid of them until it's all straight again---Welcome to Alpha testing>>>>>>

---

### Post by Starks on 2009-08-27
Why are people trying to force the upgrade?

The amd64 or i686/generic packages haven't been built yet.

---

### Post by rudenko_ruslan on 2009-08-27
> **infamousrev said:**
> How can kernel                                     2.6.31-8.28 be in building queue while kernel.org rc8 is not released yet.

Just a question, not complaining :)
It's released - [http://lkml.org/lkml/2009/8/27/386](http://lkml.org/lkml/2009/8/27/386)
[QUOTE=Linus Torvalds]This should be the last -rc, and it's really been quieting down. There's 
131 commits there, and it's all pretty trivial. For example, in the 
dirstat below, most of the arch/x86 changes are due to some vmlinux.lds.S 
changes to fix problems with older binutils, not actual code changes. And 
on powerpc, it's all the ps3 defconfig update.

   8.7% arch/powerpc/configs/
   8.7% arch/powerpc/
   2.6% arch/sparc/configs/
   5.3% arch/sparc/kernel/
   2.8% arch/sparc/mm/
  11.2% arch/sparc/
   5.9% arch/x86/kernel/
   7.0% arch/x86/
  28.3% arch/
   2.6% drivers/acpi/
   3.5% drivers/input/
   7.6% drivers/net/
  13.5% drivers/scsi/mpt2sas/
  30.3% drivers/
   7.7% fs/9p/
   3.4% fs/ext3/
   8.6% fs/notify/inotify/
  21.4% fs/
   3.5% kernel/
   4.0% lib/
   3.0% net/9p/
   5.8% net/
   2.2% sound/core/
   3.2% sound/

So apart from the trivial but somewhat bulky stuff like that, there's a 
sparc TLB loading update, there's a mpt2sas driver update, and there's 
the plan9 filesystem update. And there's a few fs/notify cleanups and 
fixes that will hopefully put the inotify problems behind us for good. 
Knock wood.

The rest is pretty much one-liners with a couple of "few-liners".

I'll be gone for the next week, but it should be quiet. But pester the 
usual suspects (aka "maintainers") about any bugs you see, and they'll fix 
it while I'm diving. And then we'll have a final release for labor day.[/QUOTE]

---

### Post by papangul on 2009-08-27
Anyhow we want to get rid of the current kernel ASAP!

---

### Post by jithin1987 on 2009-08-28
Has anyone been able to install 2.6.31-8 kernel. I cannot find them in my repository so far, other that the meta packages.

---

### Post by benmoran on 2009-08-28
Yeah, .7 is killing me!  I'm just being patient for the repos to update. It's not worth the trouble compiling myself since I still have .6 on my system anyhow.

---

### Post by jppr on 2009-08-28
just updated .31-8 kernel and works ok :)

---

### Post by hgergo on 2009-08-28
i updated too its working ok :)

---

### Post by dino99 on 2009-08-28
I've installed it too hoping that booting become easier but no it is not: always have these lines about "minimal bash-like line ..." before grub menu.

Don't see much changes with that kernel for me.

---

### Post by rudenko_ruslan on 2009-08-28
> **jppr said:**
> just updated .31-8 kernel and works ok :)
Yeah, now I can reboot and shutdown without any problems. Great! :KS

---

### Post by zenarcher on 2009-08-28
Same here.  Working fine for me, as well.

Cheers,
zenarcher

---

### Post by dino99 on 2009-08-28
restart is still a problem for me: i need to unplug & then grub2 claim with "minimal bash-like file"

---

### Post by taavikko on 2009-08-28
> **dino99 said:**
> restart is still a problem for me: i need to unplug & then grub2 claim with "minimal bash-like file"

That's an error in grub, not in kernel per se.
Start a new thread concerning your issue.

---

### Post by VMC on 2009-08-28
> **dino99 said:**
> I've installed it too hoping that booting become easier but no it is not: always have these lines about "minimal bash-like line ..." before grub menu.

Don't see much changes with that kernel for me.

I had this too. I reinstalled and updated grub2 and its now fixed.

---

### Post by Milos_SD on 2009-08-28
I can't boot vanila 2.6.31-rc8 kernel. It stops before loading my tv card (winfast 2000/xp expert -> CX23880/1/2/3 version). Is there someone here that has that problem with ubuntu version of rc8 kernel?

---

### Post by dino99 on 2009-08-28
any logs to help you ?

---

### Post by Milos_SD on 2009-08-28
Here is the syslog:

[http://pastebin.com/m588f4094](http://pastebin.com/m588f4094)

You can see where it stops. I need to do a sysrq so it can continue, but system is not usable after that (read only root, no home, etc ...)

And here is what it should be after that last line in first log:

[http://pastebin.com/m73108e5f](http://pastebin.com/m73108e5f)

---

### Post by pvelkovski on 2009-08-29
Also having boot problem with vanilla kernel 2.6.31rc8. The boot process freezes while hardware drivers are loaded. Vanilla kernel 2.6.31rc7 works fine.

---

