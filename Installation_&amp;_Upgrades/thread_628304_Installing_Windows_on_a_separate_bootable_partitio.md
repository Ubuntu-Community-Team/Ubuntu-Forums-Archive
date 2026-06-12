---
title: "Installing Windows on a separate bootable partition"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by BA005 on 2007-12-01
I would really appreciate some help.

I have been using Ubuntu 7.10 for the last few weeks and am loving it.

However, I now need to install Windows. So I will need to make a new partition on the hard drive and install Windows.

Is that possible to do? Or is it only possible for me to completely start again? i.e format the entire hard disk, install windows again and then install Ubuntu again on a separate partition?

Any help/suggestions/comments would be much appreciated!

Thanks in advance, BA.

---

### Post by Pumalite on 2007-12-01
Bad idea to install Windows second. Windows should be first, Ubuntu 2nd. Doing it the way you want; you'll run into problems with Grub and menu.lst

---

### Post by PmDematagoda on 2007-12-01
You can install Windows XP, but you will have to reinstall GRUB onto the MBR and change the menu.lst file a bit so that both Ubuntu and XP can be booted. As to reinstalling GRUB on the MBR again, you can use [SuperGRUB]("http://supergrub.forjamari.linex.org/?section=download").

---

### Post by logos34 on 2007-12-01
See this guide:

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

Restore Grub to MBR after intalling windows:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29#head-7fb1c88570b006aa14b7daaef2238b432b7f73c8](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29#head-7fb1c88570b006aa14b7daaef2238b432b7f73c8)

Add windows partition to Ubuntu fstab:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by BA005 on 2007-12-01
Thanks a lot guys!

---

### Post by Pumalite on 2007-12-01
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

