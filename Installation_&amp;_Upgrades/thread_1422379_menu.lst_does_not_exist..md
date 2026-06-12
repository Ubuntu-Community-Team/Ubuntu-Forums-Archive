---
title: "menu.lst does not exist."
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by mynameiszanders on 2010-03-05
Right, I would love to change the boot order on my laptop. Mainly because it is shared, and I am the only one who uses Ubuntu (version 9.10)... So everyone keeps moaning for me to change it!

Following all the sound advice from this forum it looks easy... Except /boot/grub/menu.lst does not exist! Huh?

If anyone can tell me why this is happening, that would be great! :D

---

### Post by bluelamp999 on 2010-03-05
Hi there,

Karmic uses a new GRUB called GRUB2 (though its' version is 1.97, go figure...)

Take a look here for a GUI to manage GRUB2 settings - [https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by Mark Phelps on 2010-03-05
Menu.lst is not used in GRUB2 -- the GRUB version installed by default in 9.10.

You can edit the /etc/default/grub file (must be root to do this), find a line that says "GRUB_DEFAULT=" and change the rest of the line to include the text string from the displayed boot menu for the default you want.

When done, save that file and run "sudo update-grub" to regenerate the actual grub file used.

Next time you boot, the new default GRUB line will be highlighted.

---

### Post by oldfred on 2010-03-05
Mark Phelps is exactly correct and the entry must be exact so I copy it this way:

Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by BbUiDgZ on 2010-03-10
can anyone tell me where i can add kernel boot options in grub2?
i'm attempting to add ```
i915.modeset=0
``` to the end of ```
/boot/vmlinuz-2.6.31-14-generic root=UUID=dc3cf399-6b13-4704-80c5-0e02fe6cd364 ro quiet splash
```
please see [here](http://www.insidesocal.com/click/2009/11/are-your-graphics-dead-in-ubun.html) for the blog post i'm following

---

### Post by Sub101 on 2010-03-10
Take a look here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

And normally you should create a new thread to ask a new question.

---

### Post by spiderbatdad on 2010-03-10
> **BbUiDgZ said:**
> can anyone tell me where i can add kernel boot options in grub2?
i'm attempting to add ```
i915.modeset=0
``` to the end of ```
/boot/vmlinuz-2.6.31-14-generic root=UUID=dc3cf399-6b13-4704-80c5-0e02fe6cd364 ro quiet splash
```
please see [here](http://www.insidesocal.com/click/2009/11/are-your-graphics-dead-in-ubun.html) for the blog post i'm following

In grub2 it would go in the file /etc/default/grub like so:
```

```GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="**i915.modeset=0**"
GRUB_CMDLINE_LINUX=""

---

### Post by BbUiDgZ on 2010-03-11
danke, both of you ;)

---

