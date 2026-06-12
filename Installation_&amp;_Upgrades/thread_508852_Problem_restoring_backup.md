---
title: "Problem restoring backup"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by polemicjunkie on 2007-07-24
Can't seem to fully restore from different kinds of backups.

1st try:

After installing Ubuntu to sda1, I tar'd the root file system from a live-cd environment to another drive.  Then I wiped out the sda1 partition by remaking the filesystem with mke2fs -j /dev/sda1.  Next, I untarred the tar file to sda1 and a quick check of the restored file system looks good.  I confirmed the MBR had not changed, and since I'm only trying to restore to the very same partition, no changes should be needed for the restored /etc/fstab and /boot/grub/menu.1st files (references to (hd0,0) don't change in this case).

Trying to reboot from sda1, the familiar Ubuntu splash screen pops up, but the progress bar never makes it beyond the first notch.  ???



2nd try:

Better progress was made by first backing up with partimage (using systemrescuecd) and then restoring the image followed by running grub interactively (find /boot/grub/stage1 produced (hd0,0);  root (hd0,0);  setup (hd0);  quit).  This time Ubuntu successfully booted to the login screen.


3rd try:

The only difference here from the 2nd try is that I wanted to try restoring to a different partition (sda2).  This implies that /etc/fstab and /boot/grub/menu.1st should be modified to replace instances of (hd0,0) with (hd0,1).  After restoring the same parition image file to sda2 with partimage and then performing the edits to fstab and menu.1st, grub was run interactively in the same manner as above, and the expected (hd0,1) popped up with the find command.  Looks good so far, but the boot splash screen seems to get stuck in same place as in the first try (nothing beyond the first notch in the progress bar).


Any ideas why the 1st and 3rd tries both fail?  Thanks.

---

### Post by polemicjunkie on 2007-07-25
I really would appreciate it if someone could help me to get the restore process working.  Most of the info I found on the web, including Linux Magazine, suggested that file updates to fstab and menu.1st and re-running grub would be the only extra steps necessary to restore to a partition different from the partition backed up.

If this question should be posted to a different topic area, could someone at least let me know that?

Thank you.

---

