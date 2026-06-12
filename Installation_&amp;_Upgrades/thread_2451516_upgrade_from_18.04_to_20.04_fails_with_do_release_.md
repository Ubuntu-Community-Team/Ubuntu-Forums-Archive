---
title: "upgrade from 18.04 to 20.04 fails with do_release_upgrade (how to fix)?"
date: 2020-10-05
forum: Installation &amp; Upgrades
---

### Post by anewbie on 2020-10-05
The install from 18.04 to 20.04 failed at the very end and I'm unsure if I need to do anything to clean up. Also how do i report this issue to the ubuntu team so they can fix their script:
------
This is the error:
        printf '%s\n' "$*" >&3
/usr/share/debconf/confmodule (line 44)
--
Not sure if they meant 1 or 2 (stdout or stderr)

This is the tail end of what was printed on the screen (is there a full log somewhere?):
---
Found kernel: /boot/memtest86+.bin
/usr/share/debconf/confmodule: line 44: 3: Bad file descriptor
dpkg: error processing package memtest86+ (--configure):
 installed memtest86+ package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 memtest86+

Upgrade complete 

The upgrade has completed but there were errors during the upgrade 
process. 

To continue please press [ENTER]
---
Today when i did apt-get autoremove I still get the same error:

Removing linux-modules-extra-4.15.0-108-generic (4.15.0-108.109) ...
Removing linux-image-4.15.0-108-generic (4.15.0-108.109) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-108-generic
/etc/kernel/postrm.d/zz-update-grub:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz
Found kernel: /boot/vmlinuz.old
Found kernel: /boot/vmlinuz-5.4.0-48-generic
Found kernel: /boot/vmlinuz-4.15.0-118-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Removing linux-modules-4.15.0-108-generic (4.15.0-108.109) ...
Removing nplan (0.99-0ubuntu3~18.04.3) ...
Removing orage (4.12.1-7) ...
Removing orage-data (4.12.1-7) ...
Removing python-asn1crypto (0.24.0-1build1) ...
Removing python-compizconfig:amd64 (1:0.9.13.1+18.04.20180302-0ubuntu1) ...
Removing python-fasteners (0.12.0-3) ...
Removing python-monotonic (1.5-0ubuntu2) ...
Removing python-urllib3 (1.22-1ubuntu0.18.04.1) ...
Removing python3-asn1crypto (0.24.0-1build1) ...
Removing unetbootin-translations (608-1) ...
Removing x11proto-damage-dev (1:2019.2-1ubuntu1) ...
Removing x11proto-fixes-dev (1:2019.2-1ubuntu1) ...
Removing x11proto-input-dev (2019.2-1ubuntu1) ...
Removing x11proto-kb-dev (2019.2-1ubuntu1) ...
Removing x11proto-xext-dev (2019.2-1ubuntu1) ...
Removing x11proto-xf86vidmode-dev (2019.2-1ubuntu1) ...
Removing xfce4-mount-plugin (1.1.3-2) ...
Removing xubuntu-icon-theme (20.04.2) ...
Removing libavutil55:amd64 (7:3.4.8-0ubuntu0.2) ...
Setting up memtest86+ (5.01-3.1ubuntu2.1) ...
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz
Found kernel: /boot/vmlinuz.old
Found kernel: /boot/vmlinuz-5.4.0-48-generic
Found kernel: /boot/vmlinuz-4.15.0-118-generic
Found kernel: /boot/memtest86+.bin
[B]/usr/share/debconf/confmodule: line 44: 3: Bad file descriptor
dpkg: error processing package memtest86+ (--configure):
 installed memtest86+ package post-installation script subprocess returned error exit status 1
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...[/B]
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.1) ...
Processing triggers for gconf2 (3.2.6-6ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu2) ...
[B]Rebuilding /usr/share/applications/bamf-2.index...
Errors were encountered while processing:
 memtest86+
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/B]

---

### Post by Bashing-om on 2020-10-05
anewbie; Hello :)

Let's start to get the ducks on a row before we start shooting.

What is in "your" file " /usr/share/debconf/confmodule " (on or about line 44)? is it particular to memtest ?

If the memtest86+ package is shown as a factor - then is this a EFI system - where then memtest is proprietary and is not subject to ubuntu.

We see what is and then do what we can.

[INDENT]just my 2 cent's worth
[/INDENT]

---

### Post by anewbie on 2020-10-05
/usr/share/debconf/confmodule
--
this file actually has a date of 2019 on it so the install did not replace it. I do not believe it is specific to memtest but the kernel.

The problem is this line:
_db_cmd () {
        _db_internal_IFS="$IFS"
        IFS=' '
       ** printf '%s\n' "$*" >&3**
        # Set to newline to get whole line.
        IFS='
---
Actually it seems specific to memtest86 and i was able to resolve it by removing the package. Reinstalling it produces the same problem so the config foo for memtest86 is broken. I'm happy to leave it removed so that resolve my issue but the package itself should be either fixed or removed from ubuntu given that it is broken.

---

### Post by Bashing-om on 2020-10-05
anewbie; Great :D

You do good work -

Again is this a EFI box ?
[http://www.memtest86.com/](http://www.memtest86.com/) <- proprietary offering

[INDENT][INDENT]maybe so
[/INDENT][/INDENT]

---

### Post by anewbie on 2020-10-06
No. It is the standard ubuntu package memtest86+. It has to my knowledge always been a gnu ubuntu offering.

---

### Post by Bashing-om on 2020-10-06
anewbie; :)

> **anewbie said:**
> No. It is the standard ubuntu package memtest86+. It has to my knowledge always been a gnu ubuntu offering.

A truth for those of us who run legacy systems :D

[INDENT][INDENT]the times, though, do change
[/INDENT][/INDENT]

---

