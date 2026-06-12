---
title: "Hangs on: update-initramfs: Generating /boot/initrd.img-2.6.32-38-generic"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by azzid on 2012-01-31
I tried upgrading the other day, but apt-get never finished.

I killed of all hung dpkg instances an ran apt-get update again.

It instructed me to:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

But when I run that command it hangs again:
```
$ sudo dpkg --configure -a
Setting up linux-image-2.6.32-38-generic (2.6.32-38.83) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-38-generic

```

It never gets past the update-initramfs. I've tried killing of dpkg a couple of times and redoing the process.
I've left the command running for ~24 hours, but it wont finish.

Since it is the boot image we're dealing with here I guess the machine won't be able to boot until I get this working?

Anyone know what might be wrong?

Any way I can troubleshoot this? Some verbose mode, or some log?

---

### Post by balduin on 2012-04-07
Same problem for me. I have no idea what to do.

---

### Post by skabople on 2012-04-07
> **azzid said:**
> I tried upgrading the other day, but apt-get never finished.

What did you type and run exactly?? 

apt-get upgrade? apt-get -y upgrade? apt-get -fy upgrade?

---

### Post by azzid on 2012-04-07
I probably ran ```
apt-get upgrade
``` possibly ```
apt-get dist-upgrade
``` since it was a kernel upgrade. But honestly I can no longer recall. =/

I've since tried copying the filesystem that I tried updating ubuntu on and that fails (ending in kernel panic) aswell, so my guess is that the sdcard has gone bork and that that is the source of my original issue.

Sorry for not getting back and ending the thread.

---

### Post by skabople on 2012-04-07
What was the kernel panic?

---

### Post by azzid on 2012-04-07
> **skabople said:**
> What was the kernel panic?

```
Kernel panic - not syncing: Attempt to kill init!
```

After that nothing more happens.

Before that error I got alot of errors like:
```
Buffer I/O error on device sda, logical block 16131
```

And this is running the machine of a live cd trying to do:
```
dd if=/dev/sda of=/mnt/usbdrive/disk.img
```

So I'm fairly confident it's hardware related. Do you agree?

---

### Post by skabople on 2012-04-07
Attempting to kill init doesn't always mean hardware. This isn't hardware. You're in a live cd? Correct?

---

### Post by skabople on 2012-04-07
That isn't how you use the dd command to copy a hard drive into a image. Plus if you're in a live cd then you can't update initramfs because initramfs is a file system itself which is running as a virtual filesystem much like a chroot....

---

### Post by skabople on 2012-04-07
Attempting to kill init is normally because grub is trying to boot the wrong device that isn't there in a way. /etc/fstab could be wrong or the hard drive could be labeled differently.

---

### Post by skabople on 2012-04-07
The command your an was apt-get dist-upgrade because that updates the initramfs and the kernel

---

### Post by azzid on 2012-04-07
> **skabople said:**
> Attempting to kill init doesn't always mean hardware. This isn't hardware. You're in a live cd? Correct?

Yes. I'm on a live cd now, to be able to copy the disk, it is easier to copy it when I am not running on it. ;) I was not running of a live cd when I tried the apt-get though.

> **skabople said:**
> That isn't how you use the dd command to copy a hard drive into a image. Plus if you're in a live cd then you can't update initramfs because initramfs is a file system itself which is running as a virtual filesystem much like a chroot....

What is wrong with how I use dd? I've used it like that successfully before.

No, the update-initramfs won't work of the live cd, but thats not where I've tried to run it either.

> **skabople said:**
> Attempting to kill init is normally because grub is trying to boot the wrong device that isn't there in a way. /etc/fstab could be wrong or the hard drive could be labeled differently.

This is waaaay past the booting process, I could agree with you if the error had occurred during boot, this however happen during the copy.

> **skabople said:**
> The command your an was apt-get dist-upgrade because that updates the initramfs and the kernel

Sounds correct to me.

---

### Post by skabople on 2012-04-07
Lol then definitely a failed hard drive. 

As for the dd command. It's not wrong but there is a better way to do this with a failed/failing drive.

```
dd if=/dev/sda bs=4k | gzip > /mnt/usbdrive/disk.img.gz
```

Or use something like dd_rescue.

---

