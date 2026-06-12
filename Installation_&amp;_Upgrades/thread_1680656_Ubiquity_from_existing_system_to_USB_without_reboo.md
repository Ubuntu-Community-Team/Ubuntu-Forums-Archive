---
title: "Ubiquity from existing system to USB without reboot"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by dsjstc on 2011-02-02
Is it theoretically possible to install to a USB target from my working desktop?  I get crashes when I try, but before I try to figure it out, I'd like to know if anyone even thinks it ought to be possible.

Basically I'm looking for Wubi-like functionality... but from Maverick.

---

### Post by dsjstc on 2011-02-23
Thus far, it looks like unetbootin is the only solution.  It doesn't do an install though, just creates a bootable live CD image on your USB device.

Contradictions welcome.  ;-)

---

### Post by bcbc on 2011-02-23
> **dsjstc said:**
> Thus far, it looks like unetbootin is the only solution.  It doesn't do an install though, just creates a bootable live CD image on your USB device.

Contradictions welcome.  ;-)

You can migrate your working desktop to the usb and make it bootable. Like a clone, but it's bootable (from the USB). 

Of course, it's the same release and the USB has to be big enough to hold all your desktop's files. (Though if you customized the script you could skip some stuff)

If you are interested I'll point you in the direction of the bash script.

---

### Post by dsjstc on 2011-02-23
> **bcbc said:**
> If you are interested I'll point you in the direction of the bash script.

Yes please, and thanks very much!  Even if I don't end up using it, I'm sure others who stumble onto this thread will.

---

### Post by bcbc on 2011-02-23
This is the link to the [Howto: migrate Wubi install to partition]("http://ubuntuforums.org/showthread.php?t=1519354") thread. The latest script there (wubi-move-2.0.sh) also supports migrating a normal Ubuntu install (it detects whether the current install is Wubi or not). 

By default it will install the grub2 bootloader on the drive you migrate to, in your case the USB drive.

If you want to limit the data you copy, modify this line:
```
rsync -a --exclude="$root"host --exclude="$root"mnt/* --exclude="$root"home/*/.gvfs --exclude="$root"media/*/* --exclude="$root"tmp/* --exclude="$root"proc/* --exclude="$root"sys/* $root $target # let errors show

```

e.g. add --exclude="$root"home/Pictures/* to bypass the data in your Pictures folder

---

### Post by dsjstc on 2011-02-23
Cool, thanks for the link.  As soon as I recover that laptop from the dreaded Toshiba bios block 3 corruption, I'll give it a whirl.

---

### Post by mErchamion on 2011-07-10
Hey Guys I am trying to do the same! did this work for you?

---

