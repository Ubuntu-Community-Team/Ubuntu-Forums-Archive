---
title: "Ubiquity partitioner blank... can't install release candidate!"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Taoye on 2009-10-28
I just downloaded a fresh copy of the release candidate live CD to install onto my tower.

When I go into the "install" process, on the "prepare partitions" page it is simply blank... does not show any partitions or any options. I can't go forward, as I get the error "No root file system is defined. Please correct this from the partitioning menu." But, alas, the partitioning menu is empty.

 Everything shows up fine under Gparted. My hard disk has an NTFS partition for Windows 7, and some unallocated space after that that I was going to use for Ubuntu.

Anybody having a similar problem with ubiquity?

---

### Post by philinux on 2009-10-28
Reboot the livecd and choose check cd for errors.

---

### Post by themusicalduck on 2009-10-28
I'm having this exact problem. The installer can only see my one IDE drive, but none of my SATA drives.

Strangely up until about the release candidate it worked, but now it just doesn't.

I've tried it with two copies too, seems unlikely to be a problem with the CD, but is some bug that's been introduced.

Looks like I'm only gonna be able to use Karmic as an upgrade from Jaunty and not a fresh install after all :/

---

### Post by Taoye on 2009-10-28
No errors... I originally used Unetbootin to create a USB stick for my live CD iso. Now I've switched to the USB Startup Disk Creator from within Ubuntu and booted up my PC with it (disk checked out with no errors) and now Ubiquity won't even run.

I'm going to try it all over from scratch.

---

### Post by philinux on 2009-10-28
Try this.


Reboot the livecd and select "try ubuntu" Then when you get the desktop do the install.

---

### Post by Taoye on 2009-10-28
Okay I recreated the boot disk and it checks out with no errors.

When I did the "try Ubuntu" option, Ubiquity refused to run.

When I do the install option from the boot menu, Ubiquity runs but I get a blank partitioner page.

---

### Post by philinux on 2009-10-28
Is it this bug, also see last comment.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/444901](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/444901)

Or this one.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054)

---

### Post by Taoye on 2009-10-28
It's not the first bug-- I'm not seeing anything at all on the partitioning screen. The second bug sounds like it, but they are talking about options showing up whereas mine looks like the attached image...

---

### Post by philinux on 2009-10-28
Blimey thats a show stopper. I'd bug that one too then.

```
ubuntu-bug ubiquity
```

Maybe you can do that from the livecd.

---

### Post by themusicalduck on 2009-10-28
That is the screen I get if I disconnect my IDE drive, otherwise the IDE drive is the only option shown. It's possible the bug reporter had a combination of drives of which some worked and some didn't.

---

### Post by Taoye on 2009-10-28
The way you describe it, it sounds like it might be the second bug after all ([https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054))... looks like for me nothing is showing up because I don't have any IDE drives.

I added myself as affected by that bug.

---

### Post by Seventh Reign on 2009-10-28
add the line 'pci=nomsi' (without the 2 ' ) after quiet splash == in your boot options

---

### Post by themusicalduck on 2009-10-28
> **Seventh Reign said:**
> add the line 'pci=nomsi' (without the 2 ' ) after quiet splash == in your boot options

Didn't work for me :(

---

### Post by Rumo on 2009-10-28
Hi, I have a slightly different problem.

Ubiquity shows my hard drive - but no partitions (they do show up with fdisk /dev/sda, though). Since I would like to keep my data, this makes it impossible for me to install ubuntu 9.10.

edit: My bad, it seems that I had overlapping partitions. Grub and fdisk didn't seem to bother (my system booted normally) but gparted didn't like it.

---

