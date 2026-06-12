---
title: "Having trouble dual booting windows/ubuntu"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by Rammstein55 on 2012-05-30
I recently installed the newest version of ubuntu  alongside windows 7, I am having trouble accessing the dual boot screen, I try holding down shift or f12 during start up but it still boots directly to ubuntu. I look at the /boot/grub/grub.cfg file and see:

menuentry 'Ubuntu, with LInux 3.2.0-23-generic --class ubuntu --class gnu-linux -class gnu --class os { recordfail
                     gfxmode $linux_gfx_mode
                     insmod gzio
                     insmod part_msdos
                     insmod ext2
                     set root='(hd0,msdos5)'

as well as:

menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
      insmod part_msdos
      insmod ntfs
      set root='(hd0,msdos2)'
      search --no-floppy --fs-uuid --set=root 1E7CC12C7CC0FF8F
      chainloader +1

I'm hesitant to edit the grub.cfg  any suggestion would be greatly appreciated, thanks!

---

### Post by deadflowr on 2012-05-30
Yeah, you should be hesistant to edit your /boot/grub/grub.cfg file as for the fact that any succeeding update to grub will revert it back to its intial configuration.
Instead, look at the file /etc/default/grub. or install start-up manager.
If /etc/default/grub seems non-sensical for you, just copy and paste it so we can look it over for any problems.
You might also want to do the same with your grub.cfg file.

---

### Post by wilee-nilee on 2012-05-30
> **Rammstein55 said:**
> I recently installed the newest version of ubuntu  alongside windows 7, I am having trouble accessing the dual boot screen, I try holding down shift or f12 during start up but it still boots directly to ubuntu. I look at the /boot/grub/grub.cfg file and see:

menuentry 'Ubuntu, with LInux 3.2.0-23-generic --class ubuntu --class gnu-linux -class gnu --class os { recordfail
                     gfxmode $linux_gfx_mode
                     insmod gzio
                     insmod part_msdos
                     insmod ext2
                     set root='(hd0,msdos5)'

as well as:

menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
      insmod part_msdos
      insmod ntfs
      set root='(hd0,msdos2)'
      search --no-floppy --fs-uuid --set=root 1E7CC12C7CC0FF8F
      chainloader +1

I'm hesitant to edit the grub.cfg  any suggestion would be greatly appreciated, thanks!

Have you modified grub with a app, like the grub customizer?

Have you run in ubuntu?
```
sudo update-grub
```You can give us a closer look at your setup by using the tool in the link, and running the bootinfo summary, post the url to it. Just run that part of the tool at this point.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by wilee-nilee on 2012-05-30
> **deadflowr said:**
> Yeah, you should be hesistant to edit your /boot/grub/grub.cfg file as for the fact that any succeeding update to grub will revert it back to its intial configuration.
Instead, look at the file /etc/default/grub. or install start-up manager.
If /etc/default/grub seems non-sensical for you, just copy and paste it so we can look it over for any problems.
You might also want to do the same with your grub.cfg file.

Startup manager is not been kept updated and will not move the boot with a kernel update. I think it still might work in lucid is all.

---

