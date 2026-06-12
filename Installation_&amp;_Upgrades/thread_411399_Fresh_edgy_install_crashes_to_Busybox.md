---
title: "Fresh edgy install crashes to Busybox"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by Shootfast on 2007-04-16
Hey guys, 

Just tried to install edgy on my Media PC, and after the reboot and grub load up, It crashes with the following error:

```

[17179579.536000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Done.
ALERT! does not exist. Dropping to a shell!

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

```

I've tried installing both feisty and dapper which get the same error, and I have looked at grubs UUID which are fine. I even added ramdisk=8190 to the kernel arguments and it still wont boot. Any ideas? This is the first step for my running Linux MCE.

---

### Post by mrquick on 2007-04-17
I also suffered this failure, will post more once I find a solution.

---

### Post by mrquick on 2007-04-17
Here's what I found.  Apparently the upgrade changes the uuid of the root volume.  The solution is to change the root=UUID portion of the /boot/grub/menu.lst file to either the new uuid of the volume (which can be found by issuing the command vol_id -u /dev/hda1 or whatever your root partition is) or simply by changing root=uuid=blahblabblah to root=/dev/hda1 or whatever your root partition is.

---

### Post by Shootfast on 2007-04-17
As I said, I've already looked at the UUID's and they are fine. I did find another thread with people having the same problem on the XPC media shuttle

[Here](http://ubuntuforums.org/showthread.php?t=374666)

And one guy said the problem was ubuntu not correctly making the initrd image.

His solution was to use yaird, but I have no idea where to start with that.

---

### Post by Shootfast on 2007-04-22
OK, in case anyone ever reads this thread, I have found the solution. You need to download the alternate cd and click Repair existing installation. After it has placed you at a command prompt, you have to 
```
sudo apt-get install yaird
``` Once that has downloaded, you type
```
sudo yaird -o /path/to/initrd
```

I just overwrote my current initrd with the yaird one (i named mine initrd.1 and typed sudo cp /boot/initrd.1 /boot/initrd-2.6.20-16 to replace the old one. After one boot it was fine! Hope this works for you!

---

