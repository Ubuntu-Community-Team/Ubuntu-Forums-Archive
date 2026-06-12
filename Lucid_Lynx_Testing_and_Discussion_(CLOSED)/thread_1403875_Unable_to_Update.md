---
title: "Unable to Update"
date: 2010-02-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Sef on 2010-02-10
After the latest round of updates, I cannot update any more.  The update manager tell me to run 'sudo apt-get install -f > that tells me to run 'sudo -dpkg --configure -a'.  However that gives me a message of  'subprocess installed post-installation script returned error exit status 1'.

What can I do to fix this problem?


> sudo apt-get install -f
[sudo] password for sef: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
sef@sefmeg:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-12-generic
cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-12-generic
dpkg: subprocess installed post-installation script returned error exit status 1Dell Inspiron 1545, AMD64-bit, 4 gb ram, onboard graphics,

---

### Post by paul_in_london on 2010-02-10
See this thread:

[http://ohioloco.ubuntuforums.org/showthread.php?t=1403446](http://ohioloco.ubuntuforums.org/showthread.php?t=1403446)

(although when I updated from my usual UK mirror a few hours ago it already seemed to have been fixed).

---

### Post by Sef on 2010-02-10
Thank you very much.   That has solved my problems.

---

