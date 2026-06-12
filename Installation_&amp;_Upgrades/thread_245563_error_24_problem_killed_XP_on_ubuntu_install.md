---
title: "error 24 problem killed XP on ubuntu install"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by crashtestyyz on 2006-08-28
```

Booting 'Microsoft Windows...'
root (hd0,0)
Error 24: Attempt to access block outside partition
Press any key to continue...

```

This is the result of a successful Ubuntu install with a functioning GRUB boot manager - my windows install appears to have been terminated.

windows lived on the first partition (/dev/sda1), and there were 100G for the ubuntu install on /dev/sda2.  

Am I stuck wasting another several hours on this or have I tripped a bug?

---

### Post by crashtestyyz on 2006-08-28
well, I went so far as to reinstall windows (it was a fresh install), at which point yes, it booted windows okay.

then, followed the instructions found in this thread:

[http://www.ubuntuforums.org/showthread.php?t=245526](http://www.ubuntuforums.org/showthread.php?t=245526)

So, here's what's reported:

```

find /boot/grub/stage1
 (hd0,1)

root (hd0,1)
 Filesystem type is ext2fs, partition type is 0x83

setup (hd0)
...

```
And everything exits cleanly with setup.  "suceeded" all around.

Reboot, choose windows...
error 24.

Just wasted another 2 hours on this... anybody have any ideas here?

This is a 160G SATA drive, first 50G for windows, remaining for ubuntu.  Nothing fancy.
--C

---

### Post by confused57 on 2006-08-28
Here's someone with a similar setup, different error messages, but thought you might want to check out the thread:
[http://www.ubuntuforums.org/showthread.php?t=244874](http://www.ubuntuforums.org/showthread.php?t=244874)

Probably totally unrelated, but could be a bug with grub.

---

### Post by caiman64 on 2006-08-28
Hi,

I had a similar problem... only Grub 1.5 reported error 25 instead...

I tried to start all over again by re-installing WinXP... only that in my case after installing WinXP it wont boot!!

If I install UBUNTU only it boots ok!

How do I make WinXP boot again,?... lokks like ubuntu did something to my disk so that it will only work on Ubuntu!!

Help will be appreicated
Regards, 
Carlos

---

### Post by crashtestyyz on 2006-08-28
whee!

Made this change:

[http://www.ubuntuforums.org/showpost.php?p=1427854&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1427854&postcount=2)

Works fine!   =D>

---

