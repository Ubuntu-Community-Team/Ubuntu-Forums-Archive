---
title: "What's the deal with new udev?"
date: 2009-01-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-07
Hi all, 
 There is a new release of udev, a big changelog, can somebody break it down for rest of us what its talking about. 
> 
udev (136-1) jaunty; urgency=low

  One of the biggest changes in this release is that the default rules
  are no longer conffiles and are now installed into /lib/udev/rules.d

  You may still add your custom rules to /etc/udev/rules.d and these
  will be processed after the default ones, and can thus override
  anything they do.

  To avoid side-effects of default rules (ie. running of programs),
  create the file with the same name.

  * New upstream release:
    - Changed to use autoconf
    - Default rules moved to /lib/udev/rules.d
    - udevadm symlinks removed.
    - udevadm info output for --device-id-of-file changed.
    - udevadm trigger has new --type option.
    - libvolume_id soname change.
    - libvolume_id now able to return multiple matches for a single block
      device, or no matches if conflicting metadata found.
    - libudev shared library introduced.
    - by-id/scsi-* and by-id/ieee-* links both created by Firewire disks.
    - Optical devices no longer probed for raid signatures.  (LP: #283316).
    - DEVTYPE=disk/partition no longer exported by default.
    - pnp support removed now that we have MODALIAS support in kernel.
    - Introduced /dev/block and /dev/char (see changelog for 124-6).
    - Rule matching engine changed, limits such as 5 ENV and ATTR matches
      and only one match for any other key are now gone.  NAME assignment
      is no longer special cased (subsequent assignments will now overwrite
      unless := is used).
    - Substantial memory footprint reduction work.

  * debian/patches/01-cdrom-vol_id-probing.patch:
    - Dropped, included in upstream release.
  * debian/patches/80-extras-dvb_device_name.patch:
    - Dropped, no longer compiles and won't be needed from the next kernel
      onwards.  Since these aren't boot critical, just do it in shell.
  * debian/patches/80-extras-firmware.patch:
    - Dropped, no longer compiles anyway so we may as well just use the
      upstream firmware.sh which also supports crazy PackageKit stuff
  * debian/patches/80-extras-ide_media.patch:
    - Dropped, the ide subsystem has had MODALIAS support since hardy using
      the media type.
  * debian/patches/80-extras-usb_device_name.patch:
    - Dropped, we no longer need to support the legacy usb_device subsystem
      since we've had the newer ENVTYPE=usb_device objects since hardy.
    - Bump minimum kernel version to 2.6.24 for the initramfs.
  * debian/patches/80-extras-vio_type.patch:
    - Dropped, we don't even build these modules.
  * debian/patches/80-extras-watershed.patch:
    - Dropped, we do not used it in any udev rules shipped in this package;
      it can be separated out into another source package if other things
      still use it (which we should try to make them not).

  * Merged our rules with Upstream default rules, this results in a number
    of minor changes but achieves consistency with other distributions:
    * /dev/net/tun is now mode 666, the kernel documentation says this is safe
      since you still need CAP_NET_ADMIN to create tunnels.
    * /dev/srN are now the definitive names of SCSI CD-ROM devices, with
      /dev/scdN as deprecated symlinks to them; this is the exact opposite of
      how we had things before.
    * /dev/nvram is now in the kmem group, the nvram group has been dropped.
    * Removable disks have moved from the floppy group to the disk group, with
      floppy now largely reserved for real old-fashioned floppy devices (and
      the /dev/fd* devices are now all in floppy).  LP: #260982.
    * CD/BD-ROM devices should now consistently be in the cdrom group.
    * Tape devices should now consistently be in the tape group.
    * More video devices consistently in the video group.
    * Printers on printer-specific ports now in the lp group, ppdev module
      loaded when necessary.
    * The scanner group has been dropped, it's become increasingly difficult
      to determine what is and isn't a scanner; especially with multi-function
      devices - access to scanners is better handled by ACL now.
    * /dev/input devices no longer group writable
    * /dev/tty devices are now group writable (wall/write enabled)
    * /dev/rtc restored to root group.  LP: #306458.
    * Various changes to the way the dialout group is assigned, should lead
      to more reliable device groups thus specific rules dropped.
      LP: #264792.
    * Support for infiniband, iowarrior, usbdpfp, sxctl, rioctl, bsg and
      etherd devices.

  * Add LSB headers to init scripts.  LP: #312324.
  * Correct name of CD Aliases generator in postinst.  LP: #250232.
  * Fixed /usr/lib/libvolume_id.so symlink.  LP: #232434.
* Dropped /dev/.static/dev.  LP: #253786.

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002619.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002619.html)

While 50-60% of the stuff I could understand but some I could not 

I understood all about the different device groups and stuff, but not so much the earlier part.

---

### Post by gnomeuser on 2009-01-07
Upstream udev has been encouraging distributions to use their reference udev rules instead of baking their own. Debian has historically been opposed to following this recommandation. This update brings Ubuntu in line with upstream. it means moving a lot of device nodes around mainly but the new locations are well tested as they are the standard in pretty much any other distro.

You may experience a few little glitches if anything has hardcoded assumptions based on the old udev layout.

---

### Post by luca_linux on 2009-01-07
That's great!

---

### Post by xebian on 2009-01-07
@shirishag
It means more consistent naming of devices.  My Debian names my IDE drives as /dev/hdan  while my Kubuntu names them /dev/sdan or /dev/sdbn which is annoying when you have fixed mount points and/or you have other sata drives as well.

---

### Post by ShirishAg75 on 2009-01-07
> **gnomeuser said:**
> Upstream udev has been encouraging distributions to use their reference udev rules instead of baking their own. Debian has historically been opposed to following this recommandation. This update brings Ubuntu in line with upstream. it means moving a lot of device nodes around mainly but the new locations are well tested as they are the standard in pretty much any other distro.

You may experience a few little glitches if anything has hardcoded assumptions based on the old udev layout.

Has Debian also moved to upstream udev ?

Also any idea why are/were they opposed to the move?

---

### Post by Eclipse. on 2009-01-07
> **ShirishAg75 said:**
> Has Debian also moved to upstream udev ?

Also any idea why are/were they opposed to the move?

The package is imported from debian so yeap their using it, in sid anyway.

---

### Post by gnomeuser on 2009-01-07
> **ShirishAg75 said:**
> Has Debian also moved to upstream udev ?

Also any idea why are/were they opposed to the move?

The polite answer is that the debian maintainer felt that he was right and that upstream was wrong. I suspect he has either been removed from his position or convinced by reason. Debian is to the best of my knowledge the only major distribution which was not on the reference udev rules so this is a big victory for sanity.

---

### Post by NoXXiOuS on 2009-01-08
well this update is nice but it actually breaks the LVM setups as initramfs is not ready for new udev change. 
During the boot ubuntu droped to initramfs shell, stating that it cannot find root LVM volume

I hand to issue:
```
lvm vgchange -a y
exit
```
to fix it

---

### Post by gnomeuser on 2009-01-08
> **NoXXiOuS said:**
> well this update is nice but it actually breaks the LVM setups as initramfs is not ready for new udev change. 
During the boot ubuntu droped to initramfs shell, stating that it cannot find root LVM volume

I hand to issue:
```
lvm vgchange -a y
exit
```
to fix it

bugs happen, welcome to the development release. Call it the birthpain of progress but we will be very happy to take your bugreports.

---

### Post by cszikszoy on 2009-01-08
Anyone have any idea if this is some sort of initial step towards moving away from hal and to DeviceKit?

---

### Post by ShirishAg75 on 2009-01-09
Just was reading about devicekit 

The relevant stuff. 

[http://lists.freedesktop.org/archives/hal/2008-May/011560.html](http://lists.freedesktop.org/archives/hal/2008-May/011560.html)

[http://fedoraproject.org/wiki/Features/DeviceKit](http://fedoraproject.org/wiki/Features/DeviceKit)

[http://lists.freedesktop.org/mailman/listinfo/devkit-devel](http://lists.freedesktop.org/mailman/listinfo/devkit-devel)

[http://hal.freedesktop.org/releases/](http://hal.freedesktop.org/releases/)

Look for devicekit, devicekit-disks devicekit-power packages latest releases.

From git one can do 

```

git clone [git://anongit.freedesktop.org/git/devicekit/devicekit](git://anongit.freedesktop.org/git/devicekit/devicekit)
git clone [git://anongit.freedesktop.org/git/devicekit/devicekit-disks](git://anongit.freedesktop.org/git/devicekit/devicekit-disks)
git clone [git://anongit.freedesktop.org/git/devicekit/devicekit-power](git://anongit.freedesktop.org/git/devicekit/devicekit-power)

```

I didn't know freedesktop also used git. Cool though :)

---

### Post by vikrant82 on 2009-01-09
One thing I know is after this update my network devices became eth2 and eth3, from eth0, eth1. So had to manually edit the rules file to get them to behave again.

---

### Post by cszikszoy on 2009-01-09
> **vikrant82 said:**
> One thing I know is after this update my network devices became eth2 and eth3, from eth0, eth1. So had to manually edit the rules file to get them to behave again.

Filing a bug report against udev on launchpad describing the problem you just had would probably be the best course of action.

---

### Post by tawmas on 2009-01-10
Did anybody notice that, after this update, a message from udev shortly appears at the beginning of boot, telling that it can't find /etc/udev/rules.d?

Boot proceeds correctly (except that usplash is not working for me since the same updates, and I have no idea if the two are related or unrelated), and I find no trace of this message in dmesg or syslog, but I do see it in the console.

---

### Post by ShirishAg75 on 2009-01-10
vikrant82 and tamwas, 
 you guys need to file bugs. 

Do the following :-

```
$ ubuntu-bug udev
```

Explain that bug as much as possible using stuff from terminal etc. 

ubuntu-bug usually pulls stuff which are necessary for sorting most of the problems. Even if it doesn't you can always post the syslog.

---

