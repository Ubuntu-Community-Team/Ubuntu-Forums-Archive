---
title: "How to use older kernel after bad upgrade"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by geovino on 2015-05-05
I just installed 14.04.2 and after the updates and reboot I got a black screen. I was able to hit esc on the Lenovo Carbon X1 and under advanced options was able to go back to 3.16.0.30 instead of 3.16.0.37 which does not work at all. How do I fix this problem?

---

### Post by geovino on 2015-05-05
correction, the 3.16.0.37 kernel works it you click on recovery option and then select normal boot. But this shouldn't be happening at all if the upgrade was successful.

---

### Post by tgalati4 on 2015-05-05
Open a terminal and post the output of:

```
uname -a
ls -la /boot
```

You might want to read the release notes for *.37 and see what changed.  If it was related to graphics then you may want to file a bug report against that version of the kernel.

Check for updates again and apply any and then reboot.

---

### Post by geovino on 2015-05-05
rogerb@X1-Carbon:~$ ls -la /boot
total 60488
drwxr-xr-x  3 root root     4096 May  5 17:17 .
drwxr-xr-x 23 root root     4096 May  5 17:17 ..
-rw-r--r--  1 root root  1207386 Jan 15 10:22 abi-3.16.0-30-generic
-rw-r--r--  1 root root  1206938 Apr 30 04:31 abi-3.16.0-37-generic
-rw-r--r--  1 root root   171768 Jan 15 10:22 config-3.16.0-30-generic
-rw-r--r--  1 root root   171816 Apr 30 04:31 config-3.16.0-37-generic
drwxr-xr-x  5 root root     4096 May  5 17:17 grub
-rw-r--r--  1 root root 19441158 May  5 11:19 initrd.img-3.16.0-30-generic
-rw-r--r--  1 root root 19448093 May  5 17:17 initrd.img-3.16.0-37-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3511040 Jan 15 10:22 System.map-3.16.0-30-generic
-rw-------  1 root root  3512899 Apr 30 04:31 System.map-3.16.0-37-generic
-rw-r--r--  1 root root  6345120 May  5 11:13 vmlinuz-3.16.0-30-generic
-rw-------  1 root root  6352304 Apr 30 04:31 vmlinuz-3.16.0-37-generic
rogerb@X1-Carbon:~$

I could reinstall Ubuntu but then after the upgrade it would be the same. I guess I have to wait until there's another upgrade to fix this problem.

---

### Post by grahammechanical on 2015-05-05
When we use Recovery Mode>Resume we load Ubuntu using an open source video driver called llvmpipe. 

There could be a conflict between the new kernel and the proprietary video driver. So, I suggest reverting to the open source video driver. Use Additional Drivers to do that. Test restarting a few times with that driver then attempt to install a proprietary driver using Additional drivers and see what happens.

Regards.

---

### Post by geovino on 2015-05-06
I don't install proprietary drivers. I let Ubuntu pick the generic video driver. It works fine. 

I reinstalled Ubuntu 14.04.2 and didn't do any updates until I hear that the kernel problem is fixed. Once they release the 3.16.0.38 I'll do the updates.

---

