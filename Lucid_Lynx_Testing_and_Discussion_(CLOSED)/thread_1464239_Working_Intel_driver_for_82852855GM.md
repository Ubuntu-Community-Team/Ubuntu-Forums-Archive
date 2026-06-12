---
title: "Working Intel driver for 82852/855GM"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by reidi on 2010-04-28
If Xorg crashes are preventing you from using the 2.6.32 #32 kernel  'cause you have an Intel 855 graphics adapter, try this.  It not only allowed a clean boot with no kernel mode-setting or xorg.conf tweaks, but I also have full compiz functionality.

Originally Posted by glasen here: [http://ubuntuforums.org/showpost.php?p=9121212&postcount=8](http://ubuntuforums.org/showpost.php?p=9121212&postcount=8)

"If you want a stable version of the intel driver (version 2.11git, updated regularly) which works nearly perfectly with KMS(*), you can try the following PPA :

[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

(*) On my Notebook (Dell Latitude D505, Intel 855GM-chipset), the system crashes when i'm closing the lid. Going into suspend mode by using the logout menu and than closing the lid works perfectly."


Highly recommended!

Fujitsu Lifebook S series
Intel 82852/855GM Integrated Graphics Device (rev 02)

---

### Post by RAOF on 2010-04-28
This is unlikely to work for everybody - the 855 chips suffer from a timing-sensitive memory mapping bug.  There's a kernel fix working its way through the various kernel processes, and we hope to pick this up as an SRU for 10.04.

This driver *may* work better for any given person, or it may work worse.  Other people have found that the older 2.8.0 drivers work better.  The workarounds that people have found are documented on the [Lucid i8xx freeze](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) page, linked to from the release notes.

---

### Post by Unicast on 2010-04-28
I tried the solution offered by **reidi** above, and it worked for me.

Removed i915.modeset=1 from grub and installed the driver = cigar. :D

---

### Post by glasen on 2010-04-28
Hi,

As the author of the mentioned PPA, i've some points to add :

[LIST]
[*]The newer driver version could improve the situation with 855GM-chipsets. But it mustn't! For my notebook everything works fine, except that, when using KMS, a lid-closure immediately crashes my notebook. Normal, menu driven suspending works fine. The crash has nothing to do with the Xserver or the intel-driver. It also occurs when i'm booting into single user text mode (Happens with all kernel version from 2.6.32 to latest drm-intel-git-kernel, see also [Launchpad Bug #474380]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474380")).

[*]There are some font rendering issues (aka glyph errors) mostly seen under Firefox. Very often a single letter is rendered not correctly (e.g. the "E" looks more than "F"). This bug is related to the memory mapping bug mentioned above.
[/LIST]
I'm currently testing a backported version of the fix for the 855GM-Bug. I've taken the intel-agp-driver from kernel version 2.6.34rc5, patched it with the bug fix from [FreeDesktop Bugzilla – Bug 27187]("http://bugs.freedesktop.org/show_bug.cgi?id=27187") and applied the other needed diffs the i915-kernel module from the latest lucid kernel. The modules compile cleanly with my own patched (Linux-PHC, 1000Hz) version of the latest Lucid-kernel.

Since yesterday everything seems to work fine. The glyph errors in KMS-mode have all disappeared and in UMS-mode my notebook runs perfectly stable with the latest intel-driver from my PPA and also with the latest Lucid intel-driver. Without the fix when using UMS-mode, my notebook crashes after a few minutes of working or browsing.

There are with issues on my system with the fixed kernel modules :

1. The "wandering dots" in the Plymouth boot-screen have false colors.

2. Some Gtk+-functions are slower than normal. But the situation is not as bad as it sounds. I can perfectly do my normal work (Browsing, emailing, etc.) and also play SDL-based games without noticing any real slowdowns. Only when running the "gtkperf"-Benchmark you can notice a slowdown (Mostly in the "Circles"-Benchmark).

I've made a small DKMS-based package, which i'm currently testing if it compiles cleanly on a normal Lucid installation. If the package does not make any problems, i will add it to my PPA at the end of the week.

---

