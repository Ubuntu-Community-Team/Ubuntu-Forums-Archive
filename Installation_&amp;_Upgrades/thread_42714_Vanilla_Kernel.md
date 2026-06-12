---
title: "Vanilla Kernel"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by luca_linux on 2005-06-19
I just want to know what happens if I compile and use a vanilla kernel from kernel.org on Ubuntu instead of the one available on Ubuntu repositories.
What are the Ubuntu kernel patches for? What do they change in particular?
The point is that I'd like to compile kernel 2.6.12 which has great improvements for my laptop.
Will I ever find kernel 2.6.12 on Ubuntu repositories?
Ok, thanks in advance for the answers.

---

### Post by luca_linux on 2005-06-20
And what about using the vanilla kernel + -mm patchset by Andrew Morton?

---

### Post by jdong on 2005-06-20
Hmm, Ubuntu Patches include , among others, evms, inotify, and various other integration/bugfixes for Ubuntu. They aren't as massive as like RedHat/Fedora kernel patches, without which those OS'es barely run..

I typically run on Ubuntu a vanilla kernel patched with -ck for performance, and then hand-picked patches from other trees where I deem necessary (i.e. new network drivers, etc).

I don't recommend using the -mm patches. It's like the kernel's beta-testing tree. Pull individual patches from it if you need, but never run the whole thing unless you want to help test the next kernel.

---

### Post by skoal on 2005-06-20
skoal@morpheus:///tmp $ uname -a
Linux morpheus **2.6.12-custom** #1 Sun Jun 19 23:07:27 CDT 2005 i686 GNU/Linux

Works great here! I don't know what patches the maintainers apply to old kernels, but I trimmed out all the fluff from mine, and added some fluff back in myself.  Make your own kernel package and give it a shot. I didn't apply any 'patch sets' myself and Ubuntu still works like a charm.  It's kernelreffic!

\\//_

---

### Post by hardwarder on 2005-06-20
How do you go about patching the kernel? I haven't tried this before as I have only used the pre-built kernels.

Edit:spelling

---

### Post by luca_linux on 2005-06-20
[QUOTE=jdong]Hmm, Ubuntu Patches include , among others, evms, inotify, and various other integration/bugfixes for Ubuntu. They aren't as massive as like RedHat/Fedora kernel patches, without which those OS'es barely run..

I typically run on Ubuntu a vanilla kernel patched with -ck for performance, and then hand-picked patches from other trees where I deem necessary (i.e. new network drivers, etc).

I don't recommend using the -mm patches. It's like the kernel's beta-testing tree. Pull individual patches from it if you need, but never run the whole thing unless you want to help test the next kernel.[/QUOTE]
 Is the performance of -ck patchset as good as the -mm's?

---

### Post by TheRealEdwin on 2005-06-20
I too need a guide on building your own kernel. i've looked for one but my googlefu sucks.

---

### Post by luca_linux on 2005-06-20
I've just written a HowTo: [http://ubuntuforums.org/showthread.php?t=43065](http://ubuntuforums.org/showthread.php?t=43065)

---

### Post by jdong on 2005-06-20
[QUOTE=luca_linux]Is the performance of -ck patchset as good as the -mm's?[/QUOTE]

Much better. I find the -mm patchset to be very quirky at times....

---

### Post by luca_linux on 2005-06-21
Ok, now I'm running a vanilla kernel 2.6.12 patched with -ck patchset.
The performances are great.
I'm wondering about why some of the -ck performance improvements are not in the vanilla tree...

---

### Post by luca_linux on 2005-06-21
Another question, but pretty useless I think: now at boot I don't have anymore the phrase "Starting Ubuntu...".
Do you have it? I'm just curious 'cause I know it doesn't matter.

---

### Post by jdong on 2005-06-21
-ck patchsets
  1) Optimize the kernel for so specific reasons (i.e. desktop interactivity, server loads, etc) that they aren't generic enough to be a part of the main kernel.
  2) Contain patches that kernel maintainers don't think are well-tested enough yet.


The Starting Ubuntu... message comes from the initrd. Since your kernel has everything compiled in, it doesn't have an initrd.

---

