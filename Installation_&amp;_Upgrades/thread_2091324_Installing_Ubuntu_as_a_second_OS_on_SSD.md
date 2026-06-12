---
title: "Installing Ubuntu as a second OS on SSD"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by Joe92w on 2012-12-04
Hi,

I am an Ubuntu rookie and who has started using the environment for a university work.

I love the OS but am not ready to make a permanent migration from Windows(7).

I have installed a new 256GB SSD in my desktop and installed Windows and a few frequently used programs, I am using a HDD as a data disk for files that don't require the increase in speed a SSD provides.

I want to install Ubuntu as a secondary OS on the SSD but am not entirely of any specific requirements of doing so. Or how I would even go about it.

Any help would be greatly appreciated.

---

### Post by snowpine on 2012-12-04
Here are easy 1-2-3 instructions with screenshots:

[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)

---

### Post by darkod on 2012-12-04
That guide is detailed and includes images, but it has to be said that using the ubuntu installer to shrink the win7 partition can break windows sometimes. This is because it gets complicated if other tools are resizing its system partition.

If the win7 takes the whole ssd right now, decide how much space you want to allocate to ubuntu and use windows Disk Management to shrink the win7 partitions. Leave the newly created space as unallocated, don't create ntfs partition into it.
Reboot few times so win7 can do disk checks if it wants.

Only after that start the ubuntu installer and go on with the install.

Resizing win7 with the ubuntu installer doesn't give it opportunity to run the disk checks which can leave it broken.

---

### Post by Joe92w on 2012-12-04
Thanks both of you for the helpful comments, about to start the process now.

Are there any steps I should take after a successful installation of Ubuntu to increase SSD performance/life?

---

### Post by suny123 on 2012-12-04
I'm a noob for Ubuntu but I'd say in windows for speed the best thing to do is keep things clean, don't load it up with junk and every once an a while, maybe twice a year do a Disk Fragmentation.

I hope I helped somewhat, I just started on this site and I hope to go further, 

Nathan

---

### Post by Joe92w on 2012-12-04
Thanks for replying suny, however, to my knowledge SSDs don't require defragging and most thing's I've read advise against it as it can shorten SSD lifespan due to unnecessary disk writes.

The question was aimed more towards are there any tweaks that I should make in Ubuntu to get the best out of my SSD and not decrease it's lifespan. I'm sorry if i didn't make that clear with the original question.

---

### Post by oldfred on 2012-12-05
Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

    You still need discard for trim and noatime to reduce writes. You can also use ext4 but turn journal off. I think that was about all I actually did. If using any newer version of gparted you should have alignment or first partition starts at sector 2048 and all partition starts are divisible by 8.

 With SSD or Flash drives, Use ext4 without journal, change sda1 to your ext4 partition:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

---

