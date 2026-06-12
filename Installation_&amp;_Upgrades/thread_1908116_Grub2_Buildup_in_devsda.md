---
title: "Grub2 Buildup in /dev/sda?"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by surenot on 2012-01-12
I have installed and reinstalled various different derivatives of Ubuntu on my netbook, trying to see which ones would work best, given the limited hardware.  Each time I installed one, I always told it to install the grub2 bootloader in /dev/sda of the harddrive.  After preforming so many installations, my question is, does each installation delete the old bootloader?  Or are there about five or six bootloaders somehow spread throughout /dev/sda?  If so, is there any way to get rid of them without reformatting the entire computer's harddrive?

Thanks.

---

### Post by drs305 on 2012-01-12
surenot,

Welcome to the Ubuntu Forums.  :-)

Each Ubuntu/Linux OS that uses Grub 2 normally installs it's own boot files in the OS's partition. The majority of the files are installed in the /boot/grub folder, with configuration scripts stored in /etc/grub.d and a configuration file (/etc/default/grub).

In addition, Grub 2 writes information to a drive's MBR. This information points to the Grub files on the OS's partition.

When you install a new Linux OS, the Grub files in other versions are not touched. On the other hand, the information in the drive's MBR is overwritten by default. The MBR information is rewritten to point to the new installation's partition and Grub files.

In some OS's and earlier versions of Ubuntu, there was an option to not install Grub 2, which left the MBR information pointing to the older installation. In the most recent Ubuntu releases, the MBR will be overwritten unless the user takes some unusual steps to prevent it.

The easiest thing to do is to allow Ubuntu to install normally, then boot into the desired default OS and reinstall Grub from there. This will rewrite the MBR to point to the OS currently in use. 

From the desired Ubuntu OS, use these commands to make that OS the one controlling Grub/booting: X is the drive letter (a, b, c as in sda, sdb, sdc).
```
sudo grub-install /dev/sd[COLOR="Red"]X[/COLOR]
sudo update-grub
```

This is a general overview. If you want to hide some of the existing OS menu options, the easiest way to tweak the menu is with Grub Customizer. It's a GUI app that lets you make lots of changes to the Grub menu. Click the "Customizer" link in my signature line.

Added:

Note: You may also see additional kernels listed for the same OS, which is not the same as seeing multiple OS's. These older kernels are now stored away in a submenu, but in older releases the older kernels of the same release are retained in the menu as newer kernels are installed.

---

