---
title: "Cannot boot after Ubuntu Software Update"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by alphasoup on 2010-12-17
This has happened to me just about every time I update a system with both an internal and a usb drive connected, when both drives have some valid Linux partitions, and when the software update includes a new kernel.

Since it happened again 2 days ago with the latest update of Ubuntu 10.04.X (and regularly since early 8.x) I thought it might be time to say something...

The issue just happened in 10.04.x with older vintage grub (from previous software
update from 8.x or 9.x to 10.04.x for example).
If your system only uses: /boot/grub/grub.cfg (aka newer grub version)
and no longer used: /boot/grub/menu.lst
you may be OK and can skip the following...
If this happens to you after a fresh install (grub.cfg) please add to this tread.


CONDITIONS of ISSUE:
1) There is another USB drive connected (even on older system that cannot boot from USB due to BIOS and/or USB 1.0 exclusive support).
2) You do a software update containing a new kernel.
3) The update is for: the internal drive, or the USB drive (if you are booted from
USB) -- i.e. there is another Linux drive present:
4) There are 2 or more drives and/or two valid Linux partitions (bootable)
available on the system (even if the second one cannot be booted from).

WHAT GOES WRONG:
The updater when creating the new menu.lst gets confused as follows:
1) it asks if You want to keep the previous config file <-- wise to always select this one.
2) it offers to view a diff between the previous an new version:
  the diff is in fact wrong, it is comparing two invalid versions from the updater,
a menu.lst and a menu.lst~ -- none of these version match the original you booted
from before the software update:
     - The first version has already replaced all the disk UUID with the (bad) UUID from
     any another disk or partition found on the system...
     - The second version has the same (bad) UUID replacement throughout.

     Then the diff can only show the additional 2 sections for the new kernel added in front (normal and recovery),
and you might assume that this is only adding the new kernel entries. WRONG!

If you do not select to keep the original, you will unknowingly commit a menu.lst
that will NO longer work -- turn your system into a paper-weight.
Your new menu.lst will try to boot from another drive probably that does NOT have the
new kernel installed, etc.

To fix this you are out of luck, the recovery option will also not work, you have to
remember exactly what your boot disk UUID is an manually enter into a boot command,
using root=UUID=THE_CORRECT_DISK_LONG_UUID
or use a logical device root=/dev/sda4 for example if you know where your root is, or
a label if you have a unique one root=LABEL=BOOT1.

It may be easier to take the disk to another Ubuntu and rewrite the menu.lst broken
after update, and also adding a couple of USEFUL recovery options that use
1) a logical device and 2) a unique label (as above) for the next software update
someone does and select the option to replace menu.lst.

sudo blkid
#--> to find out what your original UUID really is for the root (and/or boot) partitions
# grab the good UUID of your root partition and copy it:
GOODUUID="<paste valid one here>"

cd /boot/grub

# backup the bad one
cp -p menu.lst menu.lst_bad

# find the bad UUID
grep "UUID=" menu.lst_bad
# copy the bad UUID
BADUUID="<paste bad one here>"

sed -e "s/$BADUUID/$GOODUUID/g" <menu.lst_bad >menu.lst_good

#use your editor to verify menu.lst_good is what you need. Then commit it:
cp men.lst_good menu.lst

It is unfortunate that difficult manual operations are required for a standard updates
when a new kernel is provided while other software updates are so easy and work
so well. You start liking the software update and keep current, until you lose.

Hope that helps other using Debian and Ubuntu!
Great system (also runs great on older hardware) -- Thanks.

---

