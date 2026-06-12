---
title: "How to add startup script to read-only /root system"
date: 2013-06-21
forum: Installation &amp; Upgrades
---

### Post by nammunayak on 2013-06-21
Hi Everyone,

I have created read-only /root system in my Xubuntu system. Now root is read-only. Now If I want to add startup script to this system how I can add. Now /root path is /mnt/root-ro, not the default "/" path.

Can some one please help me how to do this?

Thanks,
Namratha.

---

### Post by TheFu on 2013-06-21
Which area did you make read-only?
* /
* /root - home directory for the "root" account.

I've never tried to run Linux with a read-only / partition.  There are so many temporary files written to /var and /tmp and other places that I'd have to wonder how that would work on a normal HDD install?  If the file system is read-only and you need to make a change, then you need to make the file system NOT read-only, make the change, then make it read-only again.  The options to the **mount** command allow this.  **man mount** will explain everything.  Look for **-o remount,ro** and **-o remount,rw** as options.

I'm all for being secure and for having read-only file systems ... especially for web files.

To fix the path issue ... well, if the system is booting from the HDD and not a temporary drive, then it is in the correct place. Check the correct /etc/fstab to be certain.

---

### Post by nammunayak on 2013-06-24
[https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash)

Using the above link I created my read-only /root file system. I am installing the Ubuntu in 16GB USB drive. 

Hope this will help you to how to create a read-only /root file system and get an Idea

---

### Post by TheFu on 2013-06-24
Having a read-only /root isn't hard at all.  It is having a read-only / that is difficult (/ is the "root" directory, not the /root directory).  /root is the normal HOME directory for the root user; uid of 0 (zero). This is because /home might not be mounted when something goes wrong, so having a /root that is located in the same partition as /, so mounted by default, is why.

In other threads, the use of /root has confused people.

---

