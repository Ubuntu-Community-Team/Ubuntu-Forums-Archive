---
title: "Boot repair doesn't work, and cannot work via grub rescue mode"
date: 2015-10-05
forum: Installation &amp; Upgrades
---

### Post by gongli49 on 2015-10-05
Hi everyone. These days my ubuntu is done again and this time i even cannot fix via external USB by boot repair tool. Even the first command:
> ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/mapper/isw_cdfdjdhbjc_TF0501WJGPL46R5" dpkg --configure -a   Setting up fontconfig (2.11.1-0ubuntu6) ...   Regenerating fonts cache... failed.   See /var/log/fontconfig.log for more information.   dpkg: error processing package fontconfig (--configure):    subprocess installed post-installation script returned error exit status 1   Errors were encountered while processing:    fontconfig

This is the summary via boot repair.  [http://paste.ubuntu.com/12689827/](http://paste.ubuntu.com/12689827/)
  Now the situation is that i will directly enter the grub command mode, i also try
```

set prefix=(hd0,gpt5)/boot/grub
set root=(hd0,gpt5)
insmod linux
linux (hd0,gpt5)/vmlinuz root=/dev/sdbx ro #i cannot find any related sub-dir in dev directory actually
```

I can still enter my win8.1 by typing exit to exit the grub but i cannot  enter my ubuntu. Do anyone have similar situation or any solution?  Thanks a lot!

---

### Post by oldfred on 2015-10-05
It looks like you have RAID (fakeRAID or BIOS RAID), UEFI and gpt partitioning.

Boot-Repair is having issues mounting anything. And gpt backup partition table is not at correct place at end of drive. Do not know with RAID if you can fix that or not without RAID issues.

It also looks like you left Windows hibernation on, which must be off if dual booting.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Your root is not root=/dev/sdbx but the /mapper.... or RAID partition that is / (root).

---

### Post by gongli49 on 2015-10-05
Yeah, i turn on the fast startup, but even when i turn it down. It does not help. And usually i also turn on the fast startup in Windows.
And may i ask what should i place my root directory if it is not /dev/sdxx?  



[TABLE="width: 660"]
[TR="class: comment"]
[TD="class: comment-text"]I also tried command like this: linux (hd0,gpt5)/boot/vmlinuz-2.6.xx-xx-generic. I think it is the kernels that i have, but i have several, and i tried two, they cannot work either. So i am not sure whether i have deleted the kernel
[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2015-10-05
Because it is RAID is is one of the mapper partitions.
But Boot-Repair could not open fstab or grub.cfg to see details.

Something like this?
/dev/mapper/isw_cdfdjdhbjc_TF0501WJGPL46R5

---

### Post by gongli49 on 2015-10-08
Err, i did not find those partitions either. After a few trials, i think the main reason for my case is that the kernel was broken. There are approaches to fix but they are not fit for me. Or i don't try in a correct way. Therefore in the end i re-install the while system. One thing i learn is that next time i better make a separated partition for home director so that i do not lost files while re-installing. Thank you. :)

---

