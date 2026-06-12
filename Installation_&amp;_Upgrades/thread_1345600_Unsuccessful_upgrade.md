---
title: "Unsuccessful upgrade"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by sonriente on 2009-12-04
Hello!

I have a terrible problem. I decided to upgrade my Ubuntu x64 9.04 up to the 9.10 version.
While upgrading my usb keyboard  switched off, though my usb mouse was still working for sometime. In a while the mouse stopped working as well and then a popup window appeared which suggested to replace one of the configure files. Isn't it funny really?
I rebooted my PC and the system began to boot once again but the following error arose:

/: waiting for /dev/disk/by-uuid/.....
/tmp waiting for (null)
swap: waiting for UUID=....
/proc/bus/usb: waiting for none

Could anybody help me please? I would appreciate it greatly.

---

### Post by dstew on 2009-12-04
There may be a problem with your /etc/fstab file. Does the system boot at all? Does it boot in recovery mode? If it boots, look at the UUID numbers of your partitions using the **blkid** command. Then, look at your /etc/fstab file using the command ```
more /etc/fstab
```. If the UUID numbers do not match, you can edit the /etc/fstab file to put in the correct numbers. Did you re-partition or re-format any partitions during the upgrade? In particular, did you upgrade an ext3 partition to ext4?

If you can't boot your installed system, you can do the same things from a  Live CD boot. It is more complicated, since you have to mount your hard disk linux root filesystem onto the Live CD file system in order to mess with /etc/fstab, but it can be done.

---

### Post by sonriente on 2009-12-06
Thank you for your reply and sorry for my slow response. 
I have figured out the problem.
Below I've written the steps to be done in such situations. May be they will be useful for somebody.
First of all, I've logged in the single-user mode and found an extra line in my fstab file. (I have forgotten about that I added it before).
Then I've re-mounted the filesystem in the RW mode:

# mount -o remount rw /

However it has not solved the problem.

As the next step I've tried to resume the upgrade process:

#sudo dpkg --configure -a


And this has solved the issue.

---

