---
title: "trying to install ubuntu 11.10"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by GigaRoc on 2011-10-28
I'm trying to install ubuntu 11.10 on my main PC at home, i had 11.04 installed, but i screwed up the library links and thought it was a good time to clean install.

I'm using live_cd x86_64 on a pen drive with unetbootin.
However, when i boot it says /dev/sda1 mounted to /cdrom which means i can't format my main drive.

I looked around and saw i people had success with sudo umount -l -r -f /dev/sda1 before starting the install.  This does not work for me.  If i ask the installer to format the first partition, it says i can't update the kernel about the partition, and hangs. if i tell it to just delete the /bin /var /etc ... folders, it hand on "Saving installed packages" 

I could really use some help getting this running.

Thanks
Kevin

---

### Post by critin on 2011-10-28
If you're booting from the live pen drive there shouldn't be **any** hard drives mounted.  sda/1 is mounted to the cd drive?  I'm going to watch this thread and hopefully learn how that can happen (for my own benefit).    :confused:

*<<<it says i can't update the kernel about the partition, and hangs. if i  tell it to just delete the /bin /var /etc ... folders, it hand on  "Saving installed packages" >>>*

This doesn't sound like an install to me.  Curious.

---

