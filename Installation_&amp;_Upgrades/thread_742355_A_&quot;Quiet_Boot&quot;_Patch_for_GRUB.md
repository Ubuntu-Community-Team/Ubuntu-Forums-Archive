---
title: "A &quot;Quiet Boot&quot; Patch for GRUB"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by luvr on 2008-04-01
I'm using a custom-compiled GRUB version as my primary boot loader (i.e., the one that gets loaded from the Master Boot Record).

I have been noticing that, when I select an Operating System from the GRUB menu, and boot it, GRUB will (briefly) echo the commands that it executes while it processes the menu entry, and it adds some extra output as well. For instance, when I select my main Ubuntu system from the menu, here's the output that gets produced before Ubuntu gets control:

```
  Booting '[LINUX]   Ubuntu'

unhide       (hd0,2)
unhide       (hd0,3)
root         (hd1,0)
 FileSystem type is ext2fs, partition type 0x83
makeactive
kernel       (hd1,0)/boot/vmlinuz-2.6.20-16-generic root=UUID=373dd4b0-5e00-487
c-95de-75fa84e7bfa3 ro quiet splash
   [Linux-bzImage, setup=0x1c00, size=0x1a8c4c]
initrd       (hd1,0)/boot/initrd.img-2.6.20-16-generic
   [Linux-initrd @ 0x37950000, 0x69fb83 bytes]
boot
```

I have also been noticing that the GRUB version that comes with Ubuntu, does **not** do this--it will suppress this output.

However, when I applied the Ubuntu *"quiet.diff"* patch, not only did the above output disappear, but also much of the feedback that GRUB normally produces when you enter commands at its command line, were no longer produced.

When I studied the Ubuntu *"quiet.diff"* patch, I discovered that it defines a **quiet_boot** flag variable, and sets its value to 1 (i.e., true). Even though the patch defines a **"quiet"** command (which, supposedly, is meant to turn on or off the quiet boot), all that this function does, is turn **on** the flag (again). There's no way to turn the quiet boot feature **off.**

Furthermore, all output that gets produced while GRUB is booting a menu entry, will be suppressed on the condition that *quiet_boot* is true--i.e., *_always_* (since there's no way to set it to false). Also, since the code that produces this output is also executed in response to commands typed at the command line, the feedback in such a case is suppressed as well.

That's how I got the idea for my own patch (cfr. *"quietboot.diff.tar.gz"* attached here). My patch defines a **"quietboot"** command that can toggle, or turn on or off, the quiet boot feature. Also, the output will be suppressed only while GRUB is processing an entry selected from its menu--**not** when it processes a command that you enter at the GRUB command line. (The *"quietboot"* command should go into the *"general"* section of your GRUB configuration file--i.e., before the first *"title"* line; you can also enter it at the GRUB command line.)

**Note:** The patch matches exactly my custom-built GRUB, which started off with the **"grub-0.97-13.src.rpm"** package from Fedora / Red Hat, and to which I applied the following patches:
[LIST]
[*]**"grub-0.97-disk_geometry-1.patch"** from the Linux From Scratch project;
[*]**"grub_0.97-29ubuntu16.diff"** from Ubuntu;
[*]**"debian/patches/graphics.diff,"** which comes out of the above Ubuntu patch;
[*]**"debian/patches/splashimage_help.diff,"** which also comes out of said Ubuntu patch.
[/LIST]

**P.S.:** I'm well aware that, if you're not familiar with the Linux development tools (e.g., autotools and patch), the above won't make any sense to you. (Sorry about that! I can understand your frustration--I've been there too...) I am considering writing a document that explain the process of building, patching, and installing a custom GRUB version in some detail, though I'm not sure if and when I will get around to doing it.

---

### Post by llbm on 2008-07-16
Thank you very much, it worked like a charm. I applied your patch on the source RPM grub-0.97-13.2.src.rpm for CentOS/RHEL 5.2.

---

