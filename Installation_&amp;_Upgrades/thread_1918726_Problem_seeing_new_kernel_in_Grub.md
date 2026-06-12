---
title: "Problem seeing new kernel in Grub"
date: 2012-02-01
forum: Installation &amp; Upgrades
---

### Post by clnorris on 2012-02-01
Good afternoon,

When I run update-grub, it updates menu.lst successfully with the newest kernel:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-38-generic
Found kernel: /boot/vmlinuz-2.6.31-22-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

However, when I reboot the system I do not see the menu option for the 2.6.32-38-generic.

Why are the newest kernels missing from the menu at boot time even when they are present in menu.lst?

If anyone else has seen this behavior, please let me know.

Thanks!
Chris Norris

---

### Post by oldfred on 2012-02-01
It looks like you have both grub legacy 0.97 and grub2. Often then the menu for the one you are not using is updated, but the one you are using to boot is not. Since 9.10 grub2 has been the standard.

May be best to see entire configuration:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils


You can cleaning uninstall both grub versions and as long as you have Internet reinstall just one cleanly.

If you can boot, you can skip the chroot steps.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by clnorris on 2012-02-01
Hello oldfred,

The procedure to purge and reinstall grub2 fixed my problem!

This box previously had Ubuntu 9, so I guess I needed to manually refresh this part.

Thanks much for the advice!

Regards,
Chris Norris:D

---

### Post by oldfred on 2012-02-01
Glad that worked.

I do like to have the current version liveCD available even if you upgrade. And the very newest version seems to have to have the most current version to reinstall grub2's boot loader to the MBR.

---

