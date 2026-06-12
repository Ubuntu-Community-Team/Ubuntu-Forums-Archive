---
title: "GRUB loader"
date: 2005-03-28
forum: Installation &amp; Upgrades
---

### Post by wegarnett on 2005-03-28
I have been using Windows XP, SUSE and Ubuntu on my home computer.  I recently installed SUSE 9.1 and the option to boot Ubuntu does not show when I can select which OS to use.  The partitions are still there and I can mount them in SUSE.  How can I get the loader to recognize the Ubuntu partition as a possible place to boot from short of re-installing Ubuntu?

I can always get at the info on the partitions if a re-installation is the only way.

Thanks.

---

### Post by dseomn on 2005-03-28
[QUOTE=wegarnett]I have been using Windows XP, SUSE and Ubuntu on my home computer.  I recently installed SUSE 9.1 and the option to boot Ubuntu does not show when I can select which OS to use.  The partitions are still there and I can mount them in SUSE.  How can I get the loader to recognize the Ubuntu partition as a possible place to boot from short of re-installing Ubuntu?

I can always get at the info on the partitions if a re-installation is the only way.

Thanks.[/QUOTE]
 Try looking for grub configuration in suse, and if it's not there, you'll probably have to manually edit grubs configuration file. If there's no gui tool to do it, paste the contents of /boot/grub/menu.lst or /boot/grub/grub.conf (only one should exit) here.

---

### Post by wegarnett on 2005-03-28
here are the contents of /boot/grub/menu.lst

# Modified by YaST2. Last modification on Mon Mar 28 19:34:36 2005


color white/blue black/light-gray
default 0
timeout 8
gfxmenu (hd0,5)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title Linux
    kernel (hd0,5)/boot/vmlinuz root=/dev/hda6 vga=0x31a splash=silent desktop resume=/dev/hda5 showopts
    initrd (hd0,5)/boot/initrd

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    root (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    root (fd0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe
    kernel (hd0,5)/boot/vmlinuz root=/dev/hda6 showopts ide=nodma apm=off acpi=off vga=normal noresume nosmp noapic maxcpus=0  3
    initrd (hd0,5)/boot/initrd

I have Ubuntu on /dev/hda3

---

### Post by dseomn on 2005-04-15
[QUOTE=wegarnett]here are the contents of /boot/grub/menu.lst

# Modified by YaST2. Last modification on Mon Mar 28 19:34:36 2005


color white/blue black/light-gray
default 0
timeout 8
gfxmenu (hd0,5)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title Linux
    kernel (hd0,5)/boot/vmlinuz root=/dev/hda6 vga=0x31a splash=silent desktop resume=/dev/hda5 showopts
    initrd (hd0,5)/boot/initrd

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    root (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    root (fd0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe
    kernel (hd0,5)/boot/vmlinuz root=/dev/hda6 showopts ide=nodma apm=off acpi=off vga=normal noresume nosmp noapic maxcpus=0  3
    initrd (hd0,5)/boot/initrd

I have Ubuntu on /dev/hda3[/QUOTE]
 Ok, try adding:

```

# Ubuntu
title Ubuntu
root (hd0,2)
chainloader +1

```

after the line "gfxmenu (hd0,5)/boot/message".

---

