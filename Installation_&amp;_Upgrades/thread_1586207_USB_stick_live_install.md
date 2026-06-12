---
title: "USB stick live install"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by JordanT91 on 2010-10-01
Hi. I have a very limited knowledge of Linux and I need some help.
I want to install linux on my 16gb USB stick. To do this I have been using Linux Live USB.

I want it so that anything I change, such as updating drivers, adding programs, will still be there when I reboot, which a normal Live installation wouldn't do.

I know there is a thing called persistence, but apparently it can't be used for updating core files and drivers, and can't be more than 4gb, which means I won't be able to use all the spare space on my drive.

So, using Live USB I installed Ubuntu 10.4.1. But when I downloaded some updates it said there is no more drive space.

Is there a way to do what I'm proposing?

Thanks.

---

### Post by sikander3786 on 2010-10-01
You need a live USB or an Ubuntu CD for that plus the USB Drive you want to install Ubuntu to.

Plug in the USB you want to install Ubuntu onto and boot from the installation media (live USB or CD) and install as if you were installing to a hard disk. It will be better if you unplug the internal HDDs before proceeding to be on the safe side. If you can't, select your USB on the partitioning stage for installation and at the last stage just before installation begins, select Advanced and change the target location of GRUB to your USB Drive and you are done.

---

### Post by Chris1274 on 2010-10-01
I've installed 10.04 on a 4GB USB, but I did it from a live CD, so I don't know if it would also work from a live USB. In any case, what I did was remove the hard drive from my laptop, boot from the live CD, insert the target USB drive and then unmount it, then do the installation. The flash drive should show up in the installation manager.

It can be done without removing the HDD, but it's more complicated and I don't know how to do it.

---

### Post by JordanT91 on 2010-10-01
Ok I have a spare stick lying around so I'll give it a go. I'll post back in a bit with thanks or more questions...

---

### Post by JordanT91 on 2010-10-01
I'm at the stage where I'm choosing where to install, but I don't know which file system to use. I would guess fat32, am I right?

And what about the mount point? Is that / or /boot or what?

---

### Post by sikander3786 on 2010-10-01
If you don't want to custom partition, you can select your USB drive from the drop down menu near the top of the page and select "Use entire disk".

If you want to custom partition it, you need at least 2 partitions. 1 "/" partition, ext3/ext4, mount point /, and 1 swap partition formatted swap, mount point swap.

You can use the remaining space for data storage with either ext3 or ext4 fs.

---

