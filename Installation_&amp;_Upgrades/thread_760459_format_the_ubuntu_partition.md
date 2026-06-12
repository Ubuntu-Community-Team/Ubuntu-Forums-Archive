---
title: "format the ubuntu partition"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by nik1990 on 2008-04-20
how do i format the ubuntu partition to install windows?:confused::confused::confused::confused:

---

### Post by em3raldxiii on 2008-04-20
I'm not quite following what you are trying to do.  The windows installer will not understand that you have Linux installed, and will therefore overwrite your boot loader.

If you are bent on installing windows on your system after you have installed Linux, you will need to format a partition to either NTFS or to FAT32.  Alternatively, you can shrink the size of your EXT3 partition(s) and leave a large section blank (about 30GB should be alright).  Then go through with your WIndows install.  Make sure you select the correct partition during the windows install.

After this is complete, you will have to reinstall GRUB using the Ubuntu live disc.

---

### Post by unutbu on 2008-04-20
If you want a dual-boot machine (Windows + Linux) you should install windows **first** and then linux. Windows insists on being on the first partition of the first hard drive and therefore will cause problems if you set it up otherwise. (I think there is a way around this using GRUB and the mapping feature, but it's best to avoid the problem if you have a choice.)

If you want a Windows-only machine, I think you just stick the Windows install CD in and it will happily nuke your Linux partition :) I'm no Windows expert, but I think you don't even have to format the drive, as a Windows CD should be able to install itself even on a clean operating system-less drive.

---

### Post by the8thstar on 2008-04-20
> **unutbu said:**
> If you want a dual-boot machine (Windows + Linux) you should install windows **first** and then linux. Windows insists on being on the first partition of the first hard drive and therefore will cause problems if you set it up otherwise. (I think there is a way around this using GRUB and the mapping feature, but it's best to avoid the problem if you have a choice.)

If you want a Windows-only machine, I think you just stick the Windows install CD in and it will happily nuke your Linux partition :) I'm no Windows expert, but I think you don't even have to format the drive, as a Windows CD should be able to install itself even on a clean operating system-less drive.

Windows can be installed AFTER Ubuntu. In order to do so, the target partition MUST bear the 'boot' flag before the install. This can be achieved with typing *sudo gparted* in the terminal.

---

### Post by unutbu on 2008-04-20
Thanks the8thstar, I was wrong about that.

nik1990, here's a tutorial for doing dual boot with linux already installed:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Also, if you want to run a graphical app as root, use gksudo instead of sudo:
```

gksudo gparted 
```

See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

