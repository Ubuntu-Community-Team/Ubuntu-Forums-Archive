---
title: "Install alternate from Linux"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by i71 on 2012-01-21
Is it possible to install **L**ubuntu alternate from Linux? There is a **U**buntu help page for **U**buntu [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/Installation/FromLinux"):

1. Copy your alternate ISO to the root of any partition that the installer can mount. You need to copy the ISO itself rather than the contents of the ISO.
2. Grab the initrd.gz and vmlinuz files
3. You will want to put these files in your normal /boot/ directory. It may be a good idea to create a subdirectory like newinstall.
4. Edit Grub
title installer
root (hd0,0)
kernel /boot/newinstall/vmlinuz
initrd /boot/newinstall/initrd.gz

Instead of vmlinu**z** I grabbed vmlinu**x** from **U**buntu 11.10 (I did not found **L**ubuntu) and changed Grub according to this:
kernel /boot/newinstall/vmlinu**x**

But the installation will not start. Will this work only for **U**buntu?

---

### Post by searchfgold6789 on 2012-01-21
Those instructions are old and probably won't work. Try these: [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by i71 on 2012-01-21
Well, this is exactly the URL from which I quoted.
First I tried the desktop installation, which failed after 5 min (only 256 RAM), then the alternate.
Did you mean the third method "Alternate CD Alternate Method"? Some steps I don't understand.
Earlier the installation from a CD failed obviously because of a cd drive failure (both desktop and alternate), therefor this attempt.

---

### Post by snowpine on 2012-01-21
What Linux are you already running, and does it offer LXDE in the repos?

---

### Post by i71 on 2012-01-21
Puppy linux.

---

### Post by snowpine on 2012-01-21
You install Puppy Linux but now you'd like to try Lubuntu instead, is that accurate?

Do you have another computer with a working CD drive (or the capability to boot from USB)? You can swap the hard drives, install Ubuntu, and swap the drives back (if you are comfortable opening up your computer).

---

### Post by i71 on 2012-01-21
I assume if all attempts fail, this will be the last choice.

---

