---
title: "GeexBox &amp; Ubuntu 9.10: Dual Booting &amp; editing GRUB2?"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by neu5eeCh on 2010-02-08
9.10 uses GRUB2, so the instructions below are obsolete.

Question: Is there anyone here who could provide instructions for adding Geexbox into the GRUB2 menu? 


If you already have a Linux OS installed on your system, you might just         want to add a GeeXboX entry to your existing bootloader. This  allow you         to install GeeXboX very easily.
        From GeeXboX CD, simply copy the GEEXBOX folder into your Linux /         partition (we suppose it to be /dev/sda1 here).         Modify the /boot/grub/menu.lst file to add:
        
        [B]         title       GeeXboX
        root        (hd0,1)
        kernel      /GEEXBOX/boot/vmlinuz root=/dev/ram0 rw  rdinit=linuxrc boot=UUID=$my_uuid lang=en keymap=qwerty splash ...
        initrd      /GEEXBOX/boot/initrd.gz
        quiet
        [/B]         
        Just take are about two things:
        - the field **root (hd0,1)** is to be adapted according to  the rest of your GRUB's configuration.
        - the **$my_uuid** value is the unique ID of your partition.  Check within your GRUB config file, which value is set for other OS on  the same partition or use **ls -l /dev/disk/by-uuid/** to see which  uuid matches your partition.

---

### Post by tommcd on 2010-02-09
> **VTPoet said:**
> 
Question: Is there anyone here who could provide instructions for adding Geexbox into the GRUB2 menu? 

Yes there is!
See this excellent and comprehensive tutorial for grub2 from the Ubuntu wiki:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
Specifically, the info for adding custom entries to your /boot/grub/grub.cfg (The file that has replaced the /boot/grub/menu.lst from grub-legacy) is here:
[https://wiki.ubuntu.com/Grub2#User-defined%20Entries](https://wiki.ubuntu.com/Grub2#User-defined%20Entries)
The info in that last link helped me to add a custom entry for Slackware 13 64bit to the Ubuntu 9.10 grub menu.

Did you do a clean install of Ubuntu 9.10 (as I always do) or did you do a dist-upgrade from 9.04? If you did a dist-upgrade from 9.04 then you may still have some grub-legacy files laying around. To fully upgrade to grub2 see this from the same Ubutu wiki article:
[https://wiki.ubuntu.com/Grub2#Installing%20%28Ubuntu%209.10%29](https://wiki.ubuntu.com/Grub2#Installing%20%28Ubuntu%209.10%29)
Hope this helps.

---

### Post by neu5eeCh on 2010-02-10
Thank you Tom!

I have, through various sources including those you listed, successfully installed GeexBoX on my system. The one thing not covered in any of the tutorials is the fact that GeexBoX doesn't work if booted from an ext4 partition. Once I had learned how to edit GRUB2, I created a small 8g (probably didn't have to be that big) partition and copied the GeexBoX folder into it. Worked like a charm.

For future reference (anyone else who finds this post with the same questions), here is **Grub** (above) successfully translated (on my system) into **Grub2**:

#!/bin/sh
exec tail -n +3 $0

menuentry "GeeXboX 1.2.4 for x86_32 (PC, MacIntel)"  {
    **[COLOR=Red]set root[/COLOR]**=(hd0,7)
    **[COLOR=Red]linux[/COLOR]**    /GEEXBOX/boot/vmlinuz root=/dev/ram0 rw rdinit=linuxrc boot=UUID=[COLOR=DarkRed]**fc10669d-9c82-47e8-840a-7ac7119336a4**[/COLOR] lang=en remote=atiusb receiver=atiusb keymap=qwerty splash=silent video=vesafb:ywrap,mtrr **[COLOR=Red]quiet[/COLOR]**
    initrd    /GEEXBOX/boot/initrd.gz
}

GRUB2 requires "set root" instead of "root".
GRUB2 requires "linux" instead of "kernel"
Find your own UUID (in red) using the command: **sudo blkid** (There are other commands that accomplish the same.)
GRUB2 preferred the QUIET command in its new location.

This file edited was 40_Custom, found at **/etc/grub.d. **Edit this file and run **sudo update-grub. **This will incorporate your edits of 40_custom into  grub.cfg, located at [B]/etc/grub.cfg.

[/B]Here is an excellent source of information that helped me translate GRUB  into GRUB2: [Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2")

And here is another: [How to configure Grub2 in Ubuntu 9.10 | Linuxers]("http://linuxers.org/howto/how-configure-grub2-ubuntu-910")

---

