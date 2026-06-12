---
title: "Update-manager error messages"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by macabro22 on 2008-06-07
Guys can someone help with this? My system fails to update and I get error messages like these when I install any software from the repositories. Please check the text in RED, I suspect it might lead to the cause of the problem.

```
Selecting previously deselected package libqtcore4.
(Reading database ... 229078 files and directories currently installed.)
Unpacking libqtcore4 (from .../libqtcore4_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Replacing files in old package libqt4-core ...
Replacing files in old package libqt4-gui ...
Selecting previously deselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Replacing files in old package libqt4-core ...
Selecting previously deselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Replacing files in old package libqt4-core ...
Selecting previously deselected package libqt4-script.
Unpacking libqt4-script (from .../libqt4-script_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Replacing files in old package libqt4-core ...
Selecting previously deselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Replacing files in old package libqt4-gui ...
Preparing to replace libqt4-qt3support 4.3.4-0ubuntu3 (using .../libqt4-qt3support_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Unpacking replacement libqt4-qt3support ...
Preparing to replace libqt4-gui 4.3.4-0ubuntu3 (using .../libqt4-gui_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Unpacking replacement libqt4-gui ...
Selecting previously deselected package libqt4-designer.
Unpacking libqt4-designer (from .../libqt4-designer_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Selecting previously deselected package libqt4-network.
Unpacking libqt4-network (from .../libqt4-network_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Replacing files in old package libqt4-core ...
Preparing to replace libqt4-sql 4.3.4-0ubuntu3 (using .../libqt4-sql_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Unpacking replacement libqt4-sql ...
Selecting previously deselected package libqt4-opengl.
Unpacking libqt4-opengl (from .../libqt4-opengl_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Selecting previously deselected package libqt4-svg.
Unpacking libqt4-svg (from .../libqt4-svg_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Selecting previously deselected package libqt4-assistant.
Unpacking libqt4-assistant (from .../libqt4-assistant_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Selecting previously deselected package libqt4-test.
Unpacking libqt4-test (from .../libqt4-test_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Replacing files in old package libqt4-core ...
Preparing to replace libqt4-core 4.3.4-0ubuntu3 (using .../libqt4-core_4.4.0-1ubuntu5~hardy1_amd64.deb) ...
Unpacking replacement libqt4-core ...
Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Running postinst hook script /sbin/update-grub.
[COLOR="Red"][: 25: ==: unexpected operator
exec: 25: -a: not found[/COLOR]
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.24-17-generic:
 linux-backports-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-backports-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.24-18-generic:
 linux-backports-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-backports-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.24-17-rt (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-rt
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-17-rt (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.24-18-rt (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-rt
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-18-rt (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-generic:
 linux-ubuntu-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-rt:
 linux-ubuntu-modules-2.6.24-17-rt depends on linux-image-2.6.24-17-rt; however:
  Package linux-image-2.6.24-17-rt is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-rt:
 linux-ubuntu-modules-2.6.24-18-rt depends on linux-image-2.6.24-18-rt; however:
  Package linux-image-2.6.24-18-rt is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-hardy-generic:
 linux-backports-modules-hardy-generic depends on linux-backports-modules-2.6.24-18-generic; however:
  Package linux-backports-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-backports-modules-hardy-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-rt:
 linux-image-rt depends on linux-image-2.6.24-18-rt; however:
  Package linux-image-2.6.24-18-rt is not configured yet.
 linux-image-rt depends on linux-ubuntu-modules-2.6.24-18-rt; however:
  Package linux-ubuntu-modules-2.6.24-18-rt is not configured yet.
dpkg: error processing linux-image-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-generic:
 linux-restricted-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-rt:
 linux-restricted-modules-2.6.24-17-rt depends on linux-image-2.6.24-17-rt; however:
  Package linux-image-2.6.24-17-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-rt:
 linux-restricted-modules-2.6.24-18-rt depends on linux-image-2.6.24-18-rt; however:
  Package linux-image-2.6.24-18-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-rt:
 linux-restricted-modules-rt depends on linux-restricted-modules-2.6.24-18-rt; however:
  Package linux-restricted-modules-2.6.24-18-rt is not configured yet.
dpkg: error processing linux-restricted-modules-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-rt:
 linux-rt depends on linux-image-rt (= 2.6.24.18.20); however:
  Package linux-image-rt is not configured yet.
 linux-rt depends on linux-restricted-modules-rt (= 2.6.24.18.20); however:
  Package linux-restricted-modules-rt is not configured yet.
dpkg: error processing linux-rt (--configure):
 dependency problems - leaving unconfigured
Setting up libqtcore4 (4.4.0-1ubuntu5~hardy1) ...

Setting up libqt4-xml (4.4.0-1ubuntu5~hardy1) ...

Setting up libqt4-dbus (4.4.0-1ubuntu5~hardy1) ...

Setting up libqt4-script (4.4.0-1ubuntu5~hardy1) ...

Setting up libqtgui4 (4.4.0-1ubuntu5~hardy1) ...

Setting up libqt4-designer (4.4.0-1ubuntu5~hardy1) ...

Setting up libqt4-network (4.4.0-1ubuntu5~hardy1) ...

Setting up libqt4-sql (4.4.0-1ubuntu5~hardy1) ...

Setting up libqt4-qt3support (4.4.0-1ubuntu5~hardy1) ...

Setting up libqt4-assistant (4.4.0-1ubuntu5~hardy1) ...

Setting up libqt4-opengl (4.4.0-1ubuntu5~hardy1) ...

Setting up libqt4-svg (4.4.0-1ubuntu5~hardy1) ...

Setting up libqt4-gui (4.4.0-1ubuntu5~hardy1) ...
Setting up libqt4-test (4.4.0-1ubuntu5~hardy1) ...

Setting up libqt4-core (4.4.0-1ubuntu5~hardy1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-2.6.24-17-generic
 linux-backports-modules-2.6.24-17-generic
 linux-image-2.6.24-18-generic
 linux-backports-modules-2.6.24-18-generic
 linux-image-2.6.24-17-rt
 linux-image-2.6.24-18-rt
 linux-ubuntu-modules-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-17-rt
 linux-ubuntu-modules-2.6.24-18-generic
 linux-ubuntu-modules-2.6.24-18-rt
 linux-backports-modules-hardy-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-18-generic
 linux-restricted-modules-generic
 linux-generic
 linux-image-rt
 linux-restricted-modules-2.6.24-17-generic
 linux-restricted-modules-2.6.24-17-rt
 linux-restricted-modules-2.6.24-18-rt
 linux-restricted-modules-rt
 linux-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.24-17-rt (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-rt
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-17-rt (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.24-18-rt (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-rt
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-18-rt (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-rt:
 linux-ubuntu-modules-2.6.24-18-rt depends on linux-image-2.6.24-18-rt; however:
  Package linux-image-2.6.24-18-rt is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-rt (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-rt:
 linux-ubuntu-modules-2.6.24-17-rt depends on linux-image-2.6.24-17-rt; however:
  Package linux-image-2.6.24-17-rt is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-rt (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.24-17-generic:
 linux-backports-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-backports-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-rt:
 linux-image-rt depends on linux-image-2.6.24-18-rt; however:
  Package linux-image-2.6.24-18-rt is not configured yet.
 linux-image-rt depends on linux-ubuntu-modules-2.6.24-18-rt; however:
  Package linux-ubuntu-modules-2.6.24-18-rt is not configured yet.
dpkg: error processing linux-image-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.24-18-generic:
 linux-backports-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-backports-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-rt:
 linux-restricted-modules-2.6.24-17-rt depends on linux-image-2.6.24-17-rt; however:
  Package linux-image-2.6.24-17-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-rt:
 linux-restricted-modules-2.6.24-18-rt depends on linux-image-2.6.24-18-rt; however:
  Package linux-image-2.6.24-18-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-backports-modules-hardy-generic:
 linux-backports-modules-hardy-generic depends on linux-backports-modules-2.6.24-18-generic; however:
  Package linux-backports-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-backports-modules-hardy-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-generic:
 linux-ubuntu-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-rt:
 linux-rt depends on linux-image-rt (= 2.6.24.18.20); however:
  Package linux-image-rt is not configured yet.
dpkg: error processing linux-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-generic:
 linux-restricted-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-rt:
 linux-restricted-modules-rt depends on linux-restricted-modules-2.6.24-18-rt; however:
  Package linux-restricted-modules-2.6.24-18-rt is not configured yet.
dpkg: error processing linux-restricted-modules-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-17-rt
 linux-image-2.6.24-18-rt
 linux-ubuntu-modules-2.6.24-18-rt
 linux-image-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-17-rt
 linux-image-2.6.24-18-generic
 linux-backports-modules-2.6.24-17-generic
 linux-image-rt
 linux-backports-modules-2.6.24-18-generic
 linux-restricted-modules-2.6.24-17-rt
 linux-restricted-modules-2.6.24-18-rt
 linux-restricted-modules-2.6.24-18-generic
 linux-backports-modules-hardy-generic
 linux-ubuntu-modules-2.6.24-18-generic
 linux-ubuntu-modules-2.6.24-17-generic
 linux-rt
 linux-image-generic
 linux-restricted-modules-2.6.24-17-generic
 linux-restricted-modules-generic
 linux-restricted-modules-rt
 linux-generic

```

---

