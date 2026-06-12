---
title: "Failed 9.10 beta upgrade - left with unbootable machine (kinit, mountall)"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by niroht on 2009-10-06
Edit: This is resolved, see below.

Hello,

I decided to try the Beta last night to take advantage of some of the new features I'm looking forward to. Midway through the install I was prompted to reboot. Which I then did. Now the system won't boot any longer. I've left it on this screen for  roughtly 6 minutes before calling it frozen.

CTRL+ALT+F7 screen gives:
> mountall: symbol lookup error: mountall: undefined symbol: udev_monitor_filter_add_match_subsystem_devtype
init: mountall main process (756) terminated with status 127
rm: cannot remove '/forcefsck': read-only file system
init: mountall post-stop process (757) terminated with status 1

CTRL+ALT+F1 screen gives:
> kinit: name_to_dev_t(/dev/disk/by-uuid/[...]) = dev(8,4)
kinit: trying to resume from /dev/dis/by-uuid/[...]
kinit: no resume image, doing normal boot...

There is a long uuid provided that I removed from the quote above to save me typing, but I have checked in the resume file (/etc/initramfs-tools/conf.d/resume) and it matches what it's supposed to be. I've also then just remarked the whole resume line out, to no avail.

Steps I've taken:
[LIST]
[*]Checked and eventually remarked out resume line from resume file (/etc/initramfs-tools/conf.d/resume)
[*]Changed swap partition in fstab to /dev/sda4 instead of uuid
[/LIST]

I've read about doing something like:
> sudo swapoff /dev/sda4
sudo mkswap /dev/sda4
sudo update-initramfs -u
from a live disk, but can you run update-initramfs from a live cd and have it create the right file on the right /?

Any help is appreciated as my machine currently doesn't seem to boot any longer :(

-----------
This issue has thankfully been resolved. The steps taken to fix the issue was to boot into a live cd, chroot the original drive, and complete the apt-get dist-upgrade.

---

### Post by blindvic on 2009-10-09
And if don't a have cd-rom to boot from? And i cannot boot from usb?
I have just possibility to edit menu.lst file (grub4dos)

---

### Post by Amaranth on 2009-10-09
You'll need to get a LiveCD.

---

### Post by blindvic on 2009-10-11
> **Amaranth said:**
> You'll need to get a LiveCD.
And what's next? I don't have a cd-rom.

---

### Post by VMC on 2009-10-11
> **blindvic said:**
> And what's next? I don't have a cd-rom.

Go to [Bootland]("http://www.boot-land.net/forums/") for assistance. Also have you searched poor mans install?

---

### Post by akodoori on 2009-10-13
i too suffer from the same problem.. i dont have access to Ubuntu terminal also
KINDLY HELP ... Its urgent

---

### Post by flyingflying on 2009-10-22
Could you please be more specific about how to do "The steps taken to fix the issue was to boot into a live cd, chroot the original drive, and complete the apt-get dist-upgrade."? Thank you very much.

---

### Post by chrisco23 on 2009-10-23
I'm having this same problem and my Ubuntu is a VM in VMWare Workstation.

I had just done several hours of work.  I saved my work but I wasn't expecting to not be able to reboot or access my virtual Ubuntu at all.

Can someone please help?


Thanks,
Chris

---

