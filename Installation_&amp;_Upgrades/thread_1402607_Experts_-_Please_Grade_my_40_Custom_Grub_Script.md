---
title: "Experts - Please Grade my 40_Custom Grub Script"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by neu5eeCh on 2010-02-09
Related to my [last post]("http://ubuntuforums.org/showthread.php?t=1402191").

This post was **me** trying to get GeeXboX working on my computer. 

I had no idea how to edit GRUB2 and initially posted my first effort below:

#!/bin/sh
exec tail -n +3 $0

menuentry "GeeXboX 1.2.4 for x86_32 (PC, MacIntel)"  {
    set root=(hd0,5)
    linux    /GEEXBOX/boot/vmlinuz root=/dev/ram0 rw rdinit=linuxrc root=UUID=d46e2773-aba9-41b3-a36b-fc3a6710a474 lang=en keymap=qwerty splash=silent quiet
    initrd    /GEEXBOX/boot/initrd.gz
}

---

### Post by neu5eeCh on 2010-02-09
For future reference (anyone else who finds this post with the same  questions), here is the successful **Grub2** script on my own system:

#!/bin/sh
exec tail -n +3 $0

menuentry "GeeXboX 1.2.4 for x86_32 (PC, MacIntel)"  {
    **[COLOR=Red]set root[/COLOR]**=(hd0,7)
    **[COLOR=Red]linux[/COLOR]**    /GEEXBOX/boot/vmlinuz  root=/dev/ram0 rw rdinit=linuxrc boot=UUID=[COLOR=DarkRed]**fc10669d-9c82-47e8-840a-7ac7119336a4**[/COLOR]  lang=en remote=atiusb receiver=atiusb keymap=qwerty splash=silent  video=vesafb:ywrap,mtrr **[COLOR=Red]quiet[/COLOR]**
    initrd    /GEEXBOX/boot/initrd.gz
}

The menuentry line must end with {
The last line must be }
GRUB2 requires "set root" instead of "root".
GRUB2 requires "linux" instead of "kernel"
Find your own UUID (in red) using the command: **sudo blkid** (There  are other commands that accomplish the same.)
GRUB2 preferred the QUIET command in its new location.

This file edited was 40_Custom, found at **/etc/grub.d. **Edit this  file and run **sudo update-grub. **This will incorporate your edits  of 40_custom into  grub.cfg, located at [B]/etc/grub.cfg.

[/B]Here is an excellent source of information that helped me translate GRUB into GRUB2: [Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2")

And here is another: [How to configure Grub2 in Ubuntu 9.10 | Linuxers]("http://linuxers.org/howto/how-configure-grub2-ubuntu-910")

---

