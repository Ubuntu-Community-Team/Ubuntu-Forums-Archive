---
title: "Dual boot ghost problems"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by timhump3s on 2010-07-21
Hello
I was wondering if you could help me
We have a machine which is set up for dual boot. Windows XP and Ubuntu and both OS' have been configured with the relevant software and updates (taken hours!)
We are trying to take an image of this desktop using Ghost 11 to then apply to other machines but are having issues
When running ghost we run ghost11 -ib from the ghost boot cd and create the image (doing this as previously when creating an image and restoring to another machine it just comes up with a blinking cursor (when taking an image of a desktop just running ubuntu also gives this error!) and when booting via ubuntu cd it only picks up 1 partition which appears to be corrupt)
When creating the image Ghost pops up with the following message
"Ghost has detected problems with a Linux volume. The volume was most probably not unmounted cleanly. We recommend that you quit ghost and correct the problem by running fsck on this volume. Alternatively, you many continue normally"
We continue as we don't know how to resolve this
When restoring the image on another desktop we run ghost11 -nolilo and then restore the image
When booting we get
"error: file not found
grub rescue>"
when booting from the ubuntu cd we can see and access the Windows XP partition but Ubuntu partition doesn't work
 
Basically is there other software which will let us create a working image on the desktop with 2 partitions which can be restored to other desktops or how do we unmount the ubuntu partition so that ghost can take the image without erroring and then when booting give us the option to choose which OS to load?
 
Many thanks
Tim

---

### Post by Gabby88 on 2010-07-23
Hi, I'm having the same issue and am also new to this, but this is what I've found so far:

[Howto: Backup and restore your system!         ]("http://ubuntuforums.org/showthread.php?t=35087")

 Also found this Live CD "[Parted Magic]("http://partedmagic.com/")" which contains tools that claim to be able to create images. However, I understand that the [PartitionImage]("http://www.partimage.org/Main_Page") tool doesn't work with ext4 filesystems.

I'm still evaluating options at the moment but hope this helps you somehow.

---

### Post by Gabby88 on 2010-07-23
also check out this thread:
[**best ghost image program**]("http://ubuntuforums.org/showthread.php?t=1504103")

---

