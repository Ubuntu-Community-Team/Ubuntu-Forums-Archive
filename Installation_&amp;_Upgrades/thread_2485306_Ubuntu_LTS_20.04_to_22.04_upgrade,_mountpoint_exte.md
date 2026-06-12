---
title: "Ubuntu LTS 20.04 to 22.04 upgrade, mountpoint external drive"
date: 2023-03-27
forum: Installation &amp; Upgrades
---

### Post by xinuzi on 2023-03-27
Forgot to umount external (NTFS) HDD whilst upgrading (L)Ubuntu LTS 20.04 to 22.04.
Consequence: new automatic mountpoint for external drive and e.g. favourites in PCManFM file explorer don't link (to the mountpoint of) that drive.

The same could happen to you...

(Gui) Settings like these restored things:

Go to 'Disks' and (see image attachments)...

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291967&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291968&stc=1[/IMG]

A new line gets added to /etc/fstab 

Everything is sharper in this new Ubuntu release 8-) + probably many more changes (+ possibly minor bugs) under the hood.

---

### Post by guiverc on 2023-03-27
**Thanks for passing on your discovery.**

FYI:  Lubuntu uses LXQt, thus the file-manager (*and app that handles some of the desktop actually*) is pcmanfm-qt

That app started as a port of `pcmanfm` by the original Developer [PCman]("https://github.com/PCMan") , the first port being the GTK3 version which was soon abandoned (*and documented rather extensively on issues with GTK3*), before a new port was started this time using Qt5, which is the app that LXQt relies rather heavily on (*just as LXDE relied on pcmanfm*).

pcmanfm & pcmanfm-qt are different applications; both can be installed & used (*on all releases*), but as they use different libraries/toolkits (*being intended for different desktops*) they are both different. Lubuntu hasn't used `pcmanfm` since 18.04

---

### Post by ActionParsnip on 2023-03-27
What is the output of
```

cat /etc/fstab

```

---

### Post by oldfred on 2023-03-27
Disks defaults to one set of parameters.
Its just that NTFS, SSD, external drives, ext4 and others all need different parameters.
Often easier just to copy & paste an example and edit to match UUID or label. You may have to create mount point also.

I have seen these:
NTFS mount parameters - Windows_names, big_writes
[https://wiki.archlinux.org/index.php/NTFS-3G](https://wiki.archlinux.org/index.php/NTFS-3G)
[https://linux.die.net/man/8/mount.ntfs-3g](https://linux.die.net/man/8/mount.ntfs-3g)
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000

[https://ubuntuforums.org/showthread.php?t=2467566](https://ubuntuforums.org/showthread.php?t=2467566)
[https://ubuntuforums.org/showthread.php?t=2464668](https://ubuntuforums.org/showthread.php?t=2464668)

For external devices, may also want to add the nofail option, so boot continues even when that device isn't available.
The nofail option is best combined with the x-systemd.device-timeout option. This is because the default device timeout is 90 seconds, so a disconnected external device with only nofail will make your boot take 90 seconds longer, unless you reconfigure the timeout as shown. Make sure not to set the timeout to 0, as this translates to infinite timeout. 

[https://wiki.archlinux.org/index.php/fstab#Automount_with_systemd](https://wiki.archlinux.org/index.php/fstab#Automount_with_systemd)
Either systemd-automount or autofs can be used. 
[https://manpages.debian.org/stretch/systemd/systemd.automount.5.en.html](https://manpages.debian.org/stretch/systemd/systemd.automount.5.en.html)
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
use autofs for any storage that isn't connected directly to the system with SAS, SATA, eSATA, or Infiniband connections
For USB connected stuff, use autofs, always. use /misc/<LABEL> typically

---

### Post by xinuzi on 2023-03-28
*[Response to [**[COLOR=#DD4814][B]ActionParsnip**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1079078")]*

/dev/disk/by-label/Elements /media/xx/Elements auto nosuid,nodev,nofail,x-gvfs-show 0 0

(xx = usr - not the real 1)

If I don't select 'Mount at system startup' fstab shows:

/dev/disk/by-label/Elements /media/xx/Elements auto nosuid,nodev,nofail,x-gvfs-show,**noauto** 0 0

Maybe better leave it on anyway. More automation.

If settings are set this way owner and group of the disk become 'root', not user 'xx'. 
 
No problem if user 'xx' is administrator (if he/she/it can mess with things he/she/it probably Is :-D).

---

### Post by xinuzi on 2023-03-28
*[Response to*[B]* guiverc]*
[/B]
Should keep up with versions, flavours, configurations etc.
Sometimes when things work swell, I don't always update myself quickly enough ;-)

PCManFM = My Absolutely Favourite File Explorer (and I am using the Qt-version currently) :-)

Of Thunar I especially like its (Bulk) Rename tool:

-> [https://www.maketecheasier.com/bulk-rename-files-linux-thunar-bulk-rename-tool/](https://www.maketecheasier.com/bulk-rename-files-linux-thunar-bulk-rename-tool/)

---

