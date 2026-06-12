---
title: "mkinitramfs script processing error"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by masuch on 2011-10-31
Hi,

I have been upgraded and got this error:

  # Setting up initramfs-tools (0.99ubuntu8) ...
  # update-initramfs: deferring update (trigger activated)
  # Processing triggers for initramfs-tools ...
  # update-initramfs: Generating /boot/initrd.img-3.1.0-1-generic
  # /usr/sbin/mkinitramfs: 71: basename: not found
  # /usr/sbin/mkinitramfs: 97: touch: not found
  # /usr/sbin/mkinitramfs: 98: readlink: not found
  # /usr/sbin/mkinitramfs: 168: mktemp: not found
  # update-initramfs: failed for /boot/initrd.img-3.1.0-1-generic with 1.
  # dpkg: error processing initramfs-tools (--configure):
  #  subprocess installed post-installation script returned error exit status 1
  # Errors were encountered while processing:
  #  initramfs-tools
  # sh: /usr/bin/test: not found
  # sh: /bin/echo: not found
  # E: Problem executing scripts DPkg::Post-Invoke '/usr/bin/test -e /usr/share/dbus-1/system-services/org.freedesktop.PackageKit.service && /usr/bin/test -S /var/run/dbus/system_bus_socket && /usr/bin/dbus-send --print-reply --system --dest=org.freedesktop.PackageKit --type=method_call /org/freedesktop/PackageKit org.freedesktop.PackageKit.StateHasChanged string:'cache-update' > /dev/null; /bin/echo > /dev/null'
  # E: Sub-process returned an error code
  # E: Sub-process /usr/bin/dpkg returned an error code (1)

----
I have checked mkinitramfs script and
basename, touch, readlink and mktemp files are presented.

Why this script saying that "command" not found if all files are there ?
Why script initramfs-tools looking for /usr/bin/test and /bin/echo if those commands are not there ?

what is the problem and how to fix it ?
thanks for any clue.

P.S.: 
(delete /var/lib/initramfs-tools/3.1.0-1-generic file 
and run:
sudo dpkg --configure -a
sudo dpkg --configure initramfs-tools
did not help)

regards,
M.

---

### Post by masuch on 2011-11-02
I had to solve it by creating links in appropriate directories to run mkinitramfs and other scripts smoothly. Generated script is attached if somebody is interested and get into trouble after installing coreutils 8.14 like me - (I was punished because I was lazy to read whole (INSTALL and ./configure --help) documentation and made ./configure with default settings which leads to move some commands-files to another directories than some scripts are expecting to be ).

---

