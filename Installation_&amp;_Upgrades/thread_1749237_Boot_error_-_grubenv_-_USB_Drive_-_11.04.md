---
title: "Boot error - grubenv - USB Drive - 11.04"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by mrstoney on 2011-05-04
I'm running 11.04 off of a 32gb flash drive.  Something about grub on my install is messed up.  When trying to boot after a normal shutdown, I get the following errors.

  error: invalid environment block
  error: invalid arch independent ELF magic

I think something about grubenv under /boot/grub is being corrupted. Loggin in under Ubuntu 10, I can make my way to the files on the 11.04 flash drive and issue the following commands to make it boot normally (from [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784) )

  # grub-editenv grubenv create
  # grub-editenv grubenv set default=0

Why is this file corruption happening?  How can I fix it?

---

### Post by peejavery on 2011-05-21
I have the same problem. Can't solve it either. But I did find a pattern. Is this the same for you?

[http://ubuntuforums.org/showthread.php?t=1764234](http://ubuntuforums.org/showthread.php?t=1764234)

---

### Post by mrstoney on 2011-05-23
Yes, it does it every time.  I have to boot from another drive and re-create the grubenv file.  

Oddly, I think it will reboot just fine.  It's only when I do a full shutdown that something goes wrong.

I'm going to install on another drive to see what happens.

---

