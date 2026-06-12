---
title: "Dual boot. Grub error: Out of disk"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by topviet on 2010-04-14
I installed 10.04 beta 2 into a new unallocated partition (about 80GB). The first partition (sda1) was Dell utility. The second partition (sda2) was Windows XP Media. It's also a boot partitiion. The third (sda3) was Window Recovery. Ubuntu on sda5. After installed succesful, it restarted and this error message appeared:
```
error: out of disk
grub rescue>

```Type command set, it showed:
(hd0) (hd0,5) (hd0,3) (hd0,2) (hd0,1)

I tried other grub rescue commands such as: help, exit, normal, linux, initrd, boot, ... and get this message "unknown command" or "command not found".

Re-install grub using Live-CD is not worked.

---

### Post by kansasnoob on 2010-04-14
Sounds to me like this error:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

If you need more detailed help please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by topviet on 2010-04-14
What information from RESULTS.txt should I post? For security reason, I'm prefer NOT to post complete results.

---

### Post by topviet on 2010-04-16
After I tried all three methods suggested at [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202), I decided to delete the partition for Ubuntu 10.04 and put Karmic Koala 9.10 on my hard drive. This time, a little bit better, I got a grub menu and booted in Windows XP. For Ubuntu 9.10, I got this error "No Such Device 1466abf9-419b-XXXX-XXXX-XXXX".

I clicked e to edit the command list. After several attempts to delete the command, I found delete command "search  --no-floppy --fs-uuid --set 1466abf9-419b-XXXX-XXXX-XXXX" fixed the problem.

After I got into Ubuntu 9.10, I modified grub.cfg to not run the grub search command and upgraded to Lucid Lynx. I guessed somehow grub and my hard drive did not get along. This work around fixed grub error out of disk and no such device.

---

