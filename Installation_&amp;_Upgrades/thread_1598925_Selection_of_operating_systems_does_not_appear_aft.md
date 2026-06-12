---
title: "Selection of operating systems does not appear after installing Ubuntu 10.10"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by Allyanora on 2010-10-17
I freshly installed windows 7, and after I installed maverick. I have another special partition for maverick, so all things good, until reboot.

After installation, it reboots and automatically boots windows. the list where I choose the operating systems, does not appear.

I tried to install Ubuntu several times, and i saw that the partition is installed correctly, because on the partition select, I saw its' name, and it was Ubuntu 10.10.

The check box on settings in my computer under startup and recovery is checked, and is put at 30 seconds to keep.

Any ideas how to make the list of operating systems appear after booting any of them?

thanks

---

### Post by sikander3786 on 2010-10-17
It boots directly into Windows? I doubt if GRUB is even installed. You can try reinstalling it.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Or post the output of bootinfoscript from a Live CD session so we can have a look at what is going on.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by presence1960 on 2010-10-17
If I read your post correctly you installed windows after Ubuntu. Then windows overwrote GRUB on the MBR with it's own boot loader. You need to reinstall GRUB. You will need an Ubuntu Live CD/USB.

Run the boot info script as suggested and post the contents of the Results.txt file back here. All you need to do after that is boot the Live CD/USB and run 2 commands in terminal which you will be given.

**_P.S. never mind I reread your post and it seems I misread it. Nevertheless run the boot info script and post the results so we can see what you have there._**

---

