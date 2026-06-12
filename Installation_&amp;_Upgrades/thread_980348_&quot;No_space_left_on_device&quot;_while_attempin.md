---
title: "&quot;No space left on device&quot; while attemping to install compiled linux image"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by nashibuntu on 2008-11-12
Hi there.

I am trying to compile and install a "mainline" or "upstream" linux kernel to help me test whether this resolves a bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292619]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292619")). I am following these instructions: [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild").

However, at the stage of installing the linux-image I get the following error message:
```
Done.
dpkg: error processing linux-image-2.6.28-rc4-custom_2.6.28-rc4-custom-10.00.Custom_amd64.deb (--install):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./lib/modules/2.6.28-rc4-custom/kernel/drivers/video/hgafb.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.27-7-server
Found kernel: /vmlinuz-2.6.27-7-generic
Found kernel: /vmlinuz-2.6.24-21-server
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 linux-image-2.6.28-rc4-custom_2.6.28-rc4-custom-10.00.Custom_amd64.deb

```

Does anyone here know what device it is talking about when it says that there is no space and how I can fix the problem?

The linux-image...deb file is about 258M in size. The output of df -h is: ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              950M  261M  642M  29% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G   72K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  2.7M  1.9G   1% /dev
tmpfs                 1.9G     0  1.9G   0% /dev/shm
/dev/md0              950M   43M  860M   5% /boot
/dev/md5               90G  5.5G   80G   7% /home
/dev/md4              950M   18M  885M   2% /tmp
/dev/md2               19G  747M   17G   5% /usr
/dev/md6               28G  905M   26G   4% /var
/dev/md7               75G  215M   71G   1% /var/lib/mysql

```

Thanks. Paul

---

### Post by nashibuntu on 2008-11-13
Sorry for a random post, but this thread got so far from the front of the queue so quickly that no one is looking at it any more. I'd be grateful for any help. Thanks.

---

### Post by nashibuntu on 2008-11-13
I think that my question is more suited to the following forum: [Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions  > Development & Programming > Packaging and Compiling Programs]("http://ubuntuforums.org/forumdisplay.php?f=44"). Please could a forum administrator or someone with the appropriate privileges move it there? (I don't want to double post.)

Thank you.

---

