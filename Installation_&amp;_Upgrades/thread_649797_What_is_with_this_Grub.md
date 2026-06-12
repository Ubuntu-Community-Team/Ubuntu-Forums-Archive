---
title: "What is with this Grub"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by dmbware on 2007-12-25
I have loaded ubuntu on a seperate drive from xp, and I am having problems booting period. If I use the windows start disc to boot to my windows disc I get GRUB GRUB GRUB.. What is this, How do I fix my computer to have a dual boot with xp and ubuntu

---

### Post by LaRoza on 2007-12-25
Does Ubuntu boot? Post the results of:

```

less /etc/fstab

```

```

less /boot/grub/menu.lst

```

You installed Ubuntu to another disk, but you installed Grub to the hard disk with Windows on it. Grub, unless otherwise specified, is installed to the MBR of the first hard disk, even if you don't install Ubuntu there.

If the Ubuntu drive is external, you can restore the Windows MBR with the Super Grub Disk, but you will have to reinstall the Grub to the disk with Ubuntu on it.

---

### Post by dmbware on 2007-12-25
Ubuntu does not boot, How do I get the results I am confused on what you want? Please tell me so I can get you the info that you need?

---

### Post by LaRoza on 2007-12-25
> **dmbware said:**
> Ubuntu does not boot, How do I get the results I am confused on what you want? Please tell me so I can get you the info that you need?

Is the Ubuntu disk external? If it is, disconnect it. Then, boot from the Super Grub Disk and restore the Windows bootloader (don't worry about making a mistake in this, it won't affect the rest of the drive no matter what you do and you can always redo it)

The SGD is text based, but gives instructions as you go and explains everything. (You don't have to type, only select and move forward in the prompts)

Then reboot the computer, Windows will (should) boot. After this, we will address the Ubuntu drive.

---

### Post by dmbware on 2007-12-25
do you have any steps on how to do this in super grub, I cant find anything on the net, and I am not getting anywere with the options listed in super grub?

---

### Post by Partyboi2 on 2007-12-25
This might help:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by LaRoza on 2007-12-25
> **dmbware said:**
> do you have any steps on how to do this in super grub, I cant find anything on the net, and I am not getting anywere with the options listed in super grub?

From the SGD main menu:

Advanced->Windows (Advanced)->Fix boot of Windows

---

### Post by transporter_ii on 2007-12-25
You did kind of what I did. And insead of workig from a Windows hard drive,  what I ended up doing was going into my system BIOS and upgrading the Ubuntu hard drive to have first boot priority order (not the same as setting the first boot device, I might add). I then went into Grub and told it where the Windows hard drive was. I don't know that it makes a whole lot of difference, but I kind of had the feeling that it was best to leave the Windows hard drive MBR alone and have Linux and Grub on the same disk drive. It might be six of one and a half dozen of another, but I did get it working to the point I was happy!

I actually posted step by step details of how I did my install on here:

[http://ubuntuforums.org/showthread.php?t=649403](http://ubuntuforums.org/showthread.php?t=649403)

Transporter_ii

---

