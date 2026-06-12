---
title: "Invalid arch independent ELF magic HELP"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by odh1412 on 2011-07-28
I just updated my desktop through update manager running Ubuntu 11.04 64 bit (I think? unity whatever the newest one is). It asked me to update grub and I just followed all the steps that were recommended. It restarted and at boot it just is a command line that says:

error invalid arch independent ELF magic
grub rescue> 

I am new to linux and have absolutely no idea what to do. Any help would be appreciated.

Thanks.

---

### Post by jcrada on 2011-08-01
I have the same problem after performing the (damn) partial upgrade of Ubuntu 11.04 on my MacBook 4,1. Going madder by the minute.

---

### Post by statistic on 2011-08-01
I'm currently having this problem as well, but I have a theory and maybe a temporary work around...

Theory: It has to do with EFI booting things and failing.

Workaround: I have that theory because going into the boot menu and doing a "legacy boot" seems to work.

---

### Post by YesWeCan on 2011-08-01
One possibility is that you upgraded your distro to 11.04 but you did not reinstall Grub to your MBR. The Grub you currently have installed is not compatible. The rescue> prompt appears when the Grub boot program cannot find the files it needs in /boot/grub.

There are instructions here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) about various ways to reinstall Grub.

---

### Post by statistic on 2011-08-01
I don't know about the others, but a grub reinstall was the first thing I tried. I may have installed an older version though anyways. Now that I've got it booting using "legacy" boot I can run a proper upgrade on grub.

I don't think this is likely the issue though for a couple of reasons:
1) This started for me (like the other two) right after upgrading to the newest everything.
2) The same old grub still works regardless of using the kernel from before or after the dist-upgrade when I boot in "legacy" mode.

---

