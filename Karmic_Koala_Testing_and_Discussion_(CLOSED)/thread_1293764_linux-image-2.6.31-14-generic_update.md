---
title: "linux-image-2.6.31-14-generic update"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ChrisGaeth on 2009-10-17
I have been keeping up with the updates (no partials) and things have been running fine till now.  On the linux-image-2.6.31-14-generic package I am getting the following error.

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Considering this is Grub2 and there is no menu.lst anymore I so "no" and the install fails.  Anyone else see this?

---

### Post by ajgreeny on 2009-10-17
Do you definitely have grub2?  I seem to remember reading that users who do an online version update will still be using legacy grub.  Anyone know if I'm correct?

---

### Post by eyelessfade on 2009-10-17
> **ajgreeny said:**
> Do you definitely have grub2?  I seem to remember reading that users who do an online version update will still be using legacy grub.  Anyone know if I'm correct?

That is correct

---

### Post by kansasnoob on 2009-10-17
Please post the output of:

```
grub-install -v
```

```
ls ~ /boot/grub
```

```
dpkg -s os-prober
```

---

### Post by pt123 on 2009-10-17
this update for me was a nightmare while it was installing the Linux headers it lost X,
then I couldn't boot into X. I did apt-get update then there a bunch of new linux-header 2.6.31.14 packages. Then had to uninstall nvidia packages using 
sudo apt-get remove nvidia*

then install back
sudo apt-get install nvidia-glx-185

---

### Post by ChrisGaeth on 2009-10-17
I installed from CD on a fresh machine.  This was not an upgrade.  I know I was running Grub 1.97.  Now it it says .97.

---

### Post by ChrisGaeth on 2009-10-17
I found it.  I installed Remastersys.  It put the old grub on.

---

### Post by kansasnoob on 2009-10-17
If you installed using a remastered CD grub may not be installed to the mbr, so you might not be able to boot.

And BTW whenever the kernel is updated several things are automatically run, like update-initramfs and update-grub, that's why it searches for needed grub files, etc.

---

### Post by VMC on 2009-10-17
> **ChrisGaeth said:**
> I installed from CD on a fresh machine.  This was not an upgrade.  I know I was running Grub 1.97.  Now it it says .97.
So is the below quote how you actually installed it?
> **ChrisGaeth said:**
> I found it.  I installed Remastersys.  It put the old grub on.

If so, then all you need to do is install grub2. Boot livecd, chroot, then [Recover Grub2]("https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD")

---

