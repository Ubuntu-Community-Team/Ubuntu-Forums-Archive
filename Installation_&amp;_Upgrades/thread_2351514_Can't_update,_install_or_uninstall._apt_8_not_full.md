---
title: "Can't update, install or uninstall. apt: 8 not fully installed or removed"
date: 2017-02-04
forum: Installation &amp; Upgrades
---

### Post by gotaproblemwithmything on 2017-02-04
Hi. This problem recently came up.

I can't install updates. sudo apt-get update && sudo apt-get install gives error messages. The following is the last that is printed to console:


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-107-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              E: Sub-process /usr/bin/dpkg returned an error code (1)


I think the problem has to do with my /boot/ partition being full. I am using disk encryption and /boot/ often lacks space. I used to just remove the old kernels (?) with sudo rm initrd.img-3.13.0-100-generic for example. Maybe I should not have done that. Now, if I try to remove them manually to free up space, apt-get just tries to reinstall/repair them again if I try to do any installation, and my /boot/ partition fills right back up. End result is I can't update, install or remove anything.

software updater and software center are also broken.


Thanks for any help.

---

### Post by ian-weisser on 2017-02-04
Yes very likely to be a full /boot partition.
Yes, using 'rm' on package-manager-installed files was unwise. and now there's a small-but-tedious price to pay.

For the safe process, see [https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels](https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels)

You have one additional wrinkle - all your old kernels are missing a file, which will throw an error and stop dpkg/apt each time.
Solution: Use the 'touch' command to create a properly-named (but empty) dummy file for the package manager to remove.
Use the 'dpkg -l' step to tell you the names of the files you need to create.

---

### Post by howefield on 2017-02-04
Try the easy

```
sudo apt autoremove --purge
```

If yo uare lucky that will free the space to allow you to sort out the apt mess, if not you will need to use apt or dpkg to manually remove some kernel packages to free enough space in /boot.

What's the version of Ubuntu that you are using, 14.04 ?

---

### Post by howefield on 2017-02-04
Try the easy

```
sudo apt autoremove --purge
```

If yo uare lucky that will free the space to allow you to sort out the apt mess, if not you will need to use apt or dpkg to manually remove some kernel packages to free enough space in /boot.

What's the version of Ubuntu that you are using, 14.04 ?

---

### Post by gotaproblemwithmything on 2017-02-04
I can't do sudo apt autoremove --purge, I get the same error message, I think because my /boot/ is full. 

I'm trying to purge some old kernels with dpkg now, the ones I find with dpkg -l

Yeah I use 14.04 LTS

---

### Post by gotaproblemwithmything on 2017-02-04
> **ian-weisser said:**
> Yes very likely to be a full /boot partition.
Yes, using 'rm' on package-manager-installed files was unwise. and now there's a small-but-tedious price to pay.

For the safe process, see [https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels](https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels)

You have one additional wrinkle - all your old kernels are missing a file, which will throw an error and stop dpkg/apt each time.
Solution: Use the 'touch' command to create a properly-named (but empty) dummy file for the package manager to remove.
Use the 'dpkg -l' step to tell you the names of the files you need to create.


I can find a lot of old kernels with dpkg -l, but I am not sure which dummy files to recreate. I could guess the ones I previously removed from /boot/ with rm?


Edit. Just purging the old kernels might have solved it. I can install things now, will see if everything works on next boot.

---

