---
title: "Why GRUB detects Windows Recovery Environment instead of Windows?"
date: 2015-09-01
forum: Installation &amp; Upgrades
---

### Post by Rob_Bot on 2015-09-01
Instead of Windows (10) GRUB detects Windows Recovery Environment. When selecting an ugly screen appears like with bad pixels for about 15 seconds and then Windows boots normally.
Can I change GRUB configuration somehow to run Windows directly, not trough recovery mode??
Here is part of grub.cfg:
```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Recovery Environment (loader) (na /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-AA7CB5D17CB59911' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  AA7CB5D17CB59911
    else
      search --no-floppy --fs-uuid --set=root AA7CB5D17CB59911
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###
```

---

### Post by yancek on 2015-09-01
Are windows 10 and Ubuntu both installed using UEFI?  Or are you using MBR to boot?  If you don't know, download and run the boot repair from the link below.  Just select the Create BootInfo Summary option and post the output here rather than trying to repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Rob_Bot on 2015-09-02
Here's the output:
[http://paste.ubuntu.com/12257020/](http://paste.ubuntu.com/12257020/)

---

### Post by ubfan1 on 2015-09-02
Looks like a normal legacy install boot of Windows to me.  Only the grub menu indicates "Recovery...", but it's booting the only Windows install on your system.

---

### Post by yancek on 2015-09-02
Your windows is hibernated which is why you see all the messages in the boot repair output.  You need to fully shut down windows.  I'm not sure that is the problem, I doubt it but?  Did you install windows 10 or did you upgrade an earlier version of windows?   I don't know what you have on the two ntfs logical partitions (sda5 and sda6) but I expect they are just data partitions?  

I don't see how you can change that through Grub.  Once you select windows from the Grub boot menu, you are using windows software.  You might try a windows forum about the problem of bad pixels on boot.

---

### Post by Rob_Bot on 2015-09-03
I rebooted windows so that it didn't hibernate and on ubuntu I ran update-grub but it again detected Windows Recovery Environment instead of Windows, so I think hibernation has nothing to do.
I had formated C: partition and installed Win10 from scratch not through update. I recovered GRUB then. Earlier I had Win8.1 similar way, it also hibernated and there was no such problem.
You're right, sda5 ans sda6 are just data partitions.
If only I could get rid of this 15 seconds of grey screen with bad pixels before Windows loading. Before I recovered GRUB Windows booted normally.

---

### Post by MAFoElffen on 2015-09-03
Note: I use and support Windows 10 here and to customers... Until Grub is updated in the main repos, it is also going to show the Windows 10 OS identified as "Windows Recovery" in the title in the Grub boot menu. I edit the menu title for the customers I support... But it should catch up soon in the updates. My advise on that, just note which option actually starts Windows 10 and what place it occupies in the menu.

---

