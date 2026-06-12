---
title: "How to install with no cd drive?"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by arry487 on 2008-12-02
Hi,

I would like to install Xubuntu on a laptop with no cd drive.  The laptop is currently running windows xp and I would like wipe the drive, create a new partition and install Xubuntu.

Would it be possible to unpack the .iso to a usb storage device and run a setup program from dos?     

Thanks

---

### Post by snowpine on 2008-12-02
Is the laptop capable of booting from USB? If so, you can create a live USB that functions just like a live CD. Intrepid 8.10 includes a new live USB creator (under the System->Admin menu of the live CD). Or, if you are using an older version, Unetbootin works very well.

---

### Post by thomas228 on 2008-12-02
> **arry487 said:**
> Hi,

I would like to install Xubuntu on a laptop with no cd drive.  The laptop is currently running windows xp and I would like wipe the drive, create a new partition and install Xubuntu.

Would it be possible to unpack the .iso to a usb storage device and run a setup program from dos?     

Thanks

Use windows to download iso and unebootin for windows and install onto a fat32 formated thumb
See [http://ubuntuforums.org/showthread.php?t=995489]("http://ubuntuforums.org/showthread.php?t=995489") post #8
and follow the referenced link 
[http://ubuntuforums.org/showthread.php?t=811397]("http://ubuntuforums.org/showthread.php?t=811397")
Worked for me(was better with LTS ver 8.04)
Edit: You will create the liveusb in windows but you'll boot into kubuntu and will be able to try the system before installing, partition your drive if you want, and/or install the kubuntu on a partition (dual boot) or use the entire disk. The liveusb allows many choices.

Good luck 
Tom

---

### Post by Bablefish on 2008-12-02
You could try this [http://wubi-installer.org/](http://wubi-installer.org/)

---

