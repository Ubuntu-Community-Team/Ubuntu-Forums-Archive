---
title: "Breezy can't boot"
date: 2005-10-31
forum: Installation &amp; Upgrades
---

### Post by lukastlez on 2005-10-31
Hi,

I've tryed to install breezy on my PC from both DVD and CD with no success. The first stage appears to work fine, but breezy can't boot for the first time. The boot process stops with these lines (I've copied it by hand, there might be some typing mistake):

Begin: Mounting root filesystem ...
Begin: Running /scripts/local-top ...
[4294680.229000] device_mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294680.258000] cdrom: open failed.
  /dev/cdrom: open failed: No medium found
[4292680.314000] cdrom: open failed.
  /dev/cdrom1: open failed: No medium found
  No volume groups found
/scripts/local-top/evms: 31: /sbin/evms_activate: not found
Done.
Begin: Running /scripts/local-premounts ...
[4294680.349000] Attempting manual resume
[4294680.350000] swsusp: Suspend partition has wrong signature?
Done.
FATAL: Module unknown not found.
mount: Mounting /dev/root on /root failed: No such device
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init


and then the BusyBox shell starts.
I tryed both lilo and grub, but nothing.
I've installed / on hdb5 and I tryed to put /boot on either hda2 or hdb5, but nothing.

It bothers me because I've removed hoary that worked fine.

Can someone help me?

Thanks a lot...

---

### Post by lukastlez on 2005-10-31
I'm afraid I've found what's wrong with my PC and Breezy...
It's a bug of initramfs-tools. Take a look at [https://bugzilla.ubuntu.com/show_bug.cgi?id=15537](https://bugzilla.ubuntu.com/show_bug.cgi?id=15537)

I'm sorry, but I have to abandon ubuntu...  :(

---

### Post by lukastlez on 2006-05-03
It seems that someone has found a workaround :D :
[https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/21759](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/21759)

---

### Post by cocox on 2006-05-14
hi, the solution posted by tarski ([https://launchpad.net/distros/ubuntu...ols/+bug/21759](https://launchpad.net/distros/ubuntu...ols/+bug/21759)) fixes the nomenclature change of the HardDrive?? for example ...hda to hdc... ???:confused:

here is my problem if you are wondering for something...
[http://ubuntuforums.org/showthread.php?t=174537&highlight=busybox](http://ubuntuforums.org/showthread.php?t=174537&highlight=busybox)

thank you,

---

### Post by cocox on 2006-05-15
Here is the solution good luck

[http://www.ubuntuforums.org/showthread.php?p=1017808#post1017808](http://www.ubuntuforums.org/showthread.php?p=1017808#post1017808)

:mrgreen:

---

