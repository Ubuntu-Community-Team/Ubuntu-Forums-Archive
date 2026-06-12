---
title: "/boot hosed..."
date: 2015-12-10
forum: Installation &amp; Upgrades
---

### Post by accentaigu on 2015-12-10
I probably misplaced an asterisk or something when I cleaned out old kernels as usual (with rm -f) when /boot got full. Tried boot-repair, but no success. This is when I discovered /boot was totally empty. What would you suggest: Reinstall, or is there an easy way to repair? I am an intermediate user able to follow instructions, but not knowledgeable about chroot and such or advanced enough to know the right answer... ;)
My installation is a default Ubuntu LTS installation with single boot. Or was... BIOS unchanged.

Boot repair generated the following link with output:
[http://paste2.org/bE0s8tLv](http://paste2.org/bE0s8tLv)
I am unable to understand which drive it is actually trying to fix. Should be sda...

Thanks,
/Chris

---

### Post by ian-weisser on 2015-12-10
I vote Reinstall.
Backup your data first.
By directly deleting files placed by the package manager, you have also hosed your package management, and that may be a lot more spaghetti to untangle than is worthwhile to you.

If you feel a repair is worthwhile, then use 'uname' to determine your current kernel, and 'apt-get install --reinstall' to reinstall that kernel.
However, your package manager may still require a great deal of reconstructive surgery before I would trust it as stable.

If you have a separate /boot partition, then I suspect you don't have a 'default Ubuntu LTS installation'. Separate /boot isn't default.

---

### Post by furtom on 2015-12-10
If he&#8217;s talking about chroot, I don&#8217;t think he&#8217;s running a working instance of Ubuntu, so uname &#8211;r isn&#8217;t applicable here. But the OP is on the right track.

To reinstall a kernel and repair grub, you will have to boot a live environment and chroot to install a kernel, etc. This isn&#8217;t that difficult, but this may be a good time to reinstall. Which would you prefer?

---

### Post by oldfred on 2015-12-10
Boot-Repair with its full uninstall/reinstall of grub & tick new kernel may be enough to restore it. It pretty much walks you thru a chroot. Make sure your LVM is also mounted and unencrypted if encrypted also.
Worth a try if you do not have good backups for a new install.

---

### Post by accentaigu on 2015-12-11
Thanks for the suggestions!
I was not aware of the package manager issue, but it does make sense now that you point it out. After all, new kernels do not come with the stork! ;)
I also saw somewhere that there is a setting to clean up old kernels automatically.

Thanks,
/Chris

---

