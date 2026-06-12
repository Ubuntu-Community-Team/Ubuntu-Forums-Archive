---
title: "Edgy FileBrowser doesn't show mountable drives?"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by febrile on 2007-02-06
Having upgraded from ubuntu dapper to edgy, it seems the treatment of fstab-defined mountable volumes has changed in FileBrowser's "Computer location":
- In dapper, both mounted and unmounted volumes were shown and could be (u/)mounted from the rt-click menu.
- In edgy, only mounted volumes + CDdrive are shown.

Ok, so I know I can do it all from the cmd-line, but I find mousewise mounting from the FileBrowser convenient when grabbing stuff from my ntfs partitions. Can I get this functionality back without having the ntfs partitions auto-mounted?

Here's my /etc/fstab:
```

proc            /proc                   proc            defaults                        0 0
/dev/hda5       /                       ext3            defaults,errors=remount-ro      0 1
/dev/hda6       none                    swap            sw                              0 0
/dev/hda7       /home                   ext3            defaults,errors=remount-ro      0 1
/dev/hdc        /media/cdrom0           udf,iso9660     ro,user,noauto                  0 0
/dev/hda1       /media/windoze          ntfs            noauto,users,ro,umask=0222      0 0
/dev/hda2       /media/windata          ntfs            noauto,users,ro,umask=0222      0 0
/dev/hda4       /media/crossover        vfat            auto,users,rw,umask=0000        0 0

```
(I found no good reason for the edgy upgrade rewriting fstab with unfriendly UUIDs so I stripped it back.)

Thanks
febrile

---

