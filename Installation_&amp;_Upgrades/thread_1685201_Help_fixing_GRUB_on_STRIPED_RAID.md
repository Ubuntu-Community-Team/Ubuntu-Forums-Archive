---
title: "Help fixing GRUB on STRIPED RAID"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by whitehooder on 2011-02-10
Ok, the problem is that i have tried to install Ubuntu to a USB stick using the installation CD (32-bits).
But the GRUB has set itself in the USB so it needs the USB to start the GRUB.
If i start the PC without the usb connected i get an error message and a command line that looks like

GRUB RESCUE>

I want to have the GRUB back to the Striped (RAID) Ubuntu HDD so i can boot it without the USB.

Information that you could need is that i have three harddisks 1 for NTFS and the other two in a RAID format with Ubuntu installed. the two ubuntu hdds are /dev/sda and /dev/sdb. I think that /dev/dm-1 i the RAID together.

Hope you at the forum can help me. (sorry for bad english, im from Norway)

Thanks, Whitehooder

---

### Post by ronparent on 2011-02-10
What you need to do is reinstall grub 2 per this: [https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2](https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2)

Be mindful that since you are booting from a raid0 the grub boot loader has to be installed to the MBR of your raid array. That is probably either /dev/dm-0 or the first item listed in your /dev/mapper after control.

The two step procedure given in the reference I gave you will most likely do the job. To summarize, first you mount the partition you installed to and then reinstall grub 2.

```
sudo mount /dev/mapper/<theRAIDpartitionYouInstalledTo> /mnt
```

```
sudo --root-directory=/mnt/ /dev/mapper/<yourOverallRAIDarray>
``` 
And that is /mnt/ in the last command.

You will probably be able to use either the /dev/mapper or the corresponding dm-x links to reference the appropriate raid locations. Good luck. Post if you have any problems.

---

### Post by whitehooder on 2011-02-10
Thank you RonParent for the help.

The link you sendt me helped me a lot and i did realize that it is'nt that difficult to install the GRUB 2.

Many regards to you:KS

Whitehooder

---

