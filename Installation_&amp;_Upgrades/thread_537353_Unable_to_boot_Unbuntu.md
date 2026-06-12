---
title: "Unable to boot Unbuntu"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by GokuSSL5 on 2007-08-28
I just installed Ubuntu on my Vista computer. My computer has several H.D.s with a few on SATA and others on EIDE. After several attempts in installing Ubuntu (Errored out at end of installation), I was finally able to get Ubuntu installed without any errors, but then after rebooting the computer, I was not prompted to select which OS to choose from  or anything. My computer just boots directly into Vista as if Ubuntu wasn't even there. I went into my BIOS and switched the boot order of my drives so the drive Ubuntu was installed on would get looked at first. That still didn't resolve the issue. 
Any ideas?

---

### Post by merlinus on 2007-08-28
You will have to boot from the live cd and manually mount your ubuntu partition.

```

sudo fdisk -l

```

will show which partition this is.

Then

```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu

```

(substitute the ubuntu partition from fdisk -l for sda2)

Then post results of:

```

cat /media/ubuntu/boot/grub/menu.lst

```

Also post output of sudo fdisk -l

-merlin

---

### Post by Pumalite on 2007-08-28
deleted

---

### Post by GokuSSL5 on 2007-08-28
Thanks, I'll that out when I get home later.

---

### Post by GokuSSL5 on 2007-08-28
I tried what was suggested above and I received an error, it is as follows:
"GRUB Loading Stage 1.5

GRUB loading, please wait...
Error 17"

This occurs on the black DOS looking screen when GRUB begins to load.
Any ideas?

thx

---

### Post by Bart_D on 2007-08-29
GRUB Error 17:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by GokuSSL5 on 2007-08-29
I followed the link suggested in the last post, and added "noverify" to the "root" command under the windows section.
Now when GRUB attempts to boot, it doesn't say anything on the screen and just hangs with a flashing underscore character.
Any other ideas? I'm sure we're getting close!

---

### Post by GokuSSL5 on 2007-08-29
Ok my bad, i figured this one out. I re-ordered the boot sequence of my hard drives back to their original order from when GRUB was installed.
Now it boots up just fine.
It looks like it was my fault - sorry for the time waster and thx for everyone's help!

---

