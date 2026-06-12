---
title: "re-install with harddrive encryption"
date: 2019-05-23
forum: Installation &amp; Upgrades
---

### Post by udo-groebner on 2019-05-23
hi people,

first and foremost thank you for the great work you all are doing.
background: i initially installed ubuntu-budgie 18.10 with lvm and harddrive encryption (luks?) from the installer. everything worked great. but i managed to make my installation quite flaky by also installing several other desktop environments (gnome, xfce, i3) and eventually upgrading to 19.04.
therefor i'd like to re-install the ordinary ubuntu with gnome from the live usb drive. ideally with keeping the data.

i tried to follow this tutorial: [https://www.fosslinux.com/2920/how-to-reinstall-ubuntu-by-keep-your-data-safe-in-event-of-system-failure.htm](https://www.fosslinux.com/2920/how-to-reinstall-ubuntu-by-keep-your-data-safe-in-event-of-system-failure.htm)
but due to the encrypted harddrive, the installer doesn't detect my existing installation.
i also decrypted (cryptsetup luksOpen) and mounted the lvm volume. but the installer still couldn't find it.
any ideas how to proceed?

thank you!

---

### Post by TheFu on 2019-05-23
Backup all the settings, data, programs not installed using the package manager, and a list of manually installed packages using the package manage.  You should be doing these at least weekly, if not nightly anyway.

Do a fresh install (with or without encryption and/or LVM) then restore the settings, data, and finally, restore the programs not in the package manager ... probably in /usr/local/. Put everything back where it was before. This is important - just from the file system level. You can change anything lower level than that, so don't worry about LVM or mounts or even the underlying storage.  As long as the files and directories "appear" to be in the expected locations, all will be find.

Personal settings are stored in your $HOME directory.  You might want to be selective about the GUI settings being restored, since mixing GUIs that are based on the same libraries is an issue. Same for some files in /etc/.  I backup all of /etc/ because it is tiny, but only restore the files I've manually modified. That is usually about 10 files, mostly the hosts file and some LDAP and power handling things.  On servers, there are many more files to be restored since that is where server settings are kept.

Lastly, take that list of manually installed packages ( store it in a file and back it up) and feed it into APT to be marked for install, then tell it to reinstall all of them, pulling in the dependencies (automatically). I've posted the exact commands for this in these forums THIS WEEK already.  Look for my userid and "apt-mark".

That should handle it.

---

### Post by udo-groebner on 2019-05-23
Thank you for the detailed description!
I do have a backup (for the worst case), but wanted to avoid the hassle of a complete fresh installation.
I'll have a look at "apt-mark", thanks! Your approach sounds like it makes the whole thing a bit more straightforward.

---

### Post by TheFu on 2019-05-23
> **udo-groebner said:**
> Thank you for the detailed description!
I do have a backup (for the worst case), but wanted to avoid the hassle of a complete fresh installation.
I'll have a look at "apt-mark", thanks! Your approach sounds like it makes the whole thing a bit more straightforward.

For most of my systems, a complete restore is 30-45min, tops.  That includes the 15min to do a new install and patch it up to current.  I always start with a minimal install and add an ssh-server.

Doing it this way removes all the funky storage, all the grub fighting, and there's no need to backup the entire OS, which makes backups faster and use less storage.  On one of my servers, 180 days of daily, versioned backups is under 50MB total. It don't have **any**, just provides a service.

---

