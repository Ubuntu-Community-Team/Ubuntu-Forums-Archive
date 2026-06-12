---
title: "Install Ubuntu Server From USB"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by ThexDarksider on 2010-04-04
First of all, this may have been posted somewhere else already, but I didn't find anything like this after any searching I've done, so please excuse me if this isn't of any help to anyone. Now, for the post.

I've found an easy way how to do this. After many hours of trying and failing, I finally figured out what to do and how to make this work (even though I'm not an expert myself :D). But I've seen many people struggling with installing Ubuntu Server (any version) from USB. So here is the whole solution.

[COLOR=Red][B]DISCLAIMER: I am not responsible for any data loss you may encounter due to misuse of these instructions, your computer's configuration, ISO file contents, faulty software, environmental disasters, etc. Keep in mind that this will format your USB drive, so please back it up if you have important data on it. And, most importantly, don't do this if you don't know what you're doing!
[/B][/COLOR]
Note to mods/admins: if this topic is in the wrong section, please move it to the right one.

Assuming that [COLOR=Red]**[COLOR=DarkRed]/dev/sdb1[/COLOR] is the partition on your USB drive (make sure it's not your HDD!!)**[/COLOR] that contains the installation files, and that you have a CD image named **ubuntu-9.10-server-i386.iso** (although this should work for other versions as well) in your home folder, you first need to install it *to* the USB drive, so you can run the setup from there [COLOR=Red]**(I REPEAT: BE CAREFUL WITH *mkfs*, DON'T FORMAT YOUR HDD!!)**[/COLOR]:

```
# mkfs.vfat /dev/sdb1
# mkdir /mnt/usb/
# mount /dev/sdb1 /mnt/usb/
# cd /mnt/usb/
# 7z x ~/ubuntu-9.10-server-i386.iso -x![BOOT]
# mv isolinux/ syslinux/
# cd syslinux/
# mv isolinux.cfg syslinux.cfg
# cd /
# umount /mnt/usb/
# syslinux -f /dev/sdb1
```Now for the part that's been giving me headaches: boot a machine up from your USB drive **and prepend [COLOR=Red]cdrom-detect/try-usb=true[/COLOR]** to the boot options, and just follow the setup. :D The installation took about 20 minutes on my P4 with 256 megs of RAM.
Tested only on Ubuntu 9.10 Server but it may work for other versions, and maybe even other distros, too.

NOTE: Don't forget to run **apt-get upgrade** after the installation! :P

I hope my post helped you install Linux on your machine! :) And I'm sorry if you already knew all of this, but I know for a fact that I never successfully installed Ubuntu Server before I did everything like stated here (tbh I figured most of this myself though).

Enjoy Linux! :D

---

