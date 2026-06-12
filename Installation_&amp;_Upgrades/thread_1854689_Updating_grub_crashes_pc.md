---
title: "Updating grub crashes pc"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by mUNKYsTUFF on 2011-10-04
Hi guys.
It seems, (but I'm not sure about this), that whenever grub updates, or Ubuntu updates/upgrades, grub corrupts itself, and I get the message: 'grub_rescue: symbol not found' and I have to boot into a live cd and reinstall grub manually. I am not sure if I have something wrong here, but is a recurring problem, at 4 or 5 instances now. It is probably a simple problem, but I am a simple person, when it comes to the inner workings of linux.
Any help appreciated!

---

### Post by drs305 on 2011-10-04
There could be a corrupted Grub file (or two) that triggers the response. Using the "grub-install --reinstall" command will update files but won't repair bad files nor replace files the user may have deleted.

The solution may be to completely purge Grub 2 and then reinstall it. This should at least ensure all the Grub files are uncorrupted. If your Ubuntu system is running, you don't need to chroot to do this. Just make sure you have a working Internet connection before you purge Grub as you will have to download the Grub packages again.

[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")
Follow the section "Purge & Reinstall without Chroot"

---

### Post by mUNKYsTUFF on 2011-10-04
I really don't understand any of this...
I ran this command to reinstall grub from my 9.10 live CD:
```

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
and got these results:
```

Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.
```I'm not sure if it means it's fixed, because I rebooted and it had the same problem.
I have 11.04 installed, but it hasn't been working, something about timidity midi emulation stops boot-up, just doesn't load gui...

---

### Post by drs305 on 2011-10-04
As I tried to explain, the 'grub-install --reinstall' command won't fix files that currently exist but are corrupted. You have to purge Grub 2 completely to get rid of those bad files, and then reinstall Grub 2 so that *all* the files are replaced by new ones.

You cannot use the 9.10 version of Grub 2 to fix Ubuntu 10.04 or later. You must use either a running system or use the a CD with the same Ubuntu version. The 9.04 Grub version is way too old.

The purge/reinstall probably has a better chance of working. And to be clear, the purge/reinstall would be done from a running version, not the LiveCD. If you can't get your Ubuntu to run without the LiveCD, you would have to do the entire 'chroot' procedure I provided in the previous post.

---

### Post by mUNKYsTUFF on 2011-10-04
OK, that makes it clear. I'm trying the 'graphical' procedure, that you have a link to. Will that work from my live CD?

---

### Post by drs305 on 2011-10-04
You can use the LiveCD of the same version, but you will have to use the entire 'chroot' procedure. Otherwise you would be trying to make changes to the CD's files and not to your actual installation.

So the chroot procedure has you mount your real partition, copy certain system files over to the mounted Ubuntu partition, and then chroot into it. At that point you become root and any commands you execute will act on your real Ubuntu's system files. Again, *after* you chroot, make sure you have an Internet connection before purging Grub.

---

