---
title: "Kernel Compile"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by Amaravi on 2008-01-08
Hi. I recently installed Ubuntu for the first time. I have managed to get most things running smoothly but am having trouble with the music application, RoseGarden. I am aware that it requires a real time kernel but i am having a bit of trouble compiling the kernel.

I copied the instructions from this page [http://ubuntuforums.org/showthread.php?t=84174](http://ubuntuforums.org/showthread.php?t=84174) but when i do [make-kpkg -initrd --revision=ck1 kernel_image] i get the following messages and no kernel compiled. Please help.


[INDENT]include/asm/mpspec_def.h:78: warning: ‘packed’ attribute ignored for field of type ‘unsigned char[6]’
  LD      init/built-in.o
  LD      .tmp_vmlinux1
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x3d7): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x687): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xd05): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
(.init.text+0xe01): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `parse_header':
initramfs.c:(.init.text+0x3ada): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:(.text+0x4d42): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.14cK1'
make: *** [debian/stamp-build-kernel] Error 2[/INDENT]

Thanks

---

### Post by kellemes on 2008-01-08
ck patchset is obsolete as far as I know..
You need to..
```
sudo apt-get install linux-rt
```

[https://wiki.ubuntu.com/RealTime/Gutsy]("https://wiki.ubuntu.com/RealTime/Gutsy")

---

### Post by Amaravi on 2008-01-09
> **kellemes said:**
> ck patchset is obsolete as far as I know..
You need to..
```
sudo apt-get install linux-rt
```

[https://wiki.ubuntu.com/RealTime/Gutsy]("https://wiki.ubuntu.com/RealTime/Gutsy")

Thanks very much for your help. I am running this now.
Unfortunately I am unsure really of what this is or how this impacts on the remainder of what I have to do to complete this overall process. Was that just a patch or was that a kernel? What do i do now? And most importantly does this ignore the previous settings i entered in menuconfig? I must most importantly ensure that my kernel runs in real time 1000HZ. do i have to do anything more to ensure this?

---

