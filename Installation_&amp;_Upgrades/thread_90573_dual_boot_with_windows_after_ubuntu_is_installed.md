---
title: "dual boot with windows *after* ubuntu is installed?"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by extarbags on 2005-11-15
Here's the sitch:

1. I currently have Ubuntu, and only Ubuntu, installed. My HD is 100% ReiserFS.
2. Because cursed Final Fantasy XI won't run under linux, apparently by any means, I need to install Windows.
3. So I thought I'd do this: make a 15GB or so FAT32 partition, and install Windows to it.
4. The only problem is that I'm pretty sure that will result in the NT boot loader taking over, and preventing me from booting into linux.

So how can I install Windows at this point and still have GRUB as the boot loader?

---

### Post by yesplease on 2005-11-15
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Sheco on 2005-11-15
I'd boot an Installation CD in rescue mode and...
```

# mkdir /ubuntu
# mount -t ext3 /dev/hda1 /ubuntu 
# chroot /ubuntu
# grub
> root (hd0,0)
> setup (hd0)

```

(i used hda1 which maps to hd0,0, you might have to change that)
maybe there's an easier way, I don't know :S

---

### Post by Wally68 on 2005-11-15
Yeah, the nt bootloader will overwrite the mbr. You'll have to reinstall grub after using a rescue or live cd, just like sheco said. Dam M$ anyhow.
Wally
> maybe there's an easier way, I don't know :S

Yeah there is an easier way to do it, but I don't remember off hand. The term 'grub-install' comes to mind

---

### Post by extarbags on 2005-11-15
So how should I go about making this partition? I don't have any way to unmount it while I'm booted up, obviously... what should I do?

---

