---
title: "[SOLVED] upgrade USB startup disk"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by emwaiz on 2008-11-06
Hi! I just created a USB startup disk in Intrepid. A problem arose when I went to the updates. Everthing went well until the kernel part. I got this message from the system;

"E: linux-image-2.6.27-7-generic: subprocess post-installation script returned error exit status 17"

So, when I install/uninstall other applications in my USB startup disk, that same error message came up! So, if anyone with the same problem, please tell me how to overcome this, because the error message is very annoying. TQ!

:popcorn:

---

### Post by WishMaster on 2008-11-06
I guess everything is upgradable, exept the kernel...?
 
Shouldn't be a problem I think

---

### Post by emwaiz on 2008-11-06
> **WishMaster said:**
> I guess everything is upgradable, exept the kernel...?
 
Shouldn't be a problem I think
Yea ... I supposed too. But, how-to make the error message disappear?

---

### Post by timcredible on 2008-11-06
the usb startup disk is just a copy of the livecd, you can't upgrade it.

---

### Post by emwaiz on 2008-11-06
> **timcredible said:**
> the usb startup disk is just a copy of the livecd, you can't upgrade it.
Again, I need to know, how to fix that error message? TQ!

---

### Post by emwaiz on 2008-11-06
I manage to get this error message while Linux configuring my USB startup disk;

"Setting up linux-image-2.6.27-7-generic (2.6.27-7.16) ...
Running depmod.
update-initramfs is disabled since running on a live CD
Failed to symbolic-link /boot/initrd.img-2.6.27-7-generic to initrd.img.
dpkg: error processing linux-image-2.6.27-7-generic (--configure):
 subprocess post-installation script returned error exit status 17"

So, if anyone could figure out, how to fix the problem or at least, fix the error message. It keeps annoying me!

:popcorn:

---

### Post by pastalavista on 2008-11-06
The problem is you have made a "live CD" copy on a USB stick and live CD's are "read-only". What you need to do if you want to upgrade it in any way is to do an actual install to a USB drive. This tutorial might help:

[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

---

### Post by timcredible on 2008-11-06
> **emwaiz said:**
> Again, I need to know, how to fix that error message? TQ!

re-create the usb startup disk and don't try to upgrade it.

---

### Post by emwaiz on 2008-11-06
> **timcredible said:**
> re-create the usb startup disk and don't try to upgrade it.

Yeah, I think I'll do that again!

[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

### Post by emwaiz on 2008-11-06
> **pastalavista said:**
> The problem is you have made a "live CD" copy on a USB stick and live CD's are "read-only". What you need to do if you want to upgrade it in any way is to do an actual install to a USB drive. This tutorial might help:

[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

Yeah yeah, surely do! Thanks!

---

### Post by pastalavista on 2008-11-06
There shouldn't be any reason why you couldn't use your live-cd USB flash-drive to install to a different, larger one. You'd need a larger one, the larger the better, for a full installation with extra apps and data files and such. Good luck with that. Let us know how it goes.

---

