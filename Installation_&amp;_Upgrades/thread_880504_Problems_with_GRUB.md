---
title: "Problems with GRUB"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by bb6642 on 2008-08-05
Hi.  I am relatively new to Linux/Ubuntu.  Here is my problem:  I recently installed Ubuntu Hardy to a second 80 GIG hard drive on my computer.  The main 250 GIG hard drive had Vista.  The installation went fine until it rebooted upon completion.  The GRUB menu appeared but there was no option to boot to Vista, just Ubuntu.   I checked in Ubuntu and the Vista hdd was still there, all the folders and files.  I just could no longer boot to them.  I tried reconfiguring the GRUB config file without any luck. Frustrated I eventually got rid of Ubuntu and re-installed Vista. I would like to try again but am nervous about loosing access to Vista.  Any idea what may have gone wrong the first time?  and how I can possibly prevent the same problem from happening again?

---

### Post by cdtech on 2008-08-05
You just needed to update your /boot/grub/menu.lst to include windows, no big deal. Try again.....

---

### Post by estyles on 2008-08-05
It shouldn't be too difficult.  You'll have to edit your /boot/grub/menu.lst file if grub doesn't detect Vista automatically.

Let's say that Grub puts a line like the following in your menu.lst:
```
title		Linux Mint, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda5 ro
initrd		/boot/initrd.img-2.6.24-19-generic

```

In my case, I am running Linux Mint (yours would say Ubuntu), and it's located on (hd0,2), which translates to first hard drive, third partition (actually, in my case, only the /boot folder is on that partition, but that's not important).  What's important is seeing that grub is booting Linux from hd0.  That would mean that if you only have two HD's, Vista would boot from hd1.  If Linux is being booted from hd1, then Vista is on hd0.  It's hard to tell for sure which one will be detected as which without checking in linux, and checking your menu.lst is one easy way to find out.

So, let's say that your Linux partition is on hd0.  Then, in your menu.lst file, find the line that says "### END AUTOMAGIC KERNELS LIST" (I think that's right, I've edited my menu.lst so many times, and it appears that I accidentally deleted that line - don't do that.)  After that line, you'll want to add in the following:
```
title		Microsoft Windows Vista
root		(hd1,0)
makeactive
chainloader	+1
```

...unless you have reason to believe that Vista might not be installed on the 1st partition of the drive, in which case, you might have to figure out which partition it is on and change (hd1,0) to (hd1,1) or (hd1,2), etc...

---

### Post by miguelbuenca on 2008-08-05
In uninstalling ubuntu, is it possible to do it by running the live cd and go to partition editor then delete the partition containg ubuntu? Thanks

---

### Post by Pumalite on 2008-08-05
> **miguelbuenca said:**
> In uninstalling ubuntu, is it possible to do it by running the live cd and go to partition editor then delete the partition containg ubuntu? Thanks
Gparted Live CD is safer because it works with unmounted drives/partitions:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by miguelbuenca on 2008-08-06
> **Pumalite said:**
> Gparted Live CD is safer because it works with unmounted drives/partitions:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

I downloaded and burn to cd the file on this link. I tried booting from the cd several times but it did not work. Don't know why. Is there other simple ways to uninstall Ubuntu and claimed back the disk space? Thanks

---

