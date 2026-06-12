---
title: "Can't boot after using dd"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by stamatiou on 2013-03-31
I was trying to write an iso in my usb flash drive by using dd but instead of writing it on the flash drive I did it on my hard drive. Now when I try to boot, I get stuck on the Compaq Logo before and I am unable to boot from other sources because it is frozen. What can I do now?

---

### Post by darkod on 2013-03-31
Get your latest backup. Reinstall ubuntu and restore your personal data from the backup.

And try to avoid copying ISOs with dd, it's really not a good practice. You have to be very, very careful with dd.

Right now I would guess your partition table is gone, together with the data that was at the start of the disk, the part the ISO overwrote.

If you want to, you can try recovering the partitions with testdisk but the data that was overwritten can't be restored.

---

### Post by stamatiou on 2013-03-31
I tried to boot the ubuntu live cd but as soon as I try to enter in the boot options menu, the computer freezes completely. I also tried to boot in the default source by not pressing anything but it freezes too.

---

### Post by darkod on 2013-03-31
The cd should boot into live mode regardless of the hdd. Even when there is no hdd you should be able to boot into live mode, it's working from the cd. If you can't boot into live mode then you have another problem. Maybe video driver issue, or similar.

What boot options are you talking about, the bios boot options? Is your bios freezing?

---

### Post by stamatiou on 2013-03-31
Yes. it is stuck in the bios before anything starts up and it seems like I can't boot from any source...

---

### Post by oldfred on 2013-03-31
A few systems that have multiple boot issues seem to lock up. A full power shutdown often fixes that. with laptops you have to remove battery, wait and usually holding boot key without battery may help to get capacitors to discharge.

       Laptop full power reset. post #4
[http://ubuntuforums.org/showthread.php?p=12401315](http://ubuntuforums.org/showthread.php?p=12401315)

---

### Post by stamatiou on 2013-04-01
I tried the cold finger reset without disconnecting the keyboard and it didn't work. Also I tried this and it didn't work either: [http://youtu.be/D72M6wpEhZE](http://youtu.be/D72M6wpEhZE)
EDIT: Here says that the problem was a damaged drive: [HP Logo boot screen(Stuck!) - HP Support Forum - 157688]("http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g-Windows-8-and-Software/HP-Logo-boot-screen-Stuck/td-p/157688")

---

### Post by darkod on 2013-04-01
Can you take out the hdd and connect it to another desktop so you can try restoring the partitions, or write a new empty partition table, which ever you decided to do?

---

### Post by stamatiou on 2013-04-01
I got the hdd out and it didn't freeze... Is there a way I can create an empty partition table using a live cd without putting the hdd into another pc?

---

### Post by oldfred on 2013-04-01
Does your system boot the flash drive or DVD? And if you have hard drive in a caddy you should be able to see it.

But then the issue just may  have been that BIOS/UEFI was always set to boot hard drive first and the corruption on the hard drive was the issue. Changing boot order in BIOS so hard drive was last then should have worked??

---

### Post by stamatiou on 2013-04-01
It could only detect the DVD. Also, I have no spare hard drive, except of an external one.
EDIT: I tried changing the boot order and moving the hdd last but it is stuck again...

---

### Post by darkod on 2013-04-01
So, just boot with the ubuntu cd in the dvd drive. Is that not working?

---

### Post by stamatiou on 2013-04-01
Yes it does, but how do I install it? I tried to boot the live cd and then connect the hard drive, but it did not detect it...

---

### Post by oldfred on 2013-04-01
Does BIOS see drive at all, if shown in BIOS you should be able to see it in Ubuntu.

Post this from liveCD:

sudo fdisk -lu

---

### Post by darkod on 2013-04-01
> **stamatiou said:**
> Yes it does, but how do I install it? I tried to boot the live cd and then connect the hard drive, but it did not detect it...

I hope you didn't connect the disk with the machine powered on. This is not a server with hot-plug disks, on standard desktop machines you can't connect disks while it's powered on. It should be powered off.

Connect the disk and then boot with the ubuntu cd. Open terminal and post the output of the command oldfred posted. You can also post the output of this command:
```
sudo parted -l (small L)
```

---

### Post by stamatiou on 2013-04-01
the bios does not detect the hard drive and the command gives no output

---

### Post by stamatiou on 2013-04-01
When the disk is connected, the bios gets stuck and does not boot from any source

---

### Post by oldfred on 2013-04-01
If BIOS cannot see drive, no system will be able to see drive as BIOS lets systems know what hardware is available.
You then might try another system, but it sounds like drive died in the middle of all of this. May just be coincidence.

---

### Post by darkod on 2013-04-01
> **stamatiou said:**
> When the disk is connected, the bios gets stuck and does not boot from any source

But that doesn't mean you can connect sata disks online. That is one of the ways to kill a disk.

If the bios doesn't see it, it's either dead or there is another huge problem with it. One thing is for sure, if bios can't recognize it, you can't use it ain the machine, it's like it's not there.

Try connecting it to another machine to see if it wil detect it.

---

### Post by stamatiou on 2013-04-03
Ok, I found an old laptop and took the hard drive out of it and plugged it in mine. Now the system can boot but when I plug the bootable usb in, it freezes... :/

---

