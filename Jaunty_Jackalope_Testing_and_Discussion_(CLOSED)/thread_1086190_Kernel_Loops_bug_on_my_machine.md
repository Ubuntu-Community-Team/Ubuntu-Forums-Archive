---
title: "Kernel Loops bug on my machine"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by douham on 2009-03-03
Hi, this post is in regards to this bug [http://bugs.launchpad.net/bugs/330663]("http://bugs.launchpad.net/bugs/330663")

Specifically in regards to the comment by Alan Jenkins;
"The low memory corruption warning refers to RAM.  It's likely to be the
underlying cause of the ext3 errors.  By default the first 64k is
reserved and checked for this error.  So it won't protect against
corruption above this area.  (The corruption caused by the BIOS
scribbling where it shouldn't during suspend/resume).

Maybe try increasing the reserved area.  There's a kernel option you can
add at the GRUB prompt.  E.g.

memory_corruption_check_size=1024k"

I take this instruction as editing the kernel line in my boot menu.list to look like this
```
## ## End Default Options ##

title		Ubuntu jaunty (development branch), kernel 2.6.28-8-generic
uuid		f70d5396-ed79-4feb-8c6d-b7cec0e08d1f
kernel		/boot/vmlinuz-2.6.28-8-generic root=UUID=f70d5396-ed79-4feb-8c6d-b7cec0e08d1f ro quiet splash memory_corruption_check_size=1024k
initrd		/boot/initrd.img-2.6.28-8-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-8-generic (recovery mode)
uuid		f70d5396-ed79-4feb-8c6d-b7cec0e08d1f
kernel		/boot/vmlinuz-2.6.28-8-generic root=UUID=f70d5396-ed79-4feb-8c6d-b7cec0e08d1f ro  single
initrd		/boot/initrd.img-2.6.28-8-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		f70d5396-ed79-4feb-8c6d-b7cec0e08d1f
kernel		/boot/memtest86+.bin
quiet
```

This renders Jaunty unbootable, except in recovery mode>resume normal boot. Is anyone able to pass comment on if my kernel line and to whether i'm right or wrong please
Cheers, Doug

---

### Post by douham on 2009-03-05
I can understand how comments like quiet and splash can carry through the boot process. I've read numerous online articles about the kernel parameters. and of all of them this has been the best.
[https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")

 Is it best to add a new line to grub? regards the corouption_check and how do I go about it.

Doug

---

