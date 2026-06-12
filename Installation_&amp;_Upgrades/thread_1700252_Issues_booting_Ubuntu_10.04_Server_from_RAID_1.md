---
title: "Issues booting Ubuntu 10.04 Server from RAID 1"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by thehouch on 2011-03-04
I am attempting to run Ubuntu 10.04 Server on RAID 1 and am consistently hitting the same issue when trying to boot the system for the first time (after what seems to be a successful install of the OS). I am creating the RAID 1 using the directions found in the Ubuntu Server Guide. The error I receive when trying to boot the system for the first time is...

```
mount: mounting /dev/disk/by-uuid/f35415ee-4c14-4eb1-995f-f19fbcd760c7 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

Any help in resolving this would be much appreciated. Also, any explanations as to why this happening and what I am doing wrong during the set up process would also be appreciated. Let me know if you need any additional information to help troubleshoot this issue.

---

### Post by YesWeCan on 2011-03-04
These symptoms resemble those when Ubuntu has not been given permission to boot a degraded array. In the server guide it gives instructions on how to add a directive to the grub commands to enable it.
You have to press either shift or esc during boot (I cannot recall which) to get to the grub menu, then press e to edit the boot commands and add bootdegraded to the kernel command line (check the exact wording in the server guide).

---

### Post by robsoles on 2011-03-04
Welcome to UF.

Another thing is to make sure you specify the array group rather than any specific member of it when you install.

I mean that if the installer offers /dev/sda, /dev/sdb and /dev/<insert-longish-id-string-here> for the installation target then you need to choose the one with the longish string name.

It's a while since I last did it, and I've only done it using Ubuntu twice now, so the details of what to choose in the installer a little fuzzy for me - if it's a later edition of the installer than the first release of 10.04 LTS then it may list the array with an obvious name (ie., 'array-1') but by memory the initial release of 10.04 LTS listed as I propose above.


If you install to a single member of the array then the members of the array are out of synch and it is possible that the raid array manager(s) will choose the 'un-initialised' member of the array as the 'prime' copy and start blanking/destroying your installation straight away.

Any good?

---

### Post by thehouch on 2011-03-05
Thanks for all the suggestions. It turns out I had been doing everything correctly but ultimately was provided with bad install media. I ended up downloading a copy directly from ubuntu.com and it was roughly 7MB larger in size than what I had in hand and installed and booted without issue.

---

