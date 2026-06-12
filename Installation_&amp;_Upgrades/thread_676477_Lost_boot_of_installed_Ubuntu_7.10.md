---
title: "Lost boot of installed Ubuntu 7.10"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by swerdna on 2008-01-23
Hello. I am trying to install Ubuntu 710 which I just now downloaded. Install went fine. I have multiboot with Suse & Windows. I am using a [boot manager called XOSL]("http://www.ranish.com/part/xosl.htm"). I want to boot into the installed Ubuntu 7.10 and adjust it's bootmanager (grub) to lay code in sda9 (rather than in the MBR). How do I boot Ubuntu which is on sda9? Is there a way to use the install disk to get Ubuntu on sda9 to boot? And once I do that, is there a GUI for Grub in Ubuntu?

Thanks
Swerdna

---

### Post by chewearn on 2008-01-23
During ubuntu installation steps, you can specify the location of grub (there is the "Advanced" button somewhere in there, probably in step 6 or 7).

As to how you can boot to ubuntu (once grub is install in sda9), that will depends on your choice of boot manager XOSL, which I'm not familiar with.  But I'm sure its easy to set-up.

There was a GUI for grub (see here [link]("http://ubuntuforums.org/showthread.php?t=228104")) but it was broken in gutsy.

.

---

### Post by swerdna on 2008-01-23
> **AstalaVista said:**
> 
As to how you can boot to ubuntu (once grub is install in sda9), that will depends on your choice of boot manager XOSL, which I'm not familiar with.  But I'm sure its easy to set-up.

There was a GUI for grub (see here [link]("http://ubuntuforums.org/showthread.php?t=228104")) but it was broken in gutsy.

.
Thanks AstalaVista for the reply. I reinstalled the bootloader at location hda{0,8}, corresponding to partition 9 of drive 1, using GRUB commands because Gutsy GUI_GRUB is broken. Then my boot manager worked just fine. I used this tutorial: [How to restore Grub from a live Ubuntu cd]("http://ubuntuforums.org/showthread.php?t=224351")

> During ubuntu installation steps, you can specify the location of grub (there is the "Advanced" button somewhere in there, probably in step 6 or 7).

I remember that. Tried to use it. It was uninformative, to say the least,  and I didn't want to make a wild guess, preferring to get your help later, here.

Thanks again
Swerdna

---

