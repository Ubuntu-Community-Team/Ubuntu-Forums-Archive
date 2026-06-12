---
title: "release upgrade problem"
date: 2022-05-28
forum: Installation &amp; Upgrades
---

### Post by coley9225 on 2022-05-28
Hello all. Yesterday(05/27/2022) I did a release upgrade, and, well, didn't go well. I now have a semi-usable computer. I can't install or remove packages, can't update grub, and possibly other things yet to be discovered. This is a summary of what I've done so far.
1)  I no longer get a grub menu, and that is the only way for me to get into my uefi settings. I edited /etc/default/grub as follows:
     

GRUB_DEFAULT="0"
#GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

I saved and ran sudo update grub, and got this:

```
charles:$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Sourcing file `/etc/default/grub.d/lubuntu-grub-theme.cfg'
Generating grub configuration file ...
Found theme: /usr/share/grub/themes/lubuntu-grub-theme/theme.txt
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory

```

I have timeshift installed, but seems to be acting a little strange, so decided to re4install, to which I got this;

```
charles:$ sudo apt install timeshift
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
timeshift is already the newest version (21.09.1-1).
The following packages will be REMOVED:
  linux-image-5.13.0-41-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 10.2 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 345687 files and directories currently installed.)
Removing linux-image-5.13.0-41-generic (5.13.0-41.46~20.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.13.0-41-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Sourcing file `/etc/default/grub.d/lubuntu-grub-theme.cfg'
Generating grub configuration file ...
Found theme: /usr/share/grub/themes/lubuntu-grub-theme/theme.txt
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.13.0-41-generic (--remove):
 installed linux-image-5.13.0-41-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.13.0-41-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

At 1 time, I had the script from 1 of you guys, sys-info.sh, but can't locate it. I was going to run that and post the pastebin address. If someone can give me that it may help you figure out what's going on.

At this point I don't know what to do. I need to be able to install and remove packages, update my system etc.

I did a timeshift backup 30 minutes prior to the release upgrade, should I try to restore that? How can I get my grub menu back? Without using the uefi menu entry, the only way I can get to that is open laptop, remove sdd, boot a live usb, and reboot with the usb left in. 

I desperately need help with this.  If I have to open laptop, I will, and while not my favorite option, a fresh install is possible. 
Much appreciation in advance.

---

### Post by coley9225 on 2022-05-28
I found a way to get to my grub menu...press <esc>key at boot. That will make this a bit easier. I did have another thought. If I do a fresh install, can I leave the partition unformated, just not check the format box? That should overwrite the file system, without changing the UUID, and then restore with timeshift. Just a thought.

---

### Post by coley9225 on 2022-05-28
As so often happens, I look for assistance, then get the problem solved on my own through trial and error. In this case, after finding a way to enter uefi settings, I booted to live usb and restored my last backup. All seems as it used to be, but time will tell.

---

