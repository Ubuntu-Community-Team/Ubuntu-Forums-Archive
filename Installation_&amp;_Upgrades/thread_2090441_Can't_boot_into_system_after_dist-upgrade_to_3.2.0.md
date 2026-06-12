---
title: "Can't boot into system after dist-upgrade to 3.2.0-33 linux"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by latestversion on 2012-12-02
I did a 'sudo apt-get dist-upgrade' a couple of weeks ago in Ubuntu 12.04 and was no longer able to boot into my system (Dell XPS 15z), getting the following error on a black screen that doesn't go anywhere:

```
[drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
[drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
```On the grub boot screen I was able to select 'Previous Linux versions' and boot with 3.2.0-32 successfully.

After the latest upgrade (today) to 3.2.0-34, I thought the problem might have been fixed, but it gives the same error upon startup. But booting with 3.2.0-32 still works. How can I fix this so that I can keep up to date with the updates?

This may also be related: when installing Ubuntu 12.04 for the first time on this hardware I got some similar problems and resolved them as suggested on the forums by doing the following, but those settings still apply in the grub configuration:

```
sudo vi /etc/default/grub # Change to GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq quiet splash"
sudo upgdate-grub

```

---

### Post by 2F4U on 2012-12-02
There are bug reports on such an issue from both Ubuntu and Fedora:

[https://bugzilla.redhat.com/show_bug.cgi?id=709115](https://bugzilla.redhat.com/show_bug.cgi?id=709115)
[https://bugs.launchpad.net/ubuntu/+bug/913272](https://bugs.launchpad.net/ubuntu/+bug/913272)

However, without knowing your hardware its impossible to judge if your problem is related.

---

### Post by latestversion on 2012-12-02
Thanks for the Ubuntu bug reports, they are very certainly related (a couple of comments in that issue from people with the exact same model of laptop)! I will try some of the solutions mentioned in that report.

By the way, I checked the apt logs of what else was installed in the same  dist-upgrade command that was issued when upgrading to 3.2.0-33, and it  is the following. Is there any of these packages that might be causing  this problem? (I changed the formatting to make it more readable.)

```
Start-Date: 2012-11-19  21:52:37

Commandline: apt-get dist-upgrade

Install:

linux-headers-3.2.0-33:amd64 (3.2.0-33.52, automatic),
linux-image-3.2.0-33-generic:amd64 (3.2.0-33.52),
linux-headers-3.2.0-33-generic:amd64 (3.2.0-33.52, automatic)

Upgrade:

python-libproxy:amd64 (0.4.7-0ubuntu4, 0.4.7-0ubuntu4.1),
libswscale2:amd64 (0.8.3-0ubuntu0.12.04.1, 0.8.4-0ubuntu0.12.04.1),
libqt4-declarative:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-declarative:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libavutil51:amd64 (0.8.3-0ubuntu0.12.04.1, 0.8.4-0ubuntu0.12.04.1),
libqt4-qt3support:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-qt3support:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libproxy1-plugin-gsettings:amd64 (0.4.7-0ubuntu4, 0.4.7-0ubuntu4.1),
qdbus:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
virtualbox:amd64 (4.1.12-dfsg-2ubuntu0.1, 4.1.12-dfsg-2ubuntu0.2),
gnome-settings-daemon:amd64 (3.4.2-0ubuntu0.4, 3.4.2-0ubuntu0.5),
libqt4-test:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-script:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-script:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-designer:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-designer:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-network:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-network:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-dbus:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-dbus:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libproxy1:amd64 (0.4.7-0ubuntu4, 0.4.7-0ubuntu4.1),
libproxy1:i386 (0.4.7-0ubuntu4, 0.4.7-0ubuntu4.1),
linux-generic:amd64 (3.2.0.32.35, 3.2.0.33.36),
libproxy1-plugin-networkmanager:amd64 (0.4.7-0ubuntu4, 0.4.7-0ubuntu4.1),
virtualbox-dkms:amd64 (4.1.12-dfsg-2ubuntu0.1, 4.1.12-dfsg-2ubuntu0.2),
apport:amd64 (2.0.1-0ubuntu14, 2.0.1-0ubuntu15),
libqt4-opengl:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-opengl:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libavcodec53:amd64 (0.8.3-0ubuntu0.12.04.1, 0.8.4-0ubuntu0.12.04.1),
libqt4-xmlpatterns:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-xmlpatterns:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-sql-sqlite:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqtcore4:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqtcore4:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
python-problem-report:amd64 (2.0.1-0ubuntu14, 2.0.1-0ubuntu15),
linux-headers-generic:amd64 (3.2.0.32.35, 3.2.0.33.36),
linux-image-generic:amd64 (3.2.0.32.35, 3.2.0.33.36),
libpostproc52:amd64 (0.8.3-0ubuntu0.12.04.1, 0.8.4-0ubuntu0.12.04.1),
libqt4-sql:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-sql:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-svg:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-svg:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-xml:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-xml:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libavformat53:amd64 (0.8.3-0ubuntu0.12.04.1, 0.8.4-0ubuntu0.12.04.1),
libtiff4:amd64 (3.9.5-2ubuntu1.2, 3.9.5-2ubuntu1.3),
libtiff4:i386 (3.9.5-2ubuntu1.2, 3.9.5-2ubuntu1.3),
virtualbox-qt:amd64 (4.1.12-dfsg-2ubuntu0.1, 4.1.12-dfsg-2ubuntu0.2),
libqtgui4:amd64 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqtgui4:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
python-apport:amd64 (2.0.1-0ubuntu14, 2.0.1-0ubuntu15),
linux-libc-dev:amd64 (3.2.0-32.51, 3.2.0-33.52),
libqt4-sql-mysql:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
libqt4-scripttools:i386 (4.8.1-0ubuntu4.2, 4.8.1-0ubuntu4.3),
apport-gtk:amd64 (2.0.1-0ubuntu14, 2.0.1-0ubuntu15)

End-Date: 2012-11-19  21:57:35

```

---

