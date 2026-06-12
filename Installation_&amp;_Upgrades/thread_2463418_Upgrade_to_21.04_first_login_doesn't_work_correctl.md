---
title: "Upgrade to 21.04 first login doesn't work correctly"
date: 2021-06-10
forum: Installation &amp; Upgrades
---

### Post by macca-i on 2021-06-10
Hi,

I have recently upgraded to Ubuntu 21.04 from 20.10 and I have a weird issue: when I first boot the PC and login, the desktop doesn't work as expected, most notably 1) the dock shows the system mounted drives and 2) usb flash disks doesn't mount automatically (syslog shows they are recognized correctly, just doesn't mount). However if I terminate the session and login again (without reboot) everything works correctly, the dock doesn't show the system drivers and usb flash drives mounts correctly and are shown on the dock.

This is a very weird and annoying issue because to have it fully operational I need to logout and login again after boot. Never happened before with 20.10 or previous versions, but I never upgraded from one release to the other, I always made a full install.
The only thing I have changed is disabled Wayland because doesn't works very well with the applications I'm using, and I believe it is much slower than X11, at least on my PC.

Is there someone with the same issue and a workround/fix ?

Thanks.

---

### Post by MAFoElffen on 2021-06-10
Just a question... In your fstab, is the Devices uisng names or UID's? It sounds like it might be using */dev/sdX* types of conventions which on boot, might be reassigned, but when remounted, recognized them. Just an initial guess. I always try to used UID's. Those don't change.

---

### Post by macca-i on 2021-06-11
> **MAFoElffen said:**
> Just a question... In your fstab, is the Devices uisng names or UID's? It sounds like it might be using */dev/sdX* types of conventions which on boot, might be reassigned, but when remounted, recognized them. Just an initial guess. I always try to used UID's. Those don't change.

The fstab uses UUID, never changed from the first installation, and anyway I just logout/login, no reboot, so whatever it was assigned it is still that after the second login.

```
# / was on /dev/sda3 during installation
UUID=f47b472a-b2eb-4ed2-94da-d2a9ac3279fc / ext4 errors=remount-ro 0 1
# /boot/efi was on /dev/sda2 during installation
UUID=AE31-49A6 /boot/efi vfat umask=0077 0 1
/swapfile none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
```

Maybe I should remove the floppy since I don't have floppy disks...

---

### Post by MAFoElffen on 2021-06-11
Yes, you should be able to comment out or remove your floppy line. I don't see anything at all wrong with that.

Yes. That is strange! I had thought your had rebooted. Just logging out and logging in would change nothing disk wise. That is all done in core on the init.

So explain again... What is going on?

---

### Post by macca-i on 2021-06-11
Well this is even more weird: I was going to make some screenshots to illustrate the issue and... it is gone, now all works well even at the first login!

I followed a simple tutorial on how to disable the floppy kernel module:

1. Unloaded the module
```
sudo rmmod floppy
```

2. Blacklisted:
```
echo "blacklist floppy" | sudo tee /etc/modprobe.d/blacklist-floppy.conf
```

3. Rebuilt initramfs:
```
sudo update-initramfs -u
```

Now all works well, no more system drives on the dock bar, usb flash drives mounts automatically, no need to logout and login.

I tried to revert the thing and load the floppy module at boot, like it was before, but the issue doesn't show anymore.
Looks like rebuilding initramfs has somehow fixed whatever was wrong.

I'll see if the next days or at the next kernel upgrade things will change again.

---

### Post by MAFoElffen on 2021-06-11
Yes. That was very strange and weird. None of my 6 builds here have that floppy drive line in the fstab. But then reuilding/compressing intramfs fixed it(???) almost like it had a problem when it upgraded... But if it had, you would think it would have thrown an error when it did the Release Upgrade. The code for that is usually pretty good about throwing errors and displaying them... But then again, sometimes the messages flash by so fast...

Glad that it is working now!

---

